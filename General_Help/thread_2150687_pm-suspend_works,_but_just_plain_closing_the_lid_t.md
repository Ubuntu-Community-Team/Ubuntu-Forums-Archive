---
title: "pm-suspend works, but just plain closing the lid to suspend usually doesn't."
date: 2013-06-01
forum: General Help
---

### Post by TheGuyWithTheFace on 2013-06-01
So I recently installed Ubuntu 13.04 64 bit on a Thinkpad T400, and wow, this thing flies! The only real issue I've had so far is that the suspend feature is a bit unreliable. Initially, every time I closed the lid, when I opened it and the machine came out of suspend, I was at the main logon screen, and of course I had been logged out, lost my open programs, etc.
First, I tried upgrading my kernel, as suggested by this thread:
[http://ubuntuforums.org/showthread.php?t=2140353](http://ubuntuforums.org/showthread.php?t=2140353)
When that didn't work, I figured I'd stick with the original kernel for 13.04, so I went back to 3.8.0-23-generic.

Then, at the suggestion of this article:
[http://ubuntuforums.org/showthread.php?t=2126215](http://ubuntuforums.org/showthread.php?t=2126215)
I added this to my grub file:
```
[COLOR=#000000]GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_backlight=vendor"[/COLOR]
[COLOR=#000000]GRUB_CMDLINE_LINUX="acpi_osi=Linux"[/COLOR]
```

As a result, now it sometimes works perfectly, sometimes it hangs for a while at a black screen before resuming, but usually the screen goes completely blank, and stays that way. I can hear the hard drive working, and the network light is on, and overall the system seems perfectly up and running, except for the screen.

Here's the really odd thing: So far every time I have run ```
sudo pm-suspend
``` the system resumes just fine. That being said, what I think might work is to make pm-suspend run as soon as the lid is closed. My question is, how in the world do I do that? Failing that, does anyone have any thoughts on what might be causing this? So far Dual booting fresh installs of Ubuntu 13.04 and Windows 7, I've had far less driver issues in Ubuntu than in windows, and I'd love to have Ubuntu working perfectly, if only to rub it in my Microsoft fanboy friend's face! :D

---

### Post by TheGuyWithTheFace on 2013-06-06
Bump? I could really use some help here, I've tried everything, but I just can't seem to get suspend to work right! This is really annoying, since I normally use sleep a lot, and every time I habitually close the lid, I lose whatever I've been working on...

---

### Post by claracc on 2013-06-06
I have had the same problem since 2010 in my hp compaq 6720s laptop: [http://ubuntuforums.org/archive/index.php/t-1592875.html](http://ubuntuforums.org/archive/index.php/t-1592875.html)

I haven't found any fix yet. 

I have found this bug report in launchpad: [https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/863834](https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/863834). You can try the workaround addressed in comment 30. There are people who say it works in their computers.

---

### Post by TheGuyWithTheFace on 2013-06-06
Aha! I've only tried it once so far, but it appears to work! For the sake of anyone else watching this thread, I followed claracc's link to the launchpad bug, and used the workaround in comment 30, shown here:

> [COLOR=#333333][FONT=Ubuntu Mono] /etc/acpi/[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu Mono]events/[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu Mono]lidbtn triggers /etc/acpi/lid.sh which triggers /etc/acpi/[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu Mono]local/lid.[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu Mono]sh.post at the end of the script. /etc/acpi/local/* allows you to add your own config (e.g. required for wmii).[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu Mono]generate /etc/acpi/local/lid.sh.post
make it executable
and add:[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Mono]#!/bin/bash
grep -q closed /proc/acpi/button/lid/*/state
if [ $? = 0 ]
then
/usr/sbin/pm-suspend
[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Mono]fi[/FONT][/COLOR]

---

### Post by TheGuyWithTheFace on 2013-06-06
Well darn. I suspended again, and once again was greeted by a blank screen when I re opened the lid. If it's any use to anyone, I did notice before the screen shut off completely that there was an error in the top left corner, I don't know all of what it said, I only got a quick glance at it, but it mentioned a device failing to resume, and I thought I saw "error -19". Any thoughts?

---

### Post by os2 on 2013-12-15
You have an issue with hardware/software not resuming from Suspend properly. It isn't related to the Lid Close issue.

Can you first confim /usr/sbin/pm-suspend is working without any issues? Run from a x-terminal and test it out.

---

### Post by TheGuyWithTheFace on 2013-12-17
Hi os2,I appreciate your thoughts, and I hope they're helpful to anyone else that might view this thread, but I've actually switched to Debian Wheezy, and don't have a computer on hand that runs Ubuntu at the moment. If I could test it, I would though... Anyways, if I ever do end up with Ubuntu on that machine again, I'll try that and report back.

---

### Post by os2 on 2013-12-17
Ubuntu would have better support for these sort of features straight out of the box than Debian. With Debian it's much more of a DIY affair.
I'm guessing from your response you have the issue sorted on Debian?

Create the following file:

/etc/acpi/events/lid

```

event=button/lid LID close
action=/usr/sbin/pm-suspend

```

# chmod +x lid

This will work on both Debian and Ubuntu.

Incidentally, the script you have posted in your post #4 is unnecessary and has errors in it.

---

### Post by TheGuyWithTheFace on 2013-12-17
Wow, that was a fast response! So, first, what do you mean by "features"? I wasn't aware that not suspending out of the box was a feature instead of a bug. I do agree with the DIY part of Debian, but I'm addicted to the stability and massive repositories, so I don't think I could leave even if I wanted to, which I don't.Yes, the lid close suspend works fine under Debian, but either way it's nice to know that this script will probably fix it. With regards to that other script... Yeah, I might have been a little prone to random copy-pasting from other threads... Anyways, on behalf of anyone else that may have this issue with Ubuntu, thanks for your help!

---

### Post by claracc on 2013-12-18
> **os2 said:**
> Ubuntu would have better support for these sort of features straight out of the box than Debian. With Debian it's much more of a DIY affair.
I'm guessing from your response you have the issue sorted on Debian?

Create the following file:

/etc/acpi/events/lid

```

event=button/lid LID close
action=/usr/sbin/pm-suspend

```

# chmod +x lid

This will work on both Debian and Ubuntu.

Incidentally, the script you have posted in your post #4 is unnecessary and has errors in it.

I have tried this workaround but it doesn't work for me.
I have created  lid filev with the two lines you addresses, save it and change permissions to do it executable. When I close lid nothing happens, computer continuous running. Have I missed something?

I also have tried to execute the lid file but I obtain 

```
/etc/acpi/events/lid 
/etc/acpi/events/lid: línea 1: LID: orden no encontrada
clara@clara1:~$ 

```

So it doesn't find the order LID

 As I pointed in previous threads about this same  issue, my laptop suspended when close lid in previous releases of ubuntu but since upgrading to precise it ignores the suspension when lid close.

---

### Post by os2 on 2013-12-18
1. Make sure pm-suspend is working on your system. You may also need to sudo first. Some services can prevent a system from going to Suspend.

2. There's also the possibility your machine is using another event name for the lid.

Close and reopen the lid whilst running in a x-terminal:

```

acpi_listen

```

This will capture the actual string of acpi events passed from your hardware when you close the lid and reopen it. The string generated needs to be passed to the event=XXX in the lid file.

---

### Post by claracc on 2013-12-18
It is very strange.

Only if I open a xterm and execute the command you provided:
```
acpi_listen
```

and then close the lid,  the computer suspends, and acpi_listen command returns:
```
clara@clara1:~$ acpi_listen
button/lid C154 00000080 00000001
video C099 00000080 00000000
thermal_zone TZ1 00000081 00000000
thermal_zone TZ3 00000081 00000000
button/lid C154 00000080 00000002

```

pm_suspend has always worked on my computer (of course, using sudo), also the suspension button in the upper panel.

So the conclusion is, the workaround for suspension when close lid, works only if I execute the command acpi_listen, but no in other case ???

---

### Post by os2 on 2013-12-18
Please understand the point. The reason to use acpi_listen is to get the trigger for the event.

In your case it is:

CLOSE
```

button/lid C154 00000080 00000001

```

and OPEN
```

button/lid C154 00000080 00000002

```

So put in the file /etc/acpi/events/lid

```

event=button/lid C154 00000080 00000001
action=/usr/sbin/pm-suspend

```

---

### Post by claracc on 2013-12-18
Okay, I have done as you say:

/etc/acpi/events/lid file :
```
event=button/lid C154 00000080 00000001
action=/usr/sbin/pm-suspend
```

I try to run the file but I obtain:

clara@clara1:/etc/acpi/events$ lid
El programa «lid» puede encontrarse en los siguientes paquetes:
 * id-utils
 * libuser
Intente: sudo apt-get install <paquete seleccionado>
 Translation:
Program lid can be found in the following packages:
 * id-utils
 * libuser
Try: sudo apt-get install "selected package"

What am I doing wrong?, lid file has to be a bash script and beginning by  #! /bin/bash?

As it is clear, lid file is executable by anybody in /etc/acpi/events/:

```
-rwxr-xr-x 1 root root   68 dic 18 13:53 lid

```

Tankyou for your patience

---

### Post by os2 on 2013-12-18
Why are you running the file? It should have +x attributes but you don't run the file.
Leave the file in the /etc/acpi/events directory. The acpid/service will run the action if it detects the lid event.

---

### Post by claracc on 2013-12-18
Okay, now is working, and certainly it is not necessary to put the #! /bin/bash "title" in the beginning of the file or to manually run the file. For me the problem is solved.

I was trying to run the file because when close lid before it wasn't recognized, and computer didn't suspend. I suppose it was for the "LID close" order insted of the good one for me "C154 00000080 00000001".

Thankyou for your help.

I dare to ask to the original poster to mark the thread as "solved", since the workaround propossed by os2 works.

---

