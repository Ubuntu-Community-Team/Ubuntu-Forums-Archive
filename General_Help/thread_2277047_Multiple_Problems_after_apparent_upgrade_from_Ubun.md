---
title: "Multiple Problems after apparent upgrade from Ubuntu 14.04.1 to 14.04.2"
date: 2015-05-06
forum: General Help
---

### Post by crazybear on 2015-05-06
While I see a few [2-3] other posts that might overlap with my problems, I'm not sure - so starting this one. Sometimes I check what is to be installed and other times I absentmindedly just click 'install' to whatever the Update Manager lists. About two weeks ago, I did the absentminded click [before morning coffee]. When it started to install I noticed it was a HUGE download involving MANY installs and/or upgrades. I clicked on the 'details', as I grew more worried. I noticed some error messages in terminal and seem to remember flgrx being in them. Shortly after that 'upgrade' or 'update' [I really am not sure what it was], my 14.04 basically ceased to function. 

Lucky for me, I have most of the same materials also on a 12.04 system - and used that for two weeks [how long it took to get the 14.04 working - well, partly working - it is still NOT really working yet]. The OS collapsed and turned itself off. I started it up again and it wouldn't boot. I used the latest boot repair disk and got no positive result. I then thought to delete the kernels and re-install the latest. Big mistake! The boot repair disk deleted ALL kernels - I'll NEVER choose that option again!

I finally found a posted way to install the latest kernel using a live CD and did so - not being easy, as the instructions were incomplete, but did finally find a way using the instructions [such as they were] plus internet searches as I went along. So, finally I had grub re-installed and the latest kernel installed.

However, when I try to boot from the disk, with very even timing the entire three head monitors go dark and then on again....about 75% on, 25% off. This seemed like clue two to me that some new video driver was the problem. A search showed that about that date 14.04.2 with new hardware support stack had been offered. Had I not noticed and selected that? I don't know. I see that there were many who had problems after that distribution upgrade.

Somewhere along the line in the two weeks, I also using a live CD terminal ran dist-upgrade, so assume I now have 14.04.2. 

Questions: How do I know if I have the new hardware stack? How do I test if some new video driver [or an old one] now is causing the blinking of the screens [I never had any problems along these lines before!], but getting only into TTY terminal - it won't boot into the OS. I have a MSI Radeon HD-7970 video card. I thought I was using AMD drivers [which I remember took many days to install properly, but once installed worked flawlessly - until now]. I'm a bit confused by what this thread is trying to get at [HERE]("https://askubuntu.com/questions/618575/how-do-i-find-the-current-stable-kernel-hwe-for-14-04-2") about old 14.04.1 kernels vs. new 14.04.2 kernels - and what I need to do regarding them. Then there is this launchpad bug report [HERE]("https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/1424491") that might also involve me, I'm not sure. 

I can't really use my 14.04 now without getting into it with a live CD or the TTY terminal - but I'm asking in what order should I explore the problem[s]. Lastly, for my video card I see endless certainties posted that one should/should not use/not use the AMD drivers vs. the more generic Ubuntu ones. I'm rather confused on that too - and it may well be at the heart of the problem now....though it was NOT before.

Thanks for any ideas or pointers. I'm not sure what diagnostic things to ask in terminal to narrow down the problem[s]. Nor, what things to do to stop the blinking and boot into the OS. Please, no 'fresh install' suggestions. That will be the very last thing I'll attempt. I had a LOT of special things/programs/etc. set up and a fresh install would cancel out a year's work I don't relish trying to recreate.

---

### Post by QIII on 2015-05-06
Hello!

The bug you cited is definitely where you are -- notice who reported the bug.  :)

Generally when you do an in-place point-release upgrade or a major release upgrade you should uninstall all third-party hardware drivers beforehand.

You'll need to do that now.  

Since you can't get to the GUI desktop, you'll have to do the following from the command line to get back to the desktop:

Issue the following commands in the terminal (use sudo only if you are not dropped to root):

```
sudo mount -o remount,rw /
```

That will get you into read/write mode, which you need to uninstall the fglrx driver.

Then

```
sudo apt-get purge fglrx fglrx-updates fglrx-amdcccle fglrx-amdcccle-updates
```

It is best to specify all four, since the package manager will sometimes try to install the -updates version if you uninstall the regular version and vice-versa.

On reboot, you should be able to get back to your desktop.

Then follow my instructions in post #77 in the bug report if you want  the AMD driver.  **When the bug status is "FIXED"**, you can remove the  -proposed repo, and do

```
sudo apt-get update
```

followed by 

```
sudo apt-get dist-upgrade
```

to go back to the package in the main repo -- which will by then be fixed.

---

### Post by crazybear on 2015-05-06
Thanks. Yes, I saw your thread, but was unsure if I was also so affected - I guess I am. What is not clear to me is, correct me if I'm wrong, that the bug is not yet fixed....and hopefully will be soon...but until then what will be the driver for the video card? - the Ubuntu one in Xorg? 

Also, maybe or maybe not also an issue, I was just checking and on that OS 14.04.2 I still have the 3.13.0-52-generic kernel, but understand that a clean install with 14.04.2 gives one different, newer kernels......should I get these now, or...?

---

### Post by QIII on 2015-05-06
If you uninstall fglrx, you will fall back to the open source Radeon driver - which is what is running on a fresh Ubuntu installation.  Do that before we get wrapped around the axle on the other stuff.  Then we can move on.

If, after you reboot, you still can't get to your desktop, don't panic.  Thay just means you'll need to reinstall the mesa packages, too.

---

### Post by crazybear on 2015-05-07
Ugh! What a huge mess-up on the part of some - having sent this out to everyone. How many must have been affected?! Anyway. For me, it is not going to be so easy, I can see....

When I tried [COLOR=#000000][FONT=Ubuntu Mono]sudo mount -o remount,rw /       I got an error message: line 9 in etc/fstab is bad

I tried gedit, but gedit wouldn't work in that environment....what editor will? Also, I'm not sure what I'll need to do with line 9. Can I make a new generic etc/fstab for now - just to get in? How? Thanks. I tried the next line [purging the drivers], but I was unable to boot into the OS, I got the TTY terminal and couldn't do anything much.[/FONT][/COLOR]

---

### Post by QIII on 2015-05-07
If you can't mount rw, you can't change anything, including un-installing the fglrx driver.

By the way, vi is the command line editor installed by default, but you have to know what you are doing with it.  nano is one of the first things I install after I install Ubuntu.  I may be old, but doing things old school just because it's cool and "linuxy" is silly.

OK.  Since you are not able to mount rw and you can't use your browser from the command line, could you boot a LiveCD/USB and use gedit to copy and past the contents of fstab back here?  You should be able to edit the file from a live session, but let's have a look at it first.

Edit:  By the way, when you post that back, please put it between code tags so it's easier to read.

1. If you are using the "Reply to Thread" button - highlight text and use the # button in the text box header.  Alternatively, click the # button first, place your cursor between the code tags and type or paste your text.

2. If using "Quick Reply" then type [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.  The square brackets are required.

---

### Post by crazybear on 2015-05-07
Didn't understand what you expected me to put in 'code tags' - so can't reply to that.
Line 9 is the UUID of the /dev/sda1 [there is also another UUID of the swap file]
I'm not good at this stuff and the hell of it is..when one is 'there' in TTY or kernel editor [if that is what it is called] there is precious little one can do to look things up...other than the man xyz, which often is more confusing [to me] than of help.
I thought I could get the new UUID, but couldn't save it under nano. I didn't try vi. This is exhausting.......as I have to keep switching back to another OS just to find options and information. Yes, a live CD would perhaps work better, as one can use a browser, but I'm not very good/knowledgeable about how to chroot and all that - what I need to mount and not mount. Such information is hard to find, as all you linux geeks know that from your mother's milk and forget that some of us need to learn that from first principles.... Nano told me I was in read only mode, but looking through man nano I found no way to be in a mode where I could change things and save the changes. I'm exhausted. I also don't know how to ask the UUID of a specific part [such as the /dev/sda1] vs. the UUID of the entire disk.

---

### Post by Bucky Ball on 2015-05-07
-52 is the correct kernel, just getting back to your earlier question. In other words, nothing amiss there, you are in the correct place, carry on ... ;)

---

### Post by QIII on 2015-05-07
OK. If you can't get to it graphically and won't use the Live media as I suggested please get to line 9 in the terminal via vi 

```
vi /etc/fstab
```

and snap a picture with your cell phone to post back here.

There is some sort of error.  The line is probably malformed, such as a misplaced comma or something.

And again:  since you cannot mount rw (read/write) you cannot make any changes to your system.  We need to see line 9 to know what to fix, then we can talk you through doing that in a Live session.

---

### Post by crazybear on 2015-05-07
> **Bucky Ball said:**
> -52 is the correct kernel, just getting back to your earlier question. In other words, nothing amiss there, you are in the correct place, carry on ... ;)


I know that is the one that one gets when updating from 14.04.1, but it is NOT the one that ships with a new install of 14.04.2 - wouldn't the newest kernel be best?! Is there any harm in having it? My 12.04.5 now has the kernel that is 'for' 14.04 without any apparent problem.

---

### Post by crazybear on 2015-05-07
> **QIII said:**
> OK. If you can't get to it graphically and won't use the Live media as I suggested please get to line 9 in the terminal via vi 

```
vi /etc/fstab
```

and snap a picture with your cell phone to post back here.

There is some sort of error.  The line is probably malformed, such as a misplaced comma or something.

And again:  since you cannot mount rw (read/write) you cannot make any changes to your system.  We need to see line 9 to know what to fix, then we can talk you through doing that in a Live session.

I'm one of the few people on the Planet who refuses to get a smart phone. My work needs for NSA/GCHQ and others like that to not spy on me wherever I do/go/say [more than they already do]. But I digress...

vi is not user friendly to a novice. I couldn't even get out of it except to reboot! 

The line #9 has a **UUID** [ its for /dev/sda1 (there is another two lines below for swap), but don't know if a correct one or not]** /    ext4    relatime,   [COLOR=#0000cd]errors=remount -ro 0[/COLOR] **(a space) **      1**

---

### Post by QIII on 2015-05-07
3.16.0-30 is the current kernel for 14.04.2 [I]with the HWE stack.

[/I]Bucky Ball is saying you are OK right now with your 3.13 version.  14.04.2 without the HWE stack - where you are right now because of this problem you are having -- is expected.  Don't worry about that for the moment.  We need to get you back to your GUI by getting you back to mounting rw in the terminal so we can un-install the fglrx driver before worrying about *anything* else.  We'll deal with the rest in due time.

So, we need to look at line 9 of /etc/fstab so we know how to proceed.

---

### Post by QIII on 2015-05-07
is that 

```
errors=remount -ro
```

or 

```
errors=remount-ro
```

Is that 

```
UUID=somerandomstring
```

It is important to know *exactly *what that entire line says, verbatim.

---

### Post by crazybear on 2015-05-07
> **QIII said:**
> is that 

```
errors=remount -ro
```

or 

```
errors=remount-ro
```

Is that 

```
UUID=somerandomstring
```

It is important to know *exactly *what that entire line says, verbatim.

