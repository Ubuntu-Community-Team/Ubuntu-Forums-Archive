---
title: "I need some help"
date: 2007-04-29
forum: General Help
---

### Post by disco2000 on 2007-04-29
I have just burned my Ubuntu 7.04 Live CD and tried to load it onto my Dell Inspiron 6400 laptop only to get this message:

Quote:
"[116.592000] bcom43xx: Error : microcode 'bcm43xx_microcode 5.fw" not available or load failed. further along it tells me :

(EE) VESA (0): no matching modes.
(EE) Screens found but none have usable configuration.


What can I do? Can anyone help a first timer with Linux?

disco2000

---

### Post by m.musashi on 2007-04-29
Could you give a bit more info? When, exactly do you get this error? Have you already checked the CD for errors (one of the options)? Do you see the boot menu on the CD or does this happen before that?

---

### Post by disco2000 on 2007-04-29
yes I did check the cd for errors. The boot menu appears no problem and I start Ubuntu and then I get the message it cannot find the screen.

it also says: > log file: '/var/log/xorg.0.log'
Using config file :' etc/X11/xorg.conf'

---

### Post by m.musashi on 2007-04-29
You get this booting a live CD? That seems odd - especially on a Dell. I've always had great luck with Dell and Ubuntu.

To be honest, I have no idea what is going on. One guess is that it has to do with the graphics card but I don't know where to begin to fix it. Actually, you can't change much with a live CD. You might check your bios and see if something is going on there. It's not defaulting to an external monitor or LCD by chance. I know our Dells at work sometimes boot into a black screen because they are outputting to an LCD - even if one isn't connected or turned on. That just a wild guess though. Sorry.

---

### Post by BRAXS69 on 2007-04-29
have you tried using safe graphics mode? 
this is also odd to me also all my dells work... 
there is something you could try if the live cd crashes, do you get redirected to the shell? "its like DOS" then you might be able to reconfigure the x server yourself by entering the commands.

 "sudo dpkg-reconfigure xserver-xorg" go though the step by step.
"/etc/init.d/gdm start" do this when you think its all set up right.

and then it should work, then install and if it does it to the installation as well just repeat the same steps and it will save the settings if it didn't already.... 

you could also download the "alternative cd" though that would be a pain. 
good luck mate:)

---

### Post by disco2000 on 2007-04-29
I found this bug report:
[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/89853](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/89853)

It seems I am not the only one with that problem.I have a Dell Inspiron 6400 Core Duo with ATI Mobility Radeon x1400 card. Like lots of other users qith bugs.

Disco2000

---

### Post by jerrylamos on 2007-04-29
I had the "screens found but no usable...." on another computer some months ago.  A posting said to go into Bios and make sure the shared screen memory was as large as possible.  It had been 1024 kb and I bumped it to 8096 kb.  Then I could boot.  I hit the same thing on an older computer; the largest the Bios would set was 4096 kb, which was enough to boot.

Now the first had an Intel 83845G graphics chip which actually shares 65536 kb of memory to do the graphics, but the 8096 kb was enough to get me up.  Feisty came up in 1024x768.  I then did ctrl-alt-F1, sudo dpkg-reconfigure -phigh xserver-xorg which leads to some menus.  I knew that the graphics driver was i810 so I selected that.  My LCD screen supports 1280x1024 so I used that.  After the menus completed I did a sudo killall gdm and sudo startx to get going again.

Now if you're running CD Live you have to do the sudo dpkg-.... on every boot especially since "persistent" mode is broken on Feisty (but not Edgy or Dapper).  If you install you only have to do the sudo dpkg-... once.

Cheers, Jerry

---

