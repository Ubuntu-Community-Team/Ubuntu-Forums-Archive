---
title: "Please help - Kubuntu reverts to Zulu time, will not let me correct this!"
date: 2013-07-01
forum: General Help
---

### Post by gotnexusbluz on 2013-07-01
You read that correctly, and it's not an allegation that I would make without an investigation first.

At some point, Kubuntu began doing this. Yes, I went through the Settings Date/Time dialog. First I tried the "Set time automatically" option, which it ignored (yes I did hit the Apply button), and then it accepted a manual change of the clock time (not the time zone) until the session expired (always going back to Zulu time (if that's what it's called), or four hours ahead of Eastern Standard Time when the system rebooted).

Somebody on a thread somewhere in the past alluded to the BIOS clock settings, so for what it's worth I checked this. I corrected my BIOS clock by knocking it back four hours, and then I booted into Windows.

In Windows, I surfed the net for about an hour, noting that my Windows time was problem-free throughout that session. But when I rebooted back into Kubuntu, I saw the time change again back to Zulu (on my panel widget), right before my eyes, within seconds after the system dropped the splash screen! 

I'm no qualified geek, but I have used all other variants of Ubuntu, plus other distros on my current laptop, and none have done anything quite so strange. That said, after Shuttleworth's unilateral Unity insanity left me with the choice between Kubuntu,  not-so-stable Xubuntu, or less-supported distros with the same environment problems, Kubuntu is my last-ditch effort to make Linux work for me before I head back to Windows permanently. I really don't want to do this because there are so many ways in which Linux, and specifically Ubuntu is superior to other systems, but too many inane surprises are a dangerous threat to my sanity! It should be better-designed, and it is, but it has to do what it's supposed to as well! That said, I am impressed that this is the first (and the most serious) problem which I have encountered with Kubuntu within the month that I've been using it, so given that I can set the clock straight and there aren't more nasty surprises, I think I'll keep this system for a couple of years. Can anyone help me with this?

---

### Post by Impavidus on 2013-07-02
I know the expression Zulu time. And I think Xubuntu is quite stable (I use it), but Unity is still better than returning to Windows.

There is a difference between how Ubuntu and Windows set the bios time. Windows sets it to local time, Ubuntu by default to UTC, but this can be changed in /etc/default/rcS. Check what's in that file. This is often the cause of time mix-ups in dual boot systems.

I don't have Kubuntu, so I can't tell you how to change time zone and time using the gui.

---

### Post by gotnexusbluz on 2013-07-02
> **Impavidus said:**
> I know the expression Zulu time. And I think Xubuntu is quite stable (I use it), but Unity is still better than returning to Windows.

There is a difference between how Ubuntu and Windows set the bios time. Windows sets it to local time, Ubuntu by default to UTC, but this can be changed in /etc/default/rcS. Check what's in that file. This is often the cause of time mix-ups in dual boot systems.

This is my rcS file under that path, and the "UTC=no" line was unchanged before I put the # in front of it:
```

#
# /etc/default/rcS
#
# Default settings for the scripts in /etc/rcS.d/
#
# For information about these variables see the rcS(5) manual page.
#
# This file belongs to the "initscripts" package.


# delete files in /tmp during boot older than x days.
# '0' means always, -1 or 'infinite' disables the feature
TMPTIME=0


# spawn sulogin during boot, continue normal boot if not used in 30 seconds
SULOGIN=no


# do not allow users to log in until the boot has completed
DELAYLOGIN=no


# assume that the BIOS clock is set to UTC time (recommended)
# UTC=no


# be more verbose during the boot process
VERBOSE=no


# automatically repair filesystems with inconsistencies during boot
FSCKFIX=no

```
Before I told the system to ignore that "UTC=no" command, it was ignoring my settings and changing the clock back to UTC at startup, and after I changed it it still does the same after a reboot (no matter what I tell it to do in the GUI). Not much else to see in this file - are there others culprits that you can think of?


> **Impavidus said:**
> [QUOTE=Impavidus;12714712]

I don't have Kubuntu, so I can't tell you how to change time zone and time using the gui.

You don't have to - I do know how to find my way around typical GUI features! The problem (as stated already) is that the GUI is mostly ignoring what I tell it to do. It ignored my applied selection for Eastern Time. When I addressed the clock numbers and ticked back the hour by four, it did not ignore that, but after the reboot something else again reset my time to UTC. It's annoying enough that some part of this system, which I installed for Eastern Time (just as I had installed all other Linux distros, including many Ubuntu flavors), still wants to presume that nobody on my side of the ocean would be using Ubuntu, but it's far worse when most people ignore my question for the same bad reading comprehension - nobody reads the whole of any posts anymore!

---

### Post by Impavidus on 2013-07-03
I just saw that my gui has the time zone set to central European time, although my clocks run at UTC, as intended. This means my xfce gui doesn't properly adjust the time zone either. I don't know exactly how it works, but it seems time zone settings are controlled by the files /etc/timezone and /etc/localtime.
/etc/timezone contains the path to the file describing the time zone minus the /usr/share/zoneinfo/ (in my case UTC, in your case it should be something like EST or EST5EDT or America/New_York or whatever you want exactly), the file /etc/localtime is identical to that file describing your time zone. You may be able to fix your issue by manipulating those files, but I have to admit I modified them myself in the past so this may not be the correct way. It seems to work though.

/etc/default/rcS should contain UTC=no on windows dual boot machines. If not dual booting with windows it should contain UTC=yes.

