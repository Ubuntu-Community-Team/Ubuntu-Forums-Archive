---
title: "black screen on opening lid"
date: 2014-05-16
forum: General Help
---

### Post by slumbergod on 2014-05-16
Hi all,

I was hoping someone could suggest which log would be the best one to try and diagnose a weird issue I am having with my clean install of Xubuntu 14.04 running on a Samsung laptop (about a year old).

I am trying to work out if it is a kernel issue with my hardware or the graphics driver (intel i3 cpu).

Here's whats happening: I'll close my laptop lid and go away for a few hours. When I come back and open the lid I just get a black screen. The laptop is on but I can't do anything at all to get it to come back to life. I have to hold the power button in to poweroff ungracefully. 

I am unable to drop to another login.

I have disabled suspend and hibernate in the xfce4 power manager.

I have even applied a hack I found online to permanently disable suspend and hibernate.

Still the problem happens. Not everytime, just randomly. This was not an issue for me in the previous xubuntu.

Kernel or graphics?

---

### Post by pqwoerituytrueiwoq on 2014-05-16
is it set to ask for a password on wake? my laptop is set like that and there is a issuer with lite-locker, xscreensaver is a decent workaround
[http://ubuntuforums.org/showthread.php?t=2223766&p=13022158#post13022158](http://ubuntuforums.org/showthread.php?t=2223766&p=13022158#post13022158)

---

### Post by edo_kanii on 2014-05-16
I had that issue and I resolved like this:

1. open your terminal(ctrl+alt+T)
2.type: nano ~/Documents/mydocname
3.inside nano editor copy paste these lines:
 #!/bin/bash
echo "your_admin_password"| sudo -S service lightdm restart
4.save it by typing ctrl+x and press enter
5.go to keyboard settings, and choose shortcuts card
6.press add new and navigate to your file(mydocname)
7.choose your combination
8.that's it, when you get black screen, just press your key combination

it's probably newbie but it works, also i searched for forums and didn't find any solution that actually worked

---

### Post by pqwoerituytrueiwoq on 2014-05-16
that will terminate your session and return you to the login screen
try this script instead
[https://bugs.launchpad.net/ubuntu/+source/xfce4-power-manager/+bug/1303736/comments/11](https://bugs.launchpad.net/ubuntu/+source/xfce4-power-manager/+bug/1303736/comments/11)
the 1366x768 is the screen resolution

---

### Post by su:bhatta on 2014-05-16
Well, I had the same Issue with my Samsung 305E5Z and had raised a bug report, when in Beta.
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1306549](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1306549)

Please read the Comments of the bug report,
my problem was fixed using the then latest main line kernel which I am still using with no problems 

> ~$ uname -r
3.14.0-031400-lowlatency

I guess it is both graphics and kernel.

---

### Post by slumbergod on 2014-05-16
Phew! glad I am not the only one. I've had a few weird issues with the kernel but each set of updates seems to sorting things out.

Thanks, guys, I will try these solutions today. 

If I don't experience the problem again for a few days I'll mark it is solved!

---

### Post by pqwoerituytrueiwoq on 2014-05-16
the script thing does not fix the issue, just when it happens you press the keyboard shortcut and it fixes the display

---

### Post by edo_kanii on 2014-05-16
as I didn't know any better solution, i simply thought it's better to terminate session then restarting pc :)

---

### Post by pqwoerituytrueiwoq on 2014-05-16
it is better, but the other script is better still, at least you can close your apps and dont kill them then log out and in to fix the mouse cursor

---

### Post by chw1984 on 2014-05-18
Hello,

I am having the exact same issue on my ThinkPad Edge. The script using xrandr helped me as far as avoiding the hard reboots after almost each wake up... however, there is still the issue with the missing mouse pointer.

Installing a mainline kernel build did unfortunately not help:

```

christoph@christoph-ThinkPad-Edge:~$ uname -r
3.14.1-031401-generic

```

and I am still experiencing exactly the same behavior as with the standard Kernel 3.13.



Edit: if the mouse pointer is missing it suffices to press Ctrl+Alt+Del and enter the password to resume the session, then the mouse pointer should be back and things should work normally again; no need to close any of the running apps.

---

### Post by slumbergod on 2014-05-21
For the benefit of anyone stumbling across this thread.

This is a known bug affecting 120+ users and at the time of writing this, remains unassigned and without a fix.
([https://bugs.launchpad.net/ubuntu/+source/xfce4-power-manager/+bug/1303736](https://bugs.launchpad.net/ubuntu/+source/xfce4-power-manager/+bug/1303736))

There are a range of behaviours exhibited depending on the user's hardware but all seem to be related to the kernel+light-locker+xfce4-power-manager.

---