It is errors=remount  -ro (with a space after t and before -)
..and it is a unique and normal UUID (I think I'm familiar enough with UUIDs to say it is one {right format and number of digits} - only not sure if it is the 'correct'  one for that /dev/sda1, at this time)
in vi, the errors=  statement [which I put in bold] was highlighted in yellow.

If I need to, I have a digital camera, but the file is large and I don't know the capacity for uploads here.

---

### Post by Bucky Ball on 2015-05-07
Attach the file using 'Adv Reply' (or 'Go Advanced' if you're already editing or creating a post) then the paperclip icon in the toolbar there. See how you go.

---

### Post by crazybear on 2015-05-07
No one has given a hint as to HOW I'd change anything on line 9, or if I need to.

*When I was fixing the missing kernel in live CD, I was unable to unmount **all** mounted files [worked on it for over an hour - unmounted all but one which gave a strange error message I couldn't find answer to on web]. Had to give up, as I couldn't find the problem file nor how to unmount it - maybe this caused a problem OR was just another problem - don't know...just saying.*

---

### Post by Bucky Ball on 2015-05-07
If it was requested, guess it was required. Anyhow, good luck with it.

---

### Post by crazybear on 2015-05-07
I was wrong about space between remount and -ro I looked closely at the entire file.
the UUIDs for sda1 [ext4 - line 9] and sda5 [swap] are correct.
Line nine reads: UUID=.....  ext4   relatime,   errors=remount-ro  0   1
I've looked at that 'wording' on the internet and it doesn't seem to be an 'error', only that it needs to be changed to remount-rw, which is what I was trying to do with 'mount -o remount, rw /' when it gave me the error on line 9 /etc/fstab

Any ideas? In nano and iv it is read only [as far as I could manage]

Thanks.

---

### Post by crazybear on 2015-05-08
I'm stuck. Unable to get into my 14.04.2 Any ideas or help would be appreciated. Would using a Live CD help? What would I endeavor to do then? I'm unsure all the things I must do to get mounted and unmounted [and had problems unmounting one of several last time I  tried this]...but if it is the only way, I'll try....can hardly be worse than now....I hope. Thanks in advance.

---

### Post by crazybear on 2015-05-08
```
:~$ sudo tune2fs -l /dev/sda1

tune2fs 1.42 (29-Nov-2011)
Filesystem volume name:   14.04
Last mounted on:          /media/14.04
Filesystem UUID:          453ebbf2-22d2-4d99-89e1-8f24ab5b5caa
Filesystem magic number:  0xEF53
Filesystem revision #:    1 (dynamic)
Filesystem features:      has_journal ext_attr resize_inode dir_index filetype needs_recovery extent flex_bg sparse_super large_file huge_file uninit_bg dir_nlink extra_isize
Filesystem flags:         signed_directory_hash 
Default mount options:    user_xattr acl
Filesystem state:         clean
Errors behavior:          Continue
Filesystem OS type:       Linux
Inode count:              60661760
Block count:              242616832
Reserved block count:     12130841
Free blocks:              108210085
Free inodes:              59584787
First block:              0
Block size:               4096
Fragment size:            4096
Reserved GDT blocks:      966
Blocks per group:         32768
Fragments per group:      32768
Inodes per group:         8192
Inode blocks per group:   512
Flex block group size:    16
Filesystem created:       Fri Oct 17 10:42:35 2014
Last mount time:          Fri May  8 18:52:28 2015
Last write time:          Fri May  8 18:52:28 2015
Mount count:              10
Maximum mount count:      -1
Last checked:             Wed May  6 21:25:17 2015
Check interval:           0 (<none>)
Lifetime writes:          691 GB
Reserved blocks uid:      0 (user root)
Reserved blocks gid:      0 (group root)
First inode:              11
Inode size:              256
Required extra isize:     28
Desired extra isize:      28
Journal inode:            8
Default directory hash:   half_md4
Directory Hash Seed:      275c0f3f-92bb-4d81-a295-02f23bc1f204
```

---

### Post by Bucky Ball on 2015-05-08
Please use code tags.

---

### Post by crazybear on 2015-05-08
> **Bucky Ball said:**
> Please use code tags.

Sorry, got it now....will in future...
However, can anyone help suggest a way forward for me? It is now three weeks+ since I've been able to get into this OS - and I need to. I'm managing with an older system, but that was my most up to date one. Thanks in advance.

---

### Post by crazybear on 2015-05-10
I could really use some help. I can not get that disk to remount. I was sent a message that the bug is fixed, but I can't get into my drive to take advantage of that.

---

### Post by crazybear on 2015-05-10
The recent [fglrx bug]("https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/1424491") caused my OS to fail. I first used my grub rescue disk to re-install grub, thinking that was the problem. Then I by mistake chose the option of 'remove all old kernels and reinstall latest kernel' - which failed. Finally, using live CD I got the latest kernel back in. However, now, even though I hear the bug has at last been fixed, I can't get into my disk/OS. It still has the bad old [no?] video driver and won't boot. I was told to do the following in root shell prompt [TTY is not working]

> mount -o remount,rw /

but when I do this, I get an error message of: [COLOR=#0000cd]Line 9 in /etc/fstab is bad[/COLOR]. [so can't mount as rw]
Line nine reads: [COLOR=#daa520]uuid=(uuid) / ext4 relatime, errors=remount-ro 0 1[/COLOR]
So, I'm trapped in a loop I've not found a way to get out of in many days. I've tried to change the [COLOR=#0000CD]/etc/fstab [/COLOR]but I don't know to use an editor that is not in  read-only mode in root shell prompt. [Also, can't understand what the '0' and '1' at end of line mean or should ideally be - or if this matters at this point.]
**[COLOR=#00ff00]Any suggestions would be greatly appreciated.[/COLOR]**

---

### Post by QIII on 2015-05-10
Hello again.

It would be very, very helpful if you would please use a Live session go to the terminal, navigate to /etc on your boot drive, open /fstab (just 

```
cat fstab
```

would work so you don't have to open a text editor, copy the contents of your fstab and post them back here inside code tags.

If you want to redact your UUID, then replace a few characters but leave the format intact.  

For example, this is from the Fedora laptop I am running right now while on the road.  A vanilla fstab looks a bit different in rpm-based distros, but the point is the same:  with the text rather than a slightly hard to see image, we can carefully check for the formatting error I suspect you may have.

```
/dev/mapper/fedora-root /                       ext4    defaults        1 1
UUID=efb0e803-2cea-47fb-99be-00a432aa02e0 /boot                   ext4    defaults        1 2
/dev/mapper/fedora-home /home                   ext4    defaults        1 2
/dev/mapper/fedora-swap swap                    swap    defaults        0 0

```

If there does not appear to be a formatting error, then we can check for sure to see that the UUIDs match properly.

---

### Post by dino99 on 2015-05-10
Think about the wikis made by the ubuntu community, it can help most of the time:
[https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions)

your /etc/fstab line 9 cant work (uuid=(uuid)) is not valid; check > sudo blkid to set the real uuid

---

### Post by Bucky Ball on 2015-05-10
***Threads merged.***

Please do not start new threads regarding the same issue. It confuses things, degrades your chances of getting support and dilutes community effort as you are already getting help here with your 'unable to mount' issue. Thanks.

If you feel your original issue here is solved or your support issue has changed enough to warrent it, then, by all means, mark this thread as solved and provide a link to a new thread which discusses your new issues.

---

### Post by QIII on 2015-05-10
> **dino99 said:**
> ...

your /etc/fstab line 9 cant work (uuid=(uuid)) is not valid...


I don't think the user meant that literally.  I think that represents a redaction of the UUID as in "UUID=<Insert_UUID_here>"

If you look at the image, there is a long string redacted with the white scrawling.

---

### Post by crazybear on 2015-05-10
Right, I din't mean that literally. I wanted to not print my UUID - I have my reason. I'm not totally naive about things - just have my reasons to not list my UUID. If I did, I'd have to change it. There is a UUID in the correct format [and the correct UUID for that /dev/sda#; with correct number of characters [not '(UUID)'] - that was in place of the actual numbers/letters. In post #20 is also a UUID, in which I changed a few numbers for other numbers; a few letters for other numbers, but didn't change format nor the number of them.

---

### Post by monkeybrain20122 on 2015-05-10
> **QIII said:**
> Hello!


Generally when you do an in-place point-release upgrade or a major release upgrade you should uninstall all third-party hardware drivers beforehand.



Is it? Don't know about fglrx drivers but I have never experienced problems with Nvidia's proprietary driver for point release updates. Maybe enabling LTSEnablementStack is the problem?

---

### Post by QIII on 2015-05-10
I got you.  But maybe I have not made myself clear enough:  To be absolutely sure there is not a formatting problem, it would really be best if you could use a live session to actually cut and paste the text, verbatim, here inside code tags.
  
If you are sure that the actual UUID (unredacted) you gave (redacted) in Post #20 is identical to the one in your fstab, then we don't need to worry about that.   So redact it as necessary, leaving it in the proper format and post the entire fstab back here.

The nature of the failure leads me first to the suspicion that there is a formatting error, which is the sort of thing that is hard to pick out in an image.  Sometimes errors like this may actually be in a line before or after the line given by the error, in what is often called a red-herring (just like the logical fallacy).

An incorrect UUID match or fstab formatting errors are a couple of the things that occasionally happen with an in-place upgrade.

---

### Post by crazybear on 2015-05-10
No one had responded to my thread in three days. I had 'bumped' the thread....and I need to get into my disk. This is why I starting another thread, as *no one was responding to this one*. I figured either persons were not interested in helping further on this thread, or felt it no longer related to a now repaired fgrlx bug. Somehow, my starting the other thread, even if it was moved by a moderator to here got new responses to this one. Whatever works. ;)

---

### Post by QIII on 2015-05-10
No, your other thread did not get me back here.  I didn't know about it.  My first response back to this thread today was a result of going back through my posts and following up.

Please cut and paste the contents of your fstab, verbatim, in code tags.  Your image is of low quality and I can't be sure that I am seeing what I need to see.

I do not want to be unfriendly, but you must understand that real people with real lives who volunteer their time here to help others cannot be expected to demonstrate indefinite dedication to helping you solve this problem when information that is needed to help you is not forthcoming.

Others who might have wanted to help may read the thread, see that, and decide not to jump in and pick up when person who had previously responded is otherwise occupied.

---

### Post by crazybear on 2015-05-10
Any formatting errors? [I don't see any]. The UUID in the fstab is the correct UUID shown under blkid - the one below I changed some numbers and letters of.

> root@ubuntu:/# cat /etc/fstab
# /etc/fstab: static file system information.
# added relatime - remove if problems!
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
[COLOR=#0000cd]UUID=432ebbf1-22e5-4d99-98a4-9f35ac5a4dee /               ext4    relatime, errors=remount-ro 0       1[/COLOR]
# swap was on /dev/sda5 during installation
UUID=e234e59d-d4e9-5e0f-96b9-2a0552174563 none            swap    sw              0       0

I can edit using nano in live CD, so should I just edit the /etc/fstab to what it should be?
I also deleted all the old frglx files; ran update; ran dist-upgrade and new fglrx-upates were installed. So, I think I should be good to go....just not sure what to do about /etc/fstab - edit it and save?

Much has happened on my end.....and after _**many**_ battles, I have my Ubuntu 14.04.2 working again...with the opensource Radeon drivers [I believe]. All fglrx drivers were [with GREAT difficulty and needing many special commands] removed (various installation files associated with them remain in the system). Now, the *QUESTIONS* are:

1] is the fglrx driver better for me [with a MSI Radeon HD-7970 and 3 head system] than the opensource Radeon drivers? I had the flgrx drivers before - the reason this problem began in the first place. I'm inclined to think they are better, but have heard others say not. If they are superior:

2] How do I best install the fglrx driver[s], as once in this battle I tried and all failed again [couldn't boot in] and I was back to a live CD and repairing and removing AGAIN - to where I am now.
Thanks.

NB - I'm now a semi-pro at using a live CD (and have never been before).....so that alone was a good, if hard, lesson.

Aha....this is quite the adventure...maybe this explains why my following of part of QIII's directions failed...I thought it WAS fixed...and it WAS posted as such for several days...then I just got this email!:confused:

> 
[EMAIL="po-hsu.lin@canonical.com"]po-hsu.lin[/EMAIL]

Hello Ted,
could you point me out where did you see the information about the fix release in Trusty?
I will revert it back to "Fix Committed" for now
Thanks** Changed in: fglrx-installer (Ubuntu Trusty)
       Status: Fix Released => Fix Committed

Forward into the past?!?

PFFFT! Now, I get a second email that the fix is really fixed...and I've spent about five hours (maybe more) endlessly trying to install/re-install/re-re-install  the newest version of fglrx-updates [after making sure all previous versions were purged]...and when I reboot, I can't get into the OS - some initial lines just show, then  turn to black, then show again...endlessly [much as it did when I first noticed this problem over a month ago]. Please, if anyone can help me to now get it installed, I'd be very thankfull. If I pull out the disk, move it to another computer, use a live CD, spend 20 minutes, I can delete the fglrx files and put it back on this machine and get into the OS [I guess using the Xorg drivers], but though I have three monitors, everyone is the same, rather than the one screen out of the three as originally configured...so all configuration files for Xorg and fglrx seem to be gone or inaccessible. For some strange [to me] reason, I can't do anything like the above in the shell command line. It won't update, won't install, will delete. Its been a long time since I used my 14.04...and I'd love to.....I've used terminal; I've used synaptic (making sure it was the latest version), but nothing worked. I see others declaring it worked fine - but I don't know what I'm doing wrong. I downloaded what I think [really NOT sure] was the newest tar.gz file (fglrx-installer-updates_15.200.orig.tar.gz); which I think is 2:15.200-0ubuntu0.3, but see no instructions on how to install it {get-debi?} and how do I know that _is_ the correct new driver? Thanks.

---

### Post by crazybear on 2015-05-23
Sadly, no one is offering help. Were I to start a new thread, in minutes it would be moved here. It seems that keeping those wanting help 'in line' with this Forum's rules outweighs getting help, sadly. 

I've now tried two more ways to try to install the new fglrx-updates and now all five methods end in failure and the same black screen with a little text [programs loading, I guess, but then blacking out and retrying, endlessly]. Very frustrated. Even in Xorg, it is not multi-head, but of the three monitors, two are the same, the third black. So, not using 14.04 for now until someone can help me fix this or at least diagnose this. 

I see others  on the bug report say they successfully installed the new version - but didn't say how...and to me [at least] it is far from obvious.

---

### Post by Bucky Ball on 2015-05-23
If you're getting no attention after a reasonable amount of time, simply post 'bump' to your thread. That will take it to the top of the new posts list.

If no one is giving you help, either no one is able, or the person that can hasn't seen your thread yet. Remember, we are an international forum operating across many time zones. ;)

---

### Post by crazybear on 2015-05-25
Bump. I still can NOT use my Ubuntu 12.04. I have tried everything..but nothing works. Now, even the Xorg doesn't work. Fglrx-updates when installed doesn't either. I can not get past the kernal prompt or TTY1, and I don't know what more to try in those situations. Others report they were able to install the new bug fix...but no one said how....I used what I thought were the five ways...but they all failed and now even Xorg is so messed up it doesn't work any more...so my OS is degrading with all of my attempts. Very depressing...and no one has suggested any diagnostic ideas or help with how to attempt a fix.

---

### Post by crazybear on 2015-05-27
I have even [after deleting all past fglrx drivers] used the 'Intall AMD Catalyst 14.6 Beta Graphics Driver in Linux' and it failed. [this was the driver I  had had that the 'update' bug destroyed]. I'm still without the ability to use my OS14.04 - someone please help me figure out how to proceed! Thanks in advance. I see on the internet that Catalyst 15.3 Beta is backported [whatever that means] to 14.04. This seems to be the 
2:15.200-0ubuntu0.1 - but that failed when I used synaptic to install it. I don't understand what is going on..but I've spent days trying to get this to work and I get nowhere fast.

---

### Post by crazybear on 2015-05-31
I really have to thank the Ubuntu forum community for all your recent help [sarcasm]. My system is not the same. It is worse...and now my OS12.04 was also affected - somehow, I don't know how...but without anyone offering help, thus left to try to figure out on my OWN, and trying to compare systems and etc/X11/xorg.conf files between systems I somehow messed up the 12.04 too. I just spent two days and have 12.04 working - but poorly [less well than before] - must not be the best drivers. So for two days I had NO Ubuntu at all. 14.04 only boots to tty1 [which can do nothing] or a kernel prompt [which gives error messages]. I'd really appreciate some help! I'm driving blind and looking on the internet one can find totally opposite suggestions - most of which lead to disaster. I need to get fglrx [latest/best for my VGA card] installed somehow and 12.04 back to the way it was before...now it is slow and moving a screen or within it is slow and almost beyond my control. Thanks. I think I'll soon have to abandon this website if someone can't offer some ideas. I thought the Ubuntu community was about helping each other out. On 14.04, I've tried so many things and all lead to the same non-installation of a driver; obviously I'm doing something wrong - probably a tiny step that is not obvious to me...but it seems to come out the same despite many, MANY completely different suggested ways to 'fix' it. Come on guys and gals - kindly help! Thanks in advance.

---

### Post by crazybear on 2015-05-31
Synaptic clearly shows that Xorg files [don't know if the right ones though] are installed, as are fglrx-updates and fglrx-amdccle-updates; 

[wanted to add screen shot, but only allows for url images to be uploaded?!?!?!]

yet when I ask fglrxinfo, I get

> $ fglrxinfo
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  138 (ATIFGLEXTENSION)
  Minor opcode of failed request:  66 ()
  Serial number of failed request:  13
  Current serial number in output stream:  13


And while I again have one desktop of my three  monitors, video behavior is VERY odd and VERY slow.... much worse than before 

...this is 12.04 - 14.04 I can do nothing with yet.....going on a six weeks!

Oh, and when I go to System Settings to check 'additional drivers' it says NONE are installed and won't allow me to add any video drivers either.....

xorg.conf looks like this [which is different that the .BAK one I made]
> 
Section "ServerLayout"
    Identifier     "aticonfig Layout"
    Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Module"
    Load  "glx"
EndSection

Section "ServerFlags"
    Option        "Xinerama" "off"
EndSection

Section "Monitor"
    Identifier   "aticonfig-Monitor[0]-0"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
EndSection

Section "Monitor"
    Identifier   "0-DFP5"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
    Option        "TargetRefresh" "60"
    Option        "Position" "0 0"
    Option        "Rotate" "normal"
    Option        "Disable" "false"
    Option        "PreferredMode" "1920x1200"
EndSection

Section "Monitor"
    Identifier   "0-DFP17"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
    Option        "TargetRefresh" "60"
    Option        "Position" "1920 0"
    Option        "Rotate" "normal"
    Option        "Disable" "false"
    Option        "PreferredMode" "1920x1200"
EndSection

Section "Monitor"
    Identifier   "0-DFP18"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
    Option        "TargetRefresh" "60"
    Option        "Position" "3840 0"
    Option        "Rotate" "normal"
    Option        "Disable" "false"
    Option        "PreferredMode" "1920x1200"
EndSection

Section "Device"
    Identifier  "aticonfig-Device[0]-0"
    Driver      "fglrx"
    Option        "Monitor-DFP5" "0-DFP5"
    Option        "Monitor-DFP17" "0-DFP17"
    Option        "Monitor-DFP18" "0-DFP18"
    BusID       "PCI:3:0:0"
EndSection

Section "Device"
    Identifier  "amdcccle-Device[3]-1"
    Driver      "fglrx"
    Option        "Monitor-DFP17" "0-DFP17"
    BusID       "PCI:3:0:0"
    Screen      1
EndSection

Section "Device"
    Identifier  "amdcccle-Device[3]-2"
    Driver      "fglrx"
    Option        "Monitor-DFP18" "0-DFP18"
    BusID       "PCI:3:0:0"
    Screen      2
EndSection

Section "Screen"
    Identifier "aticonfig-Screen[0]-0"
    Device     "aticonfig-Device[0]-0"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Virtual   5760 1920
        Depth     24
    EndSubSection
EndSection

Section "Screen"
    Identifier "amdcccle-Screen[3]-1"
    Device     "amdcccle-Device[3]-1"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

Section "Screen"
    Identifier "amdcccle-Screen[3]-2"
    Device     "amdcccle-Device[3]-2"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection


---

### Post by crazybear on 2015-05-31
[PHP][PHP]I ran the GUI install for fglrx-updates in System Settings again to see what error report it generated. It is below. I can't quite make it out, but I hope someone here can. [it is VERY quiet out there!]. Remember, it tells me NO additional drivers are available. But I clicked on the fglrx-updates and to 'activate' it. This is what it said....

> 2015-05-31 16:32:20,464 DEBUG: linux-lts-raring installed: False
linux-lts-saucy installed: False
linux-lts-trusty installed: True
linux minor version: 13
xserver ABI: 11
xserver-lts-quantal: False
2015-05-31 16:32:20,466 DEBUG: Instantiated Handler subclass __builtin__.CdvDriver from name CdvDriver
2015-05-31 16:32:20,466 DEBUG: cdv.available: falling back to default
2015-05-31 16:32:21,684 DEBUG: Intel Cedarview graphics driver availability undetermined, adding to pool
2015-05-31 16:32:21,684 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2015-05-31 16:32:21,727 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2015-05-31 16:32:21,728 DEBUG: Firmware for DVB cards not available
2015-05-31 16:32:21,728 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2015-05-31 16:32:21,738 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2015-05-31 16:32:21,758 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2015-05-31 16:32:21,758 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2015-05-31 16:32:21,758 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2015-05-31 16:32:21,761 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2015-05-31 16:32:21,761 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2015-05-31 16:32:21,761 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2015-05-31 16:32:21,761 DEBUG: loading custom handler /usr/share/jockey/handlers/pvr-omap4.py
2015-05-31 16:32:21,764 WARNING: modinfo for module omapdrm_pvr failed: ERROR: modinfo: could not find module omapdrm_pvr

2015-05-31 16:32:21,769 DEBUG: Instantiated Handler subclass __builtin__.PVROmap4Driver from name PVROmap4Driver
2015-05-31 16:32:22,941 DEBUG: PowerVR SGX proprietary graphics driver for OMAP 4 not available
2015-05-31 16:32:22,942 DEBUG: loading custom handler /usr/share/jockey/handlers/vmware-client.py
2015-05-31 16:32:22,944 WARNING: modinfo for module vmxnet failed: ERROR: modinfo: could not find module vmxnet

2015-05-31 16:32:22,944 DEBUG: Instantiated Handler subclass __builtin__.VmwareClientHandler from name VmwareClientHandler
2015-05-31 16:32:22,962 DEBUG: VMWare Client Tools availability undetermined, adding to pool
2015-05-31 16:32:22,962 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2015-05-31 16:32:22,997 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2015-05-31 16:32:23,012 DEBUG: Software modem not available
2015-05-31 16:32:23,013 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2015-05-31 16:32:23,021 WARNING: modinfo for module nvidia_304 failed: ERROR: modinfo: could not find module nvidia_304

2015-05-31 16:32:23,025 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver304 from name NvidiaDriver304
2015-05-31 16:32:23,026 DEBUG: nvidia.available: falling back to default
2015-05-31 16:32:26,752 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2015-05-31 16:32:26,755 WARNING: modinfo for module nvidia_304_updates failed: ERROR: modinfo: could not find module nvidia_304_updates

2015-05-31 16:32:26,759 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver304Updates from name NvidiaDriver304Updates
2015-05-31 16:32:26,759 DEBUG: nvidia.available: falling back to default
2015-05-31 16:32:30,490 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2015-05-31 16:32:30,492 WARNING: modinfo for module nvidia_experimental_304 failed: ERROR: modinfo: could not find module nvidia_experimental_304

2015-05-31 16:32:30,512 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverExperimental304 from name NvidiaDriverExperimental304
2015-05-31 16:32:30,512 DEBUG: nvidia.available: falling back to default
2015-05-31 16:32:30,528 DEBUG: NVIDIA accelerated graphics driver (**experimental** beta) not available
2015-05-31 16:32:30,530 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2015-05-31 16:32:30,534 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2015-05-31 16:32:30,534 DEBUG: nvidia.available: falling back to default
2015-05-31 16:32:30,553 DEBUG: NVIDIA accelerated graphics driver not available
2015-05-31 16:32:30,556 WARNING: modinfo for module nvidia_current_updates failed: ERROR: modinfo: could not find module nvidia_current_updates

2015-05-31 16:32:30,560 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrentUpdates from name NvidiaDriverCurrentUpdates
2015-05-31 16:32:30,560 DEBUG: nvidia.available: falling back to default
2015-05-31 16:32:30,578 DEBUG: NVIDIA accelerated graphics driver (post-release updates) not available
2015-05-31 16:32:30,581 WARNING: modinfo for module nvidia_319 failed: ERROR: modinfo: could not find module nvidia_319

2015-05-31 16:32:30,585 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver319 from name NvidiaDriver319
2015-05-31 16:32:30,586 DEBUG: nvidia.available: falling back to default
2015-05-31 16:32:30,601 DEBUG: NVIDIA accelerated graphics driver not available
2015-05-31 16:32:30,603 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2015-05-31 16:32:30,607 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2015-05-31 16:32:30,607 DEBUG: nvidia.available: falling back to default
2015-05-31 16:32:36,364 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2015-05-31 16:32:36,366 WARNING: modinfo for module nvidia_173_updates failed: ERROR: modinfo: could not find module nvidia_173_updates

2015-05-31 16:32:36,370 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173Updates from name NvidiaDriver173Updates
2015-05-31 16:32:36,371 DEBUG: nvidia.available: falling back to default
2015-05-31 16:32:36,395 DEBUG: NVIDIA accelerated graphics driver (post-release updates) not available
2015-05-31 16:32:36,397 WARNING: modinfo for module nvidia_331 failed: ERROR: modinfo: could not find module nvidia_331

2015-05-31 16:32:36,402 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver331 from name NvidiaDriver331
2015-05-31 16:32:36,402 DEBUG: nvidia.available: falling back to default
2015-05-31 16:32:44,289 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2015-05-31 16:32:44,291 WARNING: modinfo for module nvidia_experimental_310 failed: ERROR: modinfo: could not find module nvidia_experimental_310

2015-05-31 16:32:44,315 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverExperimental310 from name NvidiaDriverExperimental310
2015-05-31 16:32:44,316 DEBUG: nvidia.available: falling back to default
2015-05-31 16:32:44,334 DEBUG: NVIDIA accelerated graphics driver (**experimental** beta) not available
2015-05-31 16:32:44,336 WARNING: modinfo for module nvidia_319_updates failed: ERROR: modinfo: could not find module nvidia_319_updates

2015-05-31 16:32:44,340 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver319Updates from name NvidiaDriver319Updates
2015-05-31 16:32:44,340 DEBUG: nvidia.available: falling back to default
2015-05-31 16:32:44,358 DEBUG: NVIDIA accelerated graphics driver (post-release updates) not available
2015-05-31 16:32:44,361 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2015-05-31 16:32:44,365 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2015-05-31 16:32:44,365 DEBUG: nvidia.available: falling back to default
2015-05-31 16:32:46,947 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2015-05-31 16:32:46,950 WARNING: modinfo for module nvidia_96_updates failed: ERROR: modinfo: could not find module nvidia_96_updates

2015-05-31 16:32:46,955 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96Updates from name NvidiaDriver96Updates
2015-05-31 16:32:46,955 DEBUG: nvidia.available: falling back to default
2015-05-31 16:32:48,289 DEBUG: XorgDriverHandler(nvidia_96_updates, nvidia-96-updates, None): Disabling as package video ABI(s) xorg-video-abi-10 not compatible with X.org video ABI xorg-video-abi-11
2015-05-31 16:32:48,289 DEBUG: NVIDIA accelerated graphics driver (post-release updates) not available
2015-05-31 16:32:48,291 WARNING: modinfo for module nvidia_331_updates failed: ERROR: modinfo: could not find module nvidia_331_updates

2015-05-31 16:32:48,295 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver331Updates from name NvidiaDriver331Updates
2015-05-31 16:32:48,295 DEBUG: nvidia.available: falling back to default
2015-05-31 16:32:56,476 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2015-05-31 16:32:56,477 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2015-05-31 16:32:56,481 WARNING: modinfo for module fglrx_experimental_12 failed: ERROR: modinfo: could not find module fglrx_experimental_12

2015-05-31 16:32:56,500 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriverExperimental12 from name FglrxDriverExperimental12
2015-05-31 16:32:56,500 DEBUG: fglrx.available: falling back to default
2015-05-31 16:32:56,517 DEBUG: ATI/AMD proprietary FGLRX graphics driver (**experimental** beta) not available
2015-05-31 16:32:56,519 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates

2015-05-31 16:32:56,524 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriverUpdate from name FglrxDriverUpdate
2015-05-31 16:32:56,524 DEBUG: fglrx.available: falling back to default
2015-05-31 16:32:59,751 DEBUG: ATI/AMD proprietary FGLRX graphics driver (post-release updates) availability undetermined, adding to pool
2015-05-31 16:32:59,754 WARNING: modinfo for module fglrx_experimental_9 failed: ERROR: modinfo: could not find module fglrx_experimental_9

2015-05-31 16:32:59,774 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriverExperimental9 from name FglrxDriverExperimental9
2015-05-31 16:32:59,774 DEBUG: fglrx.available: falling back to default
2015-05-31 16:32:59,790 DEBUG: ATI/AMD proprietary FGLRX graphics driver (**experimental** beta) not available
2015-05-31 16:32:59,792 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2015-05-31 16:32:59,797 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriverHybrid from name FglrxDriverHybrid
2015-05-31 16:32:59,797 DEBUG: fglrx.available: falling back to default
2015-05-31 16:33:02,896 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2015-05-31 16:33:02,898 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2015-05-31 16:33:02,902 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2015-05-31 16:33:02,902 DEBUG: fglrx.available: falling back to default
2015-05-31 16:33:06,066 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2015-05-31 16:33:06,068 WARNING: modinfo for module fglrx_experimental_13 failed: ERROR: modinfo: could not find module fglrx_experimental_13

2015-05-31 16:33:06,088 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriverExperimental13 from name FglrxDriverExperimental13
2015-05-31 16:33:06,088 DEBUG: fglrx.available: falling back to default
2015-05-31 16:33:06,104 DEBUG: ATI/AMD proprietary FGLRX graphics driver (**experimental** beta) not available
2015-05-31 16:33:06,104 DEBUG: all custom handlers loaded
2015-05-31 16:33:06,104 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f7dd40> about HardwareID('modalias', 'acpiNP0C02:')
2015-05-31 16:33:06,105 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f7dd40> about HardwareID('modalias', 'platform:microcode')
2015-05-31 16:33:06,105 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f7dd40> about HardwareID('modalias', 'usb:v046Dp0821d0010dcEFdsc02dp01ic0Eisc02ip00in03')
2015-05-31 16:33:06,135 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f7dd40> about HardwareID('modalias', 'usb:v1D6Bp0002d0313dc09dsc00dp01ic09isc00ip00in00')
2015-05-31 16:33:06,135 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f7dd40> about HardwareID('modalias', 'usb:v1B1Cp1B11d0120dc00dsc00dp00ic03isc00ip00in01')
2015-05-31 16:33:06,136 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2015-05-31 16:33:06,256 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2015-05-31 16:33:06,256 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f7dd40> about HardwareID('modalias', 'platform:coretemp')
2015-05-31 16:33:06,256 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f7dd40> about HardwareID('modalias', 'acpi:INT0800:')
2015-05-31 16:33:06,256 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f7dd40> about HardwareID('modalias', 'pci:v00008086d0000342Dsv00000000sd00000000bc08sc00i20')
2015-05-31 16:33:06,527 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f7dd40> about HardwareID('modalias', 'pci:v00008086d00002DA2sv00001458sd00005000bc06sc00i00')
2015-05-31 16:33:06,531 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f7dd40> about HardwareID('modalias', 'pci:v00001B4Bd00009123sv00001B4Bsd00009123bc01sc06i01')
2015-05-31 16:33:06,534 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'ahci'}
2015-05-31 16:33:06,534 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2015-05-31 16:33:06,534 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'ahci'}
2015-05-31 16:33:06,534 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2015-05-31 16:33:06,534 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f7dd40> about HardwareID('modalias', 'acpiNP0C01:')
2015-05-31 16:33:06,534 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f7dd40> about HardwareID('modalias', 'dmi:bvnAwardSoftwareInternational,Inc.:bvrF9d:bd09/01/2011:svnGigabyteTechnologyCo.,Ltd.nX58A-UD7vr:rvnGigabyteTechnologyCo.,Ltd.:rnX58A-UD7:rvr:cvnGigabyteTechnologyCo.,Ltd.:ct3:cvr:')
2015-05-31 16:33:06,542 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f7dd40> about HardwareID('modalias', 'usb:vE0FFp0002d0001dc00dsc00dp00ic03isc01ip02in00')
2015-05-31 16:33:06,542 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse'}
2015-05-31 16:33:06,542 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse', 'jockey_handler': 'KernelModuleHandler'}
2015-05-31 16:33:06,542 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2015-05-31 16:33:06,542 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2015-05-31 16:33:06,542 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f7dd40> about HardwareID('modalias', 'usb:v1D6Bp0001d0313dc09dsc00dp00ic09isc00ip00in00')
2015-05-31 16:33:06,542 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f7dd40> about HardwareID('modalias', 'pci:v00008086d00003A34sv00001458sd00005004bc0Csc03i00')
2015-05-31 16:33:06,545 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f7dd40> about HardwareID('modalias', 'usb:v1D6Bp0003d0313dc09dsc00dp03ic09isc00ip00in00')
2015-05-31 16:33:06,546 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f7dd40> about HardwareID('modalias', 'acpiNP0103:')
2015-05-31 16:33:06,546 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f7dd40> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2015-05-31 16:33:06,546 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f7dd40> about HardwareID('modalias', 'acpi:LNXCPU:')
2015-05-31 16:33:06,546 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f7dd40> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,8,')
2015-05-31 16:33:06,549 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2015-05-31 16:33:06,549 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2015-05-31 16:33:06,549 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f7dd40> about HardwareID('modalias', 'pci:v00008086d0000244Esv00001458sd00005000bc06sc04i01')
2015-05-31 16:33:06,553 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f7dd40> about HardwareID('modalias', 'x86cpu:vendor:0000:family:0006:model:002C:feature:,0000,0001,0002,0003,0004,0005,0006,0007,0008,0009,000B,000C,000D,000E,000F,0010,0011,0013,0015,0016,0017,0018,0019,001A,001B,001C,001D,001F,002B,0034,003A,003B,003D,0068,006B,006C,006D,006F,0070,0072,0074,0075,0076,0078,007C,0080,0081,0082,0083,0084,0085,0087,0088,0089,008D,008E,008F,0091,0093,0094,0097,0099,00C0,00E0,00E1,00E7,0100,0101,0102,0103,0104')
2015-05-31 16:33:06,560 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'kvm_intel'}
2015-05-31 16:33:06,560 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'kvm_intel', 'jockey_handler': 'KernelModuleHandler'}
2015-05-31 16:33:06,560 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'intel_powerclamp'}
2015-05-31 16:33:06,560 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'intel_powerclamp', 'jockey_handler': 'KernelModuleHandler'}
2015-05-31 16:33:06,560 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'aesni_intel'}
2015-05-31 16:33:06,560 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'aesni_intel', 'jockey_handler': 'KernelModuleHandler'}
2015-05-31 16:33:06,560 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'ghash_clmulni_intel'}
2015-05-31 16:33:06,560 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ghash_clmulni_intel', 'jockey_handler': 'KernelModuleHandler'}
2015-05-31 16:33:06,560 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'crc32_pclmul'}
2015-05-31 16:33:06,560 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'crc32_pclmul', 'jockey_handler': 'KernelModuleHandler'}
2015-05-31 16:33:06,560 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'crct10dif_pclmul'}
2015-05-31 16:33:06,560 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'crct10dif_pclmul', 'jockey_handler': 'KernelModuleHandler'}
2015-05-31 16:33:06,561 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'coretemp'}
2015-05-31 16:33:06,561 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'coretemp', 'jockey_handler': 'KernelModuleHandler'}
2015-05-31 16:33:06,561 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f7dd40> about HardwareID('modalias', 'serio:ty06pr00id00ex00')
2015-05-31 16:33:06,565 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw'}
2015-05-31 16:33:06,565 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2015-05-31 16:33:06,565 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f7dd40> about HardwareID('modalias', 'acpiNP0100:')
2015-05-31 16:33:06,566 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f7dd40> about HardwareID('modalias', 'pci:v0000197Bd00002363sv00001458sd0000B000bc01sc01i85')
2015-05-31 16:33:06,568 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pata_jmicron'}
2015-05-31 16:33:06,568 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pata_jmicron', 'jockey_handler': 'KernelModuleHandler'}
2015-05-31 16:33:06,568 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pata_acpi'}
2015-05-31 16:33:06,568 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pata_acpi', 'jockey_handler': 'KernelModuleHandler'}
2015-05-31 16:33:06,568 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f7dd40> about HardwareID('modalias', 'pci:v00008086d00002DB2sv00001458sd00005000bc06sc00i00')
2015-05-31 16:33:06,572 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f7dd40> about HardwareID('modalias', 'pci:v00008086d00002DA1sv00001458sd00005000bc06sc00i00')
2015-05-31 16:33:06,574 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f7dd40> about HardwareID('modalias', 'pci:v00001002d0000AAA0sv00001002sd0000AAA0bc04sc03i00')
2015-05-31 16:33:06,794 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2015-05-31 16:33:06,795 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2015-05-31 16:33:06,795 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2015-05-31 16:33:06,795 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2015-05-31 16:33:06,795 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f7dd40> about HardwareID('modalias', 'usb:v1B1Cp1B11d0120dc00dsc00dp00ic03isc01ip01in00')
2015-05-31 16:33:06,795 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd'}
2015-05-31 16:33:06,795 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd', 'jockey_handler': 'KernelModuleHandler'}
2015-05-31 16:33:06,795 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2015-05-31 16:33:06,795 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2015-05-31 16:33:06,795 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f7dd40> about HardwareID('modalias', 'usb:v046Dp0821d0010dcEFdsc02dp01ic0Eisc01ip00in02')
2015-05-31 16:33:06,796 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo'}
2015-05-31 16:33:06,796 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo', 'jockey_handler': 'KernelModuleHandler'}
2015-05-31 16:33:06,796 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f7dd40> about HardwareID('modalias', 'pci:v00008086d00003A3Esv00001458sd0000A102bc04sc03i00')
2015-05-31 16:33:06,799 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2015-05-31 16:33:06,799 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2015-05-31 16:33:06,799 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2015-05-31 16:33:06,799 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2015-05-31 16:33:06,799 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f7dd40> about HardwareID('modalias', 'platform:iTCO_wdt')
2015-05-31 16:33:06,800 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt'}
2015-05-31 16:33:06,800 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt', 'jockey_handler': 'KernelModuleHandler'}
2015-05-31 16:33:06,800 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f7dd40> about HardwareID('modalias', 'pci:v00008086d00002DB1sv00001458sd00005000bc06sc00i00')
2015-05-31 16:33:06,803 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f7dd40> about HardwareID('modalias', 'pci:v00008086d0000342Fsv00000000sd00000000bc08sc00i20')
2015-05-31 16:33:06,806 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f7dd40> about HardwareID('modalias', 'acpiNP0800:')
2015-05-31 16:33:06,806 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f7dd40> about HardwareID('modalias', 'pci:v00001033d00000194sv00001458sd00005007bc0Csc03i30')
2015-05-31 16:33:06,806 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f7dd40> about HardwareID('modalias', 'pci:v00008086d00002D90sv00001458sd00005000bc06sc00i00')
2015-05-31 16:33:06,809 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f7dd40> about HardwareID('modalias', 'pci:v00008086d00003405sv00001458sd00005000bc06sc00i00')
2015-05-31 16:33:06,812 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f7dd40> about HardwareID('modalias', 'pci:v00001B4Bd00009128sv00001458sd0000B000bc01sc06i01')
2015-05-31 16:33:06,812 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'ahci'}
2015-05-31 16:33:06,812 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2015-05-31 16:33:06,812 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f7dd40> about HardwareID('modalias', 'usb:v1B1Cp1B02d0136dc00dsc00dp00ic03isc00ip00in02')
2015-05-31 16:33:06,813 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2015-05-31 16:33:06,813 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2015-05-31 16:33:06,813 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f7dd40> about HardwareID('modalias', 'pci:v00008086d00002DB0sv00001458sd00005000bc06sc00i00')
2015-05-31 16:33:06,815 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f7dd40> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2015-05-31 16:33:06,816 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw'}
2015-05-31 16:33:06,816 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2015-05-31 16:33:06,816 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'psmouse'}
2015-05-31 16:33:06,816 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2015-05-31 16:33:06,816 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f7dd40> about HardwareID('modalias', 'pci:v00008086d0000342Esv00000000sd00000000bc08sc00i00')
2015-05-31 16:33:06,819 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'i7core_edac'}
2015-05-31 16:33:06,819 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i7core_edac', 'jockey_handler': 'KernelModuleHandler'}
2015-05-31 16:33:06,819 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f7dd40> about HardwareID('modalias', 'pci:v00008086d00003A38sv00001458sd00005004bc0Csc03i00')
2015-05-31 16:33:06,821 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f7dd40> about HardwareID('modalias', 'usb:vE0FFp0002d0001dc00dsc00dp00ic03isc00ip00in01')
2015-05-31 16:33:06,822 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2015-05-31 16:33:06,822 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2015-05-31 16:33:06,822 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f7dd40> about HardwareID('modalias', 'pci:v00008086d00003423sv00000000sd00000000bc08sc00i00')
2015-05-31 16:33:06,825 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f7dd40> about HardwareID('modalias', 'usb:v046Dp0821d0010dcEFdsc02dp01ic01isc01ip00in00')
2015-05-31 16:33:06,825 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_usb_audio'}
2015-05-31 16:33:06,825 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_usb_audio', 'jockey_handler': 'KernelModuleHandler'}
2015-05-31 16:33:06,825 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f7dd40> about HardwareID('modalias', 'scsi:t-0x03')
2015-05-31 16:33:06,826 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f7dd40> about HardwareID('modalias', 'acpiNP0C0F:')
2015-05-31 16:33:06,826 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f7dd40> about HardwareID('modalias', 'pci:v00008086d00003428sv00000000sd00000000bc08sc00i00')
2015-05-31 16:33:06,830 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f7dd40> about HardwareID('modalias', 'pci:v00008086d00002DA0sv00001458sd00005000bc06sc00i00')
2015-05-31 16:33:06,833 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f7dd40> about HardwareID('modalias', 'usb:v1B1Cp1B02d0136dc00dsc00dp00ic03isc01ip01in00')
2015-05-31 16:33:06,833 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd'}
2015-05-31 16:33:06,833 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd', 'jockey_handler': 'KernelModuleHandler'}
2015-05-31 16:33:06,833 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2015-05-31 16:33:06,833 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2015-05-31 16:33:06,834 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f7dd40> about HardwareID('modalias', 'pci:v00008086d00002D81sv00001458sd00005000bc06sc00i00')
2015-05-31 16:33:06,836 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f7dd40> about HardwareID('modalias', 'usb:v046Dp0821d0010dcEFdsc02dp01ic01isc02ip00in01')
2015-05-31 16:33:06,836 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f7dd40> about HardwareID('modalias', 'pci:v00008086d00003A39sv00001458sd00005004bc0Csc03i00')
2015-05-31 16:33:06,839 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f7dd40> about HardwareID('modalias', 'pci:v00008086d00002D98sv00001458sd00005000bc06sc00i00')
2015-05-31 16:33:06,842 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f7dd40> about HardwareID('modalias', 'pci:v00008086d00002DA3sv00001458sd00005000bc06sc00i00')
2015-05-31 16:33:06,845 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f7dd40> about HardwareID('modalias', 'pci:v00008086d00003426sv00000000sd00000000bc08sc00i00')
2015-05-31 16:33:06,848 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f7dd40> about HardwareID('modalias', 'pci:v00008086d00002DAAsv00001458sd00005000bc06sc00i00')
2015-05-31 16:33:06,851 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f7dd40> about HardwareID('modalias', 'input:b0003v1B1Cp1B02e0111-e0,1,4,14,k74,75,77,7D,7E,7F,B7,B8,B9,BA,BB,BC,BD,BE,ram4,lsfw')
2015-05-31 16:33:06,851 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2015-05-31 16:33:06,851 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2015-05-31 16:33:06,851 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2015-05-31 16:33:06,851 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2015-05-31 16:33:06,852 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f7dd40> about HardwareID('modalias', 'pci:v00008086d00002D99sv00001458sd00005000bc06sc00i00')
2015-05-31 16:33:06,855 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f7dd40> about HardwareID('modalias', 'pci:v00008086d00002D91sv00001458sd00005000bc06sc00i00')
2015-05-31 16:33:06,857 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f7dd40> about HardwareID('modalias', 'platform:it87')
2015-05-31 16:33:06,858 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f7dd40> about HardwareID('modalias', 'pci:v00008086d00003A30sv00001458sd00005001bc0Csc05i00')
2015-05-31 16:33:06,861 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801'}
2015-05-31 16:33:06,861 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801', 'jockey_handler': 'KernelModuleHandler'}
2015-05-31 16:33:06,861 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f7dd40> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2015-05-31 16:33:06,861 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2015-05-31 16:33:06,861 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2015-05-31 16:33:06,861 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f7dd40> about HardwareID('modalias', 'input:b0003v1B1Cp1B11e0003-e0,1,11,k71,72,73,74,75,76,77,78,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,8B,8C,8D,8E,8F,90,91,92,93,94,95,96,97,98,99,9A,9B,9C,9D,9E,9F,A0,A1,A2,A3,A4,A5,A6,A7,A8,A9,AA,AB,AC,AD,AE,AF,B0,B1,B2,B3,B4,B5,B6,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,C3,C4,C5,C6,C7,C8,C9,CA,CB,CC,CD,CE,CF,D0,D1,D2,D3,D4,D5,D6,D7,D8,D9,DA,DB,DC,DD,DE,DF,E0,E1,E2,E3,E4,E5,E6,E7,E8,E9,EA,EB,EC,ED,EE,EF,F0,F1,F2,F3,F4,F5,F6,F7,F8,F9,FA,FB,FC,FD,FE,FF,raml0,1,2,3,4,5,6,7,8,9,A,B,C,D,E,sfw')
2015-05-31 16:33:06,861 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2015-05-31 16:33:06,861 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2015-05-31 16:33:06,861 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2015-05-31 16:33:06,861 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2015-05-31 16:33:06,861 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f7dd40> about HardwareID('modalias', 'platform:gpio_ich')
2015-05-31 16:33:06,862 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'gpio_ich'}
2015-05-31 16:33:06,862 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'gpio_ich', 'jockey_handler': 'KernelModuleHandler'}
2015-05-31 16:33:06,862 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f7dd40> about HardwareID('modalias', 'wmi:F6CB5C3C-9CAE-4EBD-B577-931EA32A2CC0')
2015-05-31 16:33:06,862 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mxm_wmi'}
2015-05-31 16:33:06,862 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mxm_wmi', 'jockey_handler': 'KernelModuleHandler'}
2015-05-31 16:33:06,862 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f7dd40> about HardwareID('modalias', 'pci:v00008086d00002DA9sv00001458sd00005000bc06sc00i00')
2015-05-31 16:33:06,865 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f7dd40> about HardwareID('modalias', 'pci:v00008086d00002D93sv00001458sd00005000bc06sc00i00')
2015-05-31 16:33:06,868 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f7dd40> about HardwareID('modalias', 'pci:v00008086d00002DA8sv00001458sd00005000bc06sc00i00')
2015-05-31 16:33:06,870 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f7dd40> about HardwareID('modalias', 'acpiNP0B00:')
2015-05-31 16:33:06,870 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f7dd40> about HardwareID('modalias', 'pci:v000010ECd00008168sv00001458sd0000E000bc02sc00i00')
2015-05-31 16:33:06,879 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'r8169'}
2015-05-31 16:33:06,879 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'r8169', 'jockey_handler': 'KernelModuleHandler'}
2015-05-31 16:33:06,879 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f7dd40> about HardwareID('modalias', 'usb:v1B1Cp1B11d0120dc00dsc00dp00ic03isc00ip00in02')
2015-05-31 16:33:06,879 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2015-05-31 16:33:06,879 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2015-05-31 16:33:06,879 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f7dd40> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,')
2015-05-31 16:33:06,879 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2015-05-31 16:33:06,879 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2015-05-31 16:33:06,879 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f7dd40> about HardwareID('modalias', 'acpiNP0200:')
2015-05-31 16:33:06,879 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f7dd40> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2015-05-31 16:33:06,880 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2015-05-31 16:33:06,880 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2015-05-31 16:33:06,880 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f7dd40> about HardwareID('modalias', 'pci:v00008086d00003427sv00000000sd00000000bc08sc00i00')
2015-05-31 16:33:06,883 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f7dd40> about HardwareID('modalias', 'pci:v00008086d00002DB3sv00001458sd00005000bc06sc00i00')
2015-05-31 16:33:06,886 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f7dd40> about HardwareID('modalias', 'pci:v00001002d00006798sv00001002sd00003000bc03sc00i00')
2015-05-31 16:33:06,888 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx_updates', 'package': 'fglrx-updates'}
2015-05-31 16:33:06,952 DEBUG: fglrx.enabled(fglrx_updates): target_alt ['/usr/lib/fglrx/ld.so.conf', '/usr/lib/pxpress/ld.so.conf'] current_alt /usr/lib/fglrx/ld.so.conf other target alt ['/usr/lib/fglrx/alt_ld.so.conf', '/usr/lib/pxpress/alt_ld.so.conf'] other current alt /usr/lib/fglrx/alt_ld.so.conf
2015-05-31 16:33:06,952 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2015-05-31 16:33:06,889 DEBUG: found match in handler pool xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2015-05-31 16:33:06,954 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates

