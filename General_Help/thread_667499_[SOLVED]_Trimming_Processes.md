---
title: "[SOLVED] Trimming Processes"
date: 2008-01-14
forum: General Help
---

### Post by Bruce M. on 2008-01-14
Hi Folks,

I'm back and at this moment my computer is using 1 process of 119
I have gedit open, Terminal open, Firefox open and 2 conkys running.
Shouldn't that read at least 5 processes?

**EDIT:** I'm running a P-III, 800Mhtz **Desktop**, with 512M RAM

How can I find and eliminate some of those 119 processes that I do not need?

I started here:
From>System>Administration>Services

And the questions add up.

First column
?: don't know if I need or not (or want it)
+: means I understand, and the selection is correct
??: see added imput

second column:
*: activated
-: not activated

Services Manager

? * Actions schedular (anacron)
? * Actions Scheduler (atd)
? - Audio settings management (alsa-utils)
? * Automated crash reports support (apport)
? * Bluetooth device management (bluetooth) --> I have no Bluetooth devices
+ - Braille display management (britty)
+ * Clock synchronization service (ntp)
? * Computer activity logger (klogd)
? * Computer activity logger (sysklogd)
? * CPU Frequency manager (powermowd)
+ * Graphical login manager (gdm)
? - Hard disk tuning (hdparm)
?? * Hardware monitor (im-sensors) - will need for conky for CPU temp when I figure out how to get it going.
? * Hardware monitor (sensord)
? * Hotkeys management (hotkeys-setup)
? - Multicast DNS service discovery (avahi-daemon)
? * Power management (acpid)
? * Power management (apmd)
?? * Printer service (cupsys)
? * Printer service (hplip)
? * System communication bus (dbus)
? - Terminal multiplexor (screen)

I see in one of the > Here are the similar threads we found:

to use $ ps -A to get processes, so here's the output:

