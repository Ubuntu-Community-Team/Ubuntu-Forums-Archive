---
title: "Ubuntu 12.04 -64 fails to boot  - after graphics driver update?"
date: 2014-04-06
forum: General Help
---

### Post by john180 on 2014-04-06
Hi, Can someone help please? 
I'm a new Ubuntu (12.04 -64 bit) user migrating from WinXP (I went for full install rather than dual boot...). PC is a Compaq Athlon 64 3700+ desktop with 2Gb memory. Having been operating okay for a couple of days, installing updates, printer drivers and apps, the system now fails to boot correctly. I see the "Ubuntu 12.04 ....." splash screen (but in plain courier text rather than high res graphics?) and then the following text on-screen:

[FONT=courier new]fsck from util-linux 2.20.1
/dev/sda1: clean, 207617/9641984 files, 2164930/38548480 blocks
Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox
Skipping profile in /etc/apparmor.d/disable: usr.sbin.rsyslogd
* Starting AppArmor profiles                                            [OK]
speech-dispacher disabled ; edit /etc/default/speech-dispacher[/FONT]

Then the system halts! The system boots ok from live dvd. I ran boot-repair from the dvd and it gave the following URL:
[http://paste.ubuntu.com/7213098/](http://paste.ubuntu.com/7213098/)
I think this started after a recommended update to the graphics card driver(?) rather than the default. The graphics card is a Nvidia GeForce 6200SE.

Do I have to perform a fresh install or can this be repaired?
Posted from my elderly laptop - just  converted from xp to Lubuntu 13.10 and running just fine!
Thanks, John.

---

### Post by irv on 2014-04-06
I am trying to remember how I fixed this problem. As I remember I held down the [shift] key when booting and it when to the grub memu. From there I ran a repair mode and then chose to fix the graphics. If I am wrong, someone please correct me.
This might help also: [http://askubuntu.com/questions/162075/my-computer-boots-to-a-black-screen-what-options-do-i-have-to-fix-it]("http://askubuntu.com/questions/162075/my-computer-boots-to-a-black-screen-what-options-do-i-have-to-fix-it")

---

### Post by egeezer on 2014-04-06
Here is something that seems to help (MOST of the time, not always) when you're running 12.04 with Nvidia 6000 series graphics:

As irv suggested, when you reboot (or start from shutdown) hold down the [shift] key - that will let you see the GRUB screen.

Before it starts booting, type "e" (without quotes), and it will give you a new screen with the full line showing what features your kernel boots with.

At the end of that line, add the word "single" (no quotes) and press [enter]

That will give you a black screen that is a terminal for your system.  Type in

```
jockey-text --list
```

(Note the double dash before the word list; you might need to preface the command with sudo)

Wait for a while, and a list of the available restricted drivers will appear.  One of them will be enabled, most of them won't.  If a driver with the number 304 appears as disabled, type in

```
sudo jockey-text -e (followed by the whole 304 driver line)
```

That enables the driver that has worked (at least for me) on the Nvidia 6000 series.

---

### Post by john180 on 2014-04-06
Hi Irv, thanks fot that. I tried following the links on the link you posted - no luck. Seems though this can be a common problem with Nvidia cards though. Not sure I understand 'ran a repair mode' - I'm new to all this Linux business! - could you explain further please?
Thanks, John.

---

### Post by john180 on 2014-04-06
Hi Egeezer, thanks for the reply. Still no success. I'm very new to all this!

After "At the end of that line, add the word "single" (no quotes) and press [enter]" I get a different set of text, including 
* Starting load fallback graphics devices            [[COLOR=#ff0000]Fail[/COLOR]]
Is this a clue?

To get to a terminal line, after starting GRUB I entered recovery menu then root to get a prompt.
jockey-text --list (or sudo jockey-text --list) just results in 

org.freedesktop.DBus.Error.FileNotFound: Failed to connect to socket var/run/dbus/system_bus_socket: No such file or directory.

Worth a try though.
Thank you, 
John.

---

### Post by john180 on 2014-04-06
All, the motherboard is an MSI 7184 if that helps  - John

---

### Post by egeezer on 2014-04-06
Try clicking on Restricted Drivers and see what comes up.  Should show what is available and what is running, at least.  Might show a recent update, in which case you could choose to revert to the original.

---

### Post by irv on 2014-04-07
Here is another link that might help. Check out the list of [troubleshooting]("https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia") on the right.
Also "eqeezer" "john180" needs to get back on the desktop before he could checkout restricted Drivers.
Here is one more place, link, that might help.
[How to fix &#8220;The system is running in low-graphics mode&#8221; error?]("http://askubuntu.com/questions/141606/how-to-fix-the-system-is-running-in-low-graphics-mode-error")

---

### Post by john180 on 2014-04-07
Hi Irv, thanks for the suggestions. 
In GRUB, when I select 'enable networking' (as the <7> in the troubleshooting link describes) I get lots of text ending in:
[FONT=courier new]
network-manager start/running, process 975
modem-manager[961]: <info> Loaded plugin Linktop[/FONT]

Then the above line repeated, ending in 'Option', 'AnyData', 'Gobi', 'Option High-Speed', 'ZTE', finally ending with

[FONT=courier new]modem-manager[961]: <info> Loaded plugin Generic

[FONT=arial]Then the system halts. So I can't access the files, if I reboot, go to GRUB and select root without trying to enable the network, then type: [/FONT][/FONT][FONT=courier new]apt-get remove --purge nvidia-current [FONT=arial]as the next part suggests,[/FONT][/FONT]
[FONT=arial]I just get the following (even if prefixed by sudo): I guess this is because the 'mount your filesystem in read/write mode' has been missed? [/FONT]

[FONT=courier new]W: Not using locking for read only lock file /var/lib/dpkg/lock
E: Unable to write to /var/cache/apt/
E: The package lists or status file could not be parsed or opened[/FONT]
[FONT=arial]
This is probably something really obvious - as I'm a total Linux newbie. Where do I go from here other than a re-install?
[/FONT][FONT=courier new][FONT=arial]John[/FONT]
[/FONT]

---

