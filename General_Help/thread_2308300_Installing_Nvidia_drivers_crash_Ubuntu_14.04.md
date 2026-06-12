---
title: "Installing Nvidia drivers crash Ubuntu 14.04"
date: 2016-01-01
forum: General Help
---

### Post by Veliko on 2016-01-01
After I installed Ubuntu 14.04 LTS and updated it. I installed the latest Nvidia driver for Linux version 352.63. This is how I did it:

I opened "**Software & Updates**", then went to "**Addition Drivers**" and chose the option "**Using NVIDIA binary driver - version 352.63 from nvidia-352(proprietary, tested)**.
After that, I restart my PC and got this error "**[    0.472102] ACPI PCC probe failed**".

I couldn't run the OS so I reinstall it and this time I did the same thing but for **Using NVIDIA binary driver - version 340.96 from nvidia-340(proprietary). **After restart I got the same error.
[IMG]https://scontent-fra3-1.xx.fbcdn.net/hphotos-xfp1/v/t34.0-12/12467990_853817908064185_1609479290_n.jpg?oh=11d72a9753f04f2a688b7e83c1fa7d44&oe=568957D5[/IMG]

---

### Post by grahammechanical on 2016-01-01
Does Ubuntu load to a working desktop?

I was seeing that message all the way through the 26 week development period of 14.04 and the 26 week development period of 15.04. And it never stopped Ubuntu loading to a desktop. 

If we use Nouveau the open source video driver we do not see that message because a purple splash screen hides it. Install a Nvidia proprietary video driver and we do not get a purple splash screen and we see any system messages that might be put on the screen. This is what I have noticed. The latest message I am seeing in 16.04 development branch is about a file system check on the Ubuntu partition. It also is just information.

[http://ubuntuforums.org/showthread.php?t=2275310](http://ubuntuforums.org/showthread.php?t=2275310)

If Ubuntu is not loading to a working desktop we will have to for an answer. But that message is not connected.

Regards

---

### Post by Veliko on 2016-01-01
> **grahammechanical said:**
> Does Ubuntu load to a working desktop?

I was seeing that message all the way through the 26 week development period of 14.04 and the 26 week development period of 15.04. And it never stopped Ubuntu loading to a desktop. 

If we use Nouveau the open source video driver we do not see that message because a purple splash screen hides it. Install a Nvidia proprietary video driver and we do not get a purple splash screen and we see any system messages that might be put on the screen. This is what I have noticed. The latest message I am seeing in 16.04 development branch is about a file system check on the Ubuntu partition. It also is just information.

[http://ubuntuforums.org/showthread.php?t=2275310](http://ubuntuforums.org/showthread.php?t=2275310)

If Ubuntu is not loading to a working desktop we will have to for an answer. But that message is not connected.

Regards
Nope Ubuntu is not loading to the desktop. When this message appears, I hit enter, screen turns fully black and after some seconds like 15-20 the message appears again.

---

### Post by tokyobadger on 2016-01-02
You're missing the nomodeset flag in the kernel parameters - you'll need to edit /etc/default grub and probably clean up all previously installed nvidia drivers
[see here](http://ubuntuforums.org/showthread.php?t=2307693)

---

### Post by Veliko on 2016-01-02
> **tokyobadger said:**
> You're missing the nomodeset flag in the kernel parameters - you'll need to edit /etc/default grub and probably clean up all previously installed nvidia drivers
[see here]("http://ubuntuforums.org/showthread.php?t=2307693")
is it going to work if I follow the instructions from this post [http://askubuntu.com/questions/160036/how-do-i-disable-acpi-when-booting](http://askubuntu.com/questions/160036/how-do-i-disable-acpi-when-booting) ?

---

### Post by Veliko on 2016-01-03
So I solved the problem. With this:
```
[COLOR=#111111][FONT=Ubuntu]sudo nano/etc/default/grub[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Change the GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" line to the following:[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Save the file, then run sudo update-grub Then reboot.
```

Now when I restart or turn on the PC the message ** ACPI PCC probe failed  **shows again, but after a few settings the OS boots to the GUI and everything seems to work fine.
Is this a problem that this message still appears for a few seconds ? Can I fix it ?[/FONT][/COLOR]

---

### Post by oldos2er on 2016-01-03
I see that same text each time I boot, but since my system loads and runs fine I just ignore it, as grahammechanical implied.

---

