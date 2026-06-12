---
title: "Can't enter os selection menu"
date: 2008-06-17
forum: General Help
---

### Post by Neville Haynes on 2008-06-17
I have a Toshiba Tecra A8-(180?) with 100(90 displayed in computer)gb hard drive. Previous to installing ubuntu I was using Vista business edition with 3 gb of RAM(noted in case it's important info that I installed another chip, it came with one 1gb). I used the option on the liveCD to install I shortcut to boot from the disk as I had tried entering BIOS and but CD boot was not a choice. I installed ubuntu 8.04 LTS on a newly created partition and all was working well. 

When I turn on the computer Ubuntu starts up automatically. However, when I start up the computer and hold esc,F1,del, or tab, that screen freezes and I never get the option to choose the OS. I have been using ubuntu for two weeks now and I have been having the same problem since its installation. I've tried looking in this forum and asking other users I know but can't find anybody that has had this exact problem. I used vista for games and have experimented with Wine but not everything works. I probably should mention that I don't have the vista CD, it is legal (I can download updates and such so I think it's legal) but it came installed without the CD.

Also while searching the forums, I have found that while I can understand some of the techniques said, I'm not that smart and would really appreciate it if the more complex processes could be dumbed down a little in case it comes to a requirement for complexity.

Edit: I just noticed that the free space on the C drive is only 100mb thanks to the partition (when I got it it was already partitioned in half). Might be important

---

### Post by manfer on 2008-06-17
Could you post the content of the file /boot/grub/menu.lst ?

---

### Post by Neville Haynes on 2008-06-17
title		Ubuntu 8.04, kernel 2.6.24-18-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=ade33b5c-0a36-459a-b944-9eb90bc53d5f ro quiet splash
initrd		/boot/initrd.img-2.6.24-18-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-18-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=ade33b5c-0a36-459a-b944-9eb90bc53d5f ro single
initrd		/boot/initrd.img-2.6.24-18-generic

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=ade33b5c-0a36-459a-b944-9eb90bc53d5f ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=ade33b5c-0a36-459a-b944-9eb90bc53d5f ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,4)
kernel		/boot/memtest86+.bin
quiet


is that the important part or the very bottom?



# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista/Longhorn (loader)
root		(hd0,1)
savedefault
makeactive
chainloader	+1

---

### Post by manfer on 2008-06-17
No more on that file? Those entries look fine but not all there.

Before those menu items there are some configuration parameters. The interesting part in this case would be there, to know if some parameter is making your grub fail.

If it starts ubuntu with no delay you must have at least this parameters:

default 0
timeout 0
....

maybe you have some mistake in other parameters that makes grub crash.

---

### Post by Neville Haynes on 2008-06-18
:( I couldn't find:
default 0
timeout 0

Instead of posting everything I opened and saved it in notepad (original menu.lst unaltered) to make it a text file and attached it to my post if it worked

---

### Post by manfer on 2008-06-18
default 0 is on line 14 of your menu.lst

timeout 10 is on line 19 of your menu.lst

The menu.lst looks fine so something must be wrong in grub installation. I suggest to reinstall grub.

The way to do that is as follows. For what it is shown in your menu.lst your /boot filesystem is on (hd0,4). Anyway you are going to confirm it on the reinstallation process.

Enter ubuntu. If your computer only enters ubuntu as you say in first post you only have to turn it on. When you are in ubuntu open a terminal. Type:

------------------------------------------------------

prompt:~$ **sudo grub**

------------------------------------------------------

Enter your root password.

The terminal would change showing you grub prompt.

------------------------------------------------------
       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]

grub>
------------------------------------------------------

Type there the command, find /boot/grub/stage1
------------------------------------------------------
       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]

grub> **find /boot/grub/stage1**
------------------------------------------------------

That would look for your /boot filesystem an would tell you where it is. If my guess from menu.lst is correct it must answer you (hd0,4)

------------------------------------------------------
       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]

grub> find /boot/grub/stage1
** (hd0,4)**

grub>
------------------------------------------------------

Now that you confirmed where the /boot filesystem is located, it is located on partition hd0,4 (the fifth partition on disk hd0) you are going to install grub. Type, root (hd0,4)

------------------------------------------------------
       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]

grub> find /boot/grub/stage1
 (hd0,4)

grub> **root (hd0,4)**

