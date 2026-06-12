---
title: "Startx  error? Need help  asap"
date: 2007-03-01
forum: General Help
---

### Post by dustin0 on 2007-03-01
Hello first post here, hope  people people around here can help me. I install ubuntu like a week ago, im still getting use to it. But today i install Beryl (i think it is) and when i rebooted  my computer I got errors. Ill post pictures in the  order i took them.

This is the error i get when i try to boot up on my slow machine
Big Picture:[http://www.dustin0.net/ubuntu/firsterror.jpg]("http://www.dustin0.net/ubuntu/firsterror.jpg")
[IMG]http://img59.imageshack.us/img59/2976/firsterrortj6.jpg[/IMG]

Here is the GUI  of Ubuntu starting up
Big picture:[http://www.dustin0.net/ubuntu/guiubuntu.jpg]("http://www.dustin0.net/ubuntu/guiubuntu.jpg")

[IMG]http://img231.imageshack.us/img231/2131/guiubuntuyq3.jpg[/IMG]

I had some other junk here but  i forgot to  take pictures, next   error i got
Big Picture[http://www.dustin0.net/ubuntu/disable.jpg]("http://www.dustin0.net/ubuntu/disable.jpg")

[IMG]http://img65.imageshack.us/img65/1386/disableev6.jpg[/IMG]

I get this when I click okay
Big Picture: [http://www.dustin0.net/ubuntu/bigerror1.jpg]("http://www.dustin0.net/ubuntu/bigerror1.jpg")
[IMG]http://img68.imageshack.us/img68/9750/bigerror1ft6.jpg[/IMG]

Then after i click okay from  the Big error thingy I get this blank screen  
Big Picture:[http://www.dustin0.net/ubuntu/blankscreenend.jpg]("http://www.dustin0.net/ubuntu/blankscreenend.jpg")
[IMG]http://img68.imageshack.us/img68/2624/blankscreenendnp8.jpg[/IMG]

I really dont want to reinstall ubuntu i had some  pictures and programs on there that i  need.  So help asap. And :P i have homework i gota type up  so the faster u help the faster i get my education for  today *cough* just thought i'd add that  :) :) 

 - Dustin

---

### Post by CocoAUS on 2007-03-01
We're gonna need a bit more information than that.  However, for now, try ```
sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf
``` and see if that fixes it...assuming you used a script or that you backed up your X configuration file before mucking with it (which you should ALWAYS do).  You can do this, possibly, by booting into safe graphics mode (a boot option...hit ESC at the GRUB timer).  If that doesn't work, you can let X fail, wait a minute, and then tell it OK.  This should (even though sometimes it doesn't) kick you into a terminal-like interface that asks you to login.  You can run commands from there.

You can also try using "dpkg-reconfigure xserver-xorg" at the command line if you didn't make a copy of your xorg.conf or use a script that did.

---

### Post by dustin0 on 2007-03-01
where can i type that command in? I have no  real place to put it.  The   first screen  has no sudo command. Ive tried recovery  mode. But it stops after Accessing Root Files
So    any ideas :)
 Thanks for the fast  reply

*Edit*
Im on a live CD but i can get to my Ubuntu Hardrive from here so if that helps any

---

### Post by Maestro23 on 2007-03-01
Do you get a screen with a command prompt before the screen in that first pic?

---

### Post by dustin0 on 2007-03-01
No  the first period was taken on my old machine when i    let it start up thats the error i get

When i plug the hardrive into this machine it   goes start to  the errors and yeah
In the hardrive there is a file called  "xorg.conf.original-0"  could  that help any?

---

### Post by CocoAUS on 2007-03-01
To get into the terminal:

When GRUB boots, hit ESC to enter the menu, then hit "e" to edit the line.  Add 3 to the end of it, then boot from there.  Doing so will boot you right into a command line where you can perform commands from.

---

### Post by jocko on 2007-03-01
When x fails and you are kicked back to a console, you should be able to type commands. If not, maybe you need to switch to another virtual terminal (try pressing Alt + F1 (or F2,3,4,5,6)).

Edit: Try copying any xorg.conf backups you may have:
```
 cd /etc/X11/ #or wherever you have mounted it if you run from a live session.
sudo mv xorg.conf xorg.conf.broken
sudo cp xorg.conf.original-0 xorg.conf
```
Reboot (if you run from a live cd).
Or if you booted from the hard drive:
```
sudo killall gdm
sudo gdm
```

---

### Post by dustin0 on 2007-03-01
> **CocoAUS said:**
> To get into the terminal:

When GRUB boots, hit ESC to enter the menu, then hit "e" to edit the line.  Add 3 to the end of it, then boot from there.  Doing so will boot you right into a command line where you can perform commands from.

When i get the Grub menu i push esc and then E and it   brings me to stuff like Root... and other crap. What do i do after that?

---

### Post by CocoAUS on 2007-03-01
Yeah, the original file should work just fine.  If there's a .backup file, that would probably be best, but if not, the command is just ```
sudo cp /etc/X11/xorg.conf.original-0 /etc/X11/xorg.conf
```

What we would need to troubleshoot this is 1) a full readout of what the blue screen tells you (this will explain why X failed to load) and 2) exactly what you did to try to install Beryl.  You might have forgotten to install a driver, or maybe your modules don't match your kernel version, etc.

It "brings [you] to stuff like Root"?  It should let you just edit the boot line...

---

### Post by dustin0 on 2007-03-01
> **CocoAUS said:**
> Yeah, the original file should work just fine.  If there's a .backup file, that would probably be best, but if not, the command is just ```
sudo cp /etc/X11/xorg.conf.original-0 /etc/X11/xorg.conf
```

What we would need to troubleshoot this is 1) a full readout of what the blue screen tells you (this will explain why X failed to load) and 2) exactly what you did to try to install Beryl.  You might have forgotten to install a driver, or maybe your modules don't match your kernel version, etc.

It "brings [you] to stuff like Root"?  It should let you just edit the boot line...

I get in this order

Root(hd0,1)
Kernel
Intrd
quiet
savedefault
boot

I tried to change the "1" to a "3" but it didnt save it

Well i cant give u a read  out... bc im not typing up        all of that :P would take me  days

---

### Post by CocoAUS on 2007-03-01
I'm gonna try rebooting and see why it's not giving you the right options.

If you can't get into a terminal, you can boot the LiveCD, mount your harddrive, then copy the xorg.conf file over that way.  You might just try that instead...it'll work just as well.

---

### Post by CocoAUS on 2007-03-01
Ok, sorry, I was making this complicated.

Just hit ESC at the Grub timer screen, then select the first recovery mode option.  This will boot you into a command line, probably as root.  You can enter your commands from there.

---

### Post by dustin0 on 2007-03-01
Got it working Thanks

---