2015-05-31 16:33:06,958 DEBUG: fglrx.available: falling back to default
2015-05-31 16:33:10,119 DEBUG: fglrx.enabled(fglrx_updates): target_alt ['/usr/lib/fglrx/ld.so.conf', '/usr/lib/pxpress/ld.so.conf'] current_alt /usr/lib/fglrx/ld.so.conf other target alt ['/usr/lib/fglrx/alt_ld.so.conf', '/usr/lib/pxpress/alt_ld.so.conf'] other current alt /usr/lib/fglrx/alt_ld.so.conf
2015-05-31 16:33:10,119 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2015-05-31 16:33:10,110 DEBUG: got handler xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2015-05-31 16:33:10,119 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx', 'package': 'fglrx'}
2015-05-31 16:33:10,127 DEBUG: fglrx.enabled(fglrx): target_alt ['/usr/lib/fglrx/ld.so.conf', '/usr/lib/pxpress/ld.so.conf'] current_alt /usr/lib/fglrx/ld.so.conf other target alt ['/usr/lib/fglrx/alt_ld.so.conf', '/usr/lib/pxpress/alt_ld.so.conf'] other current alt /usr/lib/fglrx/alt_ld.so.conf
2015-05-31 16:33:10,127 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2015-05-31 16:33:10,119 DEBUG: found match in handler pool xorg:fglrx([FglrxDriver, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver)
2015-05-31 16:33:10,130 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2015-05-31 16:33:10,134 DEBUG: fglrx.available: falling back to default
2015-05-31 16:33:13,358 DEBUG: fglrx.enabled(fglrx): target_alt ['/usr/lib/fglrx/ld.so.conf', '/usr/lib/pxpress/ld.so.conf'] current_alt /usr/lib/fglrx/ld.so.conf other target alt ['/usr/lib/fglrx/alt_ld.so.conf', '/usr/lib/pxpress/alt_ld.so.conf'] other current alt /usr/lib/fglrx/alt_ld.so.conf
2015-05-31 16:33:13,358 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2015-05-31 16:33:13,351 DEBUG: got handler xorg:fglrx([FglrxDriver, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver)
2015-05-31 16:33:13,359 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'radeon'}
2015-05-31 16:33:13,359 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'radeon', 'jockey_handler': 'KernelModuleHandler'}
2015-05-31 16:33:13,359 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f7dd40> about HardwareID('modalias', 'input:b0003vE0FFp0002e0100-e0,1,2,3,4,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,8B,8C,8E,90,96,98,9B,9C,9E,9F,A1,A3,A4,A5,A6,A7,A8,A9,AB,AC,AD,AE,B0,B1,B2,B3,B4,B5,B6,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,CE,CF,D0,D1,D2,D4,D8,D9,DB,DF,E4,E7,E8,E9,EA,EB,F0,F1,100,161,162,166,16A,16E,172,174,176,178,179,17A,17B,17C,17D,17F,180,182,183,185,188,189,18C,18D,18E,18F,190,191,192,193,195,198,199,19A,1A0,1A1,1A2,1A3,1A4,1A5,1A6,1A7,1A8,1A9,1AA,1AB,1AC,1AD,1AE,1B0,1B1,1B7,1BA,r6,a20,28,29,2A,2B,2C,2D,2E,m4,lsfw')
2015-05-31 16:33:13,359 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2015-05-31 16:33:13,359 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2015-05-31 16:33:13,359 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2015-05-31 16:33:13,359 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2015-05-31 16:33:13,359 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2015-05-31 16:33:13,359 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2015-05-31 16:33:13,359 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2015-05-31 16:33:13,359 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2015-05-31 16:33:13,359 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f7dd40> about HardwareID('modalias', 'pci:v00008086d00003A37sv00001458sd00005004bc0Csc03i00')
2015-05-31 16:33:13,363 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f7dd40> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2015-05-31 16:33:13,363 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2015-05-31 16:33:13,363 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2015-05-31 16:33:13,363 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2015-05-31 16:33:13,363 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2015-05-31 16:33:13,364 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f7dd40> about HardwareID('modalias', 'pci:v0000197Bd00002363sv00001458sd0000B000bc01sc06i01')
2015-05-31 16:33:13,364 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'ahci'}
2015-05-31 16:33:13,364 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2015-05-31 16:33:13,364 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'ahci'}
2015-05-31 16:33:13,364 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2015-05-31 16:33:13,364 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f7dd40> about HardwareID('modalias', 'usb:v04A9p176Bd0208dc00dsc00dp00icFFisc00ipFFin00')
2015-05-31 16:33:13,364 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f7dd40> about HardwareID('modalias', 'input:b0003vE0FFp0002e0100-e0,1,2,4,k110,111,112,113,114,115,116,117,r0,1,6,8,am4,lsfw')
2015-05-31 16:33:13,364 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2015-05-31 16:33:13,364 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2015-05-31 16:33:13,364 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2015-05-31 16:33:13,365 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2015-05-31 16:33:13,365 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f7dd40> about HardwareID('modalias', 'platformcspkr')
2015-05-31 16:33:13,365 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr'}
2015-05-31 16:33:13,365 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2015-05-31 16:33:13,365 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp'}
2015-05-31 16:33:13,365 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2015-05-31 16:33:13,365 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f7dd40> about HardwareID('modalias', 'usb:v04A9p176Bd0208dc00dsc00dp00ic07isc01ip02in01')
2015-05-31 16:33:13,366 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usblp'}
2015-05-31 16:33:13,366 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usblp', 'jockey_handler': 'KernelModuleHandler'}
2015-05-31 16:33:13,366 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f7dd40> about HardwareID('modalias', 'hid:b0003g0001v00001B1Cp00001B02')
2015-05-31 16:33:13,398 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'hid_generic'}
2015-05-31 16:33:13,398 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'hid_generic', 'jockey_handler': 'KernelModuleHandler'}
2015-05-31 16:33:13,398 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f7dd40> about HardwareID('modalias', 'hid:b0003g0001v0000E0FFp00000002')
2015-05-31 16:33:13,399 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'hid_generic'}
2015-05-31 16:33:13,399 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'hid_generic', 'jockey_handler': 'KernelModuleHandler'}
2015-05-31 16:33:13,399 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f7dd40> about HardwareID('modalias', 'acpiNP0A03:')
2015-05-31 16:33:13,399 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f7dd40> about HardwareID('modalias', 'input:b0003v046Dp0821e0010-e0,1,kD4,ramlsfw')
2015-05-31 16:33:13,399 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2015-05-31 16:33:13,399 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2015-05-31 16:33:13,399 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2015-05-31 16:33:13,399 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2015-05-31 16:33:13,400 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f7dd40> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2015-05-31 16:33:13,400 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f7dd40> about HardwareID('modalias', 'usb:v04A9p176Bd0208dc00dsc00dp00ic07isc01ip02in02')
2015-05-31 16:33:13,400 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usblp'}
2015-05-31 16:33:13,400 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usblp', 'jockey_handler': 'KernelModuleHandler'}
2015-05-31 16:33:13,400 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f7dd40> about HardwareID('modalias', 'acpiNP0C04:')
2015-05-31 16:33:13,400 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f7dd40> about HardwareID('modalias', 'pci:v00008086d00002C71sv00001458sd00005000bc06sc00i00')
2015-05-31 16:33:13,403 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f7dd40> about HardwareID('modalias', 'pci:v00008086d00002D92sv00001458sd00005000bc06sc00i00')
2015-05-31 16:33:13,406 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f7dd40> about HardwareID('modalias', 'input:b0003v1B1Cp1B02e0111-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,8C,8E,96,98,9E,9F,A1,A3,A4,A5,A6,AD,B0,B1,B2,B3,B4,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,sfw')
2015-05-31 16:33:13,407 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2015-05-31 16:33:13,407 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2015-05-31 16:33:13,407 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2015-05-31 16:33:13,407 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2015-05-31 16:33:13,407 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f7dd40> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfwD,')
2015-05-31 16:33:13,407 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2015-05-31 16:33:13,407 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2015-05-31 16:33:13,407 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f7dd40> about HardwareID('modalias', 'pci:v00008086d00003422sv00000000sd00000000bc08sc00i00')
2015-05-31 16:33:13,410 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f7dd40> about HardwareID('modalias', 'pci:v00008086d00003A36sv00001458sd00005004bc0Csc03i00')
2015-05-31 16:33:13,413 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f7dd40> about HardwareID('modalias', 'pci:v00008086d00003A16sv00001458sd00005001bc06sc01i00')
2015-05-31 16:33:13,417 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'lpc_ich'}
2015-05-31 16:33:13,417 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'lpc_ich', 'jockey_handler': 'KernelModuleHandler'}
2015-05-31 16:33:13,417 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f7dd40> about HardwareID('modalias', 'acpiNP0000:')
2015-05-31 16:33:13,417 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f7dd40> about HardwareID('modalias', 'usb:v1B1Cp1A95d0100dc00dsc00dp00ic08isc06ip50in00')
2015-05-31 16:33:13,417 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usb_storage'}
2015-05-31 16:33:13,417 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usb_storage', 'jockey_handler': 'KernelModuleHandler'}
2015-05-31 16:33:13,417 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f7dd40> about HardwareID('modalias', 'usb:v1B1Cp1B02d0136dc00dsc00dp00ic03isc00ip00in01')
2015-05-31 16:33:13,418 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2015-05-31 16:33:13,418 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2015-05-31 16:33:13,418 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f7dd40> about HardwareID('modalias', 'pci:v00008086d00003A22sv00001458sd0000B005bc01sc06i01')
2015-05-31 16:33:13,421 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'ahci'}
2015-05-31 16:33:13,421 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2015-05-31 16:33:13,421 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'ahci'}
2015-05-31 16:33:13,421 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2015-05-31 16:33:13,421 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f7dd40> about HardwareID('modalias', 'pci:v00008086d00003425sv00000000sd00000000bc08sc00i00')
2015-05-31 16:33:13,424 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f7dd40> about HardwareID('modalias', 'pci:v00008086d00002D9Csv00001458sd00005000bc06sc00i00')
2015-05-31 16:33:13,427 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f7dd40> about HardwareID('modalias', 'usb:v1D6Bp0002d0313dc09dsc00dp00ic09isc00ip00in00')
2015-05-31 16:33:13,427 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f7dd40> about HardwareID('modalias', 'usb:v1B1Cp1B11d0120dc00dsc00dp00ic03isc00ip00in03')
2015-05-31 16:33:13,427 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2015-05-31 16:33:13,427 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2015-05-31 16:33:13,427 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f7dd40> about HardwareID('modalias', 'pci:v00008086d00003A35sv00001458sd00005004bc0Csc03i00')
2015-05-31 16:33:13,430 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f7dd40> about HardwareID('modalias', 'input:b0003v1B1Cp1B02e0111-e0,1,2,3,4,k71,72,73,74,77,80,82,83,85,86,87,88,89,8A,8B,8C,8E,90,96,98,9B,9C,9E,9F,A1,A3,A4,A5,A6,A7,A8,A9,AB,AC,AD,AE,B0,B1,B2,B5,B6,CE,CF,D0,D1,D2,D4,D8,D9,DB,DF,E4,E7,E8,E9,EA,EB,F1,100,161,162,166,16A,16E,172,174,176,178,179,17A,17B,17C,17D,17F,180,182,183,185,188,189,18C,18D,18E,18F,190,191,192,193,195,198,199,19A,1A0,1A1,1A2,1A3,1A4,1A5,1A6,1A7,1A8,1A9,1AA,1AB,1AC,1AD,1AE,1B0,1B1,1B7,1BA,r6,a20,m4,lsfw')
2015-05-31 16:33:13,430 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2015-05-31 16:33:13,430 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2015-05-31 16:33:13,430 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2015-05-31 16:33:13,430 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2015-05-31 16:33:13,431 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2015-05-31 16:33:13,431 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2015-05-31 16:33:13,431 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f7dd40> about HardwareID('modalias', 'pci:v00008086d00002DABsv00001458sd00005000bc06sc00i00')
2015-05-31 16:33:13,433 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x194e3b0> about HardwareID('modalias', 'acpiNP0C02:')
2015-05-31 16:33:13,434 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x194e3b0> about HardwareID('modalias', 'platform:microcode')
2015-05-31 16:33:13,434 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x194e3b0> about HardwareID('modalias', 'usb:v046Dp0821d0010dcEFdsc02dp01ic0Eisc02ip00in03')
2015-05-31 16:33:13,434 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x194e3b0> about HardwareID('modalias', 'usb:v1D6Bp0002d0313dc09dsc00dp01ic09isc00ip00in00')
2015-05-31 16:33:13,434 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x194e3b0> about HardwareID('modalias', 'usb:v1B1Cp1B11d0120dc00dsc00dp00ic03isc00ip00in01')
2015-05-31 16:33:13,434 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x194e3b0> about HardwareID('modalias', 'platform:coretemp')
2015-05-31 16:33:13,434 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x194e3b0> about HardwareID('modalias', 'acpi:INT0800:')
2015-05-31 16:33:13,434 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x194e3b0> about HardwareID('modalias', 'pci:v00008086d0000342Dsv00000000sd00000000bc08sc00i20')
2015-05-31 16:33:13,434 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x194e3b0> about HardwareID('modalias', 'pci:v00008086d00002DA2sv00001458sd00005000bc06sc00i00')
2015-05-31 16:33:13,434 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x194e3b0> about HardwareID('modalias', 'pci:v00001B4Bd00009123sv00001B4Bsd00009123bc01sc06i01')
2015-05-31 16:33:13,434 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x194e3b0> about HardwareID('modalias', 'acpiNP0C01:')
2015-05-31 16:33:13,434 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x194e3b0> about HardwareID('modalias', 'dmi:bvnAwardSoftwareInternational,Inc.:bvrF9d:bd09/01/2011:svnGigabyteTechnologyCo.,Ltd.nX58A-UD7vr:rvnGigabyteTechnologyCo.,Ltd.:rnX58A-UD7:rvr:cvnGigabyteTechnologyCo.,Ltd.:ct3:cvr:')
2015-05-31 16:33:13,434 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x194e3b0> about HardwareID('modalias', 'usb:vE0FFp0002d0001dc00dsc00dp00ic03isc01ip02in00')
2015-05-31 16:33:13,434 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x194e3b0> about HardwareID('modalias', 'usb:v1D6Bp0001d0313dc09dsc00dp00ic09isc00ip00in00')
2015-05-31 16:33:13,434 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x194e3b0> about HardwareID('modalias', 'pci:v00008086d00003A34sv00001458sd00005004bc0Csc03i00')
2015-05-31 16:33:13,434 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x194e3b0> about HardwareID('modalias', 'usb:v1D6Bp0003d0313dc09dsc00dp03ic09isc00ip00in00')
2015-05-31 16:33:13,434 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x194e3b0> about HardwareID('modalias', 'acpiNP0103:')
2015-05-31 16:33:13,434 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x194e3b0> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2015-05-31 16:33:13,434 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x194e3b0> about HardwareID('modalias', 'acpi:LNXCPU:')
2015-05-31 16:33:13,435 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x194e3b0> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,8,')
2015-05-31 16:33:13,435 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x194e3b0> about HardwareID('modalias', 'pci:v00008086d0000244Esv00001458sd00005000bc06sc04i01')
2015-05-31 16:33:13,435 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x194e3b0> about HardwareID('modalias', 'x86cpu:vendor:0000:family:0006:model:002C:feature:,0000,0001,0002,0003,0004,0005,0006,0007,0008,0009,000B,000C,000D,000E,000F,0010,0011,0013,0015,0016,0017,0018,0019,001A,001B,001C,001D,001F,002B,0034,003A,003B,003D,0068,006B,006C,006D,006F,0070,0072,0074,0075,0076,0078,007C,0080,0081,0082,0083,0084,0085,0087,0088,0089,008D,008E,008F,0091,0093,0094,0097,0099,00C0,00E0,00E1,00E7,0100,0101,0102,0103,0104')
2015-05-31 16:33:13,435 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x194e3b0> about HardwareID('modalias', 'serio:ty06pr00id00ex00')
2015-05-31 16:33:13,435 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x194e3b0> about HardwareID('modalias', 'acpiNP0100:')
2015-05-31 16:33:13,435 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x194e3b0> about HardwareID('modalias', 'pci:v0000197Bd00002363sv00001458sd0000B000bc01sc01i85')
2015-05-31 16:33:13,435 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x194e3b0> about HardwareID('modalias', 'pci:v00008086d00002DB2sv00001458sd00005000bc06sc00i00')
2015-05-31 16:33:13,435 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x194e3b0> about HardwareID('modalias', 'pci:v00008086d00002DA1sv00001458sd00005000bc06sc00i00')
2015-05-31 16:33:13,435 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x194e3b0> about HardwareID('modalias', 'pci:v00001002d0000AAA0sv00001002sd0000AAA0bc04sc03i00')
2015-05-31 16:33:13,435 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x194e3b0> about HardwareID('modalias', 'usb:v1B1Cp1B11d0120dc00dsc00dp00ic03isc01ip01in00')
2015-05-31 16:33:13,435 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x194e3b0> about HardwareID('modalias', 'usb:v046Dp0821d0010dcEFdsc02dp01ic0Eisc01ip00in02')
2015-05-31 16:33:13,435 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x194e3b0> about HardwareID('modalias', 'pci:v00008086d00003A3Esv00001458sd0000A102bc04sc03i00')
2015-05-31 16:33:13,435 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x194e3b0> about HardwareID('modalias', 'platform:iTCO_wdt')
2015-05-31 16:33:13,435 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x194e3b0> about HardwareID('modalias', 'pci:v00008086d00002DB1sv00001458sd00005000bc06sc00i00')
2015-05-31 16:33:13,435 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x194e3b0> about HardwareID('modalias', 'pci:v00008086d0000342Fsv00000000sd00000000bc08sc00i20')
2015-05-31 16:33:13,435 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x194e3b0> about HardwareID('modalias', 'acpiNP0800:')
2015-05-31 16:33:13,435 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x194e3b0> about HardwareID('modalias', 'pci:v00001033d00000194sv00001458sd00005007bc0Csc03i30')
2015-05-31 16:33:13,435 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x194e3b0> about HardwareID('modalias', 'pci:v00008086d00002D90sv00001458sd00005000bc06sc00i00')
2015-05-31 16:33:13,435 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x194e3b0> about HardwareID('modalias', 'pci:v00008086d00003405sv00001458sd00005000bc06sc00i00')
2015-05-31 16:33:13,436 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x194e3b0> about HardwareID('modalias', 'pci:v00001B4Bd00009128sv00001458sd0000B000bc01sc06i01')
2015-05-31 16:33:13,436 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x194e3b0> about HardwareID('modalias', 'usb:v1B1Cp1B02d0136dc00dsc00dp00ic03isc00ip00in02')
2015-05-31 16:33:13,436 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x194e3b0> about HardwareID('modalias', 'pci:v00008086d00002DB0sv00001458sd00005000bc06sc00i00')
2015-05-31 16:33:13,436 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x194e3b0> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2015-05-31 16:33:13,436 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x194e3b0> about HardwareID('modalias', 'pci:v00008086d0000342Esv00000000sd00000000bc08sc00i00')
2015-05-31 16:33:13,436 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x194e3b0> about HardwareID('modalias', 'pci:v00008086d00003A38sv00001458sd00005004bc0Csc03i00')
2015-05-31 16:33:13,436 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x194e3b0> about HardwareID('modalias', 'usb:vE0FFp0002d0001dc00dsc00dp00ic03isc00ip00in01')
2015-05-31 16:33:13,436 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x194e3b0> about HardwareID('modalias', 'pci:v00008086d00003423sv00000000sd00000000bc08sc00i00')
2015-05-31 16:33:13,436 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x194e3b0> about HardwareID('modalias', 'usb:v046Dp0821d0010dcEFdsc02dp01ic01isc01ip00in00')
2015-05-31 16:33:13,436 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x194e3b0> about HardwareID('modalias', 'scsi:t-0x03')
2015-05-31 16:33:13,436 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x194e3b0> about HardwareID('modalias', 'acpiNP0C0F:')
2015-05-31 16:33:13,436 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x194e3b0> about HardwareID('modalias', 'pci:v00008086d00003428sv00000000sd00000000bc08sc00i00')
2015-05-31 16:33:13,436 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x194e3b0> about HardwareID('modalias', 'pci:v00008086d00002DA0sv00001458sd00005000bc06sc00i00')
2015-05-31 16:33:13,436 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x194e3b0> about HardwareID('modalias', 'usb:v1B1Cp1B02d0136dc00dsc00dp00ic03isc01ip01in00')
2015-05-31 16:33:13,436 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x194e3b0> about HardwareID('modalias', 'pci:v00008086d00002D81sv00001458sd00005000bc06sc00i00')
2015-05-31 16:33:13,436 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x194e3b0> about HardwareID('modalias', 'usb:v046Dp0821d0010dcEFdsc02dp01ic01isc02ip00in01')
2015-05-31 16:33:13,436 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x194e3b0> about HardwareID('modalias', 'pci:v00008086d00003A39sv00001458sd00005004bc0Csc03i00')
2015-05-31 16:33:13,436 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x194e3b0> about HardwareID('modalias', 'pci:v00008086d00002D98sv00001458sd00005000bc06sc00i00')
2015-05-31 16:33:13,436 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x194e3b0> about HardwareID('modalias', 'pci:v00008086d00002DA3sv00001458sd00005000bc06sc00i00')
2015-05-31 16:33:13,437 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x194e3b0> about HardwareID('modalias', 'pci:v00008086d00003426sv00000000sd00000000bc08sc00i00')
2015-05-31 16:33:13,437 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x194e3b0> about HardwareID('modalias', 'pci:v00008086d00002DAAsv00001458sd00005000bc06sc00i00')
2015-05-31 16:33:13,437 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x194e3b0> about HardwareID('modalias', 'input:b0003v1B1Cp1B02e0111-e0,1,4,14,k74,75,77,7D,7E,7F,B7,B8,B9,BA,BB,BC,BD,BE,ram4,lsfw')
2015-05-31 16:33:13,437 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x194e3b0> about HardwareID('modalias', 'pci:v00008086d00002D99sv00001458sd00005000bc06sc00i00')
2015-05-31 16:33:13,437 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x194e3b0> about HardwareID('modalias', 'pci:v00008086d00002D91sv00001458sd00005000bc06sc00i00')
2015-05-31 16:33:13,437 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x194e3b0> about HardwareID('modalias', 'platform:it87')
2015-05-31 16:33:13,437 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x194e3b0> about HardwareID('modalias', 'pci:v00008086d00003A30sv00001458sd00005001bc0Csc05i00')
2015-05-31 16:33:13,437 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x194e3b0> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2015-05-31 16:33:13,437 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x194e3b0> about HardwareID('modalias', 'input:b0003v1B1Cp1B11e0003-e0,1,11,k71,72,73,74,75,76,77,78,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,8B,8C,8D,8E,8F,90,91,92,93,94,95,96,97,98,99,9A,9B,9C,9D,9E,9F,A0,A1,A2,A3,A4,A5,A6,A7,A8,A9,AA,AB,AC,AD,AE,AF,B0,B1,B2,B3,B4,B5,B6,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,C3,C4,C5,C6,C7,C8,C9,CA,CB,CC,CD,CE,CF,D0,D1,D2,D3,D4,D5,D6,D7,D8,D9,DA,DB,DC,DD,DE,DF,E0,E1,E2,E3,E4,E5,E6,E7,E8,E9,EA,EB,EC,ED,EE,EF,F0,F1,F2,F3,F4,F5,F6,F7,F8,F9,FA,FB,FC,FD,FE,FF,raml0,1,2,3,4,5,6,7,8,9,A,B,C,D,E,sfw')
2015-05-31 16:33:13,437 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x194e3b0> about HardwareID('modalias', 'platform:gpio_ich')
2015-05-31 16:33:13,437 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x194e3b0> about HardwareID('modalias', 'wmi:F6CB5C3C-9CAE-4EBD-B577-931EA32A2CC0')
2015-05-31 16:33:13,437 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x194e3b0> about HardwareID('modalias', 'pci:v00008086d00002DA9sv00001458sd00005000bc06sc00i00')
2015-05-31 16:33:13,437 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x194e3b0> about HardwareID('modalias', 'pci:v00008086d00002D93sv00001458sd00005000bc06sc00i00')
2015-05-31 16:33:13,437 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x194e3b0> about HardwareID('modalias', 'pci:v00008086d00002DA8sv00001458sd00005000bc06sc00i00')
2015-05-31 16:33:13,437 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x194e3b0> about HardwareID('modalias', 'acpiNP0B00:')
2015-05-31 16:33:13,437 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x194e3b0> about HardwareID('modalias', 'pci:v000010ECd00008168sv00001458sd0000E000bc02sc00i00')
2015-05-31 16:33:13,437 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x194e3b0> about HardwareID('modalias', 'usb:v1B1Cp1B11d0120dc00dsc00dp00ic03isc00ip00in02')
2015-05-31 16:33:13,438 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x194e3b0> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,')
2015-05-31 16:33:13,438 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x194e3b0> about HardwareID('modalias', 'acpiNP0200:')
2015-05-31 16:33:13,438 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x194e3b0> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2015-05-31 16:33:13,438 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x194e3b0> about HardwareID('modalias', 'pci:v00008086d00003427sv00000000sd00000000bc08sc00i00')
2015-05-31 16:33:13,438 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x194e3b0> about HardwareID('modalias', 'pci:v00008086d00002DB3sv00001458sd00005000bc06sc00i00')
2015-05-31 16:33:13,438 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x194e3b0> about HardwareID('modalias', 'pci:v00001002d00006798sv00001002sd00003000bc03sc00i00')
2015-05-31 16:33:13,438 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x194e3b0> about HardwareID('modalias', 'input:b0003vE0FFp0002e0100-e0,1,2,3,4,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,8B,8C,8E,90,96,98,9B,9C,9E,9F,A1,A3,A4,A5,A6,A7,A8,A9,AB,AC,AD,AE,B0,B1,B2,B3,B4,B5,B6,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,CE,CF,D0,D1,D2,D4,D8,D9,DB,DF,E4,E7,E8,E9,EA,EB,F0,F1,100,161,162,166,16A,16E,172,174,176,178,179,17A,17B,17C,17D,17F,180,182,183,185,188,189,18C,18D,18E,18F,190,191,192,193,195,198,199,19A,1A0,1A1,1A2,1A3,1A4,1A5,1A6,1A7,1A8,1A9,1AA,1AB,1AC,1AD,1AE,1B0,1B1,1B7,1BA,r6,a20,28,29,2A,2B,2C,2D,2E,m4,lsfw')
2015-05-31 16:33:13,438 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x194e3b0> about HardwareID('modalias', 'pci:v00008086d00003A37sv00001458sd00005004bc0Csc03i00')
2015-05-31 16:33:13,438 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x194e3b0> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2015-05-31 16:33:13,438 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x194e3b0> about HardwareID('modalias', 'pci:v0000197Bd00002363sv00001458sd0000B000bc01sc06i01')
2015-05-31 16:33:13,438 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x194e3b0> about HardwareID('modalias', 'usb:v04A9p176Bd0208dc00dsc00dp00icFFisc00ipFFin00')
2015-05-31 16:33:13,438 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x194e3b0> about HardwareID('modalias', 'input:b0003vE0FFp0002e0100-e0,1,2,4,k110,111,112,113,114,115,116,117,r0,1,6,8,am4,lsfw')
2015-05-31 16:33:13,438 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x194e3b0> about HardwareID('modalias', 'platformcspkr')
2015-05-31 16:33:13,438 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x194e3b0> about HardwareID('modalias', 'usb:v04A9p176Bd0208dc00dsc00dp00ic07isc01ip02in01')
2015-05-31 16:33:13,438 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x194e3b0> about HardwareID('modalias', 'hid:b0003g0001v00001B1Cp00001B02')
2015-05-31 16:33:13,438 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x194e3b0> about HardwareID('modalias', 'hid:b0003g0001v0000E0FFp00000002')
2015-05-31 16:33:13,438 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x194e3b0> about HardwareID('modalias', 'acpiNP0A03:')
2015-05-31 16:33:13,438 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x194e3b0> about HardwareID('modalias', 'input:b0003v046Dp0821e0010-e0,1,kD4,ramlsfw')
2015-05-31 16:33:13,438 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x194e3b0> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2015-05-31 16:33:13,439 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x194e3b0> about HardwareID('modalias', 'usb:v04A9p176Bd0208dc00dsc00dp00ic07isc01ip02in02')
2015-05-31 16:33:13,439 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x194e3b0> about HardwareID('modalias', 'acpiNP0C04:')
2015-05-31 16:33:13,439 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x194e3b0> about HardwareID('modalias', 'pci:v00008086d00002C71sv00001458sd00005000bc06sc00i00')
2015-05-31 16:33:13,439 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x194e3b0> about HardwareID('modalias', 'pci:v00008086d00002D92sv00001458sd00005000bc06sc00i00')
2015-05-31 16:33:13,439 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x194e3b0> about HardwareID('modalias', 'input:b0003v1B1Cp1B02e0111-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,8C,8E,96,98,9E,9F,A1,A3,A4,A5,A6,AD,B0,B1,B2,B3,B4,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,sfw')
2015-05-31 16:33:13,439 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x194e3b0> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfwD,')
2015-05-31 16:33:13,439 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x194e3b0> about HardwareID('modalias', 'pci:v00008086d00003422sv00000000sd00000000bc08sc00i00')
2015-05-31 16:33:13,439 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x194e3b0> about HardwareID('modalias', 'pci:v00008086d00003A36sv00001458sd00005004bc0Csc03i00')
2015-05-31 16:33:13,439 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x194e3b0> about HardwareID('modalias', 'pci:v00008086d00003A16sv00001458sd00005001bc06sc01i00')
2015-05-31 16:33:13,439 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x194e3b0> about HardwareID('modalias', 'acpiNP0000:')
2015-05-31 16:33:13,439 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x194e3b0> about HardwareID('modalias', 'usb:v1B1Cp1A95d0100dc00dsc00dp00ic08isc06ip50in00')
2015-05-31 16:33:13,439 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x194e3b0> about HardwareID('modalias', 'usb:v1B1Cp1B02d0136dc00dsc00dp00ic03isc00ip00in01')
2015-05-31 16:33:13,439 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x194e3b0> about HardwareID('modalias', 'pci:v00008086d00003A22sv00001458sd0000B005bc01sc06i01')
2015-05-31 16:33:13,439 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x194e3b0> about HardwareID('modalias', 'pci:v00008086d00003425sv00000000sd00000000bc08sc00i00')
2015-05-31 16:33:13,439 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x194e3b0> about HardwareID('modalias', 'pci:v00008086d00002D9Csv00001458sd00005000bc06sc00i00')
2015-05-31 16:33:13,439 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x194e3b0> about HardwareID('modalias', 'usb:v1D6Bp0002d0313dc09dsc00dp00ic09isc00ip00in00')
2015-05-31 16:33:13,439 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x194e3b0> about HardwareID('modalias', 'usb:v1B1Cp1B11d0120dc00dsc00dp00ic03isc00ip00in03')
2015-05-31 16:33:13,439 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x194e3b0> about HardwareID('modalias', 'pci:v00008086d00003A35sv00001458sd00005004bc0Csc03i00')
2015-05-31 16:33:13,440 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x194e3b0> about HardwareID('modalias', 'input:b0003v1B1Cp1B02e0111-e0,1,2,3,4,k71,72,73,74,77,80,82,83,85,86,87,88,89,8A,8B,8C,8E,90,96,98,9B,9C,9E,9F,A1,A3,A4,A5,A6,A7,A8,A9,AB,AC,AD,AE,B0,B1,B2,B5,B6,CE,CF,D0,D1,D2,D4,D8,D9,DB,DF,E4,E7,E8,E9,EA,EB,F1,100,161,162,166,16A,16E,172,174,176,178,179,17A,17B,17C,17D,17F,180,182,183,185,188,189,18C,18D,18E,18F,190,191,192,193,195,198,199,19A,1A0,1A1,1A2,1A3,1A4,1A5,1A6,1A7,1A8,1A9,1AA,1AB,1AC,1AD,1AE,1B0,1B1,1B7,1BA,r6,a20,m4,lsfw')
2015-05-31 16:33:13,440 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x194e3b0> about HardwareID('modalias', 'pci:v00008086d00002DABsv00001458sd00005000bc06sc00i00')
2015-05-31 16:33:13,473 DEBUG: fglrx.enabled(fglrx): target_alt ['/usr/lib/fglrx/ld.so.conf', '/usr/lib/pxpress/ld.so.conf'] current_alt /usr/lib/fglrx/ld.so.conf other target alt ['/usr/lib/fglrx/alt_ld.so.conf', '/usr/lib/pxpress/alt_ld.so.conf'] other current alt /usr/lib/fglrx/alt_ld.so.conf
2015-05-31 16:33:13,473 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2015-05-31 16:33:13,513 DEBUG: fglrx.enabled(fglrx_updates): target_alt ['/usr/lib/fglrx/ld.so.conf', '/usr/lib/pxpress/ld.so.conf'] current_alt /usr/lib/fglrx/ld.so.conf other target alt ['/usr/lib/fglrx/alt_ld.so.conf', '/usr/lib/pxpress/alt_ld.so.conf'] other current alt /usr/lib/fglrx/alt_ld.so.conf
2015-05-31 16:33:13,514 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2015-05-31 16:33:13,534 DEBUG: fglrx.enabled(fglrx): target_alt ['/usr/lib/fglrx/ld.so.conf', '/usr/lib/pxpress/ld.so.conf'] current_alt /usr/lib/fglrx/ld.so.conf other target alt ['/usr/lib/fglrx/alt_ld.so.conf', '/usr/lib/pxpress/alt_ld.so.conf'] other current alt /usr/lib/fglrx/alt_ld.so.conf
2015-05-31 16:33:13,534 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2015-05-31 16:33:13,561 DEBUG: fglrx.enabled(fglrx): target_alt ['/usr/lib/fglrx/ld.so.conf', '/usr/lib/pxpress/ld.so.conf'] current_alt /usr/lib/fglrx/ld.so.conf other target alt ['/usr/lib/fglrx/alt_ld.so.conf', '/usr/lib/pxpress/alt_ld.so.conf'] other current alt /usr/lib/fglrx/alt_ld.so.conf
2015-05-31 16:33:13,561 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2015-05-31 16:33:13,578 DEBUG: fglrx.enabled(fglrx_updates): target_alt ['/usr/lib/fglrx/ld.so.conf', '/usr/lib/pxpress/ld.so.conf'] current_alt /usr/lib/fglrx/ld.so.conf other target alt ['/usr/lib/fglrx/alt_ld.so.conf', '/usr/lib/pxpress/alt_ld.so.conf'] other current alt /usr/lib/fglrx/alt_ld.so.conf
2015-05-31 16:33:13,579 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2015-05-31 16:33:24,219 DEBUG: fglrx.enabled(fglrx_updates): target_alt ['/usr/lib/fglrx/ld.so.conf', '/usr/lib/pxpress/ld.so.conf'] current_alt /usr/lib/fglrx/ld.so.conf other target alt ['/usr/lib/fglrx/alt_ld.so.conf', '/usr/lib/pxpress/alt_ld.so.conf'] other current alt /usr/lib/fglrx/alt_ld.so.conf
2015-05-31 16:33:24,219 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2015-05-31 16:33:29,347 DEBUG: fglrx.enabled(fglrx_updates): target_alt ['/usr/lib/fglrx/ld.so.conf', '/usr/lib/pxpress/ld.so.conf'] current_alt /usr/lib/fglrx/ld.so.conf other target alt ['/usr/lib/fglrx/alt_ld.so.conf', '/usr/lib/pxpress/alt_ld.so.conf'] other current alt /usr/lib/fglrx/alt_ld.so.conf
2015-05-31 16:33:29,347 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2015-05-31 16:33:37,494 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates

2015-05-31 16:33:37,494 WARNING: /sys/module/fglrx_updates/drivers does not exist, cannot rebind fglrx_updates driver
2015-05-31 16:33:37,494 ERROR: XorgDriverHandler.enable(): package or module not installed, aborting
2015-05-31 16:34:04,116 DEBUG: fglrx.enabled(fglrx_updates): target_alt ['/usr/lib/fglrx/ld.so.conf', '/usr/lib/pxpress/ld.so.conf'] current_alt /usr/lib/fglrx/ld.so.conf other target alt ['/usr/lib/fglrx/alt_ld.so.conf', '/usr/lib/pxpress/alt_ld.so.conf'] other current alt /usr/lib/fglrx/alt_ld.so.conf
2015-05-31 16:34:04,116 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2015-05-31 16:34:04,124 DEBUG: fglrx.enabled(fglrx_updates): target_alt ['/usr/lib/fglrx/ld.so.conf', '/usr/lib/pxpress/ld.so.conf'] current_alt /usr/lib/fglrx/ld.so.conf other target alt ['/usr/lib/fglrx/alt_ld.so.conf', '/usr/lib/pxpress/alt_ld.so.conf'] other current alt /usr/lib/fglrx/alt_ld.so.conf
2015-05-31 16:34:04,124 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
[/PHP][PHP][/PHP]
[/PHP]

---

