---
title: "Suddenly: &quot;Read-only filesystem&quot;"
date: 2013-09-17
forum: General Help
---

### Post by zia.newversion on 2013-09-17
So... **takes a long breath** While using the desktop, the filesystem gets remounted as read-only. All applications that rely on the filesystem stop working and dmesg (as well as other scripts running in terminal - if any) keeps complaining that the file-system is read-only. After a few seconds the system just freezes and I cannot even reboot properly, so I pull the plug and when I start the system again, at the splash, the loader says it found errors in /. If I choose to try and fix those errors, it says "*the disk drive for /tmp is not available or not yet ready*" and that I should "*continue waiting or press S to skip mounting or M for manual recovery*". I don't know anything about manual recovery, however I did try pressing M, which drops to a shell where I still cannot access anything because the filesystem is read-only. **out of breath**

I've been having this problem for about a week now. At first I thought there was something wrong with my hard drive... Turns out the hard-drive is fine. Some users experienced this problem way back in 2010 according to [this thread]("http://ubuntuforums.org/showthread.php?t=1475124&page=3&"). I was an Ubuntu user back then and I had the same hardware, too. I never encountered this problem. It's very strange that something as major (I think) as this isn't solved even after more than two years?

Also, this doesn't happen just on Ubuntu, apparently.

I've found several bug-reports, discussions and posts about this problem, but none of them lists a solution (if there is one) or whether the bug was later fixed or not. To my knowledge, the bug is still there and it's actually a bug in the kernel. How it went unnoticed from 2.6.x to 3.8.x is awfully beyond my imagination. I installed and reinstalled Ubuntu on my laptop about a dozen times during the past week. I only just started using Ubuntu again after Precise.

Can anyone advise?

---

### Post by Bashing-om on 2013-09-17
zia.newversion; Hi !

If I were in that situation ( I have been ) I would and have;
As you have installed/reinstalled and the problem persist .. indicates to me a hardware problem ->
run ubuntu's disk utility to check the hard drives health;
Would not hurt at all to obtain the hard disk manufactures' disk utility also if there is any doubt from ubuntu's disk utility.
THEN:

From a liveDVD zero out that drive with the dd tool (dd = disk destroyer)
```

sudo dd if=/dev/zero of=/dev/sda bs=1m 

```
From a liveDVD !
That command "assumes" you are working with the 1st hard drive (sda) substitute -sda- with the appropriate designation if you have more than 1 hard drive installed! 
Be very careful with dd .. it is not named disk destroyer for naught !
The use of dd is a means of last resort, however, it has proven effective for me.
It takes roughly an hour per gig to write so takes a lot of patience. If you want to get a status of where the write process is:
open up a second terminal and:
```

ps -ef | grep dd

```will yield the Process ID of both the dd command and the ps command .. the first column of numbers is what you need for next input. make sure you have the PID of "dd" and not of "ps", and in same terminal :
```

sudo kill -SIGUSR1 <the PID number>

```
each time you want an updated status.

[INDENT][INDENT]I do wish things to turn out well
[/INDENT][/INDENT]

---

### Post by zia.newversion on 2013-09-18
> **Bashing-om said:**
> zia.newversion; Hi !

If I were in that situation ( I have been ) I would and have;
As you have installed/reinstalled and the problem persist .. indicates to me a hardware problem ->
run ubuntu's disk utility to check the hard drives health;
Would not hurt at all to obtain the hard disk manufactures' disk utility also if there is any doubt from ubuntu's disk utility.
THEN:

From a liveDVD zero out that drive with the dd tool (dd = disk destroyer)
```

sudo dd if=/dev/zero of=/dev/sda bs=1m 

```
From a liveDVD !
That command "assumes" you are working with the 1st hard drive (sda) substitute -sda- with the appropriate designation if you have more than 1 hard drive installed! 
Be very careful with dd .. it is not named disk destroyer for naught !
The use of dd is a means of last resort, however, it has proven effective for me.
It takes roughly an hour per gig to write so takes a lot of patience. If you want to get a status of where the write process is:
open up a second terminal and:
```

ps -ef | grep dd

```will yield the Process ID of both the dd command and the ps command .. the first column of numbers is what you need for next input. make sure you have the PID of "dd" and not of "ps", and in same terminal :
```

sudo kill -SIGUSR1 <the PID number>

```
each time you want an updated status.
[INDENT][INDENT]I do wish things to turn out well
[/INDENT]
[/INDENT]


That was one detailed reply. Thank you very much.
I dual-boot Windows 7 and Ubuntu 13.10. When I completely re-install my system I do this