grub>
------------------------------------------------------

You tell grub with that command where is located the /boot filesystem which you want to use. And finally to install grub on MBR of hard drive you type, setup (hd0)
------------------------------------------------------
       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]

grub> find /boot/grub/stage1
 (hd0,4)

grub> root (hd0,4)

grub> **setup (hd0)**
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  16 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+16 p (hd0,4)/boot/grub/stage2
/boot/grub/menu.lst"... succeeded
Done.

------------------------------------------------------

You tell grub with that command to install on Master Boot Record of disk hd0. You are done, type quit to exit grub.

grub> **quit**

And finally close terminal and reboot computer. That must solve the problem. If not so, then there is some issue with your system that makes grub fail.

*Note: Look careful (hd0,4) no spaces, (hd0, 4) would be wrong. In order to prevent confusion it is hd"zero", zero number, not vocal o*

---

### Post by Neville Haynes on 2008-06-18
I followed the steps and got the exact messages you have written but after reboot it still starts ubuntu straight away

There is also a screen I didn't mention as it only lasts for a few seconds so I didn't think it was important. It is a blank grey screen with a darker bar at the bottom and a message "kernal is alive" and on the next line lots of numbers, mostly zeros. The screen was there before the grub reinstall

I appreciate the help, especially typing out the step by step guide

---

### Post by manfer on 2008-06-18
Those seconds you mentioned could be 10 seconds? - menu.lst timeout 10 :) default 0 corresponding to ubuntu, when those 10 seconds past, ubuntu is booted by default -

For what I'm reading about the issues with those Toshiba laptops someone says he can choose the OS to boot even he can't see the grub menu.

When that grey screen you mention appears try pressing down cursor key 6 times. That would take you to last field of menu corresponding to Windows, Then hit Enter and tell if that way it boots Windows. (even doing it all blind, not seeing the menu and what you are doing, try if it works)

The problem deals with those laptops, I would go on guessing and tell you if I find solution.

---

### Post by Neville Haynes on 2008-06-18
The grey screen lasts for one and a half seconds if my stopwatch and my reactions are accurate. I will keep trying the down key six times and then enter, but two seconds isn't long enough for me to be sure I'm hitting the key the correct amount

---

### Post by manfer on 2008-06-18
And if you start computer pressing ESC and try pressing down key when it seems to be frozen?

This all is only to guess if it works. It could probably not work at all but I haven't found any solution yet. I will tell you if I found.

It would be nice if one of these solutions works meanwhile.

---

### Post by Neville Haynes on 2008-06-18
> **manfer said:**
> And if you start computer pressing ESC and try pressing down key when it seems to be frozen?

I'm running vista!:D It happened before I saw your entry. I hit the down button too soon, on the first screen that freezes, and yet again it froze so I decided to hit it another five times and enter and after a brief wait it loaded the (BIOS?) screen with 2 selections, ubuntu on the top line and Vista (loader, or something) on the next. Vista did have to run a check on it's volumes but I suppose that is a result of the drastically low disk space which I am now getting warnings for.

I am now thinking about getting partitioning software and removing ubuntu, then installing it onto the original second partition.

Thank you for your help manfer! I have really enjoyed using ubuntu the last two weeks and the community is really active and willing to help. I still have the live CD and I'm guessing that to install onto an existing partition I need to use wubi.exe as opposed to umenu.exe that I used the first time?

---

### Post by manfer on 2008-06-18
If you use wubi.exe you will install ubuntu into Windows filesystem. It will be installed in windows as any other application and you can uninstall it when you want as any other application. You don't have to make partitioning of the hard disk. It is an easy way to install/uninstall ubuntu for people not very experienced in making dedicated partitions and doing the install.

How did you install the first time with umenu.exe? You chosed demo and full installation?

---

### Post by Neville Haynes on 2008-06-18
I double clicked on the CD drive and umenu.exe autoplayed. Out of three options I chose to add a boot from CD option to the BIOS menu and booted from live CD, then just followed the steps. I'm fairly sure I just clicked next on every screen, reading everything just to make sure it wouldn't do any harm to the computer. The slider and settings I used were all default.

Edit: So if i use wubi.exe then I would need to start vista first, then load ubuntu like a program, almost like a sophisticated emulator? That doesn't sound like the best option, as I can guess that the performance would be decreased.

---

