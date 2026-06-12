---
title: "Problem with Local file references from remote sites"
date: 2007-04-01
forum: General Help
---

### Post by curlydave200 on 2007-04-01
I have an issue with having local files load into a web page which is located on a remote server.  However, if the file is located on my local computer, there is no issue whatsoever.

The code which I used was
[HTML]
<HTML>
<HEAD>
<TITLE>test</TITLE>
<STYLE>
body {background-image: url("file:///home/dpg/gc/uc/bg.jpg");}
</STYLE>
</HEAD>
<BODY>
<P>This is a test.</P>
</BODY>
[/HTML]

Loaded on my computer, it loads the image as a background, as expected.  As soon as I try loading from my server, however, it just loads the text, with no background.  If anyone could tell me why it does this, or a way to get around it, that would be greatly appreciated.

---

