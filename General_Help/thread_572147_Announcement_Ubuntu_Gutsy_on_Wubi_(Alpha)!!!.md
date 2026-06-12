---
title: "Announcement: Ubuntu Gutsy on Wubi (Alpha)!!!"
date: 2007-10-10
forum: General Help
---

### Post by ago on 2007-10-10
Ok I finally have a version that might even work with the new Ubuntu 7.10.
It is still an (early) alpha, so be aware! Unless you run it within a VM, remember to BACK-UP!!!

[http://wubi-installer.org/devel/minefield](http://wubi-installer.org/devel/minefield)

In case you run into trouble:
* If you get stacked and do not know how to reboot, hold down Alt+SysRq and type REISUB
* Keep a recovery CD with chkdsk at hand, it shouldn't be needed but better safe than sorry.

Please let me know whether it works or not!

PS: It is highly recommended to uninstall any previous wubi version before trying the new one.
PS2: This one uses the LIVE CD ISO. So, if you want to download separately, use the appropriate FINAL DESKTOP ISO.

---

### Post by BlueFiberOptics on 2007-10-10
Testing it on my notebook (HP ZD8000) as we speak.

---

### Post by BlueFiberOptics on 2007-10-10
My notebook froze after my computer restarted and started installing Ubuntu.  Froze at 27% copying. "Installing System"

---

### Post by ago on 2007-10-10
please see [http://ubuntuforums.org/showpost.php?p=3509159&postcount=65](http://ubuntuforums.org/showpost.php?p=3509159&postcount=65)
also check wether you run out of memory (keep "free" running while files get copied)

---

### Post by neodorian on 2007-10-10
Tried this one on my tablet.  The one from a few days ago did not work but I'm posting this message from Gutsy on that same tablet so I'm at least this far ;)  There are a few bugs that I don't think are related to Wubi but I'm messing with those now.

Thanks for all the time you spend on this project.  It's the only (easy) way for me to run Ubuntu on my tablet PC.

EDIT:  although the thanks remain, the success was fleeting.  After the first round of updates and a reboot it will no longer let me boot into ubuntu.  

Filesystem type is ntfs, partition type 0x7
kernel  /vmlinuz-2.6.22-14-generic root=UUID=....etc.....
loop=/ubuntu/disks/root.disk ro quiet splash automatic-ubiquity locale=en_US

Error 17: File not found

Press any key to continue...


Windows still boots fine though.

---

### Post by pewpew on 2007-10-11
I have same problem as above

> 
Filesystem type is ntfs, partition type 0x7
kernel /vmlinuz-2.6.22-14-generic root=UUID=....etc.....
loop=/ubuntu/disks/root.disk ro quiet splash automatic-ubiquity locale=en_US

Error 17: File not found

Press any key to continue...

I have a Dell inspiron 9300 (it is a laptop which uses intell). I have tried rev 324 amd 322 with same problem. Im trying to install xubuntu and not "normal" ubuntu - if you want i can try to install ubuntu (for testing purpose) i can do that.
The stable install works on my laptop both ubuntu and xubuntu.

---

### Post by ago on 2007-10-11
It should read

kernel **/boot**/vmlinuz*
initrd **/boot**/initrd*

Edit ubuntu/disks/boot/menu.lst manually for now, I'll see if I can fix it tonight.

---

### Post by pewpew on 2007-10-11
I tried to write /boot/vmlinz* and it still doesnt work (same error), tho i could not find anything regarding initrd /boot/initrd*
I new to linux and even newer to grub so i may have f***ed something up :P

btw, great program(s) and keep up the good work!

best regards
PewPew

PS: i try to download the newest version this weekend and try again (i have to much school stuff right now to test (read about how linux, grub etc works)

---

### Post by ago on 2007-10-11
> **pewpew said:**
> I tried to write /boot/vmlinz*
By "*" i mean: keep anything else that was there, only change the initial path...

So it should be: kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=.... loop=/ubuntu/disks/root.disk ro quiet splash

The file is in ubuntu/disks/boot/grub/menu.lst

---

### Post by pewpew on 2007-10-11
ok, sorry, i may have underplayed my role, i studie software engineering - still new to linux.

I knew what you mean by "*".  I will play around some more with grub when i get time.

(in theory i know what the problem is - wrong linking or missing files)

---

### Post by neodorian on 2007-10-11
Ok, back up and running after manually editing.  Thanks.  I should have guessed it after a file not found but I didn't know where to look or the right path that it should have been using.

---

### Post by ago on 2007-10-12
Have a new revision out: #330. This one uses the release candidate CD.

---

### Post by penguin22 on 2007-10-12
When trying to install on two different Vista 64-bit machines, it crashes immediately after downloading the first file.  I am currently downloaded the Desktop 64-bit RC version to see if having the file local improves matters, but wanted to let you know of the issue if you did not already.

Thanks,

David

---

### Post by pewpew on 2007-10-12
#3.30 
will crash if you select xubuntu, when it tries to download the image.
guess it is because there isnt a xubuntu yet and it tries to download something that doesnt exist -> crash

---

### Post by ago on 2007-10-12
> **penguin22 said:**
> When trying to install on two different Vista 64-bit machines, it crashes immediately after downloading the first file.  I am currently downloaded the Desktop 64-bit RC version to see if having the file local improves matters, but wanted to let you know of the issue if you did not already.
Probably not, since the first file is the metalink, not the ISO. I will look into it.

---

### Post by penguin22 on 2007-10-12
After downloading the correct ISO and placing it in the ubuntu directory where the metafile is, it seemed to get further after complaining about and ignoring the file check.  After extracting it gave an error regarding bcdedit.  Perhaps there are other parts that need to be downloaded as well, but for now I have put installing on hold as I figured that I'd see your response first.

---

### Post by neodorian on 2007-10-15
> **ago said:**
> It should read

kernel **/boot**/vmlinuz*
initrd **/boot**/initrd*

Edit ubuntu/disks/boot/menu.lst manually for now, I'll see if I can fix it tonight.

Interestingly enough, this worked well until today.  I did new updates, rebooted, got the file not found error, changed the path, and it still didn't work.

```
## ## End Default Options ##

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=/host/ubuntu/disks/root.disk ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=/host/ubuntu/disks/root.disk ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

```

Not sure what went wrong this time.

---

### Post by gorgle on 2007-10-15
Ermm.. I'm having problem with alpha. Anyone can give me a hand? I installed wubi from windows xp. Then when I boot into Ubuntu, "Kernel Panic - not syncing: Attemped to kill init" came out. What should I do? :confused:

---

### Post by ago on 2007-10-15
> **penguin22 said:**
> After extracting it gave an error regarding bcdedit.
What error?

---

### Post by ago on 2007-10-15
> **neodorian said:**
> 
Not sure what went wrong this time.

It must be:

root (hdX,Y)/ubuntu/disks 

The above depends on # groot.

---

### Post by ago on 2007-10-15
> **gorgle said:**
> Ermm.. I'm having problem with alpha. Anyone can give me a hand? I installed wubi from windows xp. Then when I boot into Ubuntu, "Kernel Panic - not syncing: Attemped to kill init" came out. What should I do? :confused:

I'd need more information on what caused the kernel panic. Boot in vorbose mode (edit menu.lst and remove "quiet splash") to begin with.

---

### Post by neodorian on 2007-10-15
> **ago said:**
> It must be:

root (hdX,Y)/ubuntu/disks 

The above depends on # groot.

Cool.  That solved the file not found but now it gets past that and the 'ubuntu' logo comes up but the progress bar halts immediately and there is no disk activity.  Any ideas where to look for this?  I'm pretty sure the paths are right now.

---

### Post by ago on 2007-10-15
> **neodorian said:**
> Cool.  That solved the file not found but now it gets past that and the 'ubuntu' logo comes up but the progress bar halts immediately and there is no disk activity.  Any ideas where to look for this?  I'm pretty sure the paths are right now.

If you see the logo it's no longer a grub issue, but you can disable "quiet splash" to get more details

---

### Post by neodorian on 2007-10-15
halts at:

```
Clocksource tsc unstable (delta = -71448299 ns)
```

Sounds like fun.

---

### Post by gorgle on 2007-10-15
> **ago said:**
> I'd need more information on what caused the kernel panic. Boot in vorbose mode (edit menu.lst and remove "quiet splash") to begin with.

Gah! Kinda noob in Linux =/ Don't know how to even remove "quiet splash" ._. I'll try waiting for later versions. 

It did have some funny stuff before kernel panic. I'll post screenshot later if it'll help.

---

### Post by Megaduce417 on 2007-10-15
Has anyone heard of any issues with a speed error?  I have a 64x2 AMD system and it will not allow me to install.  It locks up and talks about me having to change the speed on my motherboard.  Any advice will be good, thanks.  :confused:

---

### Post by rokinroj on 2007-10-16
No luck for me.  On a Dell Precision 340 1.8Ghz, 1gig of Ram.  I can get all the way through installation, then it restarts itself, then just goes to a non responsive blinking cursor.  Thought it may have been a hosed installation so I wiped the drive and tried again same thing.  Oh well, it is alpha after all.  BTW...Love Wubi, keep up the great work!

---

### Post by mikeize on 2007-10-18
Is it possible to simply upgrade from feisty to gutsy in wubi?  I've got feisty installed on my dell laptop, and would like gutsy on there...  can I just upgrade from the command line (whatever that command is)?
Also, those HAL updates caused problems for me, is that something that would be fixed in gutsy?

-mike

---

### Post by ago on 2007-10-18
> **mikeize said:**
> Is it possible to simply upgrade from feisty to gutsy in wubi?  I've got feisty installed on my dell laptop, and would like gutsy on there...  can I just upgrade from the command line (whatever that command is)?
Also, those HAL updates caused problems for me, is that something that would be fixed in gutsy?

-mike

Hal probably will work, but I have never been able to reproduce the problems on my machine so I cannot say for sure. Upgrading is not going to be completely trivial. I may write an upgrade script later on, but that will not come before the 7.10 version stabilizes.

---

### Post by mikeize on 2007-10-18
Thanks, I'll stay tuned!

-mike

btw- wubi is awesome, it allowed me to really get into ubuntu/linux.  cheers.

---

### Post by runemaste644 on 2007-10-18
I was wondering if there was an IRC channel for Wubi.

---

### Post by ago on 2007-10-18
now on irc.ubuntu.com #wubi
but I normally open the channel on request since I cannot usually attend
I will setup something more permanent later on
I am xivulon there.

---

### Post by tyfoon786 on 2007-10-18
The 339 build does not run on my windows vista ultimate while the previous build (336) was able to run :confused:. It keeps crashing on me everytime i try running it (after i allow it to access my computer). I have not installed Wubi yet but i would like to do so with since 7.10 has released today. I can't seem to find any information about the error - I just that "Windows based UBuntu Installer has stopped working" message. 

---

Also for my knowledge, is it ok if i use the 7.04 installer instead, install and then upgrade to 7.10 using the cd i just burned? Would any new errors come up? Sorry but i an a newbie with ubuntu and wubi.

---

### Post by henriksultan on 2007-10-18
Just installed it and get the same error as another user before where he had to manualy edit grubs menu.lst and it seems right for me but still get the error?

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)/ubuntu/disks
kernel	/boot/vmlinuz-2.6.22-14-generic root=/dev/sdb5 loop=/ubuntu/disks/root.disk ro quiet splash automatic-ubiquity locale=sv_SE
initrd	/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)/ubuntu/disks
kernel	/boot/vmlinuz-2.6.22-14-generic root=/dev/sdb5 loop=/ubuntu/disks/root.disk ro single
initrd	/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,0)/ubuntu/disks
kernel	/boot/memtest86+.bin