bruloo@The-Team:~$ ps -A
  PID TTY          TIME CMD
    1 ?        00:00:02 init
    2 ?        00:00:00 migration/0
    3 ?        00:00:00 ksoftirqd/0
    4 ?        00:00:00 watchdog/0
    5 ?        00:00:00 events/0
    6 ?        00:00:00 khelper
    7 ?        00:00:00 kthread
   30 ?        00:00:00 kblockd/0
   31 ?        00:00:00 kacpid
   32 ?        00:00:00 kacpi_notify
  108 ?        00:00:00 kseriod
  127 ?        00:00:00 pdflush
  128 ?        00:00:00 pdflush
  129 ?        00:00:00 kswapd0
  130 ?        00:00:00 aio/0
 1976 ?        00:00:03 ata/0
 1977 ?        00:00:00 ata_aux
 1980 ?        00:00:00 scsi_eh_0
 1981 ?        00:00:08 scsi_eh_1
 1995 ?        00:00:00 ksuspend_usbd
 1996 ?        00:00:00 khubd
 2335 ?        00:00:03 kjournald
 2535 ?        00:00:01 udevd
 3464 ?        00:00:00 kgameportd
 3532 ?        00:00:00 kpsmoused
 3981 ?        00:05:12 mount.ntfs-3g
 3984 ?        00:00:00 kjournald
 4192 tty4     00:00:00 getty      --- what are all these?
 4193 tty5     00:00:00 getty
 4197 tty2     00:00:00 getty
 4198 tty3     00:00:00 getty
 4200 tty1     00:00:00 getty
 4201 tty6     00:00:00 getty
 4440 ?        00:00:00 acpid
 4546 ?        00:00:00 syslogd
 4603 ?        00:00:00 dd
 4605 ?        00:00:00 klogd
 4626 ?        00:00:02 dbus-daemon
 4642 ?        00:00:06 hald
 4643 ?        00:00:00 hald-runner
 4649 ?        00:00:00 hald-addon-acpi
 4657 ?        00:00:01 hald-addon-keyb
 4666 ?        00:00:00 hald-addon-keyb
 4669 ?        00:00:00 hald-addon-keyb
 4684 ?        00:00:02 hald-addon-stor
 4686 ?        00:00:02 hald-addon-stor
 4699 ?        00:00:00 dhcdbd
 4714 ?        00:00:00 NetworkManager
 4735 ?        00:00:00 avahi-daemon
 4736 ?        00:00:00 avahi-daemon
 4749 ?        00:00:00 NetworkManagerD
 4762 ?        00:00:00 system-tools-ba
 4763 ?        00:00:00 dbus-daemon
 4809 ?        00:00:00 gdm
 4812 ?        00:00:00 gdm
 4815 tty7     00:34:47 Xorg
 4820 ?        00:00:00 dhclient
 4891 ?        00:00:00 hpiod
 4900 ?        00:00:00 python
 5189 ?        00:00:00 gdomap
 5224 ?        00:00:00 sensord
 5236 ?        00:00:03 wesnothd
 5242 ?        00:00:58 gedit
 5283 ?        00:00:00 hcid
 5305 ?        00:00:00 krfcommd
 5327 ?        00:00:00 ntpd
 5360 ?        00:00:00 atd
 5374 ?        00:00:00 cron
 5466 ?        00:00:01 x-session-manag
 5506 ?        00:00:00 ssh-agent
 5509 ?        00:00:00 dbus-launch
 5510 ?        00:00:00 dbus-daemon
 5512 ?        00:00:03 gconfd-2
 5515 ?        00:00:00 gnome-keyring-d
 5517 ?        00:00:30 gnome-settings-
 5524 ?        00:00:00 sh
 5525 ?        00:00:00 esd
 5529 ?        00:00:57 metacity
 5532 ?        00:01:18 gnome-panel
 5535 ?        00:00:50 nautilus
 5541 ?        00:00:00 bonobo-activati
 5544 ?        00:00:00 gnome-vfs-daemo
 5546 ?        00:00:03 gnome-volume-ma
 5547 ?        00:00:23 python
 5548 ?        00:00:00 update-notifier
 5554 ?        00:00:00 python
 5555 ?        00:00:19 gnome-cups-icon
 5587 ?        00:00:00 mapping-daemon
 5607 ?        00:00:02 mixer_applet2
 5609 ?        00:00:00 trashapplet
 5670 ?        00:00:55 gnome-screensav
 7023 ?        00:00:17 cupsd
 9253 ?        00:16:51 firefox-bin
21319 ?        00:02:18 conky
21329 ?        00:00:00 conky
24314 ?        00:00:01 gnome-power-man
28186 ?        00:00:00 gnome-terminal
28198 ?        00:00:00 gnome-pty-helpe
28199 pts/0    00:00:00 bash
28240 pts/0    00:00:00 ps
28241 ?        00:00:00 sh
28242 ?        00:00:00 whoami  ---> I'm Bruce and you?
bruloo@The-Team:~$ 

From >Systems>Preferences>Sessions
I have stopped:
Evolution Alarm Notifier --> I don't use Evolution at all
Network Manager --> not needed, it's a single home computer.
Power Manager -->  not needed, it's a single home Desktop computer.

How do I figure out which ones I don't need and then get rid of them?

Thanks
Bruce

---

### Post by Tristam Green on 2008-01-14
2 cents:  Kill the bluetooth service if you have no devices and/or no radio.

As for the rest, I know Power Manager (g-p-m?) uses either acpid or apmd for its output; I've never figured that out since I haven't played enough with it to fully understand.

Good luck, and for posterity:  my system displays 186 processes with 1 running, and I don't notice a decrease in performance on my wimpy 1.8GHz processor :)

---

### Post by Bruce M. on 2008-01-14
> **Tristam Green said:**
> 2 cents:  Kill the bluetooth service if you have no devices and/or no radio.

As for the rest, I know Power Manager (g-p-m?) uses either acpid or apmd for its output; I've never figured that out since I haven't played enough with it to fully understand.

