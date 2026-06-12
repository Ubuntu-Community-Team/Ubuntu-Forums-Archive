---
title: "Can I set Irfanview as my default photo application?"
date: 2017-04-04
forum: General Help
---

### Post by steve169 on 2017-04-04
I'm running Ubuntu 16.04.02 along with Windows 7 on a Dell desktop PC.

I've installed Irfanview 4.44 64-bit using WINE.

When I go to System Settings/Details/Default Applications, the choices I'm given for "Photos" are:

    Image viewer
    Wine Internet Explorer
    Wine Internet Explorer
    Firefox Web Browser
    Shotwell Viewer
    ImageMagick (Display Q16)
    ImageMagick (Display Q16)

Is there any way I can specify Irfanview as my default photos viewer?

---

### Post by Kris_M on 2017-04-05
Consider XnView.  I tried to get you a link but couldn't - just google it in the AM.  I, too, used to use and love Irfanview when I had windows.

---

### Post by mastablasta on 2017-04-05
[SIZE=2]xnviewv link: [http://www.xnview.com/en/xnviewmp/](http://www.xnview.com/en/xnviewmp/)

bu tthere are so many great picture viewers already in the software center.

depends what you needs. i use one of the ismpler ones so it loads fast when you need ot just view a picture.

[/SIZE]

---

### Post by ajgreeny on 2017-04-05
The closest thing I have found to irfanview is gthumb; it used to be even closer than it is now as, being a gnome application, the GUI for it has become typically "gnome" with some things not so obviously available and much harder, in my opinion to navigate.

I remember trying shotwell when it first became the gnome default picture application, and I could not get on with it at all, so started looking for alternatives; gthumb was the answer for me.

If you really want to use irfanview with wine you may have to choose to open the photo files using "custom command" from their own properties dialogue (from right click) or by copying whatever is the command to open irfanview in your dash or menus.  I am assuming you still get a "wine" menu section with all the applications installed using wine, but I have not used it for many years now so I'm not totally sure about this.

The command you need will, from memory, be something like ```
wine ".wine/drive_c/program files/irfanview/irfanview.exe"
``` but I'm not sure if it uses backslash or as I've shown it with forward slashes nor the exact pathway used any more.

---

