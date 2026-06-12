---
title: "Ubuntu 12.04 suddenly ONLY boots to tty - can't find way to GUI"
date: 2015-07-25
forum: General Help
---

### Post by crazybear on 2015-07-25
[COLOR=#111111][FONT=Ubuntu]I've read through about 20+ threads where others had the same thing happen, however NONE of the solutions I found worked for me - been unable to log on for several weeks now![/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Some were not even possible to try or didn't apply. I'm really stuck and would appreciate some help! This happened not long ago twice.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Both times I was able to somehow get it to go back to GUI desktop after fooling around with several things in recovery mode.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]I do NOT know which one of those things 'worked', if any did...and now NONE of those past things I tried does work. I did move which pci port the video card was on, but that was changed in the BIOS and it had been working OK...this may just be a temporal coincidence. I've tried more things than I can list, they include:[/FONT][/COLOR]

[LIST]
[*]reconfiguring lightdm AND gdm. Seems no matter what I do I'm stuck with gdm only - won't allow lightdm even if it allows me to 'select' it.
[*]tying startx [get weird error messages and said it couldn't find the server]
[*]trying gdm

tried different kernels - no difference no matter which used.
[/LIST]
[COLOR=#111111][FONT=Ubuntu]if I try to 'log in' on tty1 normal characters do NOT get typed, I get strange non-letter 'characters', so can't do anything there; - I can go into recovery mode and drop to a root prompt, but from there can't (re)install anything (strangely), it says it can't read some file it needs to do that;[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]FWIW, I have an AMD video card, and also run [what I'm using now] 14.04 which is booting into GUI and working fine. I don't use unity, but it is installed. I use Gnome no effects usually.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Also don't have just ONE /etc/X11/Xorg.conf file - but many with something added after the .conf.--- How does the OS decide which one to use?! I used my good OS to look at both its and the 'bad' OS's latest [by date] Xorg.conf files - they are quite different and I don't know if this could be the problem. I can post them if needed. I have a three monitors as one desktop - but they were all working fine...until something happened and can't figure out what...!?![/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]The only other thing I can think of that changed at about the time this began was a new kernel installed, but all kernels, even older ones, don not got into GUI desktop now.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]....I'm really at wits end! Any ideas how to diagnose and then fix this? Thanks.[/FONT][/COLOR]

---

### Post by Bashing-om on 2015-07-25
crazybear; Hello;

If it were me, I would reduce to simplest terms, and focus on getting the system up with one monitor in use.
Then try and boot from the grub menu using the boot parameter " nomodeset " .
One to a terminal check that a graphics card is seen and a driver is loaded:
```

lspci -nnk | grep -iA3 vga
sudo lshw -C display

```

Else wise, we boot to terminal and see what the haps be.

[INDENT][INDENT]all in the process
[/INDENT][/INDENT]

---

### Post by crazybear on 2015-07-26
A ***new development that seems hopeful***, but is NOT there yet. I got into the root prompt  in recovery mode and typed in: startx . This had done nothing before, but now it slowly opened all three monitors as one desktop; however it was a *very strange* desktop I've never seen. It was not unity nor fallback...something barren and other - default background color [not the background I have specified in Xorg.conf, no files or folders, no panels - no menus - nothing. The ONLY way I could find to DO anything from it was to CTR+ALT+T and get a terminal...**but now what do I want to do in terminal?** I think this shows the GPU, driver and OS are working OK and the three head is not a problem...but it is not starting in fallback [PREFERRED!] or any other usable desktop I have. It is using some very basic default conf file - I know not what. **Is there a command that would direct it to get me into Gnome fallback [best!!!!] or even Unity [ugh! - HATE it with a passion!] from root prompt**; or from the strange empty desktop (with none of the desktop folders or features from any desktop I know of) using the terminal I can open in it?  If I could get into a desktop I can use [or just in terminal in the barren 'desktop'] what need I do to get it back to the normal signin window...where I put in my password and chose the desktop I wanted? 
Thanks.

---

### Post by Bashing-om on 2015-07-26
crazybear; Hey;

Yeah, keep in mind this is 'ubuntu; and is always fixable, just finding the how .
So let's see about that how.

Be aware I am not familiar with gnome-flashback, but I am sure we can learn.

Let's poke at this a bit and see what results.
Boot to a terminal .. such that X is not running. I can imagine that only one head will be recognized, but I do not know.

Boot the system to the grub menu, with the latest ubuntu kernel selected, press the 'e' key for edit mode -> boot parameters screen.
In the boot parameters screen arrow down to the line similar " linux    /boot/vmlinuz-3.13.0-24-generic root=UUID=217ed9a7-e11a-4e32-8c05-992e8c8932b6 ro  quiet splash $vt_handoff " and arrow across to "quiet splash $vt_handoff " and replace these terms with the term 'text' with out the quotes. Key combo ctl+x to continue the boot process to TTY1.
Log in here at this terminal with your user name and password - no response to the screen when pass word is entered. Just enter the password blindly and hit the enter key.

The command 'startx' is largely depreciated as the supporting files no longer exist. With the advent of 'upstart' one starts the desktop with alternate commands.

OK, now to start the GUI and see if the system scream and hollers:
```

sudo service lighdm start

```
and see if we can start unity.

Maybe the command to start gnome ?
```

sudo service gdm start

```

Anyway, what does the system say ?

To bring the system down safely:
```

sudo shutdown -h now

```
and to reboot:
```

sudo shutdown -r now

```

[INDENT][INDENT]do we have a conflict of interest here with alternate DE's
[/INDENT][/INDENT]

---

### Post by crazybear on 2015-07-26
Thanks....A bit complicated, but will give it a try...never knew about pressing the 'e' key during grub....virgin on that... 

I looked and found this on a Forum elsewhere: [COLOR=#111111][FONT=Ubuntu]From the command line the GNOME Classic Desktop is started with:   # [/FONT][/COLOR][COLOR=#111111][FONT=Consolas]gnome-session --session=gnome-classic[/FONT][/COLOR]
[COLOR=#111111][FONT=Consolas]
Will try that too, and report all the results.....

PFFFT! This is NOT going to be easy nor as easy as you thought. First, I'm no longer a virgin to what happens when you push 'e' in grub...but that line has a very idiosyncratic part between the quietsplash and the end for my fancy Corsair keyboard...so can I ask why were are doing this and can I leave in my keyboard line?...and how long will this be 'altered' until it is put back to what it was? The same line has been there with the keyboard addition for many many months and also on my 14.04 system without any apparent problems. Likely not important, but just in case it is, the bit for the keyboard reads: [/FONT][/COLOR]usbhid.quirks=0x1B1C:0x1B11:[COLOR=#000000]0x408

[/COLOR]Also, I don't understand where I'm supposed to be finding a tty I can use. I mentioned before that in tty when I type I get non-roman characters [things like diamond shapes and even stranger] - even with a 'normal' keyboard I've tried and get the same. However, in recovery mode the keyboard types what it should...can I use that for what you were proposing? [or do you suggest that your proposed changes to that line will stop the characters from outer space from channeling into my keyboards - whichever I use?]

Thanks.
[COLOR=#111111][FONT=Consolas]
[/FONT][/COLOR]

---

### Post by Bashing-om on 2015-07-26
crazybear; Hey;

Nah, :
> 
Thanks....A bit complicated, but will give it a try.

Once you have done it a time or so. only takes scant seconds. If you do a lot from the CLI, you might even find you prefer to boot to terminal ( we can make that a permanent thing) .
I do boot to terminal, and then IF I want, I start a GUI .

[INDENT][INDENT]this ain't your mama's box
[/INDENT][/INDENT]

---

### Post by crazybear on 2015-07-27
You mis-understood what I meant by complicated. While I do not do most things [unless necessary] by command line - and don't want to go that route, I have done some complex things that way, as needed. Anyway...here is what I can respond to your suggestions at this point:

- I edited out the complete end of the line and replace with 'text' [without the paren.]....then hit CTL+X and it went into something resembling the recovery mode; however it ended up with a black screen and only a blinking cursor [NO TTY]....so abandoned that.

- I went into recovery mode and dropped to command prompt. There I tried the sudo start service lightdm start. It showed: loading essential drivers....then many more lines ending in ....done; then lines showing it was starting process 747; then process 767. At that point it simply stopped....so after waiting a bit also abandoned that.

- I let it start up on the latest kernel and it went to tty; however, as I have stated above and will state again, it does not let me log in...using two different keyboards, strange characters [very strange indeed] come out and are non-Latin and certainly NOT what would ever allow a login....so I abandoned that.

So, I don't know where to go next on this. I believe I last set lightdm and not gdm as the default...but I have tried both and neither solves the problem.

Will anything from here: [http://manpages.ubuntu.com/manpages/precise/en/man1/gnome-session.1.html](http://manpages.ubuntu.com/manpages/precise/en/man1/gnome-session.1.html) help out? Earlier, a few days ago, I tried just typing in 'gnome-session' without any options added, and it did nothing that I could see.

Also, just found this:
**Manually**

[LIST]
[*]For the **GNOME Flashback (Compiz)** session, add the following to the ~/.xinitrc file: exec gnome-session --session=gnome-flashback-compiz
[/LIST]
[FONT=sans-serif]After editing .xinitrc, GNOME Flashback can be launched with *startx*. See [xinitrc]("https://wiki.archlinux.org/index.php/Xinitrc") for details.
[/FONT](I'm not sure how to find that .xinitrc file if it might be of help) It is Gnome Flashback (Compiz) that I use most of the time and prefer.

Thanks in advance.

---

### Post by Bashing-om on 2015-07-27
crazybear; Curious and curiouser :

I certainly expected you to be able to boot to terminal . That interface is prior to any desktop GUI starting, and does not utilize the graphics driver that the GUI uses.
IF you are unable to activate the TTY1 terminal, maybe best at this time to check the file system from a liveDVD(USB).

Boot the liveDVD to "try ubuntu" mode to terminal:
execute terminal commands:
```

sudo swapoff -a
sudo fdisk -lu ## to identify the ubuntu booting partition
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sda1 ## change 'sda1' to the appropriate drive and partition
#if errors: -y auto answers yes for fixes needing response see: man e2fsck
sudo e2fsck -f -y -v /dev/sda1 ##change 'sda1' to the appropriate drive and partition

```
---------------------------
~/.xinitrc I do be confused, you say (?) you edited the file, yet:
> 
 After editing .xinitrc, GNOME Flashback can be launched with startx. See xinitrc for details.
(I'm not sure how to find that .xinitrc file if it might be of help) It is Gnome Flashback (Compiz) that I use most of the time and prefer.

The .xinitrc file is with in your /home direcory ( the ~/  is shorthand for " /home/crazybear"; the leading '.' makes this file a "hidden" file.
This file is not required in a normal install, but if we want we can make one up and use it. If that file exist the system will use it.
I do, and for reference only; this is my ~/.xinitrc file:
```

sysop@1404mini:~$ ls -al ~/.xinitrc 
-rwxrwxr-x 1 sysop sysop 222 May 22 12:37 /home/sysop/.xinitrc
sysop@1404mini:~$ cat /home/sysop/.xinitrc
#!/usr/bin/env bash
#started creation of this file 23may2013
#
#
echo "starting the X session, Billy" >&2
#export XAUTHORITY=/home/sysop/.Xauthority
exec startxfce4 --with-ck-launch > /home/sysop/errors-boot.txt 2>&1
#end
sysop@1404mini:~$ 

```
Where all I am doing is making a check point for trouble shooting and - more to our discussion, I start  my GUI (xfce4) here . Doing a bit of fancy error logging .

Now as to you, you are using a login manager ( I do not ) , and we will have to see what it is and how it starts the GUI. We look at that after we have a Terminal, and can start the preferred desktop from terminal. Then we find those files that the login manager uses to start a desktop session .

Also of great probability is that you have a proprietary graphics driver installed, and in a system update process this driver got broke. We still have to have a functioning terminal to check and see what the graphics driver situation is.

We got to have a terminal ->
[INDENT][INDENT][INDENT]fault isolation to restoration
[/INDENT][/INDENT][/INDENT]

---

### Post by crazybear on 2015-07-27
Bashing-om, Thanks much for taking the time and trouble to help me. Appreciate it. I didn't say that I had made any changed to the [COLOR=#000000]~/.xinitrc file. That was just a cut and paste from another Ubuntu forum. I was just wondering if mine had something missing. Yes, I have AMD's latest  driver for Ubuntu installed and it has not had problems before, but I know it can get corrupted. I just don't know.

So, I pulled the drive with 12.02.5 out of the machine it is usually in and put in on my other computer, which is almost identical, but has a different graphics card. ( I used a live CD and did [/COLOR][COLOR=#000000][FONT=Ubuntu Mono]e2fsck - and it was fine. No problems at all).

What next, and feel free to list several things I can / should try / do at a 'go', so hopefully this will not take a very long time. I has now been weeks since I've been able to use that disk, which is my main disk and is set up more to my liking than 14.04 - which I've never been able to get to my liking as much - even if it has some nice bells and whistles...but that is another matter.

Thanks much again.

[/FONT][/COLOR]

---

### Post by Bashing-om on 2015-07-28
crazybear; Yuk;

Just not right . If the file system is intact, I do expect that you can boot to a terminal.

Let's try and boot the system from grub by telling grub and the kernel where their config files are located.
Do you know on what drive and partition that the operating system is installed to ?
Lets say that ubuntu  is installed to the 1st hard drive and the 1st partition on that hard drive:
one can boot it :
At the grub menu; 'c' key for a command line -> grub > prompt
Here at this grub > prompt execute:
```

set prefix=(hd0,msdos1)/boot/grub
set root=(hd0,msdos1)
insmod linux
linux (hd0,msdos1)/vmlinuz root=/dev/sda1 ro
initrd (hd0,msdos1)/initrd.img
boot

```

Does the system boot ?

in respect to :
> 
Yes, I have AMD's latest driver 

How did you install the driver ? From the software repository ( Additional Drivers), or from a PPA, or from AMD direct ?
I say again, a broke proprietary graphics driver can wreck havoc as it is not built to the now upgraded/installed kernel.
In the case of a broke driver, we just get us a terminal and (RE-)install the driver.

[INDENT][INDENT]but we need to boot this sucker to a terminal
[/INDENT][/INDENT]

---

### Post by crazybear on 2015-07-28
OK, some interesting [and strange] news to report.
I moved it to my other computer...both almost the same, only slight difference [which I don't think can explain the following, but who knows...] is the type of AMD graphics card...all the rest that matters is the same. On the other machine, I tried your grub line commands, but got 'unknown file system' for lines 3,4,5, so couldn't boot.

I then had the idea to reinstall grub [had to as I couldn't then do anything more, and always got an initial message of 'unknown file system'. Did so and updated grub too - not sure that was needed.

Then I just tried to boot into the newest kernel and it opened up as good as new.....only it was three small desktops, not one large one on three monitors - but that was as usual when I swap computers and GUI was working as normal and expected...all was there and fine!

I next ran, not walked, to my usual computer it is in, put it in and tried it....guess what...it went into tty with the crazy characters. Remember that the same graphics driver using the same computer is working fine on my 14.04 OS 
disk. You asked how I installed the graphics driver and honestly I forget. It was a loooong and difficult battle, and tried many ways...which one finally worked I honestly do NOT remember as that was many months ago, and it long was working fine. As I mentioned at the top I looked at what I thought were comparable Xorg.conf files [a bit hard to know, as both have multiple ones with extra endings and I don't know which the computer is using for either], but they were very different for 12.04 and 14.04 and wonder if the one for 12.04 is now not correct enough to allow GUI desktop on the main computer. The differences between the two computers, however, are very minimal...but obviously 'enough'. the other also has three monitors, but they are different monitors. So: different monitors, different graphics card (but also AMD) - but in the past I could always swap from one to the other and only had go to into CCC [catalyst control panel] and modify the settings slightly - as what would work with the three heads as one big desktop on one would give three small desktops on the other]. And to anticipate a possible question, no, the 12.04 had not just been moved from the other computer to this one. It went 'strange' on this computer after working fine. Maybe it was a kernel upgrade, but hard to tell, there are so many so often. Could  have been something else - but I didn't notice a direct association between a change of something and the disk not booting. Is there a file that would show the last date it opened up in GUI before last night on the other computer? Then I could match that date with what new programs were installed and maybe figure out something. However, I suspect a change in some configuration file is doing it...but that is just a hunch...I'm no Linux geek for sure!

I'm mystified.....but suspect it is only one small thing 'wrong'..but what?!

Any ideas?!

Thanks.

---

### Post by Bashing-om on 2015-07-28
crazybear; Yuk ...

All that ^^ still in my mind points to the graphics driver/graphics card . Supported in 14.04, not on 12.04 ??
Bet 14.04 is using the " llvmpipe " default driver. !4.04 is a bit smarter about graphics drivers.

So we are back to booting to a terminal ... some how, some way. IF you can not boot to a terminal in the problematic machine, well .. we boot up a 12.04 liveDVD, CHange Root into the install from the liveDVD, and I imagine purge/(RE-)install the graphics driver.
Once we determine what the graphics card is, IF xserver still supports it, ect, ect ....

Why you are able to install the hard drive to a different box, and it boot, is a bit of a mystery, and I am surprised that the fstab UUIDs and grub.cfg's UUIDs do not require to be changed ... In order to boot in that alternate box.

We can examine the problematic hard drive's fstab and grub.cfg files from that CHange Root while we are there. See that they all match the out put of terminal commands:
```

sudo blkid
sudo fdisk -lu

```
Before entering the CHange Root .

We are working with so many variables here.
Conflicting Desktop Environments --
graphics driver 
Grub's config files
Ownership of the desktop files

It is tough to see that tree for all the forest to isolate what is at fault here. We poke at it enough, we will find out.

Bottom line, we need a terminal interface !

All things are relative and 
[INDENT][INDENT][INDENT]inquiring minds want to know[/INDENT][/INDENT][/INDENT]

---

### Post by crazybear on 2015-07-29
I'm fairly sure I installed the AMD driver in both 14.04.2 and 12.04.5. You didn't say which machine you wanted me to try this in....as it seems the results will be different.  I'll try in both and see what the results are.

---

### Post by crazybear on 2015-07-29
Bashing-om, This is stranger than either of us thought. I think however, I found the problem. I didn't think to mention that the two computers also have different Corsair keyboards. This one [my main one on which 12.04 was having problems] has the newest Corsair's K-95-RGB million-color backlit, reprogrammable, multi-macro, full of bells and whistles keyboard. However, it was designed for Windoz, and I don't use Windoz but once in a blue moon. However, there is a great guy who worked on a project without Corsair's help [Corsair offers no Linux driver and doesn't plan to] [to build a driver for the keyboard for Linux and OSX]("http://forum.corsair.com/v3/showthread.php?t=133929"). I use it and it has functioned without problems until now. However it was the keyboard and/or keyboard driver that [I'm almost sure!] WAS/IS the problem. I unplugged the keyboard and the disk booted to desktop on this computer. I was even able to plug back  in the keyboard after - but when the keyboard was plugged in during boot up, this was causing the problem; so I've emailed him as to what I can do to fix this. 

I thank you for your patient help, but think it is now in the realm of this Linux-Corsair 'keyboard guru'. **I only wish I had figured that out a long time ago! **Computers are the damnedest things! 

> An aside to anyone viewing this, I have eyesight problems and also have need of a multi-function top-drawer keyboard. This one is built for gaming, but I don't do gaming. It is a great keyboard, but without this amazing project it didn't work on Linux systems at all. Now it does. So if anyone is looking for the ultimate in keyboards [not cheap however!], I do suggest this combination.

---

### Post by crazybear on 2015-07-29
Bashing-om, This is stranger than either of us thought. I think however, I found the problem. I didn't think to mention that the two computers also have different Corsair keyboards. This one [my main one on which 12.04 was having problems] has the newest Corsair's K95-RGB million-color, backlit, reprogrammable, multi-macro, full of bells and whistles keyboard. However, it was designed for Windoz, and I don't use Windoz but once in a blue moon. However, there is a great guy who worked on a project without Corsair's help to build a driver for the keyboard for Linux and OSX. [http://forum.corsair.com/v3/showthread.php?t=133929](http://forum.corsair.com/v3/showthread.php?t=133929) - I use it and it has functioned without problems until now. However it was the keyboard that [I'm almost sure!] WAS the problem. I unplugged it and the disk booted to desktop on this computer. I was even able to plug  in the keyboard after - but the keyboard plugged in during boot up was causing the problems - so I've emailed him as to what I can do to fix that. 

I thank really you for your patient help, but think it is now in the realm of the 'keyboard guru'. I only wish I had figured that out a looooong time ago! Computers are the damnedest things!

> N.B. I have need for a very high-end backlit programable keyboard. This one is top of the top. It is built for gaming, but I don't do gaming. Corsair only has Windoz drivers and plans no Linux drivers, sadly. However, the man (see url link above) has built a great Linux driver and is still improving it. If anyone wants a top of the line all bells and whistles keyboard in Linux...try it...however the keyboard is NOT cheap!

---

### Post by Bashing-om on 2015-07-29
crazybear; Hey, Hey !

Wonders never cease. In the end all that matters is the fault has been identified. Great that you have a course of action to obtain resolution.

My pleasure to aid and assist you, and yes I too learned a bit more .
As this matter is now concluded :
Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

cheers.
[INDENT][INDENT]I look forward to 
[INDENT][INDENT][INDENT][INDENT]our next adventure
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by crazybear on 2015-07-30
Now, I'm not sure it is solved....certainly it is not working again...and on this machine is always again going only to tty. This now is even when what I thought was the offending keyboard is not plugged in. However, on my other machine, it still goes to the desktop. Very strange indeed. I'm stumped. For some days it was working...and then suddenly after some updates [may not be at all related] and rebooting it would ONLY go into tty and with any keyboard give nonsense 'characters', so login is not possible.

---

### Post by crazybear on 2015-08-13
Would looking at the [many] xorg.conf files be of help. My 14.04 starts up every time on the same machine. I'm sure on each OS, the OS is only looking at [using] one conf file...but on each there are many with slightly different names. I have NO idea how the OS prioritize them to choose which it will use. I have noted, however, that what seem to be equivalent files on the two OS are very different....moving one from 14.04 to 12.04 might work [and it might not too]....or there could be a clue as to what is wrong or missing. Just a thought. Some of the files with .bak are obviously older files and likely need not be examined, but there are many others with various extensions and names that vary only slightly.

As before, if I drop to a command prompt and type 'startx' it does go to a very strange and blank GUI screen [one desktop with the three monitors]...but what would I do there?...no programs show, but I think I can call up a terminal.

---

### Post by Bashing-om on 2015-08-13
crazybear; Yuk;

Tough to make a call .
As you can boot to a terminal // Let's see what we can find out.

What Desktop Environment does the system think is in use ?
```

echo $DESKTOP_SESSION " " $XDG_CURRENT_DESKTOP

```

Next is reduce to simplest terms and try the system with but one monitor connected.
Termianl command:
```

sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak

```
Now with only the one monitor connected, let's regenerate the xorg.conf file:
```

sudo nvidia-xconfig

```

Reboot the system to see the effect.
Do you now boot to the GUI ?

[INDENT][INDENT]maybe yes 
[/INDENT][/INDENT]

---

### Post by efflandt on 2015-08-13
I may have run into a similar issue with my Acer P500W tablet PC. I had not used it for quite some time because it is a slow 2 core 1 GHz cpu with 2 GB RAM that has Win7 Pro on its 32 GB SSD (used to field program some electronic devices for work). I have Lubuntu and Ubuntu 12.04 on their own separate partitions with common /home on 3rd partition of a 32 GB SD card.

Ubuntu had not been updated for quite some time and apparently doing updates with the normal gui may not have completed everything (may have installed kernel image, but not headers). So on reboot fglrx was not working for AMD HD 6250 graphics, but nothing I tried to rectify that in the dialog about low graphics did anything useful. I don't recall if I could get to a text terminal or if I rebooted to recovery, enabled networking from that menu (which also remounts the drive read-write), and used a root terminal. But I saw something somewhere that said to do the first line below (you do not need sudo if done from root terminal) which took a while, and the apt-get install -f installed the missing kernel headers and compiled fglrx modules, etc.```
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get install -f
```After that Ubuntu 12.04 was able to boot and function fine.

I did not have that problem when I updated Lubuntu 12.04, but it had a newer previous kernel which had apparently been updated more recently and may have already had some other updates that made this update go more smoothly.

---

### Post by crazybear on 2015-08-14
> **Bashing-om said:**
> crazybear; Yuk;

Tough to make a call .
As you can boot to a terminal // Let's see what we can find out.

What Desktop Environment does the system think is in use ?
```

echo $DESKTOP_SESSION " " $XDG_CURRENT_DESKTOP

```

Next is reduce to simplest terms and try the system with but one monitor connected.
Termianl command:
```

sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak

```
Now with only the one monitor connected, let's regenerate the xorg.conf file:
```

sudo nvidia-xconfig

```

Reboot the system to see the effect.
Do you now boot to the GUI ?[INDENT][INDENT]maybe yes 
[/INDENT]
[/INDENT]


Will try the first part. Not sure I want to reduce the system to one monitor unless **absolutely** necessary. I do NOT have a nvidia card, so will not try the third. I have a MSI AMD card using fglrx drivers. Maybe I should try to see if ccc will start up and configure the monitors and video system..but as I said the command startx gives me a solid three head 'desktop', only one with almost nothing on it...no panels, no programs, basically no nothing. Will see what I can do....and report back.

Looking on internet, found lots of incomprehensible stuff perhaps relevant...but this page looked good... [https://wiki.gentoo.org/wiki/Xorg/Guide](https://wiki.gentoo.org/wiki/Xorg/Guide)  and this one too [http://wiki.cchtml.com/index.php/Gentoo_Installation_Guide](http://wiki.cchtml.com/index.php/Gentoo_Installation_Guide)

---

### Post by Bashing-om on 2015-08-14
crazybear; Hello;

The command "startx" is UNgood unless your system is configured to utilize THAT means to start the GUI. Depending on the Login Manager and the Desktop Environment that you have is the terminal command to start the GUI . Furthermore, IF you have 'sudo'd' "starx" you have generated additional problems in regards to permissions and access rights .

[INDENT][INDENT]bad things can happen
[/INDENT][/INDENT]

---

### Post by crazybear on 2015-08-15
> **Bashing-om said:**
> crazybear; Hello;

The command "startx" is UNgood unless your system is configured to utilize THAT means to start the GUI. Depending on the Login Manager and the Desktop Environment that you have is the terminal command to start the GUI . Furthermore, IF you have 'sudo'd' "starx" you have generated additional problems in regards to permissions and access rights .[INDENT][INDENT]bad things can happen
[/INDENT]
[/INDENT]


I thought you wanted me to get into the 'desktop' produced by startx, as that is what I had described as giving the only GUI desktop [and with three heads too]. So where do you want me to ask what 'desktop' is being used...as I can NOT get into any other. I can NOT get past the tty - nothing I type in will do anything, as none are characters in asci. Today, there is even a new problem, and recovery mode doesn't complete as it used to. I might have to strip down the system, but that is a lot of work, as it is complex and will take a lot to get it back up to where I can do work. Oddly, on the other computer [same MB, similar processor, similar graphics card - but not the exact same, similar memory, both have three heads, but different monitors; on the other it starts up first time, every time [except giving three single/mirrored monitors - I could fix this, but don't want to as I'd have to redo this on this computer having different monitors and graphics card...making me think it is some configuration file that is unhappy with the hardware on this other [main] computer - or it might be set to work with that on the other. As to permissions, both computers have but one user who is the administrator who is I. I didn't put sudo before startx last I was able to get in to do that....I'll try again later with some things. That gentoo guide I gave the url to seemed to say that startx was an ok thing to do. You say no. Others have said it is an old and unsupported command and program. I dunno.

---

### Post by crazybear on 2015-08-15
FRUSTRATING! I took out all the other disks. So, that was the ONLY disk in the computer. I disconnected two monitors. I tried several things..but I can't get past it booting into a terminal tty terminal...from there nothing can be done. I can drop down to a command prompt in recovery mode, but don't know what to do there....very little I tried seemed to work - that is some kind of special environment, unlike a normal terminal...and one I'm not familiar with. Even stranger, I took a clone [a few months old - predating any of this problem] of this now troublesome disk...put it in and it did the EXACT same thing....neither had before...I believe, that I've kept the clone updated on the other machine from time to time...so that doesn't rule out some new updated software causing this....but I don't know where to go at all. Again, I'm tempted to move xorg config files from 14.04 to 12.04...but know the danger of that if it fails. I'd rather compare them first...but as I said...there are many and I have no idea which the OS is using as the default and how it orders them. Ohk, and before [two weeks ago or so] it did go to some GUI with startx, now it give a long list of options for startx and none were intuitively obvious, so I left it alone. I tried older kernels - but no difference.

---

### Post by Bashing-om on 2015-08-15
crazybear; Sheeesshhh ...

I am having difficulties identifying what you mean by "  I can NOT get past the tty  " .
"nomenclature" : TTY is a system terminal, as opposed to what you might be booting to " grub > " prompt or perhaps a "grub rescue > " prompt ?

If you can boot to a system terminal (TTY) then that indicates the base system is sound;
If you boot to "grub >" prompt then grub is having problems with it's config files;
If you boot to "grub rescue >" then grub's files can not be determined.

We must identify which of these conditions - if ANY - are the true state. A picture is worth a thousand words and 2 weeks of time.

We must know what we are working with to know what we are working toward.

[INDENT][INDENT]all in which process
[/INDENT][/INDENT]

---

### Post by crazybear on 2015-08-16
> **Bashing-om said:**
> crazybear; Sheeesshhh ...

I am having difficulties identifying what you mean by "  I can NOT get past the tty  " .
"nomenclature" : TTY is a system terminal, as opposed to what you might be booting to " grub > " prompt or perhaps a "grub rescue > " prompt ?

If you can boot to a system terminal (TTY) then that indicates the base system is sound;
If you boot to "grub >" prompt then grub is having problems with it's config files;
If you boot to "grub rescue >" then grub's files can not be determined.

We must identify which of these conditions - if ANY - are the true state. A picture is worth a thousand words and 2 weeks of time.

We must know what we are working with to know what we are working toward.[INDENT][INDENT]all in which process
[/INDENT]
[/INDENT]

Hmmm....I'm confused by your confusion and 'definitions'/'statements' above.
It boots into a black screen with only one terminal [the central one] showing what I have always considered the tty prompt...asking me to login..but I can do nothing as any typing I do on any keyboard produces weird non-ascii symbols.

I don't understand exactly the second or third alternative you discuss above. Yes I get a grub screen, and can choose which kernel or the grub rescue [isn't is called something else]....and in that I can sometimes get to a command prompt. As the command prompt in grub rescue as you call it is the only working [sort of] command line I have now...what shall I do there? It seems sometimes that one has to set whether it is mounted as ro or rw and I'm not sure what is needed for what nor how to do so. Next time I'll take a photo, but not sure I can post it here, as they will be very large files.

---

### Post by Bashing-om on 2015-08-16
crazybear; K;

> 
asking me to login..but I can do nothing as any typing I do on any keyboard produces weird non-ascii symbols.

Indicates to me that you are booting to TTY1 ( THE terminal).
Not able to enter text from the keyboard makes me consider what bios is handing off to the operating system as far as drivers are concerned. Maybe the kernel is not picking up a keyboard driver ?
What type of keyboard do you use ?
If a USB keyboard, see what is set in bios for USB devices and that the option "plug and play" is enabled .

[INDENT][INDENT]sometimes I do wonder
[/INDENT][/INDENT]

---

### Post by crazybear on 2015-08-16
Yes, it is tty1 [as it even says so]. I have tried various keyboards, as if you look way up on the thread I had a very special one with all kinds of special setting for it. But I also have a plane vanilla keyboard which does the same things - exactly. Both are USB keyboards. But these are used on this machine for 14.04 [and two other operating systems - all on separate disks], and they work fine, so the settings have to be OK in BIOS...no?! Although I don't claim by any means to be an expert in Linux/Ubuntu I'm not completely a green bean.

I have an image, but I can only see uploading from a url and I have it on the computer...why does it have to be from a url?

---

### Post by Bashing-om on 2015-08-16
crazybear; Humm ...

Beats me, I do not have any other ideas for the keyboard.
I am convinced that what you are booting to is the TTY1 terminal. I have no other advise I can give to have a functional keyboard input to the terminal.

Though now a picture is not required, for your reference to upload a picture. in the 'advanced reply' there is a paper clip icon in the tools bars. This tool will enable you to post screenshots/images .


[INDENT][INDENT]stuck
[INDENT][INDENT][INDENT]all 4 wheels spinning
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by crazybear on 2015-08-17
Ugh! Not good news. In fact, I found that I had two clones [so three disks of this OS 12.04 from about six, three and 1/2 month ago last used without problem on this computer....all do about the same thing. The only difference is that the newest one [the one I had been using on this computer] won't even go into the recovery mode now [new in only the last few days - as if something is getting worse]. But all three open up fine on my other computer which is very very similar in hardware to this one. Is there something I can do on that other computer [since I can do anything we want there]? Such as looking at config files and seeing if they compare to my working 14.04 config files here on this machine. This machine is my main machine. The other is really used for when this computer is not working or I have need to make a clone, do some testing, et al. As this computer has the better hardware, it is the primary computer and will remain that way. My huge video card wouldn't even fit in the other computer - nor does it have all the swap bays and other bells and whistles. Wouldn't the xorg.config files on 12.04 and 14.04 be similar, if not the same? What I do not know is if the OS sensing the slightly different hardware changes some config files or not. As I mentioned there are a LOT of config files. Some are .bak, but a lot of them just have a variety of slightly different names and I can't seem to find out which [or with which preference] the OS 'looks for and at them'. There must be one that the OS uses in preference to the others. Where does one find that heirarchy listed and how did I get so many. I never knowingly generated all of them...the OS somehow did this, likely when installing the Lixus AMD driver and later when I installed the different proprietary AMD drivers [and those installations were NOT easy on 12.04!!!]. On 14.04 the installation of the proprietary driver was a whole lot easier. I have mentioned before that I noted what seemed to be parallel config files [12.04 vs 14.04] were quite different. Unless they changed [?!] they both worked fine for a long time!...suddenly none of my 12.04 disks will work on this machine which seems strange. Originally, I thought it was the fancy Corsair keyboard, so I removed it, but it didn't make a difference. If you remember, a few weeks back I had marked this as 'solved', and for a week [appox.] I could again get into the 12.04 and was happy....then it again went to the tty1 with nonsense characters on any keyboard and has remained that way. [on this machine only]. Ghosts?

---

### Post by Bashing-om on 2015-08-17
crazybear; Well ...

I will continue to work with you to find out and repair the 12.05 install.

1) Reduce to simplest terms;
a) a simple keyboard that you know works ; preferably USB type
b) All other peripheral devices removed, 1 monitor 
c) Prefer that we only have the one hard drive installed that contains the ubuntu operating system, such that there is no confusion which/where file system we are working with.

OK, NOW get to work in an organized manner to find what the root cause of this problem is.

2) We will as a 1st step make sure the file system is intact.
Boot up the liveDVD to "try ubuntu" mode and activate a terminal;
Verify the file system - from the liveDVD:
```

sudo fdisk -lu

```
##So we know what the hard drive is identified as ( I do expect sda IF the live medium is a DVD, IF a USB thumb drive will have to 'see';
check the file system:
```

sudo e2fsck -C0 -p -f -v /dev/sda1
#if errors are reported in the above: -y auto answers yes for fixes needing response see: man e2fsck
sudo e2fsck -f -y -v /dev/sda1

```

3) Next is to know the graphics situation that is present in this live environment, that later we will compare to that of the install.
```

lspci -nnk | grep -iA3 vga
sudo lshw -C display

```

Reboot the machine to that install - remember to reset the boot priority as required -.

In this install we are going to purge all the graphics drivers, and install the open source driver to get to a stable system.

4) clean up and install. when we get to this point I will provide the means !
----------------------------------------
"But all three open up fine on my other computer which is very very similar in hardware to this one." -> the kernel is compiled with certain modules attached, though the kernel makes some adjustments for different hardware, can not make all adjustments, and can not reconfigure it's config files for booting systems with alternate UUIDs without some small amount of help.

" Such as looking at config files and seeing if they compare to my working 14.04 config files here on this machine. " -> One may read the files and attempt to follow the logic, and compare that the "logic" is similar. You can not swap out config files from one to the other . There WILL be differences in the UUIDs and as well the hardware recognized.

"What I do not know is if the OS sensing the slightly different hardware changes some config files or not. " ->Yeah, there is a lot of checking hardware going on starting in bios , bios hands off to the operating system what/condition of recognized hardware - boot up without the splash screen to get an idea of just how complex booting is and get an idea of how much checking is being conducted ! The kernel in booting is 1st set up in ram, then wrote back to the hard drive as the system boots. The system can and does make adjustments. But, not all !

"As I mentioned there are a LOT of config files. Some are .bak, but a lot of them just have a variety of slightly different names and I can't seem to find out which [or with which preference] the OS 'looks for and at them'. There must be one that the OS uses in preference to the others." -> Yes, there can be many backups of config files. IF and only IF they no longer serve a purpose we need to get rid of them and only have on the system the config file that the system requires. (now we need to get specific ) .

----------------------------------

Present situation: after the file system checks/repair is conducted, we will clean this system up, and as noted above, purge all graphics drivers, install the open source graphics driver, IF all looks good as of that time in the process of installing the driver we will also RE-write the kernel image that the system uses to write-to-disk . A valid image  For this hardware in this particular configuration! 
------------------------

It is not that tough, just follow trouble shooting procedure to isolate the fault.
Boot to terminal, good, we can troubleshoot all other issues such as graphics and configuration issues. GOT to have a terminal to ask the system what in the world is going on .

[INDENT][INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT][/INDENT]

---

### Post by crazybear on 2015-08-20
This is weirder than weird! I spent several hours with the problem disk on the other computer [the one it works on]. I found that in /etc/fstab it listed the wrong uuids - so how was it booting on one machine? Anyway, I changed that to be correct. I also went into the CCC [catalyst control center for AMD driver] and changed it to one desktop. When I switch from one machine to the other it always reverted to three cloned monitors - logical as they are not the same and it sensed something different. So, then I return to my main computer and go into that OS. It OPENS [first time in weeks!!!!], but with the expected three cloned monitors. I then went into CCC to correct, but when I rebooted as it asked, it reverted to tty1

One other problem was also noted and I'm trying to eliminate it so I can find out where in the World this problem is!...I tried to update the driver for the Corsair keyboard and it gave error messages. I didn't note them down in detail, as I though it would reboot back into GUI and I could fix then. It is touchy, but there is always [was always] a way through and I unplugged that keyboard and am using another. Still, only boots into tty1. 

Even more strange, for the first time when I gave up and started my 14.04 OS [on a separate disk], it also went to tty1. My heart fell. I went into rescue mode in grub and tried a number of things [I never know which one fixes anything - sometimes just going into that mode does]...and it did boot to GUI...but 12.04 is back to the other computer to start messing around with it as I did yesterday. Again, the problem has to be small and 'simple' - but I can't find it and it is certainly NOT obvious to me. Any ideas would be helpful. I don't even understand how fstab's uuids could have changed - or if that was a part of the problem. If it was, it shouldn't start on either computer, I'd think. I looked at the grub.cfg file, but it has a 'DO NOT EDIT' warning at the top...so didn't.....it is long and complex, but looked reasonably OK to an untrained eye.

---

### Post by Bashing-om on 2015-08-20
crazybear; Sheesshh ...

I am a simple man - with a simple mind.

Too much going on for my simple little mind to keep up with.

[INDENT][INDENT][INDENT]exit stage right
[/INDENT][/INDENT][/INDENT]

---

