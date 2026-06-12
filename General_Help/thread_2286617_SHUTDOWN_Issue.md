---
title: "SHUTDOWN Issue"
date: 2015-07-13
forum: General Help
---

### Post by enemy2 on 2015-07-13
Hello there. I have a huge issue that bugs my mind. I have the infamous issue of my laptop not shutting down. I have an Acer Aspire ES1-512 that came preinstalled with Windows 8.1. The problem is that it doesn't shut down properly. I tried all sorts of things in the grub. I tried putting on the GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" acpi=off

and also apm=power_off etc.

I have tried everything that I could have ever find on the ubuntu forums, and it still doesnt shut down. I have installed it in Uefi mode, on unallocated
space created in the Windows 8.1 partition.

It simply doesn't want to shut down. Neither sudo -h shutdown doesn't shut it completely. It remains at Ubuntu will now halt, when I hear the HDD shuting down.

But the monitor remains on, the LED remains on and the fan keeps on blowing. I install Ubuntu 14.04.02.

Help please, it is really annoying to always shut it down from the hardware power button. I'm afraid it will harm my laptop in the long term.

---

### Post by jay98 on 2015-07-13
Have you tried logging out THEN powering off from the Log-in Screen?

Do you see any messages / failures on the screen during boot or shut down?  Anything in your logs?

Did you see this post?
[http://www.linuxquestions.org/questions/linux-newbie-8/ubuntu-14-04-lts-not-shutting-down-on-acer-aspire-es1-512-a-4175536327/](http://www.linuxquestions.org/questions/linux-newbie-8/ubuntu-14-04-lts-not-shutting-down-on-acer-aspire-es1-512-a-4175536327/)

Did you try:
```
sudo systemctl poweroff
```
or
```
GRUB_CMDLINE_LINUX_DEFAULT=quiet splash noapic irqpoll
```

This post 
[http://askubuntu.com/questions/155733/ubuntu-12-04-not-shutting-down-properly](http://askubuntu.com/questions/155733/ubuntu-12-04-not-shutting-down-properly)
talks about the nomodeset option
```
GRUB_CMDLINE_LINUX_DEFAULT="nomodeset"
```

And please remember to update grub after you edit /etc/default/grub !!
```
sudo update-grub
```

---

### Post by enemy2 on 2015-07-13
Thank you so much for your help, but nothing solved the shutdown issue.

What I find interesting is that when i set "nomodeset", i cannot change the brightness from the Fn key combination, and when I drag a window around with my mouse it stutters a bit and looks all around choppy, almost like the graphics driver isn't installed. But i know that the kernel installed the graphics card automaticaly, which is an integrated intel gpu. So I do not know what to do anymore... 

I remember, during boot, seeing some kind of error regardind ELAN. But the touchpad works great, even the two-finger scrolling function works. So i dunno.

Edit:

Every time I try to edit something in the grub, this appears on the terminal : "Gtk-WARNING **: Calling Inhibit failed: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files
". But I can save the grub just fine, and it remembers the save.

---

### Post by jay98 on 2015-07-13
Did you see the Ubuntu Grub 2 page? [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

"[COLOR=#333333][FONT=Ubuntu]your machine freezes upon attempts to shutdown or reboot, try modifying /etc/default/grub. Open the file with [/FONT][/COLOR]*gksudo gedit /etc/default/grub*[COLOR=#333333][FONT=Ubuntu] (graphical interface) or [/FONT][/COLOR]*sudo nano /etc/default/grub*[COLOR=#333333][FONT=Ubuntu] (command-line). Any other plaintext editor (Vim, Emacs, Kate, Leafpad) is fine too. Find the line that starts with [/FONT][/COLOR]**GRUB_CMDLINE_LINUX_DEFAULT** [COLOR=#333333][FONT=Ubuntu]and add [/FONT][/COLOR]*reboot=bios*[COLOR=#333333][FONT=Ubuntu] to the end. 
[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]If done properly it should result in something like *GRUB_CMDLINE_LINUX_DEFAULT="quiet splash reboot=bios" *
[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]Then save the file, run *sudo update-grub* and reboot in any way that's possible for you. After that, reboots and shutdowns should start working properly."[/FONT][/COLOR]

---

### Post by enemy2 on 2015-07-13
Yes, I have tried that too. It still won't shut down, still the last message says ubuntu will now halt. And then the hdd stops, but the power led and the fan keeps working. The funny thing is that Sleep works properly.

---

### Post by enemy2 on 2015-07-13
bump

Edit: I believe the problem could be that the dual operating systems are installed in UEFI Mode. In legacy, I remember some time ago I could make linux shut down, but being in legacy mode, my touchpad didn't work. So the sacrifice isn't worth it. Maybe I haven't followed a proper guide on installing ubuntu in uefi alongside windows 8.1?

---

### Post by enemy2 on 2015-07-13
After a week of sweat blood and tears I can finally shutdown my laptop! And guess what fixed it? A bios update! The last thing that I would've thought. Sooo happy right now!

It can be closed.

---

### Post by loricaire on 2015-08-16
Hello,

I have the same issue, with an Aspire ES1-512-20BV, Xubuntu 14.04.02, bios V1.10.
Could you please tell me which bios do you use ?

Sincerely

---

