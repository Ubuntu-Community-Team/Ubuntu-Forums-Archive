---
title: "Help wanted with customising the markdown panel in gedit"
date: 2013-07-19
forum: General Help
---

### Post by vasa1 on 2013-07-19
I have gedit 3.6.2 and I've installed a plugin ([gedit-markdown: support for Markdown language in gedit]("http://www.jpfleury.net/en/software/gedit-markdown.php")) that allows me to preview markdown text as html in a separate panel within gedit.

I want to know if it's possible to change the background color of the lower panel from white to something else like #999. My guess is that I may need to edit some css in my theme.  I'm using Greybird (from "shimmer-themes" in the Software Center).

For the upper (main) panel, I use a slightly modified Cobalt color scheme.

---

### Post by vasa1 on 2013-07-30
I can get what I want by including:
```
<link rel="stylesheet" type="text/css" href="file:///home/vasa1/mkd.css">
``` at the top of each markdown file where mkd.css contains the style I wish to apply to the html preview. However, this requires editing each of my existing markdown files.

I'm hoping there's a way to do this by modifying the plug-in itself so as to avoid adding this code to each markdown file but that seems to require knowledge of Python :(

---

### Post by vasa1 on 2013-08-02
By way of a "bump", the image shows how markdown (right) is displayed as html (left).

I looked at~/.local/share/gedit/plugins/markdown-preview/__init__.py for any changes a non-Python, non-coder person can make easily. The closest thing I can think of is:
```

# Can be used to add default HTML code (e.g. default header section with CSS).
htmlTemplate = "%s"
``` lines 39 and 40 in the link over here: [http://paste.ubuntu.com/5938766/](http://paste.ubuntu.com/5938766/)
but I don't know how to proceed, if that is indeed what has to be changed.

---

### Post by vasa1 on 2013-08-03
Got the answer here: [http://stackoverflow.com/a/18026416/1771119](http://stackoverflow.com/a/18026416/1771119)

---

