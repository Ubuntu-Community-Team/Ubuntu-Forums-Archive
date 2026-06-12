---
title: "Script to split HTML files"
date: 2015-08-05
forum: General Help
---

### Post by dwlamb on 2015-08-05
I am working on utf-8 xhtml files to split into epub's.  Using a particular <hr> tag those tags  serve to act as split markers so content can be divided in chapters.  Is there a method using bash or can any point me in the direction of a  script (bash, python, perl, sed, etc.)_ that will start and stop reading lines based on the occurrence of a string?


If you are familiar with Sigil, you may know of the functionality with the tag ```
<hr class="sigil_split_marker" />
```. Once commanded, with a tag of that hr class in place, the software will split a  file into two, wrapping it in the appropriate code.


So far, I can only envision such a function using Python.  I am not yet very adept at programming and am surveying if there is a solution before diving into creating something.


Please don't suggest to simply use Sigil.  I am exploring ways to make epubs without relying on Sigil, Jutoh or the editor within Calibre.

---

### Post by QDR06VV9 on 2015-08-05
Calibre supports the conversion of many input formats to many output formats [http://manual.calibre-ebook.com/faq.html](http://manual.calibre-ebook.com/faq.html)
So disregard the above if calibre is out?

And this page might also be helpful
[http://www.jedisaber.com/eBooks/editors.shtml](http://www.jedisaber.com/eBooks/editors.shtml)

I wish there were more that I knew of.
Regards

---

### Post by SeijiSensei on 2015-08-06
I don't know whether this will work, but you can give it a try:
```

awk -F'<hr class="sigil_split_marker" />' '{print $1}' < somefile.html > page1.html
awk -F'<hr class="sigil_split_marker" />' '{print $2}' < somefile.html > page2.html

```
The first line should write all the text from somefile.html up to the <hr ..> tag into page1.html.  The second command should put the text after the tag into page2.html.

---