---

### Post by ahecht on 2007-10-18
I downloaded the ubuntu-7.10-desktop-i386.iso and the Wubi 7.10 alpha and put them in the same directory. However, since Wubi detects that I have a Core 2 Duo in my system, it insists on downloading the AMD64 version of Ubuntu.

Even though my processor can handle it, I don't want to use the 64 bit version because of the compatibility issues. Is there any way to force Wubi 7.10 to install from my i386 image?

An "Advanced Options" control panel would be nice for this sort of thing.

---

### Post by ago on 2007-10-19
> **henriksultan said:**
> Just installed it and get the same error as another user before where he had to manualy edit grubs menu.lst and it seems right for me but still get the error?

Hmmm strange, your menu.lst looks good to me. Comment out hidemenu and press C at the grub menu. Then try to enter the commands manually and see if some of the files is not available (you can use tab completion).

---

### Post by ago on 2007-10-19
> **ahecht said:**
> 
Even though my processor can handle it, I don't want to use the 64 bit version because of the compatibility issues. Is there any way to force Wubi 7.10 to install from my i386 image?


Not at the moment but there will be. Go ahead with 64 bits for testing! :P

---

### Post by linlay on 2007-10-19
please release a new minefield build of Wubi..Thanks! :)

I'm still trying to get Ubuntu 7.10 to work. Currently it stops at the 'Guided Partition' step of the  ubuntu installation ..complaining that the filesystem is NTFS ...

---

### Post by ago on 2007-10-19
Attach here /var/log/syslog and partman log. Press alt+f2 and copy it over the windows partition (you may need to mount that manually). If it exits too quickly, remove automatic-ubiquity from install/boot/grub/menu.lst. Then when in the gnome desktop open a terminal and run: ubiquity --automatic.

---

### Post by linlay on 2007-10-19
> **ago said:**
> Attach here /var/log/syslog and partman log. Press alt+f2 and copy it over the windows partition (you may need to mount that manually). If it exits too quickly, remove automatic-ubiquity from install/boot/grub/menu.lst. Then when in the gnome desktop open a terminal and run: ubiquity --automatic.


Ok here's what you need! Hope this helps man.
I removed the automatic-ubiquity from the menu.1st, and I tried to intall it. So the wubi boots me into the LiveCD session, and I try to install from there ...and I get the same error at the 'Guided Partition' step.

Attached are the logs needed.


**Here's an extract of syslog:**
> 
Oct 19 17:04:15 ubuntu ubiquity: Accounting clusters ...
Oct 19 17:04:15 ubuntu ubiquity: Cluster accounting failed at 14806196 (0xe1ecb4): extra cluster in $Bitmap
Oct 19 17:04:15 ubuntu ubiquity: Filesystem check failed! Totally 1 cluster accounting mismatches.
Oct 19 17:04:15 ubuntu ubiquity: ERROR: NTFS is inconsistent. Run chkdsk /f on Windows then reboot it TWICE!
Oct 19 17:04:15 ubuntu ubiquity: The usage of the /f parameter is very IMPORTANT! No modification was
Oct 19 17:04:15 ubuntu ubiquity: and will be made to NTFS by this software until it gets repaired.
Oct 19 17:04:15 ubuntu ntfsresize: ntfsresize v1.13.1 (libntfs 9:0:0)
Oct 19 17:04:15 ubuntu ntfsresize: Device name        : /dev/sda1
Oct 19 17:04:15 ubuntu ntfsresize: NTFS volume version: 3.1
Oct 19 17:04:15 ubuntu ntfsresize: Cluster size       : 4096 bytes
Oct 19 17:04:15 ubuntu ntfsresize: Current volume size: 80015491584 bytes (80016 MB)
Oct 19 17:04:15 ubuntu ntfsresize: Current device size: 80015491584 bytes (80016 MB)
Oct 19 17:04:15 ubuntu ntfsresize: Checking filesystem consistency ...
Oct 19 17:04:15 ubuntu ntfsresize: Accounting clusters ...
Oct 19 17:04:15 ubuntu ntfsresize: Cluster accounting failed at 14806196 (0xe1ecb4): extra cluster in $Bitmap
Oct 19 17:04:15 ubuntu ntfsresize: Filesystem check failed! Totally 1 cluster accounting mismatches.
Oct 19 17:04:15 ubuntu ntfsresize: ERROR: NTFS is inconsistent. Run chkdsk /f on Windows then reboot it TWICE!
Oct 19 17:04:15 ubuntu ntfsresize: The usage of the /f parameter is very IMPORTANT! No modification was
Oct 19 17:04:15 ubuntu ntfsresize: and will be made to NTFS by this software until it gets repaired.
Oct 19 17:04:15 ubuntu ubiquity: + return 1
Oct 19 17:04:15 ubuntu ubiquity: + logger -t partman
Oct 19 17:04:15 ubuntu ubiquity:  Error running 'ntfsresize --info'
Oct 19 17:04:15 ubuntu partman: Error running 'ntfsresize --info'
Oct 19 17:04:15 ubuntu ubiquity: + return 1
Oct 19 17:04:15 ubuntu ubiquity: + logger
Oct 19 17:04:15 ubuntu ubiquity:  -t partman-auto-loop Error: Failed to get NTFS resize range for /var/lib/partman/devices/=dev=sda/7773696-80023265279
Oct 19 17:04:15 ubuntu partman-auto-loop: Error: Failed to get NTFS resize range for /var/lib/partman/devices/=dev=sda/7773696-80023265279
Oct 19 17:04:15 ubuntu ubiquity: + exit 1
Oct 19 17:04:15 ubuntu ubiquity: + rm -rf
Oct 19 17:04:15 ubuntu ubiquity:  /tmp/partman-auto-loop.o10004
Oct 19 17:04:18 ubuntu ntfsresize: ntfsresize v1.13.1 (libntfs 9:0:0)
Oct 19 17:04:18 ubuntu ntfsresize: Device name        : /dev/sda1
Oct 19 17:04:18 ubuntu ntfsresize: NTFS volume version: 3.1
Oct 19 17:04:18 ubuntu ntfsresize: Cluster size       : 4096 bytes
Oct 19 17:04:18 ubuntu ntfsresize: Current volume size: 80015491584 bytes (80016 MB)
Oct 19 17:04:18 ubuntu ntfsresize: Current device size: 80015491584 bytes (80016 MB)
Oct 19 17:04:18 ubuntu ntfsresize: Checking filesystem consistency ...
Oct 19 17:04:18 ubuntu ntfsresize: Accounting clusters ...
Oct 19 17:04:18 ubuntu ntfsresize: Cluster accounting failed at 14806196 (0xe1ecb4): extra cluster in $Bitmap
Oct 19 17:04:18 ubuntu ntfsresize: Filesystem check failed! Totally 1 cluster accounting mismatches.
Oct 19 17:04:18 ubuntu ntfsresize: ERROR: NTFS is inconsistent. Run chkdsk /f on Windows then reboot it TWICE!
Oct 19 17:04:18 ubuntu ntfsresize: The usage of the /f parameter is very IMPORTANT! No modification was
Oct 19 17:04:18 ubuntu ntfsresize: and will be made to NTFS by this software until it gets repaired.
Oct 19 17:04:18 ubuntu partman: Error running 'ntfsresize --info'
Oct 19 17:04:18 ubuntu ubiquity[9364]: switched to page stepPartAdvanced


