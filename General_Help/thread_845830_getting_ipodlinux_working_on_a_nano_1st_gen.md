---
title: "getting ipodlinux working on a nano 1st gen"
date: 2008-07-01
forum: General Help
---

### Post by |{urse on 2008-07-01
Okay, I'm about to pull someone's hair out. lol I traded up my nano 3rd gen for a friends nano 1st gen for the simple fact that i would be able to use it on linux (without the crappy extra encryption layer the 3rd gen has) So all that works flawlessly with gtkpod (so not a total loss). 

So now taht everything works, I decide to try ipodlinux. I used this howto 

[http://mikesubuntu.blogspot.com/2007/09/how-to-install-ipodlinux-on-your-ipod.html](http://mikesubuntu.blogspot.com/2007/09/how-to-install-ipodlinux-on-your-ipod.html)

the installer seemed to run through perfectly, and restarted my ipod to a snazzy blue-screen with 4 options 1. Apple Os 2. IpodLinux 3. Disk mode 4. Sleep. So i select IpodLinux and linux starts to load then hangs on this

> Kernel Panic: VFS: unable to mount root fs on 03:02

now 03:02 would be hda2 if I'm not mistaken. 

Anyone have a solution for this, or has experienced this problem? Thanks for any help.

---

### Post by |{urse on 2008-07-01
By the way I fixed this. The kernel in ipodlinux's installer is too new for the 1g. So installing ZeroSlacker was actually easier, and works awesome. It comes with iBoy (gboy emu) and Idoom and a bunch of other emu's games and features. 

[http://sourceforge.net/projects/zeroslackr/](http://sourceforge.net/projects/zeroslackr/) <-- get it here.

make a working directory 

> mkdir zeroslackr && cp ZeroSlackr-stable-snapshot-2008-04-28.7z /zeroslackr && cd zeroslacker

it's in .7z format so you'll need this

> sudo apt-get install p7zip-full 

extract it with this

> 7z x ZeroSlackr-stable-snapshot-2008-04-28.7z

make it executable

> chmod +x patcher

run it (make sure your ipod is connected and mounted of course)

> sudo sh patcher

now copy and paste the entire contents of the zeroslackr folder to your ipod's root directory.

reboot your ipod by holding down the menu and middle button for 5 seconds.
Select ZeroSlacker from the menu and you should be running linux on your ipod ^^ note: this will not work with the nano 3g, don't bother trying (like i did)

If anyone needs a .deb for mvpdmake (to generate 1st gen nano viewable movies from .mpg .avi and .mp4) let me know and i'll find you the link.

---

### Post by Shigoki-linux on 2010-03-27
uh, yeah. i used alien to make a .deb of mvpdmake, but i cant find the program. idk if this is because of alien of what. i am using 9.10 Karmic.

---

### Post by |{urse on 2010-04-21
Check google for a program called smoovepod. It makes mvpd's easily.

---

### Post by |{urse on 2010-04-21
Just an fyi on that program, you'll need to run it under wine. Or perhaps some nice person will see this and write a linux version.

---

