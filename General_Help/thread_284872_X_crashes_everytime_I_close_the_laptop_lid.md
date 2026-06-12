---
title: "X crashes everytime I close the laptop lid"
date: 2006-10-26
forum: General Help
---

### Post by line72 on 2006-10-26
I have a Dell Precision M50 laptop and have recently upgraded from Dapper to Edgy (I did a fresh install), and now everytime I close my laptop lid, X Crashes with the following backtrace:

```

ProcXCloseDevice to close or not ?

Backtrace:
0: /usr/X11R6/bin/X(xf86SigHandler+0x81) [0x80c3971]
1: [0xffffe420]
2: /lib/tls/i686/cmov/libc.so.6(__strtoul_internal+0x3f) [0xb7da47df]
3: /usr/X11R6/bin/X [0x80e5a27]
4: /usr/X11R6/bin/X(xf86HandlePMEvents+0x3b) [0x80d264b]
5: /usr/X11R6/bin/X(xf86Wakeup+0x153) [0x80c4e23]
6: /usr/X11R6/bin/X(WakeupHandler+0x59) [0x808a5c9]
7: /usr/X11R6/bin/X(WaitForSomething+0x1b9) [0x8194489]
8: /usr/X11R6/bin/X(Dispatch+0x82) [0x8086832]
9: /usr/X11R6/bin/X(main+0x485) [0x806e715]
10: /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xdc) [0xb7d8c8cc]
11: /usr/X11R6/bin/X(FontFileCompleteXLFD+0xa1) [0x806da51]

Fatal server error:
Caught signal 11.  Server aborting

```

This crash happens with both the proprietary nvidia driver, and the opensource nv driver.  However, if I use the vesa driver, everything is ok.  Thanks in advance.

/Mark

---

### Post by Monstertje on 2006-10-26
Ive got a similiar problem

both open nv and Nvidia drivers crash when i close the lid of my:
Dell latitude c840

Also how can i check the backtrace... i will post it to further evaluate the problem8)

edit:

I'm running Ubuntu Edgy Eft! 6.10 
with Xgl and Beryl 0.1.1

It crashes with Gnome/Metacity as well

---

### Post by line72 on 2006-10-26
After a crash, take a look at the end of /var/log/Xorg.0.log.old.  I saw a post somewhere else that recommeneded turning off the bootsplash stuff, which I did and still have the same problems

---

### Post by Monstertje on 2006-10-27
```

ProcXCloseDevice to close or not ?

Backtrace:
0: /usr/X11R6/bin/X(xf86SigHandler+0x81) [0x80c3971]
1: [0xffffe420]
2: /lib/tls/i686/cmov/libc.so.6(__strtoul_internal+0x3f) [0xb7da47df]
3: /usr/X11R6/bin/X [0x80e5a27]
4: /usr/X11R6/bin/X(xf86HandlePMEvents+0x3b) [0x80d2]64b]
5: /usr/X11R6/bin/X(xf86Wakeup+0x153) [0x80c4e23]
6: /usr/X11R6/bin/X(WakeupHandler+0x59) [0x808a5c9]
7: /usr/X11R6/bin/X(WaitForSomething+0x1b9) [0x8194489]
8: /usr/X11R6/bin/X(Dispatch+0x82) [0x8086832]
9: /usr/X11R6/bin/X(main+0x485) [0x806e715]
10: /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xdc) [0xb7d8c8cc]
11: /usr/X11R6/bin/X(FontFileCompleteXLFD+0xa1) [0x806da51]

Fatal server error:
Caught signal 11.  Server aborting

```

as you can see it is 100% the same as yours....:confused:

---

### Post by line72 on 2006-10-27
I found this:

