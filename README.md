JageDown
========

[JageDown] [0] = [PageDown] [1] + [jQuery] [2]

JageDown modify file `Markdown.Editor.js`, so you can freedom use PageDown editor everywhere, easy as `$('textarea').jagedown();`, other functions still the same.

> PageDown is the version of Attacklab's Showdown and WMD as used on Stack Overflow and the other Stack Exchange sites.

> It includes a converter that turns Markdown into HTML, a Markdown editor with realtime preview of the generated HTML, and a few useful plugins, e.g. for sanitizing the generated HTML according to a whitelist of allowed tags.

> The Markdown converter can be used both in the browser (usually in conjunction with the editor, to display a real time preview), and on the server using Node.JS.

## Demo


## Installation

    ...
    <head>
    <link rel="stylesheet" type="text/css" href="demo.css" />
    <script type="text/javascript" src="https://ajax.googleapis.com/ajax/libs/jquery/1.7.2/jquery.min.js"></script>
    <script type="text/javascript" src="../../Markdown.Converter.js"></script>
    <script type="text/javascript" src="../../Markdown.Sanitizer.js"></script>
    <script type="text/javascript" src="../../Markdown.Editor.js"></script>
    <script>
    $("#jagedown").jagedown();
    </script>
    </head>
    ...
    <textarea id = "jagedown"></textarea>
    ...

## Advanced usage
    // advanced example
    var help = { handler: function() { alert("Do you need help?"); }}
    var options = {
        'delay': true,  // don't run editor now
        'help': help    // include help button
    }
    // jagedowns = [ jagedown1, jagedown2 ]
    // jagedown = { editor: MarkdownEditor, converter: MarkdownConverter, element: element }
    var jagedowns = $("#another-jagedown").jagedown(options);
    for(var i=0; i<jagedowns.length; i++) {
        var jagedown = jagedowns[i];
        converter = jagedown.converter;
        editor = jagedown.editor;
        converter.hooks.chain("preConversion", function(text) {
            return text.replace(/\b(a\w*)/gi, "*$1*");
        });
        converter.hooks.chain("plainLinkText", function(url) {
            return "This is a link to " + url.replace(/^https?:\/\//, "");
        });
        editor.run();
    }


[0]: http://olragon.com/jagedown
[1]: http://pagedown.googlecode.com
[2]: http://jquery.com