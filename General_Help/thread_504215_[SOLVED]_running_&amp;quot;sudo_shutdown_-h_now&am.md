---
title: "[SOLVED] running &amp;quot;sudo shutdown -h now&amp;quot; doesn't shutdown, it restarts!?"
date: 2007-07-18
forum: General Help
---

### Post by moore.bryan on 2007-07-18
[I]i recently did a feisty server install to my laptop and am running openbox.... so, i added "sudo shutdown -h now" to my menu, just as i have it on my desktop, but when i run shutdown, the laptop just restarts.  i've also tried the "sudo halt" command; same thing.  "sudo shutdown -P now" restarts as well.

any ideas?
[/I]

---

### Post by trak87 on 2007-07-18
"sudo shutdown -h now" is what I use and it works. What happens when you run it from the command line rather than from the menu? You many need gksudo instead of sudo when running from a menu. sudo is for the terminal and gksudo is for the GUI.

---

### Post by moore.bryan on 2007-07-18
[I]command-line restarts as well... tried the gksudo choice, too.
[/I]---------------
[I]EDIT
------------------
alright... tried the following (all from cli):
sudo shutdown -H now
sudo shutdown -P now
sudo shutdown -HP now
sudo shutdown -h -P now
sudo shutdown -H -P now

ALL of the above choices simply rebooted the machine; however, sudo poweroff shut the thing down without even shutting-down x.  now, i'm REALLY confused.
[/I]

---

### Post by bettlebrox on 2007-07-19
Odd indeed.

How about "sudo init 0" ?

---

### Post by moore.bryan on 2007-07-19
> **bettlebrox said:**
> Odd indeed.

How about "sudo init 0" ?
*that immediately restarts my machine.  could it be something funny in my /etc/event.d/rc0 file?*

---

