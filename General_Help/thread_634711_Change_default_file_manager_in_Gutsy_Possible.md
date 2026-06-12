---
title: "Change default file manager in Gutsy? Possible?"
date: 2007-12-08
forum: General Help
---

### Post by immolat3 on 2007-12-08
Hey there, I am using 64bit Gutsy (7.10) at the moment, and on my laptop I have a different distro of linux that uses Thunar for file management, and I really prefer Thunar's lightweight feel over Nautilus, is there a way to change the default file manager in Gutsy without messing a lot of stuff up?

Sorry if this is a newb question, still sorta new to Ubuntu and such. :P

---

### Post by -grubby on 2007-12-08
right click on a folder and select "properties", tab over to "open with" and you can click "add" and add thunar in the list and then just click on the circle next to "thunar" and you're good to go

---

### Post by amadeus266 on 2007-12-08
> **nathangrubb said:**
> right click on a folder and select "properties", tab over to "open with" and you can click "add" and add thunar in the list and then just click on the circle next to "thunar" and you're good to go

You'll need to install thunar first. Just in case that wasn't obvious.

---

### Post by immolat3 on 2007-12-08
now does that change how nautilus is usually running in the background taking up some of my memory? or is that a whole different ballgame?


thanks, btw!

---

### Post by immolat3 on 2007-12-08
im guessing since i have no folders open and nautilus is running and taking up 50mb of RAM i need to switch something elsewhere?

---

### Post by michaelzap on 2007-12-08
See this link: [http://tenjinonline.blogspot.com/2007/03/thanks-to-psychocats-site-i-have-dumped.html](http://tenjinonline.blogspot.com/2007/03/thanks-to-psychocats-site-i-have-dumped.html)

---

### Post by immolat3 on 2007-12-08
ill check that out, thanks

---

### Post by az_s_za on 2007-12-11
> right click on a folder and select "properties", tab over to "open with" and you can click "add" and add thunar in the list and then just click on the circle next to "thunar" and you're good to go
this doesn't work.  It will not let me select any other program to open the folder with.

> See this link: [http://tenjinonline.blogspot.com/200...ve-dumped.html](http://tenjinonline.blogspot.com/200...ve-dumped.html)
The instructions here work for opening folders from the Ubuntu places menu, but folders on my desktop are still opened with the Gnome file-manager.

Does anyone know how we can open folders directly from the desktop with other than the default file manger?

---

### Post by xlinuks on 2007-12-11
Just wanna second your problem, I have exactly the same issue..

---

### Post by uberMongo on 2007-12-13
same here

---

### Post by shafin on 2007-12-25
I've found this in the net,maybe this will help you:
> [SIZE=3][COLOR=Black]Check this out everyone: A better way to replace Nautilus with Thunar. (I did today after being tired of using Nautilus for three years)
BTW, this was done on Ubuntu Feisty but should work with any GNOME based distro.

1)  Make sure that Nautilus doesn't respawn when you kill it.  Goto Sessions applet and set it to normal.

2)  Kill Nautilus.  (the fun part!)

3)  Install Thunar and xfdesktop

What these apps will handle is self explanatory.

4)  Make sure you remove Thunar from starting in you GNOME session in the Sessions applet.

5)  Add xfdesktop to your sessions.  Set it to respawn if it dies.

6)  Enjoy yourself!

This way xfdesktop handles the desktop and it automatically uses Thunar for the file manager. [/COLOR][/SIZE]

got it from a comment in [here]("http://linuxondesktop.blogspot.com/2007/03/thunar-versatile-and-impressive.html")

---

### Post by az_s_za on 2007-12-27
This works well, and I even like some of the opions the xfdesktop gives me other than thunar, but how do I make these settings persist after a logout.

At the moment, if I logout or shutdown, when I restart, the xfdesktop starts up but is quickly replaced by Nautilus and the default desktop.

The only way I can stop this happening is to select the option "automatically remember running applications when logging out" from the session manager. 

Any ideas?

---

### Post by zvacet on 2007-12-27
Maybe you can try [this](http://www.psychocats.net/ubuntu/nonautilusplease).

---

### Post by az_s_za on 2007-12-27
> **zvacet said:**
> Maybe you can try [this](http://www.psychocats.net/ubuntu/nonautilusplease).
Thanks, that seemed to work, although I don't know if it was that or something else I did as I had already used that script.

There is just one thing that I still need Nautilus for... how do I graphically connect to another computer using ssh without using Nautilus?

---

### Post by cegpope on 2008-01-07
> **zvacet said:**
> Maybe you can try [this](http://www.psychocats.net/ubuntu/nonautilusplease).

I've tried this three times now and I can not convince gnome to use thunar over nautilus, trying to browse a folder still opens nautilus instead.  (gutsy)

---

### Post by az_s_za on 2008-01-10
How do you open the folder?  
If you use a keyboard shortcut for "home" for example, you'll get Nautilus.

---

### Post by cegpope on 2008-01-10
I get nautilus unless I go to applications > accessories > thunar any other method of opening a browser opens nautilus.

---

### Post by az_s_za on 2008-01-15
You could also give the instructions in shafin's post a try, that has worked for me, but I had to run the script again after doing that.

---

