---
title: "all KDE related programs will not run in gnome in edgy"
date: 2006-11-02
forum: General Help
---

### Post by cptjaben on 2006-11-02
I'm currently running gnome in Edgy. All my programs that are related to KDE, such as Kaffeine, amarok, kcalc, and k3b all will not run. In dapper and earlier this week in edgy the seemed to run fine, but now when I try to run any of them they simply do not start. does anyone know how i can make them run again.

---

### Post by TigerWolf on 2006-11-02
Have you tried running any of them from the console and seing what messages it outputs? This may be helpful in solving your problem.

---

### Post by cptjaben on 2006-11-02
When I try to run K3b in the terminal I get this message:

DCOP aborting call from 'anonymous-13094' to 'kded'
kded: ERROR: Communication problem with kded, it probably crashed.
DCOP aborting call from 'anonymous-13083' to 'k3b'
ERROR: Communication problem with k3b, it probably crashed.

When I try to run kaffeine in the terminal I get this message:

DCOP aborting call from 'anonymous-13219' to 'kded'
kded: ERROR: Communication problem with kded, it probably crashed.
DCOP aborting call from 'anonymous-13208' to 'kaffeine'
ERROR: Communication problem with kaffeine, it probably crashed.

When I try to run amarok in the terminal I get this message:

Floating point exception (core dumped)

Got any ideas?

---

### Post by kerry_s on 2006-11-02
It looks to me like kdeinit is not starting. try putting kdeinit in the startup programs, then log out and back in.

---

### Post by cptjaben on 2006-11-02
Amarok is the same.

when I run KAffeine I now get this message:

ERROR: Communication problem with kaffeine, it probably crashed.


When I run k3b I now get this message:

ERROR: Communication problem with k3b, it probably crashed.


Any Ideas?

---

### Post by kerry_s on 2006-11-02
Try renaming the hidden .kde folder to .kde.old, then log out and back in. This will create a new .kde folder with the default/stock settings.

---

### Post by cptjaben on 2006-11-02
Where do I find this .kde folder?

---

### Post by d3v1ant_0n3 on 2006-11-02
should be in your user folder (/home/<yourusername>)

It's a hidden folder, so you'll have to show hidden folders. IN Nautilus it's View>Show hidden files

---

### Post by cptjaben on 2006-11-02
When I try to run the 3 programs I get the same message for all 3 of them. In addition I've tried uninstalling and re-installing all of them which seems to have no effect.

---

### Post by caldevil on 2006-11-02
Do you have KDE installed? If yes then can you just log in to KDe then logout?

---

### Post by cptjaben on 2006-11-02
no, I only have gnome

---

### Post by Archmage on 2006-11-03
> **kerry_s said:**
> Try renaming the hidden .kde folder to .kde.old, then log out and back in. This will create a new .kde folder with the default/stock settings.

Easiest way to do this would be

ALT+F2
mv .kde .kde-old

---

### Post by cptjaben on 2006-11-03
I Was able to move them, but it had no effect on the programs when i restarted my computer and tried to run them.

---

### Post by jbs99999 on 2006-11-18
Are you using flgrx?  If so set your driver back to ati and restart X.  This worked for me.

---

### Post by karmaflimmern on 2006-11-21
hy guys,

i have this problem, since i choose to use the unstable version of debian ca. one year ago. this problem occurs in the testing section of debian since xorg7 was put into. ca half year. i also use elive..same problem. and now here in ubuntu. the error is related to all kde programms in debian based distros. first i thought it must have something to do with the fglrx driver and dualscreen setup. in moment i run an ubuntu edgy with mesa and i have the same problem when i use dualscreen. this problem doesn't occur after an fresh install. only if you update/install the packages with kde support.
you can also forget all that other error messages, it has definitely something to do with that line

   Floating point exception (core dumped)

i think it would be the best way to write down, which programs are affected by that error and take a look at the dependencies! i think that there is a bug in a kde lib that affects the dualscreen setup!

my crashin' programs are:

   opera
   skype
   kaffine
   amarok
   k3b

i hope, that the new fglrx 8.31 driver will fix that problem, cause it's also for xorg7! 

sorry for the bad language, i'm no native speaker...

---

### Post by karmaflimmern on 2006-11-21
hi me again,

i have did some testings and can say. it must be the dualscreen setup. is there someone out there with that problem and no dualscreen? i will now test the new fglrx 8.31 driver(if it compiles)

---

### Post by jbs99999 on 2006-11-21
I was not using Dual Screen in fglrx, and still had the problem.  I'm using a Xpress 200g (RS485) chipset. ](*,)

---

### Post by gcote on 2006-11-22
I have the same problem. Any KDE app I tried to launch via the terminal gave me the Floating Point Exception message. My graphic card is an ATI 1800 and I used the latest drivers from ATI web site. 

Finally, I restored my xorg.conf in order to use the default "vesa" and it started working. Except that the performance of the vesa driver is so low that it is unusable. 

I had a NVidia 6600 PCIe card lying around which I installed. After many hours of headaches because of the drivers not working in dual-head mode, I finally have it working and I can use KDevelop and other KDE apps.

---

### Post by cornlegend on 2006-11-24
It's not just KDE apps that have this conflict between fglrx/Xorg7.  I have the same problem with anything using the xine-lib. ](*,) 

That really stinks, because I want the hardware 3D acceleration for OpenGL and DirectX games in WINE. :evil:

---

### Post by cornlegend on 2006-11-25
After some digging around on Google, I found a workaround for the problem while still being able to use the ATi accelerated fglrx driver.

Check this link:

[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=384325;msg=47](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=384325;msg=47)

It's due to the dpi/size of the screen not being set, and a bug report has been filed for the Debian packages.  If patches are accepted, hopefully we'll see a more permanent fix downstream. :-D

---