Good luck, and for posterity:  my system displays 186 processes with 1 running, and I don't notice a decrease in performance on my wimpy 1.8GHz processor :)

Yea, figured that about blurtooth.
WIMPY!!!!!!!!!!!!!!!!!!
Try mine:  P-III at 800MHtz, just under 1/2 of your power.  :lolflag:
Thats why I want to "trim the fat"

I should edit my post.  :)

Bruce

---

### Post by Tristam Green on 2008-01-14
[This]("http://ubuntuforums.org/showthread.php?t=89491") is a great tool that I was attempting to find (had to Google; Ubuntu Forum Search didn't find it for some reason).

It has a breakdown of the major services that you can and might want to turn off, and some other performance tips.

Good luck :)

---

### Post by Bruce M. on 2008-01-14
> **Tristam Green said:**
> [This]("http://ubuntuforums.org/showthread.php?t=89491") is a great tool that I was attempting to find (had to Google; Ubuntu Forum Search didn't find it for some reason).

It has a breakdown of the major services that you can and might want to turn off, and some other performance tips.

Good luck :)

I notice it is for any ubuntu version older than 6.10, but it is a very good place to start.

Thank you for this link.
Bruce

---

### Post by PeterJS on 2008-01-14
> **Bruce M. said:**
> Hi Folks,

I'm back and at this moment my computer is using 1 process of 119
I have gedit open, Terminal open, Firefox open and 2 conkys running.
Shouldn't that read at least 5 processes?

**EDIT:** I'm running a P-III, 800Mhtz **Desktop**, with 512M RAM

How can I find and eliminate some of those 119 processes that I do not need?

I started here:
From>System>Administration>Services

And the questions add up.

First column
?: don't know if I need or not (or want it)
+: means I understand, and the selection is correct
??: see added imput

second column:
*: activated
-: not activated

Services Manager

? * Actions schedular (anacron)

The cron scheduler is important, it handles automated tasks like running update manager, organizing logs, and other system task that need to be done on a schedule. You probably want to leave that running.
> 
? * Actions Scheduler (atd)

This is the back end that runs jobs setup by at. I'm pretty sure that all the system tasks use cron, so if you haven't written any scripts that use at, you can safely disable it.
> 
? - Audio settings management (alsa-utils)

If your sound is working fine, with alsa-utils disabled no need to bother enabling it.
> 
? * Automated crash reports support (apport)

This one's not so critical, all it does is send Canonical reports when things crash, for finding trends and bugs.
> 
? * Bluetooth device management (bluetooth) --> I have no Bluetooth devices

As was mentioned in other posts if you have no bluetooth devices go a head and disable it.
> 
+ - Braille display management (britty)
+ * Clock synchronization service (ntp)
? * Computer activity logger (klogd)
? * Computer activity logger (sysklogd)

I've never come across a linux machine that had it's loggers disabled, on the other hand I can't think of a technical reason they need to be on if you're not worried about monitoring system security.
> 
? * CPU Frequency manager (powermowd)

Power Manager is comprehensive power manager that sets the CPU governor, and has some hooks in to acpi power management for suspend and hibernate. If power's not a concern it's not strictly necessary.
> 
+ * Graphical login manager (gdm)
? - Hard disk tuning (hdparm)

HD Param sets up some of the configurable settings on hard drives. It improves hard drive access times, but you've really got to know what you're doing to make it work, I don't.
> 
?? * Hardware monitor (im-sensors) - will need for conky for CPU temp when I figure out how to get it going.
? * Hardware monitor (sensord)

I believe that sensord might be required for im-sensors, but don't quote me on that as a fact.
> 
? * Hotkeys management (hotkeys-setup)

Hotkey setup manges any extra funky keys you might have on your keyboard like an Internet button. If you've got no extra buttons, or don't use them it's not so useful.
> 
? - Multicast DNS service discovery (avahi-daemon)

