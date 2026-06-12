---
title: "Error 15 - menu.lst wasn't found"
date: 2008-05-22
forum: General Help
---

### Post by Core2uu on 2008-05-22
I have 2 hard drives installed on my computer... XP is the only system installed and it is installed on C:\... I downloaded the Ubuntu ISO and installed it yesterday on D:\ using the install inside windows option on the installer... It installed smoothly... But when I tried to boot Ubuntu I got the error of /ubuntu/install/boot/grub/menu.lst was not found... I checked and it indeed was there and other places as well... 

Any suggestions? I'm running chkdsk right now on D:\ but I dont think it is a physical problem of the drive...

---

### Post by tamoneya on 2008-05-22
it is supposed to be /boot/grub/menu.lst.  Do you have anything there?

---

### Post by Core2uu on 2008-05-22
You mean it should be on the root of D: ??:confused:

---

### Post by tamoneya on 2008-05-22
D: is a windows term.  Since you installed on "d:" that means that d:/ is your linux root.  so if menu.lst is at /boot/grub/menu.lst then it is d:/boot/grub/menu.lst

---

### Post by Core2uu on 2008-05-22
The path did not exist... So I made it exist... Nothing happened, same error, no difference...

---

### Post by peter sanders on 2008-05-23
I have the same problem.

The path and file appear to be all present and correct but do not get found by the boot system  :(

---

### Post by tinybit on 2008-05-23
Please try to copy /ubuntu/install/boot/grub/menu.lst to both C:\ and D:\ and try again. You may also press c to get a command line, and type these at the grub prompt:

```

find --set-root --ignore-floppies /ubuntu/install/boot/grub/menu.lst
configfile /ubuntu/install/boot/grub/menu.lst

find --set-root --ignore-floppies /menu.lst
configfile /menu.lst


```

---

### Post by peter sanders on 2008-05-23
> **tinybit said:**
> Please try to copy /ubuntu/install/boot/grub/menu.lst to both C:\ and D:\ and try again. You may also press c to get a command line, and type these at the grub prompt:

[COLOR="Blue"]Did this, I created the correct path and copied the menu.lst file there.  This did not fix things :([/COLOR]

```

find --set-root --ignore-floppies /ubuntu/install/boot/grub/menu.lst

[COLOR="blue"]Did this and got Error 15, file not found :([/COLOR]

configfile /ubuntu/install/boot/grub/menu.lst

[COLOR="blue"]Did this and got Error 16 inconsistent filesystem structure :([/COLOR]

find --set-root --ignore-floppies /menu.lst

[COLOR="blue"]Did this and got Error 15 again :([/COLOR]

configfile /menu.lst

[COLOR="blue"]Did this and got the Error 16 message again.....[/COLOR]


```


PCS

---

### Post by Core2uu on 2008-05-23
Well, I'm gonna speculate that it was trying to find menu.lst on C: instead of on D... I copied the boot folder out of D: and put it on the root of C: and also made a new folder on the root of C: (ubuntu\install\) and pasted boot into the install folder... I restarted the machine and YES... no error... Now it is doing something that looks strangely similar to installing ubuntu on C: ...

What I currently see on the screen is the background picture with the picaso bird and a window that says...

-----------------------------------------
-----------------------------------------
Checking Installation Files
-----------------------------------------
Installing System...
-----------------------------------------
Progress Bar... 78%                     |
-----------------------------------------
Copying Files (less than a minute remaining)
-----------------------------------------
-----------------------------------------

---

### Post by Afromonkey0 on 2008-05-23
I get the same error 15 for every boot option given, except my ubuntu hardyheron was working fine for a long time, then it froze and I did a hard reboot, now this.
Is there a way of restoring this stuff from a live cd?

---

### Post by Core2uu on 2008-05-23
Was your hardyheron installed on it's own partiton or was it WUBI? If it was WUBI maybe try what I did... Put the menu.lst in the two places I did on your disk0... myabe all of them...

---

### Post by tinybit on 2008-05-24
To see if it would help, please refer to

[http://ubuntuforums.org/showthread.php?t=798283](http://ubuntuforums.org/showthread.php?t=798283)

and this thread

[http://ubuntuforums.org/showthread.php?t=782663](http://ubuntuforums.org/showthread.php?t=782663)

---

### Post by Afromonkey0 on 2008-05-25
Thanks guys. Yeah it's a WUBI installation, I'll check out those other threads.

"Put the menu.lst in the two places I did on your disk0"
I don't know how I would do that, linux noob here. If I can work out what that is and how to do it i'll give it a shot.

Looking at those other threads made me realise how stupid i am for not mentioning that my system is already partitioned once, it's a school machine and they insist on having a 'school side' and a 'home side' partition. It didn't occur to me to say this because I figured if that were a problem I wouldn't have been able to install at all. As i say it worked fine for several days before this problem occurred. I select 'home' from the first bootloader, then it asks me to pick an OS, which all worked fine until now.

---

### Post by ago on 2008-05-26
[https://wiki.ubuntu.com/WubiGuide#head-7e4c85ef744a4fd4bae6766a5e6abc67f608d742](https://wiki.ubuntu.com/WubiGuide#head-7e4c85ef744a4fd4bae6766a5e6abc67f608d742)

---