### Post by manfer on 2008-06-18
Ok, the first option:

Demo and full installation
--------------------------
Try ubuntu without installing! Simply reboot your machine with the CD in the tray. You will later have the option to perform a full installation from within the demo itself.

But after going to demo (live CD) you made a full installation, don't you? The installation created partitions for ubuntu or you had those partitions done before? For the menu.lst entries I guessed it was a dual boot system with a Windows installed on first partition and ubuntu on fifth one. I hope it was not wrong.

---

### Post by manfer on 2008-06-18
> **Neville Haynes said:**
> So if i use wubi.exe then I would need to start vista first, then load ubuntu like a program, almost like a sophisticated emulator? That doesn't sound like the best option, as I can guess that the performance would be decreased.

I'm not sure how it works exactly but something like that. Not exactly a virtual machine but I some decrease on performance for sure.

Wubi.exe would be lunch if you chose the second option on umenu. And it says this:

Install inside Windows
----------------------
You can install ubuntu without modifying your disk setup. Suspend and hibernation are not enable in this mode and performance is slightly reduced. Uninstalling is easy.

---

### Post by Neville Haynes on 2008-06-18
> **manfer said:**
> Demo and full installation
--------------------------
Try ubuntu without installing! Simply reboot your machine with the CD in the tray. You will later have the option to perform a full installation from within the demo itself.

This is what I did

> **manfer said:**
> But after going to demo (live CD) you made a full installation, don't you? The installation created partitions for ubuntu

Yes, I originally had two partitions, C and E drives. Ubuntu installation created two more (that apparently can't be seen by windows) called file system and 

> **manfer said:**
> For the menu.lst entries I guessed it was a dual boot system with a Windows installed on first partition and ubuntu on fifth one. I hope it was not wrong.

Fifth? The only way I can think of a third partition (before the two ubuntu ones) is if it counted my 500mb SD card which I have always left in the computer

I would like to know if it is possible, and how to, install ubuntu separate from windows onto the E drive

---

### Post by manfer on 2008-06-18
and ... linux swap :)

No, that card doesn't count.

I suppose it is a first recovery partition. Most laptops have one. Probably a fat32 partition and besides a small one.

Don't you know how to show the partition table on a Windows System to confirm that? I'm not familiarized with Vista but I know it has it for sure because XP just had it. Looking on web I think it is Disk Manager:

"To access Disk Management, right click on My Computer, and select Manage from the context menu – this will open the Computer Management console (alternatively, Disk Management may be accessed from Control Panel> Administrative Tools> Computer Management)."

On that disk manager you would see a graphical view of your hard drive and its partitions.

On ubuntu that graphical view of the disk and its partitions can be shown with the program gparted if installed on system.

In both not recommended to touch nothing if you don't know exactly what you are doing. They are good for the purpose of seeing that graphic but are dangerous to touch if not sure what you are doing.

---

### Post by manfer on 2008-06-18
> I would like to know if it is possible, and how to, install ubuntu separate from windows onto the E drive

That was the way you installed. You did it the wright way I think.

If I remember how it works, when you installed that way, the ubuntu installation program got free space, probably from that so called E: drive from windows (not a drive at all, only a partition on your only one hard drive, or that is what I guess) to make its needed partitions, one for the root filesystem (/) and one for swapping.

So you had and have, I suppose you still don't uninstalled it, a good fresh installation of ubuntu on its own partition.

---

### Post by manfer on 2008-06-18
The presence of that first small recovery partition can be guessed too from menu.lst that shows Windows on second partition (hd0,1).

I had made a mistake about this on previous post where I said Windows was on first partition. But all the process we done was fine, we didn't touch menu.lst which shows it the wright way.

---

### Post by manfer on 2008-06-18
> **Neville Haynes said:**
> 
Ubuntu installation created two more (that apparently can't be seen by windows).


The partitions are seen from Windows as you can check if you use the disk manager I mentioned before.

What Windows can't do is access the filesystems on those partitions.

There is no need to access the swap partition because it is only a partition that ubuntu needs to use for operating system activity. Something like the pagefile on Windows Systems.

However you could sometime want to access the ubuntu root filesystem (ext2 or ext3 filesystems) from Windows and you can do it with programs as Explore2fs, DiskInternals Linux Reader, or if you want read and write installing fs-driver on Windows.

---