I personally hate avahi with a passion, I've never seen it work in any beneficial sort of way, and usually causes all kinds of network trouble. What it's supposed to be is a service for broadcasting and finding services on the local network in an ad hoc fashion. Unless you have other machines on the same network running avahi, there's no point.
> 
? * Power management (acpid)

ACPI, is the Advanced Configuration and Power Interface, it handle fun stuff like powering down monitors, sleep mode, suspend, thinks like that, generally a good thing to have on.
> 
? * Power management (apmd)

APM was replaced by ACPID, so unless you've got something that you know requires amp, it's safe to disable.
> 
?? * Printer service (cupsys)

Cups is the interface that manages all print queues, drivers, configurations, etc. It's pretty much the brain of all things priting.
> 
? * Printer service (hplip)

Extensions to CUPS and drivers specific to HP printers, if you don't have an HP printer, it's not needed.
> 
? * System communication bus (dbus)

DBus is what allows programs to communicate between each other. DBus enables things like drag and drop, sharing data between applications, scripting graphical apps, and generally holds the system together. Probably should be left on. As a personal aside, learning to program with DBus is the sort of thing that drives a person mad.
> 
? - Terminal multiplexor (screen)

Screen is a handy little program that allows you to detach and reattach terminal session in different locations. What the screen service allows you to do is create screen session that multiple users can attach and share. The screen service isn't particularly useful on a single user machine, in fact it's down right useless.

> 
I see in one of the 

to use $ ps -A to get processes, so here's the output:

bruloo@The-Team:~$ ps -A
  PID TTY          TIME CMD
    1 ?        00:00:02 init
    2 ?        00:00:00 migration/0
    3 ?        00:00:00 ksoftirqd/0
    4 ?        00:00:00 watchdog/0
    5 ?        00:00:00 events/0
    6 ?        00:00:00 khelper
    7 ?        00:00:00 kthread
   30 ?        00:00:00 kblockd/0
   31 ?        00:00:00 kacpid
   32 ?        00:00:00 kacpi_notify
  108 ?        00:00:00 kseriod
  127 ?        00:00:00 pdflush
  128 ?        00:00:00 pdflush
  129 ?        00:00:00 kswapd0
  130 ?        00:00:00 aio/0
 1976 ?        00:00:03 ata/0
 1977 ?        00:00:00 ata_aux
 1980 ?        00:00:00 scsi_eh_0
 1981 ?        00:00:08 scsi_eh_1
 1995 ?        00:00:00 ksuspend_usbd
 1996 ?        00:00:00 khubd
 2335 ?        00:00:03 kjournald

These are all different kernel threads and other really low level services that the system absolutely needs.
> 
 2535 ?        00:00:01 udevd

Udev is an interesting little piece of work, udev is the lowest level of the plug and play system, it's job is to identify devices as they are connected, and then from a predefined set of rules and descriptions name and create device nodes for them.
> 
 3464 ?        00:00:00 kgameportd
 3532 ?        00:00:00 kpsmoused
 3981 ?        00:05:12 mount.ntfs-3g
 3984 ?        00:00:00 kjournald

More kernel threads, and the user space component of the ntfs driver.
> 
 4192 tty4     00:00:00 getty      --- what are all these?
 4193 tty5     00:00:00 getty
 4197 tty2     00:00:00 getty
 4198 tty3     00:00:00 getty
 4200 tty1     00:00:00 getty
 4201 tty6     00:00:00 getty

These are the actual login prompts on tty1-6, so when you press ctrl+alt+f1, that login prompt is the getty for that tty. Think of it as gdm for text logins.
> 
 4440 ?        00:00:00 acpid
 4546 ?        00:00:00 syslogd
 4603 ?        00:00:00 dd
 4605 ?        00:00:00 klogd