[http://www.linuxforums.org/forum/linux-laptops/58492-dell-c610-display-close-crashes-x-org.html](http://www.linuxforums.org/forum/linux-laptops/58492-dell-c610-display-close-crashes-x-org.html)

but it doesn't seem to work for me.

---

### Post by nilssss on 2006-11-04
I've got a related problem since upgrading from Dapper to Edgy on a Amilo M7405 laptop. Initially, X starts fine, however, after killing X and trying to start it again, it fails with a backtrace very similar to the ones listed above:

```
(EE) I810(0): unknown reason for exception
(EE) I810(0): cannot continue
(EE) I810(0): VBE initialization failed.

Backtrace:
0: X(xf86SigHandler+0x81) [0x80c3971]
1: [0xffffe420]
2: X(InitOutput+0x9c2) [0x809ff12]
3: X(main+0x276) [0x806e506]
4: /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xdc) [0xb7dc18cc]
5: X(FontFileCompleteXLFD+0xa1) [0x806da51]

Fatal server error:
Caught signal 11.  Server aborting
```

The only way to get X back I found so far is rebooting.

I'd think, the problem with closing the laptop lid is just a special case of that problem, as (judging from the traces) X tries to restart after opening the lid again. 

I'm using the i810 driver.

---

### Post by blink on 2006-11-04
I've had a similar problem and I have a solution.
Hopefully it works for you too.

X is listening to acpi events and crashes while processing it. You can tell X not to listen to acpi in 6.10 edgy by editing /etc/X11/gdm/gdm.conf if you're using gdm.

In there I adjusted the command line to add "-noacpi". So the section now reads:

```

# Definition of the standard X server.
[server-Standard]
name=Standard server
command=/usr/X11R6/bin/X -br -audit 0 -noacpi

```

This wouldn't be the official way to fix it (this file shouldn't be edited) but if it works..

Good luck,
bk

FWIW, my system is a Dell Inspiron 8200 running 6.10 edgy with the nvidia driver. The behavior happened with the default nv driver as well though.

---

### Post by line72 on 2006-11-07
This worked for me.  Thanks for your help!

---

### Post by BoredByPolitics on 2006-11-20
Solution worked for me too - Dell Latitude C840.

However, I decided to try and adjust the /etc/X11/gdm/gdm.conf-custom file instead of the gdm.conf file itself, and didn't manage to get it to work, at least initially.

The easiest way to implement this solution is to use gdmsetup (System -> Administration -> Login Window).  Select the 'Security' tab, then hit the button in the bottom right hand corner labeled 'Configure X Server'.

In the window that appears, add the -noacpi option to the string in the 'Command:' field, as per the original instructions.  Hit the close button, and then again on the 'Login Window Preferences' window.  Restart GDM (I logged out then hit CTRL-ALT-BACKSPACE at the login screen), and voila!  :-D

Pete

---

### Post by ReapeX on 2007-01-07
I'm using a Latitude D800, the above solution did not work for me.

Also my xorg.0.log file does not contain the word backtrace.  I am using Edgy Eft and I am able to succesffuly enter standby or suspend mode.

My bios is password protected, so once I try to resume from suspend the password screen for the bios appears.  I type in the password then I see a black with that is filled with 2 non standard characters (meaning the screen is filled with two characters that are you normally don't see).

With Windows XP, after coming out of standby I type my password and the Welcome Screen loads.  So what problem does Ubuntu have with my hardware is Nvidia Video card an issue here or is it something else?

---

### Post by line72 on 2007-01-07
Does suspend or hibernate work correctly for you if you turn off password protection in the bios?  I've had trouble with my precision M50 if the bios shows a message while linux is running (like if I plug in a dc adapter that isn't powerful enough), then it shows the grey bios screen, then locks up.  If suspend and hibernate still don't work correctly with the bios password disabled, try these steps:

In your xorg.conf, add the following to the "Device" section:
```

Option "NvAGP" "1"

```

Edt /etc/default/acpi-support and change:

```

POST_VIDEO=true
to
POST_VIDEO=false

```

---

### Post by ReapeX on 2007-01-08
I notice standby works fine when I just close the lid of my laptop instead of selecting standby from the Quit menu.

I'm not sure if the changes I made, from posts on the first page, affected this or not.
But I am fine with it working by closing the lid of the computer.

