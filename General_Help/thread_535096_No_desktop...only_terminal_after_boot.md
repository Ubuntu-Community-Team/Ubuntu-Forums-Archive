---
title: "No desktop...only terminal after boot"
date: 2007-08-26
forum: General Help
---

### Post by Disciple75 on 2007-08-26
Strange thing happened on the way to the opera this evening…I popped in my ubuntu drive and booted up and everything looked normal momentarily and then a couple of screens full of text flashed by and then this final screen.  Naturally it was XP to the rescue (yes, I’m a little peeved at the moment, so the kudos go to Bill this time) with my other drive and logged into the forums to hunt down this monster.  I read something about fsck checking for hard disk errors every 30 boots…that’s just swell, but how do I get to my desktop at this point.  Forgive the sarcasm, but I use my Ubuntu drive most of the time.

Starting up…
Loading, please wait…
kinit: name_to_dev_t(/dev/disk/by-uuid/213a10a-b7b7-a3bb-355c5336617ca) = hda5(3,5)
kinit: trying to resume from /dev/disk/by-uuid/213a10a-b7b7-a3bb-355c5336617ca
kinit: no resume image, doing normal boot…
Ubunto 7.04 Tux tty1
Tux login:

After typing my login and password it displayed a big long license message and this is what I got…now what????

brian@Tux: ~$

---

### Post by Twiggy003 on 2007-08-26
Unless im misreading the situation, to get to the desktop, type startx, see if that does anything.

---

### Post by southernman on 2007-08-26
My first suggestion without much more info than you gave is to run this command at the prompt:

> sudo dpkg-reconfigure xserver-xorg

This command will take you though a series of questions in order to (re)setup your video card, keyboard, and mouse. For the most part, the default options are a safe bet, just take your time and read the text as you go along.

After you complete the process, the next command to start your desktop would be:

