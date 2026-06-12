---
title: "beryl: No GLXFBConfig for Depth 32"
date: 2007-01-22
forum: General Help
---

### Post by thusi02 on 2007-01-22
Hello, 

I am using the beryl-manager and have installed all the latest patches etc suggested by the sites: 

[http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/AiGLX](http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/AiGLX)

Also followed: 
[http://www.ubuntuforums.org/showthread.php?t=263851&highlight=beryl+nvidia](http://www.ubuntuforums.org/showthread.php?t=263851&highlight=beryl+nvidia)

My Nvidia driver I have on ubuntu 6.10 edgy version is: 1.0-9746


I keep getting: 

beryl: GLXFBConfig for depth 32

Also I cannot open up new terminals or move any windows around. Can someone PLEASE help me. 

I have a Nvidia GeForce Go 7300. 

Any help would be appreciated. 

Thank you
Thusjanthan Kubendranathan

---

### Post by Stemp on 2007-01-22
Are you in 32 mode depth ? 

Check your file /etc/X11/xorg.conf and search for DefaultDepth in the "Screen" section.

If you are in 32 mode try to change it to 24.

---

### Post by nikloveland on 2007-02-07
I found the fix to this at [http://www.linuxquestions.org/questions/showthread.php?t=493176](http://www.linuxquestions.org/questions/showthread.php?t=493176)
I had to add these two lines to my xorg.conf file in the Screen section:

Option         "AddARGBGLXVisuals" "True"
Option         "DisableGLXRootClipping" "True" 

Now it works great.  GO Ubuntu!

---

### Post by Fbxrd on 2007-03-15
Yes it works!

---

### Post by Pronker on 2007-03-20
> **Stemp said:**
> Are you in 32 mode depth ? 

Check your file /etc/X11/xorg.conf and search for DefaultDepth in the "Screen" section.

If you are in 32 mode try to change it to 24.

I roughly had the same problem, though it didn't help me to add the "AddARGBGLXVisuals" option in xorg.conf. However, when I changed my default depth from 16 to 24 beryl jumped right out of the box and left me drooling... WOOAAH!

---

### Post by gronbaek on 2007-03-20
> **nikloveland said:**
> 
Option         "AddARGBGLXVisuals" "True"
Option         "DisableGLXRootClipping" "True" 


Yes, that also worked just fine for me.

---

### Post by shakma on 2007-03-22
thank you, nikloveland!  your first post helped me get beryl back working 100%.  Long live ubuntuforums!!!

---

### Post by SamRoth on 2007-04-22
Works great now, thanks so much!

---

### Post by gregsheu on 2007-04-22
> **nikloveland said:**
> I found the fix to this at [http://www.linuxquestions.org/questions/showthread.php?t=493176](http://www.linuxquestions.org/questions/showthread.php?t=493176)
I had to add these two lines to my xorg.conf file in the Screen section:

Option         "AddARGBGLXVisuals" "True"
Option         "DisableGLXRootClipping" "True" 

Now it works great.  GO Ubuntu!

This is great. It works on my GeForce 6200. Thanks!

---

### Post by Sfinx on 2007-04-24
I have the same problem only with a ATI Radeon X600..

I have XGL, Compiz and Beryl installed.... Or is this wrong.. I'm a newbie in Linux and i want to learn so please tell me how to get my windows back to normal when i start Beryl...

I also have 2 screen instead of 4... And i can only run on 1024x768 not higher can that be fixed also?

:( 

Thanks in forward

---

### Post by kentshultz on 2007-05-02
great fix, guys.  Those extra two lines in xorg.conf allowed me to apply emerald themes as well.

btw, running Beryl in Feisty with NVIDIA.

---

### Post by Hellion DarkLord on 2007-10-11
I too have the same problem and the same error:

beryl: No GLXFBConfig for depth 32
 

I have even tried writing my own for depth 32, but evidently I didn't write it in the right place or didn't write it correctly because I get the same error.


What is it going to take to get window decorations?   This is VERY annoying.  it must be something new because I've done this b4 with no problems.

Thanks for any help.

---

### Post by joker99 on 2007-11-15
It works great with nvidia drivers! Big thanks !!

---

