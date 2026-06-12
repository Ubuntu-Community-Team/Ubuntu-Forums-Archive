---
title: "Dual Boot - change default once only?"
date: 2007-08-11
forum: General Help
---

### Post by wombat20 on 2007-08-11
I'm dual booting with WinXP, but Ubuntu is my default OS from Grub (if I don't press anything). 90% of the time I'm using Ubuntu so I'd like to keep it like this.

What would be handy, however is if I could, say, click an icon which would edit my grub settings to make Windows XP the default, then after it has rebooted and been selected, it would automatically change it back to Ubuntu.

I've heard grub has some scripting options, so is this possible?  Has anyone tried it?

This would be very handy, so I could click the icon and walk away for a drink or whatever rather than hanging around to press ESC and so on.

Any ideas appreciated.  :)

---

### Post by kellemes on 2007-08-11
The only thing I can think of is you can make a bashscript that switches your /boot/grub/menu.lst
You make menu.tux and menu.xp and let the bashscript replace the current menu.lst with one of these versions.
And obviously make this script point-click from your environment.

---

### Post by wombat20 on 2007-08-11
Thanks, yeah, that's what I figured, but it's the changing it back that I'm not sure about...

---

### Post by Herman on 2007-08-11
kellemes suggestion seemed like the most correct answer.

An alternative would be to edit your /boot/grub/menu.lst file and in particular the line beginning with the **default** command.
In most menu.lst files there will be the number **0** after the **default** command.
That tells GRUB to boot the first entry (counting from **0**), entry in the menu.lst file. (Counting from the top down).

You can replace the number **0** there with the word **saved** if you like. Then GRUB will boot whichever operating system you booted last time.
That won't be exactly what you wanted, but you could try it and see if it does something near enough to what you want for a start.

Then, to take kellemes idea a step further, still with your /boot/grub/menu.lst's default command set to **saved**,  maybe you could make a bash script that runs grub-set-default, and writes the number for  your Windows entry to your /boot/grub/default file for a while.
```
[COLOR=Blue]#!/bin/sh[/COLOR]
sudo grub-set-default 4
```Where: Windows is the 5th entry (corresponding with the fifth instance of the command **title** in your menu.lst file, or the number 4 entry when you start counting from zero).


You could have another script that will run grub-set-default again, and revert your /boot/grub/default file to whichever number your Ubuntu entry would be, in most cases 0. 
```
[COLOR=Blue]#!/bin/sh[/COLOR]
sudo grub-set-default 0
```I have tested this already and it is working very well for me so far, but I never use Windows for anything except to test ideas like this.  

Regards, Herman :)

EDIT: You will need to **#** comment out your **savedefault** commands in each operating system's entry near the bottom of your /boot/grub/menu.lst file so those won't overwrite your settings in your /boot/grub/default file again if you want the settings to remain until next time you run sudo grub-set-default.

---

### Post by jeremy1138 on 2007-08-11
> **Herman said:**
> kellemes suggestion seemed like the most correct answer.

An alternative would be to edit your /boot/grub/menu.lst file and in particular the line beginning with the **default** command.
In most menu.lst files there will be the number **0** after the **default** command.
That tells GRUB to boot the first entry (counting from **0**), entry in the menu.lst file. (Counting from the top down).

You can replace the number **0** there with the word **saved** if you like. Then GRUB will boot whichever operating system you booted last time.
That won't be exactly what you wanted, but you could try it and see if it does something near enough to what you want for a start.

Then, to take kellemes idea a step further, still with your /boot/grub/menu.lst's default command set to **saved**,  maybe you could make a bash script that runs grub-set-default, and writes the number for  your Windows entry to your /boot/grub/default file for a while.
```
[COLOR=Blue]#!/bin/sh[/COLOR]
sudo grub-set-default 4
```Where: Windows is the 5th entry (corresponding with the fifth instance of the command **title** in your menu.lst file, or the number 4 entry when you start counting from zero).


You could have another script that will run grub-set-default again, and revert your /boot/grub/default file to whichever number your Ubuntu entry would be, in most cases 0. 
```
[COLOR=Blue]#!/bin/sh[/COLOR]
sudo grub-set-default 0
```

I have tested this already and it is working very well for me so far, but I never use Windows for anything except to test ideas like this.  

Regards, Herman :)

Thanks!  I'm really new to Linux and I've wanted to change the default os of my bootloader for a while...  Now I finally can!  I replaced the default  0 with default saved and all is well.  Thanks again!

---

### Post by Herman on 2007-08-12
Cool! :)

If you want to learn more tricks you can do with GRUB, just click on my third sig link and try out some of the ideas in there. 
Lots of us have fun customizing our GRUB menus as well as customizing Ubuntu itself. 
It's a good idea to have a [Super Grub Disk Disk]("http://geocities.com/supergrubdisk/") if you want to play with GRUB, just in case.

Enjoy!
Regards, Herman :)

---

### Post by kellemes on 2007-08-13
Found this today, maybe you can use it.

[http://www.dcheng.members.sonic.net/friends/jspaar/pub/bootnext/]("http://www.dcheng.members.sonic.net/friends/jspaar/pub/bootnext/")

---

### Post by sawjew on 2007-08-13
Check out Startup Manager from here [http://web.telia.com/%7Eu88005282/sum/index.html]("http://web.telia.com/%7Eu88005282/sum/index.html")

I've been using it for quite a while, you can just select which entry in grub you want to boot and you can even set it to boot the last used system.  This means that if you hit restart in Windows it will reboot into Windows and if you hit restart in Ubuntu it will reboot in Ubuntu.

You can also select your grub splash image and change your usplash theme.

Excellent tool, give it a go.

---