> startx
If it complains you need to be root (shouldn't) just put sudo in front of it.

If that doesn't work, when you come back here, below are some questions that may help us help you... figure this out.

Do you run Beryl?

What video card to you have?

What were you doing in Ubuntu, before you shut it down last (eg... software you may have installed, configuration changes you may have made and so on ).

---

### Post by Disciple75 on 2007-08-26
Well, using the startx command worked. Thanks for that. At least now I can get to my desktop.

However, I have a new problem now. The desktop doesn't give me the option of doing a shut-down anymore, only log-out, switch user or hibernate. 
Logging out just takes me back to the terminal screen again. Am I going to have to type startx every time I use Ubuntu. What happened to the start sequence? Why do I now have to type my login and password from the terminal screen instead of the desktop? I haven't changed anything in my original setup.

Disciple75

---

### Post by merlinus on 2007-08-26
From what I see, the system is trying to restart from a failed shutdown.

At the CLI, try:

shutdown -h now

and then restart.

-merlin

---

### Post by por100pre1 on 2007-08-26
> **Disciple75 said:**
> Well, using the startx command worked. Thanks for that. At least now I can get to my desktop.

However, I have a new problem now. The desktop doesn't give me the option of doing a shut-down anymore, only log-out, switch user or hibernate. 
Logging out just takes me back to the terminal screen again. Am I going to have to type startx every time I use Ubuntu. What happened to the start sequence? Why do I now have to type my login and password from the terminal screen instead of the desktop? I haven't changed anything in my original setup.

Disciple75

Now that everything is working fine backup your xorg.conf file:

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
```

To restore it if needed:

```
sudo cp /etc/X11/xorg.conf_backup /etc/X11/xorg.conf
```

---

### Post by por100pre1 on 2007-08-26
```
sudo dpkg-reconfigure gdm
```

If using Kubuntu

```
sudo dpkg-reconfigure kdm
```

---

### Post by Disciple75 on 2007-08-26
Thank you all for trying, but nothing seems to work. I got the following result from the last code. Now what? Is there some type of undo command? Although, I have no clue what I did to cause this.

brian@Tux:~$ sudo dpkg-reconfigure gdm
Password:
/usr/sbin/dpkg-reconfigure: gdm is not installed
brian@Tux:~$ 

Also, there is no "Login Window" in my System-Administrator to enable accessibility login. So there's no way I could have changed this.:(

---

### Post by por100pre1 on 2007-08-26
> **Disciple75 said:**
> Thank you all for trying, but nothing seems to work. I got the following result from the last code. Now what? Is there some type of undo command? Although, I have no clue what I did to cause this.

brian@Tux:~$ sudo dpkg-reconfigure gdm
Password:
/usr/sbin/dpkg-reconfigure: gdm is not installed
brian@Tux:~$ 

Also, there is no "Login Window" in my System-Administrator to enable accessibility login. So there's no way I could have changed this.:(

Need to install gdm:

```
sudo aptitude install gdm
```

---

### Post by por100pre1 on 2007-08-26
Forgot to say how to start gdm after installing!

```
/etc/init.d/gdm start
```

---

### Post by Disciple75 on 2007-08-26
This is what I got:

brian@Tux:~$ sudo aptitude install gdm
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Building tag database... Done      
The following packages have been kept back:
  dbus dbus-1-utils libdbus-1-3 libgl1-mesa-dri libgl1-mesa-glx 
  libglu1-mesa mesa-utils python-launchpad-bugs tzdata 
The following NEW packages will be installed:
  gdm 
0 packages upgraded, 1 newly installed, 0 to remove and 9 not upgraded.
Need to get 1814kB of archives. After unpacking 13.8MB will be used.
Writing extended state information... Done
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main gdm 2.18.1-0ubuntu1 [1814kB]
Fetched 1814kB in 9s (187kB/s)                                                  
Preconfiguring packages ...
Selecting previously deselected package gdm.
(Reading database ... 109474 files and directories currently installed.)
Unpacking gdm (from .../gdm_2.18.1-0ubuntu1_i386.deb) ...
Setting up gdm (2.18.1-0ubuntu1) ...
grep: /etc/X11/default-display-manager: No such file or directory
Adding group `gdm' (GID 118) ...
Done.
Warning: The home dir you specified already exists.
Adding system user `gdm' (UID 109) ...
Adding new user `gdm' (UID 109) with group `gdm' ...
The home directory `/var/lib/gdm' already exists.  Not copying from `/etc/skel'.
adduser: Warning: that home directory does not belong to the user you are currently creating.
 * Reloading GNOME Display Manager configuration...                              * Changes will take effect when all current X sessions have ended.
invoke-rc.d: initscript gdm, action "reload" failed.

brian@Tux:~$ /etc/init.d/gdm start
open: Permission denied
 * Starting GNOME Display Manager...                                            open: Permission denied
                                                                         [fail]
brian@Tux:~$

---

### Post by Disciple75 on 2007-08-26
That did it. I had to do a complete shutdown first. You Rock!

I posted the result in the last thread just in case it didn't work.

Thanks...to everyone for their input!!!!:)

---

### Post by shadyyx on 2007-11-25
Hi there.

I have the same problem as **Disciple75**.

The thing is I was just upgrading from FF to GG through console (upgrading through Adept has frozen for 3 times). During doing an upgrade there was some error when trying to reload display manager (I had KDM and GDM, KDM was the default) and an echo, that I will have to reload it manually... So after the upgrade have finished I restarted my computer (though it didn't ask for) and guess what happened???

It has started to boot normally, but when it should run into the login screen, it only stops on the tty1 screen. I can then walk around all tty's, but when hitting [ALT+F7] nothing happens. On [ALT+F8] screen echoes this:
```
*Checking battery state.                                                              [OK]
No starting K display manager (kdm). It is not the default desktop manager.
*Running local boot scripts (/etc/rc.local)                                           [OK]
```

and on the first screen (where tty1 is) it echoes the same things as to **Disciple** (that with _kinit_ and no resume image, etc).

When I tried to run KDM manually it said, that it has already started (but no KDE), so I reconfigured the KDM and set the GDM as default. After this step I can manualy run GDM by ```
sudo /etc/init.d/gdm start
``` but still it is not running by default during normal boot. I tried to uninstall KDM, no change. 

**Can anybody HELP???**

I'm glad I can run my Kubuntu, but I have to run GDM manually before that (same way as **Disciple** but it is boring and uncomfortable...

---

