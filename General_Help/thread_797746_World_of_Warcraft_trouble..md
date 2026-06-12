---
title: "World of Warcraft trouble."
date: 2008-05-17
forum: General Help
---

### Post by 1omgz on 2008-05-17
Ok i type this in in terminal


 wine "C:\Program Files\World of warcraft\WoW.exe"


And for a second my screen turns black like its gonna work, than i just see my desktop but its really enlarged, and my comp freezes. I dont no what to do anymore.

Can anyone help?

---

### Post by 1omgz on 2008-05-17
Anyone???

---

### Post by 1omgz on 2008-05-17
i cant figure it out

---

### Post by johnl on 2008-05-17
What video card do you have?
What version of wine do you have?
Did you make any changes to the Config.wtf file in the WoW directory?

---

### Post by 1omgz on 2008-05-17
i have wine 0.9.9

i used the same video card when i played World of Warcraft on Windows, and it worked fine

And no, i did not make any changes to config.wtf


and im running ubunnu 6.06

---

### Post by liquidfunk on 2008-05-17
In more detail can you say what Graphics card you have. For example I have the Nvidia Geforce 8500GT. 

 Do you have the correct drivers installed for your card? 

 How about you try it in a window first and then try full screen, then if it crashes you can return.

 Type winecfg into the terminal and change the settings so that You have:

 Allow Window Manager to Decorate the windows - Selected

 Allow Window Manager to control the windows - Selected

 Then Emulate a virtual desktop - Selected and choose a resolution that is smaller than your screen. E.g. 1024 x 768 if your screen is 1280 x 1024 like mine.

 Also, there is no version of Wine called 0.9.9. It went 0.9.61 straight to 1.0.Rc-1.

 So type in Wine --version into a terminal and tell us what version you have.

 Those are my thoughts.

---

### Post by johnl on 2008-05-17
I'm more interested in if you have an Nvida card, ATI card, etc.  I have an Nvidia card on my desktop, which plays WoW much better than my laptop with ATI.

Heres how I setup WoW on my desktop (once it was installed):

winecfg

Under the 'Applications' tab, change the default windows version to Windows XP

open your Config.wtf file with a text editor : 
(assuming you installed to the default location)
gedit ~/.wine/drive_c/Program Files/World of Warcraft/WTF/Config.wtf

Make sure you have:
SET gxApi "opengl"

somewhere in the file.

Now trying running WoW as you did before.


You can find some additional tips & tricks here:

[https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)
[http://www.wowwiki.com/Linux/Wine](http://www.wowwiki.com/Linux/Wine)

---

### Post by 1omgz on 2008-05-17
Thx for the help, 

but when i type

 gedit ~/.wine/drive_c/Program Files/World of Warcraft/WTF/Config.wtf

I get


 (gedit:5210): Gtk-WARNING **: Locale not supported by C library.
        Using the fallback 'C' locale.

(gedit:5210): Gdk-WARNING **: locale not supported by C library

any idea why?  That is my location

---

### Post by johnl on 2008-05-17
Those warnings shouldn't affect your ability to edit the file.  The mistake is that the path has spaces in it, so gedit gets confused :)

Either open up gedit and then browse to that file (you might have to right click in the open file window and choose 'show hidden files' to find the .wine folder), or try:

gedit ~/.wine/drive_c/Program\ Files/World\ of\ Warcraft/WTF/Config.wtf

---

### Post by 1omgz on 2008-05-17
when i type 

gedit ~/.wine/drive_c/Program\ Files/World\ of\ Warcraft/WTF/Config.wtf

i get the same notifications, but a blank folder pops up called config.wtf

EDIT: Ok i found my wow folder but now when i click WTF in the wow folder, nothing is there... even after i click show hidden

Sorry for all these questions, but im new to ubuntu

---

### Post by 1omgz on 2008-05-17
I just got the WoW launcher to open, than when i clicked play, it crashed ): i made Some progress atleast

---