The top to should be familiar from above, the dd in there (I'm surprised it doesn't have the full command listed) is part of the system log that copies logs from dmesg to the various logfiles in real time.  And the klogd down at the bottom is the kernel logger itself.
> 
 4626 ?        00:00:02 dbus-daemon

> 
 4642 ?        00:00:06 hald
 4643 ?        00:00:00 hald-runner
 4649 ?        00:00:00 hald-addon-acpi
 4657 ?        00:00:01 hald-addon-keyb
 4666 ?        00:00:00 hald-addon-keyb
 4669 ?        00:00:00 hald-addon-keyb
 4684 ?        00:00:02 hald-addon-stor
 4686 ?        00:00:02 hald-addon-stor

Hal is the Hardware Abstraction Layer, it's the top part of the plug and play system and is responsible for mounting drives after udev finds them and the like.
> 
 4699 ?        00:00:00 dhcdbd
 4714 ?        00:00:00 NetworkManager
 4735 ?        00:00:00 avahi-daemon
 4736 ?        00:00:00 avahi-daemon
 4749 ?        00:00:00 NetworkManagerD

This block here are the network services, funny I seem to remember avahi being disable... Like I said it's nothing but trouble.
 4762 ?        00:00:00 system-tools-ba
 4763 ?        00:00:00 dbus-daemon
 4809 ?        00:00:00 gdm
 4812 ?        00:00:00 gdm
 4815 tty7     00:34:47 Xorg
 4820 ?        00:00:00 dhclient
 4891 ?        00:00:00 hpiod
 4900 ?        00:00:00 python
 5189 ?        00:00:00 gdomap
 5224 ?        00:00:00 sensord
> 
 5236 ?        00:00:03 wesnothd

There's one thing you can chop out, you're running a battle for wesnoth game server, why it defaults to installing itself as a system service, and not just running when you want to host a game is beyond me.
> 
 5242 ?        00:00:58 gedit
 5283 ?        00:00:00 hcid
 5305 ?        00:00:00 krfcommd
 5327 ?        00:00:00 ntpd
 5360 ?        00:00:00 atd
 5374 ?        00:00:00 cron

And there's atd, ntpd, and cron. Below here it looks all like stuff from your gnome session which is between you and gnome.

---

### Post by Tristam Green on 2008-01-14
Thanks for the thanks, Bruce :) Glad it helped a little bit.

PeterJS's post is much more in-depth and it taught me a lot also :D

---

### Post by Bruce M. on 2008-01-14
> **PeterJS said:**
> There's one thing you can chop out, you're running a battle for wesnoth game server, why it defaults to installing itself as a system service, and not just running when you want to host a game is beyond me.

And there's atd, ntpd, and cron. Below here it looks all like stuff from your gnome session which is between you and gnome.


 1. I'm printing out your post.  Most enlightening.
 2. "you're running a battle for wesnoth game server" - I am?  News to me, I just downloaded the game. I don't play anything on the web at all.  In fact I haven't played this game beyond the tutorial, and that was a LONG time ago. But I do recall getting extra scenarios, maybe that's why..  Having too much fun setting up conky and learning about Linux/Ubuntu.  I'll have to delete the game completely and then install "just the game"

  Thanks a bunch for the five star post.
 :KS + :KS + :KS + :KS + :KS + :KS

Bruce

PS: Yes, I can count!  :-\"

EDIT: Didn't need to delete all of Wesnoth.  I'm happy. :-D

---

### Post by Bruce M. on 2008-01-14
Interesting.

So far all I've done is delete Bluetooth (3 or 4 files), had to keep one or two because J-Pilot requires them and the two files for Wesnoth server ( see previous post) and my processes has dropped from 119 to 104 at the moment but was 97 when I opened Firefox.

Getting there, more work to do.

Bruce

---

### Post by Bruce M. on 2008-01-15
Hi PeterJS

> ? * Actions Scheduler (atd)
> **PeterJS said:**
> This is the back end that runs jobs setup by at. I'm pretty sure that all the system tasks use cron, so if you haven't written any scripts that use at, you can safely disable it.