1- Perform a selective backup
2- Boot with [UBCD]("http://www.ultimatebootcd.com/")
3- Start [DBAN]("http://www.dban.org/") (Darik's Boot and Nuke) and wipe the whole disk with zeros - takes ~10 hours
4- Boot win Windows 7 disk and create a partition for Windows C: (Windows creates /dev/sda1 for Windows Bootloader and /dev/sda2 for C:)
5- Install Windows - then my drivers for Windows and a few absolutely essential applications - takes 1/2 to 2 hours
6- Download the latest LiveCD for the Linux distribution I choose (normally it's Ubuntu, but it has been Fedora, OpenSuSE, Debian, Mint and Crunchbang in the past) - takes 3-6 hours
7- Mess around in Live evnironment for a while (if the distribution is new) or install the distribution - takes 1-2 hours
8- Boot into the distribution - choose repos, aptitude update and aptitude upgrade and aptitude dist-upgrade - takes 1/2 to 2 hours
9- Install all my software (I only recently found about dpkg --get-selections and --set-selections) - takes 3-6 hours

And then I'm good to go. I don't do steps 2 and 3 every time, only after 9 to 12 months. Last time I did the whole thing 1-9 was about 2 weeks ago.

[SIZE=3]**About Testing the Disk**[/SIZE]
I downloaded and installed smartmontools last night. I just performed a smartctl -x /dev/sda and the output isn't so encouraging - meaning I'm convinced the hard-disk is shot to hell. It's a miracle how it's working as it is.

[SIZE=3]**My Questions**[/SIZE]
[LIST]
[*]How is it that Windows C: (and another NTFS D: drive) working fine if the hard-disk is so messed up?
[*]Is doing a wipe with dd any different than doing with DBAN?
[*]Should I still wipe the disk using dd when I did it with a similar tool only two weeks ago?
[*]Do hard-disks have lives, for example, can't my hard-drive be restored to an acceptable level of working standard?
[*]Is there an easy workaround to avoid having to do all 1-9 again every time? And finally ...
[*]Is anyone interested in buying a laptop with slightly damaged LCD, heating issues and now apparently a destroyed hard-drive?
[/LIST]

[I]
[COLOR=#008000]Don't take the last question too seriously, it's meant as a joke. I have a bad sense of humor.[/COLOR][/I]

---

### Post by ian-weisser on 2013-09-18
> **zia.newversion said:**
> 

[LIST]
[*]How is it that Windows C: (and another NTFS D: drive) working fine if the hard-disk is so messed up? 
[/LIST]
 
Coincidence. They are probably having significant issues that you have not noticed yet.
 

> **zia.newversion said:**
> 

[LIST]
[*]Do hard-disks have lives, for example, can't my hard-drive be restored to an acceptable level of working standard? 
[/LIST]

Hard disks contain (rapidly) moving parts, so of course it has a limited life. Even solid-state technology has a (longer) limited life.
Restoration of hard drives involves opening them up and replacing many of those moving parts. Parts, labor, and data recovery make restoration much more expensive than simply replacing the drive with new.

---

### Post by Bashing-om on 2013-09-18
zia.newversion;

There you have it from the horses' mouth - ian-weisser - !
Compared to all the time you have already spent ... a new Hard Drive is cheap !( but look at all that you have learned !)
What else can I say but ->
In a similar situation I did zero out a HD with "dd" and spared that drive off after a successful write, to use as a non-critical data disk. That disk has been in use with no problems now for about 3 years.
Do your homework on "dd" and you will be amazed what that utility can do as well as what it can teach you about the hardware configurations.
You know there are several utilities around - but most have their base in "dd" anyway - so the bottom line ... learn "dd" and use the manufactures tools to look at that disk.

There are a lot of reasons for a disk to fail ..
From what you relate there can be little doubt that that hard disk has problems ->
and there are limited solutions to bad sectors/faulty blocks. The manufactures disk utility may be able to help in moving "bad Blocks" about .. and restoring the drive to use ... but I would never fully trust that disk again.

[INDENT][INDENT]just keep on keep'n on
[/INDENT][/INDENT]

---

### Post by zia.newversion on 2013-09-19
> **ian-weisser said:**
> Coincidence. They are probably having significant issues that you have not noticed yet.

Hard disks contain (rapidly) moving parts, so of course it has a limited life. Even solid-state technology has a (longer) limited life.
Restoration of hard drives involves opening them up and replacing many of those moving parts. Parts, labor, and data recovery make restoration much more expensive than simply replacing the drive with new.

I have a slightly related question, if you know the answer. If I replace the hard-drive (since I certainly won't be able to find the same model now) how would I know if a certain model fits the slot in my laptop? (Or are there like standard dimensions or something such that I need to find a drive with Class <X> chassis, etc.)

> **Bashing-om said:**
> zia.newversion;

There you have it from the horses' mouth - ian-weisser - !
Compared to all the time you have already spent ... a new Hard Drive is cheap !( but look at all that you have learned !)
What else can I say but ->
In a similar situation I did zero out a HD with "dd" and spared that drive off after a successful write, to use as a non-critical data disk. That disk has been in use with no problems now for about 3 years.
Do your homework on "dd" and you will be amazed what that utility can do as well as what it can teach you about the hardware configurations.
You know there are several utilities around - but most have their base in "dd" anyway - so the bottom line ... learn "dd" and use the manufactures tools to look at that disk.

There are a lot of reasons for a disk to fail ..
From what you relate there can be little doubt that that hard disk has problems ->
and there are limited solutions to bad sectors/faulty blocks. The manufactures disk utility may be able to help in moving "bad Blocks" about .. and restoring the drive to use ... but I would never fully trust that disk again.
[INDENT][INDENT]just keep on keep'n on
[/INDENT]
[/INDENT]


Thank you. I'll try to study more about dd. I am planning on dragging this installation along just as long as possible. I'll have to postpone the whole procedure for now because of work commitments. But sure, I'll try it out.
The disk is a Toshiba MK5056GSYF (whatever that means) and from what I hear, Toshiba doesn't have an exceptional support system. Still, I'm Googling for "Toshiba Hard Disk Utilities" right now. Let's see what that comes to.

Thank you all (rather both) of you for helping me out. I agree with Bashing-om: it's not about getting it done anymore, it's about learning something on the way. Have a lovely day! ;)

---

### Post by ian-weisser on 2013-09-19
> **zia.newversion said:**
> how would I know if a certain model fits the slot in my laptop? (Or are there like standard dimensions or something such that I need to find a drive with Class <X> chassis, etc.)

Standard dimensions.
3.5-inch for desktops and towers and non-portables.
2.5-inch for laptops.

Make sure you get the same connector (PATA/SATA/ATA/etc.)

The disk model you wrote (MK5056GSYF) is a 2.5-inch, SATA, 500GB drive. You generally want the first two characteristics to be the same in your replacement.

---