---

### Post by henriksultan on 2007-10-19
> **ago said:**
> Hmmm strange, your menu.lst looks good to me. Comment out hidemenu and press C at the grub menu. Then try to enter the commands manually and see if some of the files is not available (you can use tab completion).

Sorry to bother again but what exactly do u want me to type? tried boot and it said kernel must be loaded? I really dont know what to do there?

---

### Post by henriksultan on 2007-10-19
Hi again :p
wrote the entire kernel /boot/** line at the menu and then boot and got this error message:

[  265.660648]kernel panic - not syncing: VFS: Unable to mount root fs on unkown wn-block(0,0)

Hopes this makes it clearer for someone coz it truly dont make any sense to me :p

Keep up the work btw, love wubi and been using it for a while (just not never registerd at the forum coz I never had a problem before)

---

### Post by ago on 2007-10-19
> **linlay said:**
> Ok here's what you need! Hope this helps man.
I removed the automatic-ubiquity from the menu.1st, and I tried to intall it. So the wubi boots me into the LiveCD session, and I try to install from there ...and I get the same error at the 'Guided Partition' step.

Attached are the logs needed.


**Here's an extract of syslog:**

Oct 19 17:04:18 ubuntu ntfsresize: ERROR: NTFS is inconsistent. **Run chkdsk /f on Windows **then reboot it TWICE!

---

### Post by ago on 2007-10-19
> **henriksultan said:**
> Sorry to bother again but what exactly do u want me to type? tried boot and it said kernel must be loaded? I really dont know what to do there?

You have to type the full block as you see it in menu.lst. 

I.e. the lines

root ....
kernel ...
initrd ...
boot

You can press tab at any time for suggestions.

---

### Post by MSchenker on 2007-10-19
I was running Wubi 7.04 (loved it).  Last night,  I decided to try Wubi 7.10 alpa. I uninstalled Wubi 7.04 and installed Wubi 7.10 alpha.

I'm still making the transition to Linux, so everything I do at this point is experimental and I don't care if things breaks.  That makes me a perfect candidate to try things!

Overall, it looks like Wubui 7.10 is almost there, but not quite...

1. After installation, and reboot, I got the "install" script as if I was running the Live CD.  Another reboot got rid of this.
2. In Adept, I installed Thunderbird and Firefox.  They appeared in Adept as "installed" but don't show up in any system menus.
3. Several small errors occur when running Adept or making various system settings. I kept getting a crash message: the screen with the gear and the sparks!
4. The system no longer was able to read my external hard drive.  It kept telling me the volume was not mounted, and when I tried to mount it, it said the device was "disabled."  Strangely, the correct volume label showed up in Dolphin.

I'm going to uninstall Wubi 7.10 alpha and reinstall Wubi 7.04.  At a later date, I'll run Wubi 7.10 again.

As I said, Wubi 7.04 is terrific and very stable.  But I am looking forward to getting a stable Wubi 7.10 release.  I really like a lot of the new features in 7.10.

You guys are doing great work!

---

### Post by henriksultan on 2007-10-19
> **ago said:**
> You have to type the full block as you see it in menu.lst. 

I.e. the lines

root ....
kernel ...
initrd ...
boot

You can press tab at any time for suggestions.

Tried, but he alwys stops at kernel and says it cant find the file? Lets just make sure Im doing it right.

Press c for command lines: then I type 
root* press enter
kernel * enter (get error cant find file)
initrd* enter (must load kernel obviously i havent :p)

Im I doing somthing wrong or is the kernel entery still just pointed at the wrong place? Might try a reinstall to see if it gets better?

---

### Post by ago on 2007-10-19
kernel /[TAB]
kernel /boot/[TAB]
...

Using tab is a way of navigating the files, so you can see what is available and what is not

---

### Post by gurpartap on 2007-10-19
Used wubi installer to install gutsy from hdd; mounted the iso on a virtual drive. Everything ran well, upto after reboot, and Ubuntu linux selection, i have to wait for almost 10 minutes and then it leaves me at ash terminal.

(drive is ntfs, maybe it won't be supported?)

Any proper walkthrough for Gutsy's included wubi installer?

---

### Post by henriksultan on 2007-10-19
> **ago said:**
> kernel /[TAB]
kernel /boot/[TAB]
...

Using tab is a way of navigating the files, so you can see what is available and what is not

Do I feel stupid :p The one thing i use the most in linux is the tab command and i didnt thing of it... haha 

Im in linux right now, the kernel boot thingi pointed to the wrong hdd for some reason? Should have been hd1,4 not 0.0.. thanks for the hint haha

But now it wont let me mount my external hdd, says:
Mound denied because NTFS is marked to be in use.

Then he babbels along about if in windows I should saftly remov hardware or force a mount? Ill try the force and see what happens... just wanted to say it worked :guitar:

---

### Post by henriksultan on 2007-10-19
I cant for the like of me mount the external hdd? He wont let me, and to force it i need to be root but there isnt any root???

---

### Post by ago on 2007-10-19
I doubt mounting issues are linked to wubi. As for the root, in Ubuntu you have to use "sudo".

---

### Post by henriksultan on 2007-10-19
Guesd so to :p but how to use sudo? <- ignore I used man sudo :p my bad for this dumb question

---

### Post by ago on 2007-10-19
> **henriksultan said:**
> Guesd so to :p but how to use sudo?

sudo command

---

### Post by henriksultan on 2007-10-19
I got it working after reading man sudo :) Thanks for all, and keep up the awsome wubi work! :)

---

### Post by mfigueroaj on 2007-10-19
This is my first post!!

I've tryin wubi 7.10 (wubi-cdboot.exe), but when restart I just got a live session... not an installation on a virtual disk.
Wubi never ask me for the drive, the size, user, pass, etc.

any idea?

Miguel 

PD: do you understand my english? ;o)

---

### Post by ago on 2007-10-19
> **mfigueroaj said:**
> This is my first post!!

I've tryin wubi 7.10 (wubi-cdboot.exe), but when restart I just got a live session... not an installation on a virtual disk.
Wubi never ask me for the drive, the size, user, pass, etc.

any idea?

Miguel 

PD: do you understand my english? ;o)
Wubi cdboot does what it says on the tin: it lets you boot from CD. It is used to go around bios issues. 
Once in the live session you can run the standard installer (which will require changing the partitions).

To install to a file (without changing the partition) you have to use the installer you find on our website. That was supposed to be on the CD but there was no time for that.

---

### Post by frenchy82 on 2007-10-19
Hello Ago

I'm sorry but my english is not so good to urderstand all i have to do

i've downloaded "Ubuntu-7.10-alpha.exe". I've launched it and install it.

In the folder "C:\ubuntu\disks" there is no the file image.

If i boot on linux i'm just on the live ubuntu.

So i've missed something!

What is wrong for me. Is the a doc to understand what i have to do

Big thanks for this sofware

---

### Post by mfigueroaj on 2007-10-19
> **ago said:**
> Wubi cdboot does what it says on the tin: it lets you boot from CD. It is used to go around bios issues. 
Once in the live session you can run the standard installer (which will require changing the partitions).

To install to a file (without changing the partition) you have to use the installer you find on our website. That was supposed to be on the CD but there was no time for that.

I put the wubialphaexe file in c:\ubuntu and works fine!
But, after restart I get an Error 17: File not found...

---

### Post by mfigueroaj on 2007-10-19
> **frenchy82 said:**
> Hello Ago

I'm sorry but my english is not so good to urderstand all i have to do

i've downloaded "Ubuntu-7.10-alpha.exe". I've launched it and install it.

In the folder "C:\ubuntu\disks" there is no the file image.

If i boot on linux i'm just on the live ubuntu.

So i've missed something!

What is wrong for me. Is the a doc to understand what i have to do

Big thanks for this sofware

I think your ordinateur is booting from the CDROM drive and installation never done (you only play a live session).
Look for the boot sequence in Bios utility and change it.

suerte!!!

---

### Post by frenchy82 on 2007-10-20
Ok I've succeed whith it. It's great.
I had to first boot with safe graphics mode and after all was ok

Gutsy is great too

---

### Post by ago on 2007-10-20
> **mfigueroaj said:**
> I put the wubialphaexe file in c:\ubuntu and works fine!
But, after restart I get an Error 17: File not found...

[http://ubuntuforums.org/showpost.php?p=3578157&postcount=46](http://ubuntuforums.org/showpost.php?p=3578157&postcount=46)

---

### Post by mfigueroaj on 2007-10-20
Please, help with this. The error msg is:
[FONT="Courier New"]
Booting 'Ubuntu 7.10, kernel 2.6.22-14-generic
Filesystem is fat, partition type 0xde
kernel /boot/vmlinuz-2.6.22-14-generic root=/dev/sda3 loop=/ubuntu/disks/root.disk ro quiet splash automatic-ubiquity locale=es_CL
Error 17: File not found'
[/FONT]
menu.lst in C:\ubuntu\disks\boot\grub:
[FONT="Courier New"]
title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)/ubuntu/disks
kernel		/boot/vmlinuz-2.6.22-14-generic root=/dev/sda3 loop=/ubuntu/disks/root.disk ro quiet splash automatic-ubiquity locale=es_CL
initrd		/boot/initrd.img-2.6.22-14-generic
[/FONT]
Miguel

---

### Post by henriksultan on 2007-10-20
I had the same problem, but it was the root (hd0,0)/ubuntu/disks that was pointing to the wrong hdd. Mine was (hd1,4) might be the same problem for u?

Try to go into command line and then root (hd and then tabb to see with hdd is the correct one.

---

### Post by barbulo on 2007-10-20
I get bcdedit error when i try to install wubi 7.10 on vista 64, with 7.04 it is all ok.

---

### Post by mfigueroaj on 2007-10-20
> **henriksultan said:**
> I had the same problem, but it was the root (hd0,0)/ubuntu/disks that was pointing to the wrong hdd. Mine was (hd1,4) might be the same problem for u?

Try to go into command line and then root (hd and then tabb to see with hdd is the correct one.

Mmmm. How I can go into commandline if I got this Error 17? 
Ctrl-Alt-F1 or something?

If run a live session I might know it?

Miguel

---

### Post by ago on 2007-10-20
> **barbulo said:**
> I get bcdedit error when i try to install wubi 7.10 on vista 64, with 7.04 it is all ok.

what error?

---

### Post by lonestarone on 2007-10-20
Good Morning Folks,,
  This is my "problem" using Wubi!!!
WARNING:::Unrecognized partition table for device 80.  Please rebuild it using MS compatible FDISK tool (err-26).   Current C/H/S=16383/255/63
(HD0,0)
 This repeated 3 times, then loading please wait
No raid disks
 Check root= bootary cat / proc cmdline
or missing modules, devices: cat/proc/mpdules ls /dev
ALERT: does not exist. dropping to a shell!
BusyBox v 1.1.3 (debian 1:1.1.3-3ubuntu2) built-in shell (ash)
Enter help for list of commands.
/bin/sh: can't access tty: job control turned off.
(initramfs)
  HELP - HELP!!!! what does ALL that mean?

 Why is it asking to partition the disk?  I thought wubi installed in a file for use on ntfs 
System: compaq presario V2630US
Thanks for suggestions / John in Dallas.

---

### Post by barbulo on 2007-10-20
> **ago said:**
> what error?

It simply says "Error running bcdedit".
I have a dual boot Vista 64 and Xp sp2, i'll try running wubi from xp...

---

### Post by sichbo on 2007-10-20
> **henriksultan said:**
> I had the same problem, but it was the root (hd0,0)/ubuntu/disks that was pointing to the wrong hdd. Mine was (hd1,4) might be the same problem for u?

Try to go into command line and then root (hd and then tabb to see with hdd is the correct one.

I tried stalling wubi on a second machine and got the dreaded Error 17 also. After googling around for a few hours trying contig defrags and all other manner of foolishness, this suggestion fixed it.... soooo I guess our modus operandi for using wubi alpha in some scenarios is;

[LIST=1]
[*]Run wubi setup, reboot, let Ubuntu install.
[*]Boot into Ubuntu, receive your Error 17.. hit enter, then c to go to command prompt
[*]type 'root' into the command prompt, you should see something like hd(0,1) or whatever...
[*]Edit c:\ubuntu\disks\boot\grub\menu.lst (I booted back into Windows and used a text editor because I'm lame), change all instances of hd0,0 to whatever you saw on the earlier command prompt (eg hd0,1)
[*]Reboot and it should work... unless it doesn't, then it won't. Worked for me though.
[/LIST]

---

### Post by ago on 2007-10-20
> **barbulo said:**
> It simply says "Error running bcdedit".
I have a dual boot Vista 64 and Xp sp2, i'll try running wubi from xp...

Can you run wubi with the "--debug" argument?

---

### Post by ago on 2007-10-20
I have uploaded rev347 it should deal with grub issues. Please note that the URL has changed. Please use the following one:


[http://wubi-installer.org/devel/minefield](http://wubi-installer.org/devel/minefield)

---

### Post by barbulo on 2007-10-21
> **ago said:**
> Can you run wubi with the "--debug" argument?

I get the message EDITBCD 3 HDD error and then VISTABOOTDRIVECODE={}. I have tryed also running with the iso burned on a cd and i get the same messages.
No problem from xp.

---

### Post by earanha on 2007-10-21
I've downloaded the Xubuntu 7.10 Desktop CD, and I'm trying to install it with WUBI, but I coundn't... (rev 347)

In the --debug mode, it says that my file is smaller than 600MB... and then try to download a new one...

The official Xubuntu 7.10 Desktop CD ISO is 566MB, so why this is happening?

If I disconnect my computer from Internet wubi program crashes in the 2nd attempt to connect... I'm using Win98SE.

Is there any option to force the installation with the 566MB ISO?

Thank you guys for making wubi!

---

### Post by ago on 2007-10-21
> **earanha said:**
> I've downloaded the Xubuntu 7.10 Desktop CD, and I'm trying to install it with WUBI, but I coundn't... (rev 347)

In the --debug mode, it says that my file is smaller than 600MB... and then try to download a new one...

The official Xubuntu 7.10 Desktop CD ISO is 566MB, so why this is happening?

My fault. I'll fix that. Will be available in next revision

---

### Post by ago on 2007-10-21
> **barbulo said:**
> I get the message EDITBCD 3 HDD error and then VISTABOOTDRIVECODE={}. I have tryed also running with the iso burned on a cd and i get the same messages.
No problem from xp.
I'll need to come back on that

---

### Post by MSchenker on 2007-10-21
I just downloaded Wubi 7.10 alpha rev 357.  Before I install it, are the issues mentioned above resolved?

Thanks!

---

### Post by barbulo on 2007-10-21
I still have the same issue with Vista, no problem from xp with the 64 bit Gutsy edition, the 32 bit hangs on copying files...

---

### Post by earanha on 2007-10-21
> **ago said:**
> My fault. I'll fix that. Will be available in next revision

The size verification is OK now, but I still can't install Xubuntu, every time WUBI try to connect and download the ISO... I've tried diferent ISOs (in the same folder than wubiXXXX.exe, tried with the CD, and all the same... Iif I disconnect from Internet, in the 2nd attemp wubi crashes... I've tested rev 347, 355, 357 and 358.

---

### Post by ERGLupin on 2007-10-21
I have the same bcdedit problem with the 347 wubi as well as the newest one. Hopefully this will be fixed soon cause otherwise this looks to be an ingenious little app.

---

### Post by ago on 2007-10-22
> **earanha said:**
> The size verification is OK now, but I still can't install Xubuntu, every time WUBI try to connect and download the ISO... I've tried diferent ISOs (in the same folder than wubiXXXX.exe, tried with the CD, and all the same... Iif I disconnect from Internet, in the 2nd attemp wubi crashes... I've tested rev 347, 355, 357 and 358.

Maybe you need 64bit versions. To force 32bit, try starting wubi with the argument "--32bit". The crash is more interesting. If you could reproduce it, that would help a lot.

---

### Post by ago on 2007-10-22
NOTE TO ALL: from version 358 you should find a log file in %TEMP%\wubi*.log in windows feel free to attach the log here for any problem happening BEFORE rebooting .

---

### Post by earanha on 2007-10-22
I have a K6-II running Win98SE... I don't think I need the 64bit version... Tonight I will post more information about the crash in Win98...

---

### Post by ago on 2007-10-22
Look into the logfile to see why your local images are discarded.

---

### Post by earanha on 2007-10-22
> **ago said:**
> Look into the logfile to see why your local images are discarded.

I've disconnected from Internet, put the ISO in the same folder of the .exe. Wubi begins installation, and then try to connect to download the ISO, in the 2nd attempt it crashes.

Wubi-7.10-alpha-rev358.log:
```
============ New Session ============
arch=i386
DetectCD
cddrive=
DetectIso
IsValidIso ispoath=C:\TEMP\xubuntu-7.10-desktop-i386.iso
C:\WINDOWS\TEMP\nsdC096.TMP\7z.exe e -y -i!.disk/info -oC:\WINDOWS\TEMP C:\TEMP\xubuntu-7.10-desktop-i386.iso
C:\WINDOWS\TEMP\nsdC096.TMP\7z 
 0 
 
7-Zip 4.42  Copyright (c) 1999-2006 Igor Pavlov  2006-05-14

Processing archive: C:\TEMP\xubuntu-7.10-desktop-i386.iso

Extracting  .disk\info

Everything is Ok
 
  
 
isvalid Xubuntu 7.10 "Gutsy Gibbon" - Release i386 (20071016)
 cdinfo=Xubuntu 7.10 "Gutsy Gibbon" - Release i386 (20071016) cdversion=7.10 cddistro=Xubuntu cdarch=i386 cdcodename=Gutsy Gibbon cdsubversion=Release 
success Xubuntu 7.10 "Gutsy Gibbon" - Release i386 (20071016)
DetectCD
cddrive=
DetectIso
IsValidIso ispoath=C:\TEMP\xubuntu-7.10-desktop-i386.iso
C:\WINDOWS\TEMP\nsdC096.TMP\7z.exe e -y -i!.disk/info -oC:\WINDOWS\TEMP C:\TEMP\xubuntu-7.10-desktop-i386.iso
C:\WINDOWS\TEMP\nsdC096.TMP\7z 
 0 
 
7-Zip 4.42  Copyright (c) 1999-2006 Igor Pavlov  2006-05-14

Processing archive: C:\TEMP\xubuntu-7.10-desktop-i386.iso

Extracting  .disk\info

Everything is Ok
 
  
 
isvalid Xubuntu 7.10 "Gutsy Gibbon" - Release i386 (20071016)
 cdinfo=Xubuntu 7.10 "Gutsy Gibbon" - Release i386 (20071016) cdversion=7.10 cddistro=Xubuntu cdarch=i386 cdcodename=Gutsy Gibbon cdsubversion=Release 
success Xubuntu 7.10 "Gutsy Gibbon" - Release i386 (20071016)
Moving iso C:\TEMP\xubuntu-7.10-desktop-i386.iso -> c:\ubuntu\install\xubuntu-7.10-desktop-i386.iso

```

And here the details about the Win crash (my win98 is in portugues):
```
WUBI-7 causou uma falha de página inválida no
módulo <desconhecido> em 0000:7b47171c.
Registros:
EAX=c15635a4 CS=0177 EIP=7b47171c EFLGS=00010202
EBX=00000000 SS=017f ESP=01e1f6fc EBP=01e1f744
ECX=c15c9970 DS=017f ESI=7b47171c FS=125f
EDX=00000100 ES=017f EDI=00000000 GS=0000
Bytes em CS:EIP:

Esvaziamento da pilha:
bff850cf 0000fffe 00000000 000000c0 00000000 00000000 00000000 00000000 00000001 81b841b4 00000001 c15635a4 0049f2c0 01e1f52c 01e1ff88 bffc05b4 

```

```
WUBI-7 causou uma falha de página inválida no
módulo MSAFD.DLL em 0177:7b47171c.
Registros:
EAX=c1565e14 CS=0177 EIP=7b47171c EFLGS=00010202
EBX=00000000 SS=017f ESP=01f3f6fc EBP=01f3f744
ECX=c15cd580 DS=017f ESI=7b47171c FS=48e7
EDX=00000100 ES=017f EDI=00000000 GS=0000
Bytes em CS:EIP:

Esvaziamento da pilha:
bff850cf 0000fffe 00000000 000000c0 00000000 00000000 00000000 00000000 00000001 81b84834 00000001 c1565e14 004a5b78 01f3f52c 01f3ff88 bffc05b4 

```

Any clue?

---

### Post by HampusW on 2007-10-23
earanha: It crashes inside msafd.dll, which is the " Microsoft Windows Sockets 2.0 Service Provider" (looked that up on the net). Wubi should work without winsock 2.0, so this is a bit strange. Apparently your system supports winsock 2 and I think Wubi will use it then (not sure, this happens inside libcurl). There might be something wrong with your system (ie msafd.dll = winsock 2.0), but I don't know really. I found a few discussions about similar problems:
[http://www.computing.net/windows95/wwwboard/forum/149254.html](http://www.computing.net/windows95/wwwboard/forum/149254.html)
[http://antionline.com/archive/index.php/t-136902.ht%20%3C/t-244858.html](http://antionline.com/archive/index.php/t-136902.ht%20%3C/t-244858.html)

Are you running a 64-bit processor? In that case Wubi will download a 64-bit iso for you (there's no way to change that). It should not crash though...

Have you got any problems with other internet applications? Wubi crashes like this every time?

---

### Post by HampusW on 2007-10-23
> I've disconnected from Internet
What happens if you don't disconnect from internet?

---

### Post by ERGLupin on 2007-10-23
Ago, I tried to use BCD Edit Pro or whatever it is called and it told me my Vista partition didnt exist or it was hidden. I dont know if this could be causing the problem with Wubi but just wanted to let ya know. Now to watch that Pyro video from TF2 :popcorn:

EDIT:

I looked online and it seems the reason for this error with vista boot pro at least is because of a couple recent upgrades that start requiring signed drivers. According to the post dated August 31st it was KB 932596 and KB 938979 that caused the errors with that app. Link to thread:

[http://www.pro-networks.org/forum/about95210.html&sid=02c9211de7858be603754d0c1c373d07](http://www.pro-networks.org/forum/about95210.html&sid=02c9211de7858be603754d0c1c373d07)

---

### Post by ago on 2007-10-23
> **ERGLupin said:**
> Ago, I tried to use BCD Edit Pro or whatever it is called and it told me my Vista partition didnt exist or it was hidden.
Hmm if BCDEdit does have problems with Vista, then Wubi will have issues to. It would help if you could provide more info on your Vista setup as far as the bootloader goes.

---

### Post by earanha on 2007-10-23
> **HampusW said:**
> Are you running a 64-bit processor? In that case Wubi will download a 64-bit iso for you (there's no way to change that). It should not crash though...

Have you got any problems with other internet applications? Wubi crashes like this every time?

My processor is a K6-II 450MHz... I'm sure it's not 64bit...

I have no problem with other internet apps... this error only occurs with Wubi, and it happens every time I try to install Wubi without Internet... If I try to install with the internet on, he begins to download the ISO from begin... 0% of 566MB.... but I never waited to finish... my Internet is not so fast at home....

---

### Post by jai_mantravadi on 2007-10-23
I tried using the gutsy (release) iso and placing it in the same directory (it was the alternate install iso), but wubi Alpha didn't seem to want to use the iso. I tried canceling the install (no internet connection, so it was easy), and then copying it to the install directory (both c:\ubuntu and c:\ubuntu\install), and restarting wubi hoping it would see the "finished" file and move on. No dice. Does the new alpha not support using the iso image? On my computer, it kept trying to connect to the internet with aol, even after turning the connection type to "never dial a connection". I happened to have a usb wireless dongle and a neighbor with an unsecured network, but was I doing something wrong to get wubi to install using the iso? BTW: using ver 363 of the alpha. thanks!
Jai

---

### Post by ago on 2007-10-23
> **jai_mantravadi said:**
> I tried using the gutsy (release) iso and placing it in the same directory (it was the alternate install iso), but wubi Alpha didn't seem to want to use the iso.
Did you use the DESKTOP ISO?

---

### Post by jai_mantravadi on 2007-10-23
Should I have? I used the alternate install iso because I thought that's what the documents called for. Should I go with the desktop iso? The name of the file I'm using is "ubuntu-7.10-alternate-i386.iso" Based on the description of the previous releases (beta for feisty for instance), I thought it was the alternate. What am I doing wrong? Thanks!
Jai

---

### Post by ago on 2007-10-23
You need to use the desktop ISO with 7.10

---

### Post by penguin22 on 2007-10-23
With the new builds the Ubuntu desktop for AMD64 downloads fine, but when you run it on Vista (64-bit), I consistently get the bcdedit.  As per this thread, I have rebooted disabling driver signing to no avail.  Is there any idea what is causing this or if there is a way to get past this?

---

### Post by ago on 2007-10-23
What is the vista error you get? Can you look in the log in %TEMP%\wubi.log?

Also try editbcd

---

### Post by jai_mantravadi on 2007-10-23
Thanks ago. I'll keep that for future ref. Is that going to be the standard now? Or will it depend on release #?
Thanks!
Jai

---

### Post by penguin22 on 2007-10-23
0
UncompressFilesPriorInstall
editbcd 
 3 
 HDD 
  
 error

---

### Post by ago on 2007-10-23
What happens if you execute:

bcdedit /create /d "test" /application bootsector

[http://msdn2.microsoft.com/en-us/library/ms791568.aspx](http://msdn2.microsoft.com/en-us/library/ms791568.aspx)

---

### Post by ago on 2007-10-23
> **penguin22 said:**
> 0
UncompressFilesPriorInstall
editbcd 
 3 
 HDD 
  
 error
see also [http://ubuntuforums.org/showpost.php?p=3608294&postcount=87](http://ubuntuforums.org/showpost.php?p=3608294&postcount=87)

---

### Post by BallBrain on 2007-10-24
Hi I'm having the same bcdedit error as above.

Same message in the log file.
I uninstalled the windows updates that according to some people seem to be the cause, but this did not help.

I executed the command: bcdedit /create /d "test" /application bootsector

This was the outcome : The entry {498dfd6b-81f1-11dc-af8d-0018f3d99bf2} was successfully created.

Hope this helps

---

### Post by ago on 2007-10-24
Can you see if easybcd works? [http://neosmart.net/](http://neosmart.net/)

---

### Post by BallBrain on 2007-10-24
Just tried it and that seems to work.

Here is the outcome ( I created a test entry)

```

Windows Boot Manager
--------------------
identifier              {9dea862c-5cdd-4e70-acc1-f32b344d4795}
device                  partition=C:
description             Windows Boot Manager
locale                  en-US
inherit                 {7ea2e1ac-2e61-4728-aaa3-896d9d0a9f0e}
default                 {bbcbc250-49e8-11dc-b5db-a4db0721c043}
resumeobject            {bbcbc251-49e8-11dc-b5db-a4db0721c043}
displayorder            {bbcbc250-49e8-11dc-b5db-a4db0721c043}
                        {498dfd6c-81f1-11dc-af8d-0018f3d99bf2}
toolsdisplayorder       {b2721d73-1db4-4c62-bf78-c548a880142d}
timeout                 30

Windows Boot Loader
-------------------
identifier              {bbcbc250-49e8-11dc-b5db-a4db0721c043}
device                  partition=C:
path                    \Windows\system32\winload.exe
description             Microsoft Windows Vista
locale                  en-US
inherit                 {6efb52bf-1766-41db-a6b3-0ee5eff72bd7}
osdevice                partition=C:
systemroot              \Windows
resumeobject            {bbcbc251-49e8-11dc-b5db-a4db0721c043}
nx                      OptIn

Real-mode Boot Sector
---------------------
identifier              {498dfd6c-81f1-11dc-af8d-0018f3d99bf2}
device                  boot
path                    \NST\NeoGrub.mbr
description             NeoSmart Linux

```

---

### Post by penguin22 on 2007-10-24
Hello Ago,

I have the same results when running bcdedit manually.  All works well.  I have also removed the two patches and have rebooted disabling driver signing to no avail.  I know that the bcdedit is based on the variables on the first screen, but can you provide what the string it is trying to enter and I can run it manually.  I selected the L drive, 30GB and Ubuntu, which should be all that is needed if I am not mistaken.

I am not sure what the Wubi install does after the bcdedit, but it would be great to be able to get past this even if it requires more debugging or handholding.  I don't think that I mentioned this, but Wubi 7.04.04 worked on both of these systems that I am testing with.

Thanks,

David

---

### Post by canTsTop on 2007-10-24
hello,

i install Wubi-7.10-alpha-rev364.exe, when i reboot and get this error:

```
find --set-root --ignore-floppies /ubuntu/install/boot/grub/menu.lst

Error 17: file not found
```

---

### Post by nickbw2003 on 2007-10-24
I've got the same problem.

Is there anyone who knows how to fix it?

---

### Post by ago on 2007-10-24
pressing "ins" when it starts helps to get more info...
you have to start grub4dos in manual mode then run the find command manually
use 

configfile /ubuntu/install/[hit tab]

---

### Post by canTsTop on 2007-10-24
then i press ins its says something about: MRR cylinders is greater then the BIOS one

with
configfile /ubuntu/install/[hit tab]   

i get file not fond

with
configfile /[hit tab]   

it shows me files from c: disk, but i installed in g: disk

---

### Post by ago on 2007-10-24
> **canTsTop said:**
> then i press ins its says something about: MRR cylinders is greater then the BIOS one

with
configfile /ubuntu/install/[hit tab]   

i get file not fond

with
configfile /[hit tab]   

it shows me files from c: disk, but i installed in g: disk

Try

configfile (hd[tab]

Should be something like: configfile (hd0,4)/ubuntu/install

---

### Post by canTsTop on 2007-10-24
> **ago said:**
> Try

configfile (hd[tab]

Should be something like: configfile (hd0,4)/ubuntu/install

its
configfile (hd1,0)/ubuntu/install

but i get error could not mount this partition

this HDD is connected to pci card

---

### Post by ago on 2007-10-24
> **canTsTop said:**
> its
configfile (hd1,0)/ubuntu/install

but i get error could not mount this partition

this HDD is connected to pci card

So that's the reason!
You can send a msg to bean123 for further clarifications.
Easiest way around it is to install on a different partition

---

### Post by canTsTop on 2007-10-25
> **ago said:**
> So that's the reason!
You can send a msg to bean123 for further clarifications.
Easiest way around it is to install on a different partition

thank you, for help

is it fixable? will it be corrected in the final version?

---

### Post by ago on 2007-10-25
> **canTsTop said:**
> thank you, for help

is it fixable? will it be corrected in the final version?

Grub4dos is the domain of bean123 and tinybit...

---

### Post by rubber fingers on 2007-10-25
Hi not having any luck here with the install using Vista. When I reboot I get:

Unrecognized partition table for device 80. Please rebuild it using MS compatible FDISK tool (err-114).......

twice


then it starts to load the ubunti splash screen and hangs there for ever and day.....

any ideas?

thanks

---

### Post by ago on 2007-10-25
You might need acpi=off in menu.lst. The partition table thingy is a separate issue, but if you can boot it, it should be okish.

when you have the countdown at boot with the black screen, press ESC , then select the third option

---

### Post by rubber fingers on 2007-10-25
Hi

I tried the 3rd option ACPI? and it did the same thing get to the ubuntu screen with the progress bar then did not get any further

thanks

---

### Post by ago on 2007-10-25
can you redownload wubi 371+ and try again?
Try the 3rd option first and in case the 4th

---

### Post by Kamiyay on 2007-10-25
When using Wubi-7.10-alpha-rev373.exe I get all the way to the ubuntu graphical install and get  > The file system type ntfs cannot be mounted on /, because it is not a fully functional unix filesystem. Please choose a different file system, such as ext2. I don't know how to get past this.

Windows XP Pro
30GB Wubi file
Dell Inspiron 9100

---

### Post by molk on 2007-10-25
Kamiyay,

The host NTFS on which you are installing Wubi is dirty/corrupted. You need to go back into Windows and run chkdsk /r   After your NTFS filesystem is repaired run Wubi installer again. At that point it should not give you this error.

This is a very common problem with Wubi 7.10 . 

Ago, you think it might be beneficial to see if there is a way to lessen the sensitivity of the installer to very minor NTFS problems or maybe to have an error message show up which does a better job of telling the user what the problem is and how to correct it? Not sure if either one of those is possible.

---

### Post by ago on 2007-10-25
You have to run chkdsk /r before running Wubi
By the way there is a new rev 377

---

### Post by molk on 2007-10-25
Ago, also maybe checking for NTFS problems initially in  Windows and either showing a meaningful error or maybe even offering to run chkdsk /r for the user is worth considering .

---

### Post by ago on 2007-10-25
> **molk said:**
> Ago, also maybe checking for NTFS problems initially in  Windows and either showing a meaningful error or maybe even offering to run chkdsk /r for the user is worth considering .

Sounds like I good idea

---

### Post by Kamiyay on 2007-10-25
I had already ran a chkdsk /r, so I decided to defragment my drive. So far it's at 4% and I have been running it for a half hour. I think that may be the problem lol.

---

### Post by rubber fingers on 2007-10-26
Wow the latest version works!

I still get the err-114 as I did before but the install went fine (thanks for fixing it)

One problem I have is that I cant see my (windows) E drive, where I installed Ubuntu onto. I have C drive as my Primart with VIsta on it, D Drive with XP and E drive with all my data (and Ubuntu).

Any ideas why I cant get to this drive?

thanks

---

### Post by ago on 2007-10-26
> **rubber fingers said:**
> 
One problem I have is that I cant see my (windows) E drive, where I installed Ubuntu onto.
/host

---

### Post by ago on 2007-10-26
I think rev377 is a good candidate. Give it a good try and let me know whether it works or not.

---

### Post by rubber fingers on 2007-10-26
rev377 works fine here (all others did not)

---

### Post by rubber fingers on 2007-10-26
oh btw any ideas on the err-114 issue yet?

thanks

---

### Post by ago on 2007-10-26
Send a PM to bean123. But I suspect that the partition table was edited with some tools that did not do a clean job.

---

### Post by anrichp on 2007-10-27
Hi everyone

I'm kinda new to ubuntu, and need some help I've got the latest version of wubi alpha rev 377 but after i install it and reboot my system , and boot up in ubuntu linux , it has the ubuntu starting screen and then goes to a black window saying something about busybox debian etc.
What do i need to do to get this working?

thnx

---

### Post by Futureking on 2007-10-27
> **sichbo said:**
> I tried stalling wubi on a second machine and got the dreaded Error 17 also. After googling around for a few hours trying contig defrags and all other manner of foolishness, this suggestion fixed it.... soooo I guess our modus operandi for using wubi alpha in some scenarios is;

[LIST=1]
[*]Run wubi setup, reboot, let Ubuntu install.
[*]Boot into Ubuntu, receive your Error 17.. hit enter, then c to go to command prompt
[*]type 'root' into the command prompt, you should see something like hd(0,1) or whatever...
[*]Edit c:\ubuntu\disks\boot\grub\menu.lst (I booted back into Windows and used a text editor because I'm lame), change all instances of hd0,0 to whatever you saw on the earlier command prompt (eg hd0,1)
[*]Reboot and it should work... unless it doesn't, then it won't. Worked for me though.
[/LIST]



THANK YOU SO MUCH. THIS WORKED FOR ME.:):KS

---

### Post by Six_Digits on 2007-10-27
Linux installation either stalls or freezes around 45% on the latest revision. Tried 3x with the same result.

---

### Post by b15h0p7 on 2007-10-27
Latest revision.  Stopped when it was formatting the virtual disks.

Error: "The file system type ntfs cannot be mounted on /, because it is not a fully functional Unix file system.  Please choose a different file system, such as ext2."

---

### Post by Frak on 2007-10-27
Great Job and thanks Ago :D

---

### Post by gaffer_65 on 2007-10-28
> **b15h0p7 said:**
> Latest revision.  Stopped when it was formatting the virtual disks.

Error: "The file system type ntfs cannot be mounted on /, because it is not a fully functional Unix file system.  Please choose a different file system, such as ext2."

As well at me as well

---

### Post by ago on 2007-10-28
> **Six_Digits said:**
> Linux installation either stalls or freezes around 45% on the latest revision. Tried 3x with the same result.

Do you install on a FAT partition?
Also pres ctrl+f2 and type: cat /var/log/syslog
See if there is any error about migration-assistant

---

### Post by ago on 2007-10-28
> **b15h0p7 said:**
> Latest revision.  Stopped when it was formatting the virtual disks.

Error: "The file system type ntfs cannot be mounted on /, because it is not a fully functional Unix file system.  Please choose a different file system, such as ext2."

Run chkdsk /r on windows then reboot into ubuntu

---

### Post by ago on 2007-10-29
Wubi 381 should be able to work without editing menu.lst. Please test it out and let me know.

---

### Post by Incursis on 2007-10-30
I think I have found a bug that is worth mentioning. I used wubi revision 377 to install Ubuntu, and whenever I copy a large amount of files, the system will lock up and I have to do a hard reboot.

I was able to repeat it using console and via the file manager. I was attempting to copy fonts to .fonts in home directory. I have attempted the same thing in Kubuntu and I get no crashes.

If you need any more info I will gladly provide it.

---

### Post by ago on 2007-10-30
> **Incursis said:**
> I think I have found a bug that is worth mentioning. I used wubi revision 377 to install Ubuntu, and whenever I copy a large amount of files, the system will lock up and I have to do a hard reboot.

I was able to repeat it using console and via the file manager. I was attempting to copy fonts to .fonts in home directory. I have attempted the same thing in Kubuntu and I get no crashes.

If you need any more info I will gladly provide it.
That's interesting! So kubuntu is not affected by this?
Do the crashes always happen when you copy the same file? Is it the number of files or their size that trigger the problem?
There is a loopfile issue at kernel level under investigation that might be linked to that.

---

### Post by flyincat on 2007-10-30
i'm a chinese user. these problems happened after i finished my installation by the newest version of wubi(381)
1. it cost me much time to wait for the system to start, which means the ubuntu system started very very slowly.
2. there's no start screen during the system started. all i saw was just a black screen.
3. i can't input chinese although i choose the simplify Chinese option of the installation language.
4. whenever i use pidgin, the system was down. 

anyway, thanks for your work.
hope everything goes well.

---

### Post by Incursis on 2007-10-30
> **ago said:**
> That's interesting! So kubuntu is not affected by this?
Do the crashes always happen when you copy the same file? Is it the number of files or their size that trigger the problem?
There is a loopfile issue at kernel level under investigation that might be linked to that.

I believe it is the number of files. I also tried copying 5 fonts and that didn't crash. I didn't try copying the same number of files in Kubuntu, I think it was a lot less though. But I don't have wubi installed so I can't recheck, and I don't know what effect a hard shut down will do. i already have 1MB of bad sectors that came out of nowhere.

---

### Post by n5xyo on 2007-10-30
Your installer worked fine for me!
I installed Ubuntu 7.10 on my old desktop and Kubuntu 7.10 on an old TP x24 with Wubi.
The install went FAST and best part...sound, networking and WiFi work.
Thanks for your effort!
John

---

### Post by dbclinton on 2007-11-01
My download of Wubi 7.1.0 alpha was flawless (actually, better than that, as my DSL connection is supposed to get not more than 500kps and the Edubuntu distro came down the pipe in around 4 minutes)!
After the reboot, the install program got to 82% before freezing while "scanning mirror" (I believe).
I'll probably try booting to ubuntu again later.
Thanks for the project!

---

### Post by dbclinton on 2007-11-01
An addition to that last post:
I happened to have the edubutu desktop 7.1.0 cd in the drive while installing...is it possible that it was *that* version which was installed (explaining the quick download)?

---

### Post by iwarp62 on 2007-11-01
Hello,

I downloaded the latest Wubi-7.10-alpha-rev381.exe. Downloads and install was flawless but upon attempting to start ubuntu for the first time I get far enough to see the usplash loading page and then....(checkout the screenshot).



Thanks for all your hardwork and I look forward to seeing this in action!

---

### Post by Six_Digits on 2007-11-02
Sorry I never got around to posting my syslog output, but revision 381 worked perfectly for me! Whens the beta expected?

---

### Post by ago on 2007-11-02
> **iwarp62 said:**
> Hello,

I downloaded the latest Wubi-7.10-alpha-rev381.exe. Downloads and install was flawless but upon attempting to start ubuntu for the first time I get far enough to see the usplash loading page and then....(checkout the screenshot).



Thanks for all your hardwork and I look forward to seeing this in action!
Is this after the first reboot, or the second reboot? Second reboot will be after the chocolate fudge with lots of progressbars. If it's the first one type:

cat /casper.log

And report relevant errors, you can scroll with shift + page up

---

### Post by ago on 2007-11-02
> **dbclinton said:**
> An addition to that last post:
I happened to have the edubutu desktop 7.1.0 cd in the drive while installing...is it possible that it was *that* version which was installed (explaining the quick download)?

If it was in the cd tray, then yes, that will be preselected and used.

---

### Post by ago on 2007-11-02
> **dbclinton said:**
> After  the reboot, the install program got to 82% before freezing while "scanning mirror" (I believe).
I'll probably try booting to ubuntu again later.
Thanks for the project!
If it stops please attach here the content of /var/log/syslog

---

### Post by ericesque on 2007-11-02
Ago, thank you very kindly for your hard work.  Wubi 381 is a go on my desktop.  32-bit AMD.

I've rebooted, updated, and installed/configured just about everything.  Not a hiccup along the way!  

Kudos, good sir.  Kudos. :KS

---

### Post by dbclinton on 2007-11-02
> **ago said:**
> If it stops please attach here the content of /var/log/syslog

If I'm back in Windows (as the install obviously didn't complete) where will I find /var/log/syslog?
I've looked through the /ubuntu and /ubuntu-backup folders and done a search of my hard drive for syslog.
Thanks

---

### Post by ago on 2007-11-02
> **dbclinton said:**
> If I'm back in Windows (as the install obviously didn't complete) where will I find /var/log/syslog?
I've looked through the /ubuntu and /ubuntu-backup folders and done a search of my hard drive for syslog.
Thanks

You have to access that from Ubuntu. Uninstall, run chkdsk and if it stops again, press alt+F2 and look into /var/log/syslog

---

### Post by dbclinton on 2007-11-02
> **ago said:**
> You have to access that from Ubuntu. Uninstall, run chkdsk and if it stops again, press alt+F2 and look into /var/log/syslog

Ok. I guess I was just impatient. I tried alpha release 384 (I think) again and then went out for an hour or so. When I came back, the install had completed and on reboot Ubuntu loaded successfully (I'm writing this from Ubuntu now).
There is one problem that I'm unsure is directly related to Wubi: my screen now has a terrible flicker (I won't be able to use it for more than a few minutes). I recently ran 7.1.0 as a live CD session a few times and there was no problem (and Windows ran perfectly too just a few minutes ago).
Thanks!

---

### Post by ago on 2007-11-02
> **dbclinton said:**
> 
There is one problem that I'm unsure is directly related to Wubi: my screen now has a terrible flicker (I won't be able to use it for more than a few minutes). I recently ran 7.1.0 as a live CD session a few times and there was no problem (and Windows ran perfectly too just a few minutes ago).
Thanks!
Search the general forum, with reference to your video card

---

### Post by iwarp62 on 2007-11-02
> **ago said:**
> Is this after the first reboot, or the second reboot? Second reboot will be after the chocolate fudge with lots of progressbars. If it's the first one type:

cat /casper.log

And report relevant errors, you can scroll with shift + page up

This was after the very first reboot (from wubi on windows to ubuntu's setup routine but I never got that far).

Unfortunately I can't seem to reproduce that screen either. Now after running the wubi installer and going through my first reboot ubuntu will make it until it gets to guided partitioning. There I am met with this error:

"The file system type ntfs cannot be mounted on / because it is not a fully-functional Unix file system. Please choose a different file system, such as ext2."

---

### Post by ago on 2007-11-02
> "The file system type ntfs cannot be mounted on / because it is not a fully-functional Unix file system. Please choose a different file system, such as ext2."
Is that with rev383+?
Anyway run chkdsk /r from windows

---

### Post by winol5 on 2007-11-02
Hi, i'm pretty confussed is it safe to install this alpha release? I have seen bad reps in the very begginig of the post but in the last ones they were good.... so I was thinking if there's an actualizated verssion of this alpha since the first posts.

---

### Post by Frak on 2007-11-02
> **winol5 said:**
> Hi, i'm pretty confussed is it safe to install this alpha release? I have seen bad reps in the very begginig of the post but in the last ones they were good.... so I was thinking if there's an actualizated verssion of this alpha since the first posts.
"Alpha" and "Beta" are african terms meaning "Expect great breakage"

---

### Post by winol5 on 2007-11-02
Really? i didnt knew that i thoughht it was about the greek letters.... but is it safe? because is strage first people to post a reply said a bad reply and last people says good ones, so it makes me think the alpha was actualized between 2 types of replys

---

### Post by Frak on 2007-11-02
> **winol5 said:**
> Really? i didnt knew that i thoughht it was about the greek letters.... but is it safe? because is strage first people to post a reply said a bad reply and last people says good ones, so it makes me think the alpha was actualized between 2 types of replys
It really depends on the machine.

---

### Post by winol5 on 2007-11-03
I suposse al wubi versions depend of the computer, but should I take the risk of usng tje alpha? or it is going to be fixed later? really can not wait for trying ubuntu! and I can not partion my disk because of some stupid things of sony that make gparted unusable in my C :S

---

### Post by sankoz on 2007-11-03
Hi,

I just ran rev 383. It ran fine and installed, but after rebooting to ubuntu, checking the installation is stuck at "Copying files" 30%. 

Thanks,
Sanjeev

---

### Post by ajskhan on 2007-11-03
Is there any chance it would screw up my XP installl?

---

### Post by hums07 on 2007-11-04
I ran Wubi installer for Ubuntu, and it failed to start saying it encounters problem and need to close.
Then I run the intaller for Xubuntu. I already have the iso but it stil tries to download a new iso file.

---

### Post by ago on 2007-11-05
> **hums07 said:**
> I ran Wubi installer for Ubuntu, and it failed to start saying it encounters problem and need to close.
Then I run the intaller for Xubuntu. I already have the iso but it stil tries to download a new iso file.

Can you be more specific? What was on the error?

---

### Post by mikedep333 on 2007-11-05
> **ajskhan said:**
> Is there any chance it would screw up my XP installl?

A very small chance. Still, if you are concerned about this, you should use the stable wubi release based on Ubuntu 7.04.

---

### Post by chris53825 on 2007-11-27
ago, do you plan on having a new build any time soon? It's been a while since the last one (Nov. 11) and that version wouldn't install - it would get stuck at around 33% installation

---

### Post by garferi on 2007-11-27
Hi ago!

Would not be better if you buid the Wubi 7.10 on the Ubuntu 7.10 alternate CD?
I think 7.04 was very stable with the alternate installer...

---

### Post by ago on 2007-11-27
No that would not change anything since alternate and livecd use the same kernel

---

### Post by syarost on 2007-11-30
Ago,  What is the status of a new build that will work with SATA drives?   My install hangs at 47%.

---

### Post by bnmjosh on 2007-12-01
Testing it now after a fresh reinstallation of Windows XP. I'll just edit this post when I'm on Ubuntu :)

Well, that didn't work... xD I don't exactly remember what the error said, but I'll write it down next time I try it (maybe tomorrow.)

---

### Post by shuttleworthwannabe on 2007-12-01
Ago, Thanks for the development of Wubi. So let me get this right:
 
1. Download the Wubu installer (exe file) (there are 2 of them one for 7.04 and one in alpha 7.10 build 38x??; download to a folder in Windows (XP or Vista). In this case I will use the alpha 7.10 version.
2. I have an Ubuntu desktop iso 7.10 already downloaded on my hard drive--copy this to the same folder Wubi.exe setup was downloaded.
3. Disconnect from the internet (remove ethernet cable, or switch wifi signal off)--is this necessary??
4. Fireup the wubi exe ad setup as required in the gui.
5. Let it pick-up the ubuntu iso in the same folder
6. Complete the installation.
7. Reboot iinto Ubuntu (at the bootup screen).
8. Hopefully, all is well and it will run ubuntu fine? unless, it need installation of restricted graphics drivers like in my case (ATI).
 
Is this what I need to do? Am I missing something? Thanks

---

### Post by riverstore on 2007-12-01
Does anyone check wubi alpha 7.10 with Kubuntu.

---

### Post by bnmjosh on 2007-12-02
Okay this is what happens when I try to install using Wubi-7.10-alpha-rev383:

Console comes up with:

[ 501.490898] Buffer I/O error on device fd0. logical block 0

It repeats that a few times with the first 3 numbers changing a little, 530 was the next in line. Then my computer crashed... (It was not because of Wubi/Ubuntu though...)

Any help on fixing the error?

---

### Post by ago on 2007-12-03
> **shuttleworthwannabe said:**
> Ago, Thanks for the development of Wubi. So let me get this right:
 
1. Download the Wubu installer (exe file) (there are 2 of them one for 7.04 and one in alpha 7.10 build 38x??; download to a folder in Windows (XP or Vista). In this case I will use the alpha 7.10 version.
2. I have an Ubuntu desktop iso 7.10 already downloaded on my hard drive--copy this to the same folder Wubi.exe setup was downloaded.
3. Disconnect from the internet (remove ethernet cable, or switch wifi signal off)--is this necessary??
4. Fireup the wubi exe ad setup as required in the gui.
5. Let it pick-up the ubuntu iso in the same folder
6. Complete the installation.
7. Reboot iinto Ubuntu (at the bootup screen).
8. Hopefully, all is well and it will run ubuntu fine? unless, it need installation of restricted graphics drivers like in my case (ATI).
 
Is this what I need to do? Am I missing something? Thanks

Yep except that there is no need to disconnect from internet, if you use 7.10 DESKTOP ISO you need the wubi-7.10

---

### Post by shuttleworthwannabe on 2007-12-03
Cool I think I will download the iso first from my local mirror first; (i noticed if the iso is not in the same folder as wubi.exe, then wubu-exe connects to the internet (I am not sure where the download is coming from (mirror??)

Anyway, thanks for the development again. BTW, when is the official release date for the 7.10?

---

### Post by chris53825 on 2007-12-14
Can we at least get an idea of when the sata fix will be out? This wait is driving me crazy!!

---

### Post by ago on 2007-12-17
That requires an 2.6.24 kernel, which makes it quite unlikely for 7.10, since 2.6.24 is not out yet and by the time it is out we might just as well move forward to wubi 8.04. If you can install 7.10, you can install the 2.6.24 kernel manually, that should fix the issues.

---

### Post by chris53825 on 2007-12-17
> **ago said:**
> That requires an 2.6.24 kernel, which makes it quite unlikely for 7.10, since 2.6.24 is not out yet and by the time it is out we might just as well move forward to wubi 8.04. If you can install 7.10, you can install the 2.6.24 kernel manually, that should fix the issues.

I'm assuming 6.04 had this? 6.04 installed flawlessly on my sata drive

---

### Post by ago on 2007-12-17
The kernel that shipped with Ubuntu 7.04 (I assume that is what you mean) was ok, the one in 7.10 has issues with loopfiles, hopefully 8.04 will be good again...

---

### Post by chris53825 on 2007-12-17
Yes that was what I meant lol. Hopefull they correct that problem. Thanks for letting us know

---

