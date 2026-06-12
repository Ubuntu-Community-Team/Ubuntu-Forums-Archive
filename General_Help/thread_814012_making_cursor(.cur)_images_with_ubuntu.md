---
title: "making cursor(.cur) images with ubuntu"
date: 2008-05-31
forum: General Help
---

### Post by zizzdude on 2008-05-31
is there a program in linux (ubuntu/debian more preferred) that can design cursor images? I tried gimp, but it doesnt work.

thanks. :)

---

### Post by NilsE on 2008-05-31
I assume you are looking to create Windows cursors and if so I am not sure what to recommend.  There are however programs (free) in windows to convert .png images to .cur and .ani images.

If you are thinking of cursors for Ubuntu then they use .png files run through xcursorgen to create the actual cursors

---

### Post by zizzdude on 2008-06-01
> **NilsE said:**
> I assume you are looking to create Windows cursors and if so I am not sure what to recommend.  There are however programs (free) in windows to convert .png images to .cur and .ani images.

If you are thinking of cursors for Ubuntu then they use .png files run through xcursorgen to create the actual cursors

well, its really for css stuff. it wont take any other image file besides .cur files.

---

### Post by simon_w on 2009-01-08
I guess this is a bit late for zizzdude, but in case it helps anyone else, the solution you're looking for is this:

1) creat your image in png format
2) convert the image using icotool from the icoutils package (# apt-get install icoutils)

Have fun!

Simon
:))

---

### Post by phoenixstormcrow on 2011-04-10
I made a .png file with gimp, then at the command line I did 

$ mv path/cursorname.png path/cursorname.cur 

and it loaded fine on the html page I'm building.  What I can't get quite right is how to handle transparency.  If anyone can give me a tip, I'd appreciate it.

---

