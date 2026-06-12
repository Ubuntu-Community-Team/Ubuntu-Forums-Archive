---
title: "With Firefox's '-save-to-folder' now broken, replacement is?"
date: 2014-03-13
forum: General Help
---

### Post by u2nTu on 2014-03-13
This command line option (-save-to-folder) was usable in a bash script to both download web pages and expand the javascript (outputting innerHTML) in one easy step:```
firefox http://www.awful-player.com -save-to-folder ~/myfile.txt
```No extra programs were needed (since Firefox comes standard).

Output was to a text file which could then be scraped. Example usage would be for websites that offer content in playlists, but have awful players; the scrape could be for links to content.

But this most recent update broke it, for Linux versions anyway (found [this post]("http://support.mozilla.org/en-US/questions/989471")). With documentation on this option being sparse to begin with, can it be that Mozilla has quietly killed it?

In any case, **a replacement is needed**. Ideally, it would be a single program that could be directly substituted for 'firefox' in scripts. The dead-ends I've run into while looking are:

[LIST]
[*]Use wget to grab the site text, insert a <base> tag and some JS to write the rendered page: Doesn't work because Firefox won't allow cross-site scripting, a security measure. 
[*]Try text-based browsers w3m and lynx: JS content is not expanded. 
[*]Create local file with [html5 import method]("http://www.html5rocks.com/en/tutorials/webcomponents/imports/"):  HTML5 is not yet fully supported by Firefox. 
[*]Combinations of javascript in a local file: Nothing that can write the rendered page's innerHTML to file. 
[/LIST]
 Installing a PHP server (php-cli) and scripting a local page would work, but that not only requires an extra step, it seems like cheating. :mrgreen:

So this simple task is not so easy to replicate. Any easy suggestions?

---

