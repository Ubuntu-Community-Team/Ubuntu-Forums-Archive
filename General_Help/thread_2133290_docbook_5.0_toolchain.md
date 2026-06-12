---
title: "docbook 5.0 toolchain"
date: 2013-04-07
forum: General Help
---

### Post by rplantz on 2013-04-07
Edit: I first called this a "workflow" but I think "toolchain" is better.

I am having trouble getting a good docbook toolchain. I am okay writing in xml, but none of the xsl processors seem to work completely. I have tried xsltproc, saxon, and xalan, all on Ubuntu 12.10. Each seems to almost work, but not completely.

For example, when I try to make the examples that are installed with saxon, following the instructions in the README.Debian file that comes with the installation, I get:
```

~/saxon-examples$ make DESTFILE=./tmp
[ -d . ] || mkdir -p .
uudecode -o /dev/stdout < openlogo.png.uu > ./openlogo.png
[ -d . ] || mkdir -p .
xsltproc --xinclude --nonet -o ./saxon.ext.001.noext.html \
	         --param use.extensions 0 \
	         db2html.xsl saxon.ext.001.xml
Cannot insert mycode.c. Check use.extensions and textinsert.extension parameters.
make: *** [saxon.ext.001.noext.html] Error 10

```
When the included example will not work out of the box, it makes learning more difficult.

I am writing a programming book, so I need to include external files that are source code for programs. I got xsltproc working well enough to do the includes, but from what I've read, line numbering is not a feature of xsltproc.

I've done a lot of searching, but nearly all of what I've found is very out of date.

I have written a similar book in LaTeX, so I'm comfortable using a complex markup language. However, LaTeX does not have a reasonable path to html/epub, which I want for this second book. I've played with pandoc, but it seems fairly limited for my needs.

Overall, docbook seems like the best solution for me -- if I can get it to work properly. What I'm looking for is up-to-date documentation that tells how to set up a good toolchain.

---