### Post by UJoe4 on 2007-07-19
I was having a slightly different problem on my desktop: Shutting down would log me out, etc, but not actually power off the machine. (It wouldn't restart either, it would just sit there.) Turns out it was because my BIOS is dated 1999 and ACPI doesn't load automatically unless the BIOS is from 2000 or later. Followed a suggestion from an old thread and added "acpi=force" to the end of the kernel line in GRUB, and it now works fine.

Worth a try if you have an old BIOS.

---

### Post by p_quarles on 2007-07-19
My server runs an older BIOS, as well, and I've found that I need to use both -P and -h to shut it off. Like so: ```
sudo shutdown -Ph now
```
Worth a try.

---

### Post by moore.bryan on 2007-07-19
> **UJoe4 said:**
> I was having a slightly different problem on my desktop: Shutting down would log me out, etc, but not actually power off the machine. (It wouldn't restart either, it would just sit there.) Turns out it was because my BIOS is dated 1999 and ACPI doesn't load automatically unless the BIOS is from 2000 or later. Followed a suggestion from an old thread and added "acpi=force" to the end of the kernel line in GRUB, and it now works fine.

Worth a try if you have an old BIOS.
*i think you and i found the same thread... ;-)  tried the acpi=force "trick," no dice.  i have a BRAND new lenovo thinkpad z61e, so i don't think it's the bios being old, but that's worth a shot...*
> **p_quarles said:**
> My server runs an older BIOS, as well, and I've found that I need to use both -P and -h to shut it off. Like so: ```
sudo shutdown -Ph now
```Worth a try.
*yeah, i've tried that one... strange.*

---

### Post by Nythain on 2007-07-19
how about just
sudo shutdown now
with no options

---

### Post by moore.bryan on 2007-07-19
> **Nythain said:**
> how about just
sudo shutdown now
with no options
*it shuts-down x, but locks from there and asks for the root password for disk management.*

---

### Post by moore.bryan on 2007-07-19
[I]could it be acpi isn't permitted in the kernel?  i tried to install the acpid package and got a boatload of errors about it not being able to be started...
-------
EDIT:
-------
never mind... i check my kernel configs and acpi is supported.  i've been able to install acpi, acpid, and acpi-supports, but still no luck.  i've added every possible choice to acpi= in the kernel boot, but--again--nothing.  this is really irritating and something which, logically, shouldn't be happening.
[/I]

---

### Post by moore.bryan on 2007-07-19
[I]so, here's another one for the community:
changing nothing, altering nothing, editing nothing, "sudo poweroff now" reboots now.  HUH!?  i'm beginning to think my machine is possessed.  :x

how about this... can anyone point me to the exact files/scripts which are called when one issues the "sudo shutdown -h now" command?  i've already gathered the stuff in /etc/rc0.d and /etc/event.d/.  more specifically, could someone post the files used and attach copies of those files so i can compare mine?

the ONLY difference to the machines is the one which won't shutdown is running a wireless connection using the madwifi drivers.
[/I]

---

### Post by moore.bryan on 2007-07-23
*is everyone out there running ubuntu on a newer lenovo successfully and this is just an isolated problem?  the linux-thinkpad mailing list suggested it's a kernel problem, but i don't think so because my desktop running the same setup shuts-down properly.  so... could this be a hardware issue?  if so, could i get some brainstorms (or at least brain-drizzle) about where to look for a solution?  not necessarily a website, but just ideas...*

---

### Post by p_quarles on 2007-07-23
Okay, I'll throw out some ideas that come to mind. 

1) Did you install this system with the same CD that you used with the system that's shutting down correctly? If not, it could be a problem with the kernel due to a download/burn error.

2) The BIOS. Have you tried fiddling with the relevant settings and/or updating it? 

3) Did the laptop come with a Windows OEM installation? If so, did it shut down properly when that was installed? (if yes, then it's likely an OS problem; if not, it's BIOS or hardware)

4) I've never actually *tried *to install any alternatives to bash, but I know they're out there. It might be worth seeing if another CLI gets it to work. 

Probably not that helpful, but it's all I can think of. Good luck.

---

### Post by moore.bryan on 2007-07-23
*first off, thanks "hal;" i was beginning to think no one was checking on this thread.  ;-)*
> 1) Did you install this system with the same CD that you used with the system that's shutting down correctly? If not, it could be a problem with the kernel due to a download/burn error.*same cd... good thought, though...*
> 2) The BIOS. Have you tried fiddling with the relevant settings and/or updating it?*at first, i actually figured it was the bios, so i updated it to the most current (written in may, posted on the lenovo website in june)*
> 3) Did the laptop come with a Windows OEM installation? If so, did it shut down properly when that was installed? (if yes, then it's likely an OS problem; if not, it's BIOS or hardware)*my xp pro shuts-down, restarts, and even suspends/hibernates fine.*
> 4) I've never actually *tried *to install any alternatives to bash, but I know they're out there. It might be worth seeing if another CLI gets it to work.*other cli's?  what do you mean?  xterm vs. aterm?  i'm a bit confused...*
> Probably not that helpful, but it's all I can think of. Good luck.*don't sell yourself short, this is exactly the kind of feedback for which i was looking... i've been "staring" at this problem so long, i wanted "fresh eyes."  once, again, thanks so much for your insight!*

---

### Post by p_quarles on 2007-07-23
> *first off, thanks "hal;" i was beginning to think no one was checking on this thread.  :wink:*You're quite welcome, Dave. :)

It definitely sounds like a software problem, with Linux. This would be a serious pain, but you might be able to get it working with a Linux distro that uses either a newer or older kernel version than the one used by Ubuntu. You might even just install the current beta of Gutsy Gibbon (on a new partition) -- it's currently unstable, but it's supposed to come with several improvements for laptop power management. If I were in your position, I would at least want to know whether the next version of Ubuntu would solve the problem.

The alternative shell thing was really a shot in the dark, but maybe worth a try. Bash is one of several shells based on bsh (Bourne Shell). Another is the Almquist shell, which has a Debian specific version called dash. The commands are (so I've read) virtually the same.

---

### Post by moore.bryan on 2007-07-23
*i've already tried compiling my own kernel (2.6.22.1), but that didn't shutdown properly either.  the alternative shell sounds interesting... could it be a bash issue?  if that's the case, i should be able to reinstall it, shouldn't i?*

---

### Post by p_quarles on 2007-07-23
Reinstalling bash might work, but I wouldn't trust apt to get it right. I mean, apt just isn't very good and reliably removing every part of a program, and beyond that, removing the shell could very well break your installation. 

My thinking is that this really is a power management issue (because Ubuntu is kinda bad at that). But, if you want to test the shell, I think you should try to find a .deb of dash and install that.

---

### Post by moore.bryan on 2007-07-24
[I]according to [wikipedia]("http://en.wikipedia.org/wiki/Debian_Almquist_shell"), as reliable as that may/may not be, ubuntu uses dash by default:
> [/I]dash is a modern replacement for [ash]("http://en.wikipedia.org/wiki/Almquist_Shell") in the [Debian]("http://en.wikipedia.org/wiki/Debian") project, and (as of the 6.10 release) is the default /bin/sh in [Ubuntu]("http://en.wikipedia.org/wiki/Ubuntu_%28Linux_distribution%29").**

---

### Post by p_quarles on 2007-07-24
Wikipedia's usually pretty reliable for tech information (given the userbase and all). That's news to me, though.

I ran "man" for both bash and dash, and they produced different pages, so it would appear that dash is indeed installed. Whether it's a default, or whether running "the shutdown" command in one or the other would make a difference, I don't know. 

You could try, though. "sudo [d/b]ash" to run both shells as root, and then see what happens.

---

### Post by qamelian on 2007-07-24
> **p_quarles said:**
> Wikipedia's usually pretty reliable for tech information (given the userbase and all). That's news to me, though.

I ran "man" for both bash and dash, and they produced different pages, so it would appear that dash is indeed installed. Whether it's a default, or whether running "the shutdown" command in one or the other would make a difference, I don't know. 

You could try, though. "sudo [d/b]ash" to run both shells as root, and then see what happens.

Actually, dash has been the default shell on Ubuntu for a while now which has the unfortunate effect of breaking some scripts and applications that expect the shell to be bash. There are workarounds but it's still annoying.

---

### Post by azc on 2007-07-24
Regarding the shutdown problem, here's something else I've tried, and so far (a couple of time) it's shutdown properly. (So far anyway...)

References:
[http://www.debian.org/releases/stable/i386/release-notes/ch-information.en.html](http://www.debian.org/releases/stable/i386/release-notes/ch-information.en.html)
[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=390547](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=390547)

Added:
acpi=off apm=power_off
To the kernel command line in /boot/grub/menu.lst

-and-

Added:
apm power_off=1
To /etc/modules

Of course, after I post this the darn thing won't shut down tonight lol.

---

### Post by moore.bryan on 2007-07-24
> **azc said:**
> Added:
acpi=off apm=power_off
To the kernel command line in /boot/grub/menu.lst

-and-

Added:
apm power_off=1
To /etc/modules

*system won't start with acpi=off and apm is not enabled in the 2.6.20-16-server kernel.  i'll try this after i recompile the 2.6.22.1 kernel (which hadn't worked before either).*

---

### Post by yorkie on 2007-07-25
Try  sudo shutdown halt

---

### Post by moore.bryan on 2007-07-25
> **yorkie said:**
> Try  sudo shutdown halt
[I]"halt" isn't a "legal" time... it does nothing...
i'm beginning to think this is an error with the thinkpad drivers.  i really don't get it, though.  NO ONE on the linux-thinkpad mailing list is having this problem.  in fact, one suggested it is LITERALLY just my machine.  weird.
[/I]

---

### Post by p_quarles on 2007-07-25
The above command was missing a time parameter, but I don't think it'll work anyway, because it's the same as shutdown -h.

But it did give me an idea:
```
sudo shutdown -P +1
```
Which tells it to power off after waiting one minute. I think it's *very *unlikely that this will act any differently, but thought I'd offer it anyway.

And one more: does the same thing happen if you log out of Gnome, and then use the login screen's power down function? 

It sounds like this problem is pretty deep down in the OS, so none of these "alternative" shutoff commands are likely to do anything, but it doesn't hurt to exhaust all of them.

---

### Post by moore.bryan on 2007-07-25
*i've tried setting the time differently, but to no success.  i don't run gnome... it's a straight server-install with openbox as my wm.*

---

### Post by moore.bryan on 2007-07-25
*okay, so on a whim i thought i'd try something...```
sudo halt -fp
``` shuts-down my system immediately; therefore, i'm beginning to think the fault lies in my shutdown scripts, since "halt -f" doesn't call shutdown.*

---

### Post by moore.bryan on 2007-07-25
[I]SOLVED!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

(can you tell i'm excited?)

after much research and playing, i decided to take a much deeper look into what's happening in my /etc/rc0.d directory and something caught my eye; a symlink to reboot.  i thought that strange because rc6.d handles reboots and rc0.d is supposed to handle shutdown... it was a K10reboot link.  removed it and voila, the machine shuts-down properly!

yee-haw.  thanks to all of you who added suggestions; you kept me going when i thought all might be lost.  this community is the only reason i've stuck in here this long!
[/I]

---

### Post by p_quarles on 2007-07-25
Wow, that's crazy. Any idea how that symlink got there? 

I think that's my favorite thing about Linux, though: configuration settings are in text files, and those files contain clear file paths to everything else it interacts with (in most cases). I wouldn't even know where to begin with a problem like this in Windows, and I've used that for far longer.

---

### Post by moore.bryan on 2007-07-25
*no idea.  in my other machine, there's one too, but i've never had this problem over there.  whatever the case may be, you're right: thank the good developers for keeping things "verbose."*

---

### Post by MarkusSchulte on 2007-07-30
Hi,

a User and myself are having the problem discussed here. When shutting down the system, it restarts instead. Both of us are already using ACPI, and tried kernel-boot options mentioned here, but it doesnt help. "sudo halt -fp" causes my machine to restart, his to crash. I checked my /etc/rc0.d, it seems to be normal (at least there is no symlink to reboot), well my mate's /etc/rc0.d is empty (^^).

Here is the syslog when i enter "sudo shutdown now": [Link to syslog]("http://www.uni-koblenz.de/~markuss/syslog.txt")

```
ul 30 21:12:13 KLJB gconfd (kljb-7495): Signal 15 erhalten, ordungsgemäßes Herunterfahren
```
means: received Signal 15, shutting down correctly

```
Jul 30 21:12:13 KLJB gconfd (kljb-7495): Beenden
```
means: shutdown

```
Jul 30 21:12:23 KLJB exiting on signal 15
Jul 30 21:14:11 KLJB syslogd 1.4.1#20ubuntu4: restart.
```
Well i dont get this lines. Exiting on signal 15, but still restarting...

Greetz from Germany ):P and thx for your help

---

### Post by MarkusSchulte on 2007-08-02
Öhm, any suggestions?

---