The only "scripts" I'm aware of are for "Conky".  Is there a way to find out if there is a script relying on this?
----------------------------------------
> ? - Audio settings management (alsa-utils)
> **PeterJS said:**
> If your sound is working fine, with alsa-utils disabled no need to bother enabling it.

Sound only works through "Headphones" here, therefore the "Master" control on the left of the bottom panel doesn't control it.  My motherboard only has "In" "Out" and "Mic". Strangely enough the Volume buttons on my keyboard work just fine. Have tried this active and non active ... no difference.  Stays off.
----------------------------------------
? * Computer activity logger (klogd)
? * Computer activity logger (sysklogd)[/quote]
> **PeterJS said:**
> I've never come across a linux machine that had it's loggers disabled, on the other hand I can't think of a technical reason they need to be on if you're not worried about monitoring system security.
OK, I've had Ubuntu up an running for almost 6 months now, the desktop version, not the server.  A couple of months ago I installed "Firestarter" looked at the default config for the iptables (sp) and closed it.  Haven't changed a thing, haven't opened Firestarter since.  And of course even Wesnoth server is now gone. I've had no problems, and to make things worse, I have no idea where these "logs" are to even read them. Therefore I'm turning them off.
----------------------------------------
> ? * CPU Frequency manager (powermowd)
> **PeterJS said:**
> Power Manager is comprehensive power manager that sets the CPU governor, and has some hooks in to acpi power management for suspend and hibernate. If power's not a concern it's not strictly necessary.
Turned it off.  Then turned it back on, I lost Hibernate with it off.  What is "Suspend"?
----------------------------------------
> ?? * Hardware monitor (im-sensors) - will need for conky for CPU temp when I figure out how to get it going.
? * Hardware monitor (sensord)
> **PeterJS said:**
> I believe that sensord might be required for im-sensors, but don't quote me on that as a fact.
Will keep both running until I figure out how to get the temps working in Conky for CPU and HD if possible.  Once that'd done, I'll turn "sensord" off and see if it still works. If not, I reactivate it.  Simple test really.
----------------------------------------
> ? * Hotkeys management (hotkeys-setup)
> **PeterJS said:**
> Hotkey setup manges any extra funky keys you might have on your keyboard like an Internet button. If you've got no extra buttons, or don't use them it's not so useful.
Remember my sound problem above ... need the keys  :)  They all work, except "Multimedia" wants to call up Rhythmbox which is gone. As a matter of fact they work better in Linux than they did in Win2K.
----------------------------------------
> ? * Power management (apmd)
> **PeterJS said:**
> APM was replaced by ACPID, so unless you've got something that you know requires amp, it's safe to disable.
How can I find out if I have something that requires apmd?
If I disable it, can it prevent Ubuntu from working?
----------------------------------------

Well that takes care of that section, on to the next:
**First a question:** How would I stop these processes from starting or turn them off if not necessary?
----------------------------------------
> bruloo@The-Team:~$ ps -A
----------------------------------------
[quote]4626 ? 00:00:02 dbus-daemon

Looks like we missed something here.
----------------------------------------
> 4699 ? 00:00:00 dhcdbd
4714 ? 00:00:00 NetworkManager
4735 ? 00:00:00 avahi-daemon
4736 ? 00:00:00 avahi-daemon
4749 ? 00:00:00 NetworkManagerD
> **PeterJS said:**
> This block here are the network services, funny I seem to remember avahi being disable... Like I said it's nothing but trouble.
YEA, me too!  So I wonder why they are here?
----------------------------------------
> 4762 ? 00:00:00 system-tools-ba
4763 ? 00:00:00 dbus-daemon
4809 ? 00:00:00 gdm
4812 ? 00:00:00 gdm
4815 tty7 00:34:47 Xorg
4820 ? 00:00:00 dhclient
4891 ? 00:00:00 hpiod
4900 ? 00:00:00 python
5189 ? 00:00:00 gdomap
5224 ? 00:00:00 sensord

