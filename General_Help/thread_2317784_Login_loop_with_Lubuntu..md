---
title: "Login loop with Lubuntu."
date: 2016-03-19
forum: General Help
---

### Post by timin on 2016-03-19
I'm perplexed.  I unknowingly checked the Use Upstart flag in my Lubuntu 14.04 server settings.  

Now the system continually loops through the login process, i.e., as soon as the user/pass combo is entered, the desktop displays and then the system reverts back to the graphical login.  Is there a way for clearing the Upstart flag via a command-line boot?

As you can imagine, such is quite frustrating and more so given that I'd finally finished tweaking the setup (for Plex) just the way I needed it.

Help

---

### Post by timin on 2016-03-19
Not sure if this thread is best but here goes:

I have a somewhat similar issue wherein my Lubuntu 14.04 system login-loops.  

- Boot's ok to graphical login.
- Enter credentials, Lubuntu desktop loads briefly, then bang, sytem reverts to graphical login again

Last thing I changed was the graphical check-box flag for Upstart, believing it would be part of the a method that would allow me to delay the launch of Plex HT until after my WiFi was fully up.  Obviously I was il-informed about what Upstart was. Now I can't get out of the re-login-loop.

Got everything else, RAID, WiFi, Plex Media Server, audio, all set up nicely after many hours of work......and don't want to have to start over!

Thanks to any/all in advance for your help!!

---

### Post by Bashing-om on 2016-03-19
timin; Hello;

As a couple of stabs at this:
did you loose authorization to access your desktop ?
what returns:
```

ls -al .Xauthority
ls -al .ICEauthority

```

and also, is there now no graphic's driver for the GUI layer ?
```

sudo lshw -C display

```

What release did you install ? ... 15.10 has systemd as the initiate system, procedures differ now greatly.
What desktop are you running ? - stock Lubuntu runs on lightdm with LXDE.. maybe see what results when we attempt to start the desktop from terminal.

[INDENT][INDENT]The GUI
[INDENT][INDENT][INDENT]just another thing
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by coffeecat on 2016-03-19
@timin, I have moved the two posts you made to two different (old) threads into your own thread. It is almost always better to start your own thread - you are more likely to get help that way. Posts bringing old threads back to a half-life are usually overlooked.

Also - please do not post about the same thing in different parts of the forum, or to different threads. This dilutes community effort.

---

### Post by timin on 2016-03-20
@Bashing-om:

Thanks so much for the help!

- I'm certain that this is not a credentials problem as I actually get logged in to the desktop briefly before getting kicked into the loop again

- I cannot run the command line entries ls - al .Xauthority, etc. because I cannot get out of the login loop

- There IS graphic's driver for the GUI layer because the GUI gets loaded - all the way to the grpahical background and graphical login, then further to the (briefly - as described above) Desktop...and then kick-out, right back to the login

The installed system is 14.04.

The desktop is LXDE.

The problem must surely be related to the Upstart flag I checked as that is absolutely the last thing I did from a nicely running, logged-in, Lubuntu LXDE session.

Thanks again for any help you can provide!

---

### Post by Bashing-om on 2016-03-20
timin; Wellll ...

Let's boot to terminal, see then what we can find .

Boot to the grub menu and with the latest kernel selected to boot, press the 'e' key for edit mode -> boot parameters screen.
Arrow down to the line starting with linux, and across to "quiet splash" . replace these terms with the term 'text' - with out the quotes.
Key combo clt+x to continue the boot process to TTY1 . Log in here with username and password . There will be no response to the screen when pass word is entered. Enter pas word blindly and hit the enter key.

Now what does the system report when we start that GUI from terminal:
```

sudo service lightdm start

```
which should activate the GUI in TTY7 .
Key combo ctl+alt+F1 will return you to terminal
alt+F7 to go back to the GUI.

What happens, what is reported ?
From here we can go looking for that file that was changed, see about the graphic's driver, read the log files ... bunches of options.

[INDENT][INDENT]all in the process
[/INDENT][/INDENT]

---

### Post by timin on 2016-03-20
Basihin-om;   More wellll...back at ya...

Thanks very much for the reply.

This is a RAID-1 set up so the Linux line appears as follows:

linux     /vmlinuz-3.19.0.-56-generic root=/dev/mapper/vg0-lv_root ro    nomdmonddf  nomdmonisu

I.e., there is no "quiet splash" on this line (or anywhere else in the Grub).  When I place 'text' (no quotes) at the end of this line and continue, the machine boots to a blank screen with flashing cursor and no further.

:-|

---

### Post by Bashing-om on 2016-03-20
timin: Yikes .

Sorry, booting with raid is out of my skill set . We await those who have this knowledge.

[INDENT][INDENT]If I know everything
[INDENT][INDENT][INDENT]I would not be me
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by timin on 2016-03-20
@Bashing-om;

Booting on RAID is not too difficult.  Would gladly assist with such when/if such a project arises for you.

The issue here is definitely not RAID related.  It's the silly flag I set without enough prior-knowledge.

Hopefully someone will spot this thread shortly!

Best,

- Timinski

---

### Post by Bashing-om on 2016-03-20
timin; Yeah ...

Thing here is to boot to terminal . and not able to get past grub. How grub is installed and booted differs from a desktop, and depending on the raid level is how grub installs the boot code.
Depending on how the boot code is installed is how we tell grub where the boot files are so grub can tell the kernel. 

I just do not have the experience to know.

[INDENT][INDENT]once we are at a terminal in the install we can do something
[/INDENT][/INDENT]

---