I took off the bios password, then tried standby and hibernate from the quit menu.
When trying to resume from hibernate, the ubuntu logo loaded, then the screens colors wents 60's!  By that I mean everything was green and purple and the colors were sliding around like some sorta psychadelic lava lamp o.o (or a screensaver that is included with Ubuntu).  
When trying to resume from standby (after selecting it in the quit menu), those two weird characters reappeared.

I wouldn't mind trying your post line72 but I need to know if I have the correction Device section by xorg.confi file says:

Section "Device"
     Identifer "NVIDIA Corporation NV31m [GeForce FX Go5650]"
     Driver    "nvidia"
EndSection

Is this the correct section I should add your code snippet too?

---

### Post by ReapeX on 2007-01-08
Nevermind, my power options settings were set to load a blank screen when the lid is close.  In my previous post, I stated that standby worked when closing the lid...I was wrong.

---

### Post by line72 on 2007-01-08
> **ReapeX said:**
> 
I wouldn't mind trying your post line72 but I need to know if I have the correction Device section by xorg.confi file says:

Section "Device"
     Identifer "NVIDIA Corporation NV31m [GeForce FX Go5650]"
     Driver    "nvidia"
EndSection

Is this the correct section I should add your code snippet too?

yes, that is the correct section.

---

### Post by ReapeX on 2007-01-11
Thank you, 

I'll try it out later today!

---

### Post by ReapeX on 2007-01-14
IT WORKED, EVEN WITH THE BIOS PASSWORD ON IT WORKS!!!

You managed to solve a problem with the D800 that sssssssooooo many other Ubuntu users have tried to solve but gave up on!

THANKS!!!!!  Now there is even less of a region for me to login to Windows!!!

Mind explaining it to me what the commands did?

I know POST_Video = false told the video card not to do a warm boot with the hardware, if it is not doing a warm boot what is it doing a cold boot?  Does it mean, Ubuntu will turn off the video card and then turn it back on?

Also what did the NvAGP=1 do?  I'm guessing it turned the Nividia Advance Graphic Port, if that is the case, does that mean any video extensive games or video will render graphics faster to the system memory?  //Can't believe it was turned off! o_o

Thanks again!

---

### Post by zukakog on 2007-04-06
> **BoredByPolitics said:**
> Solution worked for me too - Dell Latitude C840.

However, I decided to try and adjust the /etc/X11/gdm/gdm.conf-custom file instead of the gdm.conf file itself, and didn't manage to get it to work, at least initially.

The easiest way to implement this solution is to use gdmsetup (System -> Administration -> Login Window).  Select the 'Security' tab, then hit the button in the bottom right hand corner labeled 'Configure X Server'.

In the window that appears, add the -noacpi option to the string in the 'Command:' field, as per the original instructions.  Hit the close button, and then again on the 'Login Window Preferences' window.  Restart GDM (I logged out then hit CTRL-ALT-BACKSPACE at the login screen), and voila!  :-D

Pete
This works great for me...as long as I use GDM.  I prefer using KDM since I'm usually in KDE.  I couldn't find an equivalent place to add the -noacpi switch.  Any Ideas?  By the way, I came across [<this thread>]("http://ubuntuforums.org/showthread.php?t=56498") that has some other tips concerning laptop lids and acpi.

---

### Post by king_growler on 2007-04-15
> **zukakog said:**
> This works great for me...as long as I use GDM.  I prefer using KDM since I'm usually in KDE.  I couldn't find an equivalent place to add the -noacpi switch.  Any Ideas?...Look in /etc/kde3/kdm/kdmrc.

---

### Post by ReapeX on 2007-05-19
Heya Line72 and everyone else :D,

I just updated to Fiesty Fawn and the previous solution for the Nvidia 5650 card on standby doesn't work.

I have disabled desktop effects too.

When I come out of standby it shows a list of the files ubuntu was loading during start up.
Then the words in the center of the display get distorted (almost scramble)

The screen goes black and I belive their is a blinking cursor in the top left hand corner of the screen.

You cannot type and none of the keyboard commands work.
I have to do a manual hard shutdown.

Any advice will be greatly appreciated

---