Missed these too.
I see 6 that (I think) are necessary (with my limited knowledge) and I may be wrong.  **READ:** I probably am wrong!
----------------------------------------

---

### Post by psusi on 2008-01-15
APM is an old crappy power management standard for laptops.  Unless you are running on a laptop built before 2002 or so, you can disable apmd.

Unless you are wanting to learn more about the system, I'd suggest you find more useful things to do with your time since at best, you're going to end up saving maybe 100 kilobytes of ram/swap by disabling these things.

---

### Post by Tristam Green on 2008-01-15
Does *any* power management software utilize apmd in GNOME?  I toyed with disabling apmd and acpid (always left ONE running), but was unable to get g-p-m to respond correctly afterwards.  Since my reinstall after that, I have always left both running.

I'd like to keep one or the other going, though, and nuke the other one.

---

### Post by Bruce M. on 2008-01-15
> **psusi said:**
> APM is an old crappy power management standard for laptops.  Unless you are running on a laptop built before 2002 or so, you can disable apmd.

From the original post:
> EDIT: I'm running a P-III, 800Mhtz Desktop, with 512M RAM
So I guess I don't need it.

> **psusi said:**
> Unless you are wanting to learn more about the system, I'd suggest you find more useful things to do with your time since at best, you're going to end up saving maybe 100 kilobytes of ram/swap by disabling these things.

psusi, no disrespect meant, but what's "useful" is a matter of opinion and changes from person to person, be it time, money, or something else.  Maybe you spent a lot of time getting codex files so you could rip DVD's and CD's.  I simply put them in my DVD Player and Stereo to use them. (although I can rip a DVD and CD ... did that just to learn how)

It would stand to reason that I'm trying to learn something about the system as I'm here in: Ubuntu Forums > The Ubuntu Forum Community  > Main Support Categories  > General Help  > Trimming Processes

And since I have to do something until the day I die, and I'm retired, it's my choice what to do with my time and what is or isn't valuable to me in that respect.

To be quite honest I simply never gave a thought about if  this is going save 1 MB, 100 KB or only 1 KB.  It has no bearing on it, it's the enjoyment of learning something that will help my system run a little more efficient on this old P-III.

Bruce

---

### Post by Bruce M. on 2008-01-15
> **Tristam Green said:**
> Does *any* power management software utilize apmd in GNOME?  I toyed with disabling apmd and acpid (always left ONE running), but was unable to get g-p-m to respond correctly afterwards.  Since my reinstall after that, I have always left both running.

I'd like to keep one or the other going, though, and nuke the other one.

Well, according to PeterJS:

> **PeterJS said:**
> 
ACPI, is the Advanced Configuration and Power Interface, it handle fun stuff like powering down monitors, sleep mode, suspend, thinks like that, generally a good thing to have on.

APM was replaced by ACPID, so unless you've got something that you know requires amp, it's safe to disable.

So on that advice I've had it off all day. Couldn't wait for a reply to fine out if there is a way to find out if I need it or not.  So here I am, testing, to see if I need it   :)

> So far my computer has crashed 6 times,
there's smoke coming out of the back of my cas ...
[SIZE="5"]**SLAP!**[/SIZE]

**Ooops, another Windows nightmare!**
Yes, everything is working just fine  :)
What's **g-p-m** ?

Bruce

---

### Post by Tristam Green on 2008-01-17
gnome-power-manager.  it's got a cute little battery/plug icon in the system tray in Panel #1 (the top by default) showing if you're plugged in, or how much battery life you have left.

---

### Post by Bruce M. on 2008-01-17
> **Tristam Green said:**
> gnome-power-manager.  it's got a cute little battery/plug icon in the system tray in Panel #1 (the top by default) showing if you're plugged in, or how much battery life you have left.

Oh, don't have one.  I'm a Desktop user.  :)
But good to know.

Bruce

---

