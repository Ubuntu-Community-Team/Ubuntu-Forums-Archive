---
title: "System Hangs at shutdown -- Showing tasks blocked and Tainted: P"
date: 2015-12-12
forum: General Help
---

### Post by jpagels on 2015-12-12
I've been running Ubuntu on my laptop (Lenovo Yoga 3 - 11) for a while and now, for whatever reason, it is hanging during all reboots and shutdowns. 

When shutting down I get a black screen with a blinking cursor. After 2 minutes I get the following error messages:
[IMG]http://i.imgur.com/KI7oaqy.jpg[/IMG]

This happens both when attempting to shutdown via GUI or via terminal running commands:
[PHP]sudo shutdown - h now, sudo halt -p, sudo reboot, &c. [/PHP]

The only time I can get it to shut down is when running:
> sudo halt -p --force

I have been searching for days without any fix yet in sight. There have been others with a similar problem who fixed theirs by adding various commands to grub. This has not made any change to my problem though. Any help debugging this would be much appreciated. 

Running Ubuntu 14.04.3 dual-boot with Windows
3.19.0-031900-generic

---

### Post by matt_symes on 2015-12-13
Hi

There are loads of things that can cause this, including memory and resource exhaustion.

Have you checked the amount of available memory when you want to shutdown ?

Interestingly, as the halt command with the --force switch will shut the system down, this would maybe point the finger at something in the init system and not an ACPI issue.

To start with, i would stop lightdm and so stop X, then try to shutdown from there.

ctrl + alt + f1 to get to a console.

```
sudo service stop lightdm
```

```
sudo halt -p
```

Does it still hang ?

If it does the unload your wireless card driver as well and try to shutdown.

As there are a number of things that can cause this, don't expect it to be an easy diagnosis of the problem.

Kind regards

---

### Post by jpagels on 2015-12-13
I have plenty of memory when shutting down. My system runs pretty smooth, all things considered. 

When stopping lightdm my system hangs with a blinking cursor and I have to reboot via REISUB.

Unloading my wireless adaptor didnt help either; just the same error message as in the picture posted above.

---

### Post by Geoffrey_Arndt on 2015-12-13
So, you've indicated you have been running Ubuntu on that Lenovo laptop for some time.   Did it always behave this way at shutdown?   From day 1 of the install?   If not, can you recall what updates or system changes you've made?   Especially if any changes involved non-standard software (from outside repos for example).   Did you try to install a Virtual Machine?   If it did in fact run this way from day 1 . . . have you installed any required graphics drivers - - especially from external sources for example?

---

### Post by jpagels on 2015-12-14
Don't know if this helps, but here's the output: ps aux

[ http://paste.ubuntu.com/14000874/]("http://paste.ubuntu.com/14000874/")

---

### Post by jpagels on 2015-12-14
>  			 				[INDENT] 					So, you've indicated you have been running Ubuntu on that Lenovo  laptop for some time.   Did it always behave this way at shutdown?    From day 1 of the install?   If not, can you recall what updates or  system changes you've made?   Especially if any changes involved  non-standard software (from outside repos for example).   Did you try to  install a Virtual Machine?   If it did in fact run this way from day 1 .  . . have you installed any required graphics drivers - - especially  from external sources for example? 				[/INDENT] 			
  			   		


I have had this install for about six months now. The only problem that I have ever had was the wireless card not being supported...but was able to apply a patch and rebuild my kernel to get things sorted out; but even then I never experienced any problems shutting things down. About a week ago this started happening...I want to say it was after a routine upgrade...but to be honest I'm not entirely sure as I tend to upgrade just about daily. 

As far as video card drivers, I've never touched them and simply use what what is suggested by the distro.

OEM Software...nothing that I can think of...just about everything I use I generally get via apt-get...even my Wm and its associated components (xmonad).

---