---

### Post by SeijiSensei on 2013-07-03
Check the hardware clock with "hwclock".  If it is set to the wrong time zone, reset it by first running "ntpdate" to get the correct system time, then running "sudo hwclock --utc --systohc" to reset it.  If it needs to be set to local time to conform to Windows use "--localtime" rather than "--utc".

---

### Post by gotnexusbluz on 2013-07-03
> **Impavidus said:**
> I just saw that my gui has the time zone set to central European time, although my clocks run at UTC, as intended. This means my xfce gui doesn't properly adjust the time zone either. I don't know exactly how it works, but it seems time zone settings are controlled by the files /etc/timezone and /etc/localtime. /etc/timezone contains the path to the file describing the time zone minus the /usr/share/zoneinfo/ (in my case UTC, in your case it should be something like EST or EST5EDT or America/New_York or whatever you want exactly), the file /etc/localtime is identical to that file describing your time zone. You may be able to fix your issue by manipulating those files, but I have to admit I modified them myself in the past so this may not be the correct way. It seems to work though.  /etc/default/rcS should contain UTC=no on windows dual boot machines. If not dual booting with windows it should contain UTC=yes.  These files seem to display what they are supposed to, with the exception of /etc/localtime which does not exist on my system. /etc/timezone does, and it's contents are  ```
 America/New York 
``` Should such a file contain more code that's missing?  I had looked at /etc/default/rcS previously, and it did say "UTC=no" where it was supposed to. But I believe the condition of at least one of these files is due to the fact that I was able (within the session that I am now running) to use the GUI to tick back my time by four hours. The problems were that other time operations, such as selecting a time zone (which was ignored when I selected New York - Eastern Time and pressed the Apply button) have been ignored. Also, the change which I have been able to make lasts only for this session - something is causing my system to revert to UTC with every new session, and whatever that is it's going to ignore these files just as it had before. Can you think of a different cause? Can it possibly be that file which is missing?

---

### Post by gotnexusbluz on 2013-07-03
> **SeijiSensei said:**
> Check the hardware clock with "hwclock".  If it is set to the wrong time zone, reset it by first running "ntpdate" to get the correct system time, then running "sudo hwclock --utc --systohc" to reset it.  If it needs to be set to local time to conform to Windows use "--localtime" rather than "--utc".  I looked at the "hwclock" specifications, and they look appropriate. But I think this is due to the fact that I have ticked back my hour setting by four in the GUI. Something is wrong which has caused the system to ignore other time-related GUI actions, e.g. after I select "New York Eastern Time" and press the Apply button, this action is ignored (UTC is still displayed in my panel widget). Also, although ticking back the hour may change files for this session, at every new session the system reverts to UTC - there must be something else it follows at startup that causes this! Any more guesses (getting pretty desperate here, and I hate to dump this install after so much time loading apps and configuration hours).  Also, I fear I may be misunderstood concerning Windows - if it's presumed that this only happens after a Windows session, that was an exception - this happens at every new Kubuntu session irreguardless.

---

### Post by Impavidus on 2013-07-04
Maybe it's the missing /etc/localtime, maybe it's the fact your /etc/timezone contains "America/New York" and not "America/New_York", but I'm guessing here. You could experiment a bit, but I cant help you further.

---

### Post by gotnexusbluz on 2013-07-04
I may have a clue here for those who can interpret it, but first to be clear on the file content:

Whoops, I stand corrected on the file /etc/localtime being missing this was presumed so when I called it up from the Terminal without checking to see if it had a Dolphin listing. What did in fact happen when I entered  ```
 sudo kate /etc/localtime 
``` is I got an empty file. As I have seen it with text editors, when you give one a nonexistent file name through Terminal, it will handle this by creating a new file of whatever name you give it, therefore this is what I had presumed happened. I didn't save it, therefore this empty file must have been there previously. Of course, this makes it no less strange to me that anyone (it would have been the software develper or his installation system, it sure wasn't me) could ever save an empty file!    

Whoops again - the lack of an underscore in line "America/New_York" in the file /etc/timezone was my typo on this forum. It is not missing from the file text, and I never altered what is there.   

Here's something I noticed just now, which may hold the answer for one who would understand it - when I tell Terminal to open these files (which it does), I still get these errors: ```
 Satellite-L305:~$ sudo kate /etc/timezone 
[sudo] password for dave:  
QDBusConnection: session D-Bus connection created before QCoreApplication. Application may misbehave. 
Error: "/var/tmp/kdecache-davos" is owned by uid 1000 instead of uid 0. 
Error: "/tmp/kde-dave" is owned by uid 1000 instead of uid 0. 
``` 
Something very definitely is misbehaving - is this a clue to what needs fixing? Can it be fixed?

---

### Post by SeijiSensei on 2013-07-04
That's the standard complaint from X Windows and KDE about trying to spawn a graphical application that is running with root privileges on a non-root-user's desktop.  To do so it has to write some files in /tmp and /var/tmp and discovers that they already exist and are owned by dave.  At that point, kate punts.

Use a text editor like nano instead:  "sudo nano /etc/timezone".  Nano has menus at the bottom of the screen.  Basically you will enter the text, then hit Ctrl-S to save the file and Ctrl-X to exit.

---

### Post by Impavidus on 2013-07-05
It's a binary file, so no text editor will be really useful.

---

### Post by SeijiSensei on 2013-07-05
Sorry, I meant /etc/timezone.  That's a file with just the zone string.  Mine reads "America/New York".

---

