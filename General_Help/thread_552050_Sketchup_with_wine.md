---
title: "Sketchup with wine"
date: 2007-09-16
forum: General Help
---

### Post by jrharvey on 2007-09-16
I just wanted to say to all the architecture students out there that I got sketchup working under wine. It seems that most people gave up trying to figure this out. I am sooooo happy and I dont mean to spam the forums with this comment but I thought I would throw a pic up there to prove it.

[SIZE="3"]**[COLOR="Red"]EDIT 081126: Please visit the following link :[http://wiki.winehq.org/GoogleSketchup](http://wiki.winehq.org/GoogleSketchup)[/COLOR]**[/SIZE]

---

### Post by newman on 2007-09-16
I'm interested in getting Sketchup working in wine also.

---

### Post by jrharvey on 2007-09-16
well here is the pic

---

### Post by jrharvey on 2007-09-16
ok well there are a few things that you need to do. First is install opengl for windows with wine. Once you install sketchup you will notice that all the buttons are missing but if you dissable the window manager in wine then you will get them back. Oh ya and also put your toolbars away from the window. For some reason it doesnt like it when you layer windows.

---

### Post by jrharvey on 2007-09-16
OH YESSS and this is version 6.0

---

### Post by newman on 2007-09-16
It's not working for me.  Menu is all jacked up.

---

### Post by jrharvey on 2007-09-16
Ya, im not really sure what happened but when I rebooted skechup this morning it seems to have reverted back to the same thing. BUT!!!! the menu's still apear in fullness if you take them out of the window. Im not sure why this is but it is usable.

---

### Post by bouncingmolar on 2007-10-15
I found these instructions. I have no idea how to follow them. but maybe someone will find them useful [http://aksels.de/software.php#sketch](http://aksels.de/software.php#sketch)

---

### Post by seanf on 2007-11-07
> **jrharvey said:**
> ok well there are a few things that you need to do. First is install opengl for windows with wine.

How did you install OpenGL for Windows with wine?

---

### Post by arpad on 2007-11-07
If you've got Wine installed then dowload OpenGL for Windows from:

[http://berkelium.com/OpenGL/sgi-download.html](http://berkelium.com/OpenGL/sgi-download.html)

This link worked for me. 

[ftp://ftp.meer.net/pub/gold/sgi-opengl/opengl2.exe](ftp://ftp.meer.net/pub/gold/sgi-opengl/opengl2.exe)

---

### Post by bouncingmolar on 2007-11-15
does the 3d warehouse work?

---

### Post by ArtInvent on 2007-11-28
I have Sketchup 6.0.515 working pretty flawlessly for about a month in Wine 0.9.49 on Feisty. I have an NVidia 6200 and OpenGL is indicated in the Preferences dialog, saying it is GL Version 2.1.0 NVIDIA 96.31, GLU Version 1.3.  Hardware accel. and fast feedback are switched on. I have even downloaded online posted models from the 3D Warehouse, which would be one thing I would expect not to work. I'm pretty sure I never made an effort to install OpenGL separately. If you visit the AppDB at wine.org there is more info on overrides etc.

 I have not upgraded to Gutsy on my main machine because I have heard that a number of 3D apps may not work right. Feisty is working so well. On my older laptop Gutsy won't run Blender or Sketchup. (But that may well be the 4 year old weird ATI card which is always a problem.) If anyone can attest to Blender and Sketchup working well in Gutsy I may give it a go.

---

### Post by bouncingmolar on 2007-12-06
i can download objects from the 3d warehouse but I can't search for items by typing in the search field. Actually typing in any fields seems pretty useless.

---

### Post by originalsurfmex on 2007-12-14
ive downloaded wine 0.9.50 and with nothing extra sketchup is running allllmost perfectly!

only one major problem: the cursor always has a medium sized white box under it (about 3 times the size of the cursor) which makes it impossible to do detailed work.

any ideas on a workaround for the cursor problem??


gutsy
dual core centrino
ati radeon 9800
2 gig ram

---

### Post by bouncingmolar on 2007-12-16
yeh i fixed that problem by making sure wine was loading as winxp instead of win98.  My cursor square was black though, so I dunno if its the same problem. 

So you can type things in the sketchup warehouse and it gives you results? mine just says request invalid.

---

### Post by ThomThom on 2008-06-01
> **originalsurfmex said:**
> ive downloaded wine 0.9.50 and with nothing extra sketchup is running allllmost perfectly!

only one major problem: the cursor always has a medium sized white box under it (about 3 times the size of the cursor) which makes it impossible to do detailed work.

any ideas on a workaround for the cursor problem??


gutsy
dual core centrino
ati radeon 9800
2 gig ram

What ubuntu version?
I got Hardy. Just installed Wine and installed SketchUp. However, when I try ot launch SU nothing happens.

---

### Post by ThomThom on 2008-06-01
This time I got an error message:
> 
SketchUp was unable to initalize OpenGL!
Please make sure you have installed the correct drivers for your graphic card.

Error: ChoosePixelFormat failed


Currently I'm using the official ATI drivers in Ubuntu and running Desktop Effects. Could Desktop Effects be an issue?

---

### Post by Joeb454 on 2008-06-01
I think you'll be better off creating a new thread outside of the Archive for this - wine has come a long way since December :)

---

### Post by bapoumba on 2008-06-01
> **Joeb454 said:**
> I think you'll be better off creating a new thread outside of the Archive for this - wine has come a long way since December :)
+1. ThomThom, please give me a link, and I'll redirect this thread. Thanks.

---

### Post by ThomThom on 2008-06-01
Sorry. Didn't notice it was an archived thread. Came over it via google.
No need to create new thread for this issue. I just found out that v1.0RC3 fixed it. (RC2 actually according to the changelog.)

---

### Post by bapoumba on 2008-06-01
> **ThomThom said:**
> Sorry. Didn't notice it was an archived thread. Came over it via google.
No need to create new thread for this issue. I just found out that v1.0RC3 fixed it. (RC2 actually according to the changelog.)

Just fine. As the issue is solved with current version, I'm closing here. Please PM me if there is any good reason to reopen, thanks.

---

### Post by bapoumba on 2008-11-26
> **jrharvey said:**
> I just wanted to say to all the architecture students out there that I got sketchup working under wine. It seems that most people gave up trying to figure this out. I am sooooo happy and I dont mean to spam the forums with this comment but I thought I would throw a pic up there to prove it.

[SIZE="3"]**[COLOR="Red"]EDIT 081126: Please visit the following link :[http://wiki.winehq.org/GoogleSketchup](http://wiki.winehq.org/GoogleSketchup)[/COLOR]**[/SIZE]

---

