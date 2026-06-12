---
title: "Make Hoary Boot Faster?"
date: 2005-09-18
forum: General Help
---

### Post by fordfan753 on 2005-09-18
My laptop is getting a little older and slower than I would probably like, it is a PIII 600MHz with 192MB RAM. I have Hoary installed because I think it is a great distro, BUT on my laptop it takes over 5 minutes to boot!

I don't run Gnome, I use Windowmaker and Openbox for speed, and I use WDM as my display manager.

I searched the internet all day today for tips to speed up my boot, there were a few good looking ones, BUM and initNG in particular.

InitNG shaved about a minute off my boot time, but it didn't want to load WDM. BUM looked very good, but I don't want to install half of Gnome to get it to work, as I want to keep this a very minimal system.

Boot time is important to me, and I'd love to get it down to around 2 minutes, so any tips and tricks would be much appreciated. How well does hibernate work in Hoary? Most of my boot time is comumed by hotplugging and loading modules for NDIS Wrapper, is there any way I can disable these at startup or get them to run in the background *after* the display manager has loaded. Also, it would be great if I could get the display manager (wdm) to load as early as possible, and for everything else that is unneccesary (ie ntp) to load up behind it.

And yes, I know my boot time would be reduced if I never had to reboot...everyone knows that.

---

### Post by FLeiXiuS on 2005-09-18
[QUOTE=fordfan753]Most of my boot time is comumed by hotplugging and loading modules for NDIS Wrapper, is there any way I can disable these at startup or get them to run in the background *after* the display manager has loaded. Also, it would be great if I could get the display manager (wdm) to load as early as possible, and for everything else that is unneccesary (ie ntp) to load up behind it.

And yes, I know my boot time would be reduced if I never had to reboot...everyone knows that.[/QUOTE]

[COLOR=Red]WARNING: It is very dangerous to modify boot sequence.  You could cause serious damage to your system.  Only modify what you are absolute certain of.  Please, don't hesitate to ask questions![/COLOR]

What I typically do for situations like this is...I go in and look at what takes the longest time loading and what is just...NOTE NEEDED.   I had a lot of processes which were irrelevent to my computer.  For example, fetchmail, ppp, ppp-dns, etc..

One of the easiest ways to fix this is to remove executable permissions to the process.

1.) Change directories to the startup scripts path.
```

$ cd /etc/init.d/

```

2.) Now view each and every one and determine whether or not you need them. 
```

$ ls

```

3.) For the processes you don't need you simple folow this command with the name of the script.
```

$ sudo chmod -x NAME

Example:
$ sudo chmod -x fetchmail

```

That'll just about do it for you.


Now for changing WHEN processes are initiated you can rely on your runlevel.  Default runlevel for Ubuntu is 2, which is Multi-User / GUI.  Each runlevel path has a symbolic link to certain scripts found in /etc/init.d/.  The links defined in the runlevel's folder will be executed at boot.  How do you know when?  Well each symbolic link is named with a priority + name.  For example...
```
S99fetchmail
```

The "S" certifies that the program is going to be STARTED/INITIATED.  The "99" is the priority it has.  The lower the priority, the sooner if will initiate.  The higher the priority, well of course this would impede when the process will be initiated.  So simply rename the scripts which you want to run after others with a higher priority.  99 is the highest, so don't try to trick the system into thinking there is a priority level of 1000!  

```

$ sudo mv S99fetchmail S70fetchmail

```

This should set you up and on your way!  Please let me know if you have any questions!

---

### Post by fordfan753 on 2005-09-18
Thanks for the tips!

Do you think that hotplug is absolutely necessary? It takes up most of my boot time and my hardware configuration never changes....And if I stopped hotplug do you think I would still be able to manually mount USB flash drives?

---

### Post by mlomker on 2005-09-18
[QUOTE=fordfan753]Thanks for the tips!

Do you think that hotplug is absolutely necessary? It takes up most of my boot time and my hardware configuration never changes....And if I stopped hotplug do you think I would still be able to manually mount USB flash drives?[/QUOTE]

Yeah, but keep in mind hotplug is taking a while because it's loading all of those drivers that you see in **lsmod** in the background.  You could disable hotplug but then you'd have to manually add all of the right modules to /etc/modules. 

You could manually load the drivers for the flash drive.

I really don't recommend messing with hotplug, though.  You're better off disabling things like fetchmail and ntpdate.

Oh, and there's a command-line tool for managing your scripts.  Grab the **sysvconfig** package.

---

### Post by Iesos on 2005-10-28
Hi
I got a problem concerning boot. Its something wrong with fsck. At boot it says that it cant check my hdb1. But it seems to work fine while in ubuntu. So all i want to do is to turn off fsck at boot (or is there a better way?). when fsck fails it says that i should 'repair manually', how do i do that?
Hope you can help me.

---

