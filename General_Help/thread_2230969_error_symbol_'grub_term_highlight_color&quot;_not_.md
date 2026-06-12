---
title: "error: symbol 'grub_term_highlight_color&quot; not found. grub rescue&gt;"
date: 2014-06-22
forum: General Help
---

### Post by SUPERFITTER on 2014-06-22
I have a duel boot Windows 7 and Ubuntu 12.10. I used a disk to update 12.10 to 14.04.  After I updated and rebooted I got a black screen and this.

error: symbol 'grub_term_highlight_color" not found.
grub rescue>

Is there a command line that I can type in to correct this problem?

Thank you

---

### Post by SUPERFITTER on 2014-06-22
Has anyone found an answer to this problem with grub?

---

### Post by Bashing-om on 2014-06-22
SUPERFITTER; Hello;

"error: symbol 'grub_term_highlight_color" not found."

Known condition, possible bug:
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1289977](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1289977)
The solution is to (re-)install grub, suggested is via:
'dpkg-reconfigure grub-pc ' for effect.

best
[INDENT][INDENT]regards
[/INDENT][/INDENT]

---

### Post by SUPERFITTER on 2014-06-23
> **Bashing-om said:**
> SUPERFITTER; Hello;

"error: symbol 'grub_term_highlight_color" not found."

Known condition, possible bug:
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1289977](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1289977)
The solution is to (re-)install grub, suggested is via:
'dpkg-reconfigure grub-pc ' for effect.

best[INDENT][INDENT]regards
[/INDENT]
[/INDENT]


I tried that and had no luck.

---

### Post by Bashing-om on 2014-06-23
SUPERFITTER; Well,

We can try and (re-)install grub from the liveDVD.
Post back the outputs of terminal commands :
```

sudo fdisk -lu
sudo parted -l

```
So I know what we are working with and I will provide the commands to do the deed.

[INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT]

---

### Post by SUPERFITTER on 2014-06-25
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0007b338

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   204802047   102400000   83  Linux
/dev/sda2       204812685   976771071   385979193+   f  W95 Ext'd (LBA)
/dev/sda5       204812748   943288604   369237928+   7  HPFS/NTFS/exFAT
/dev/sda6       943298560   976771071    16736256   82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x88acbdd4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048   307210994   153604473+   7  HPFS/NTFS/exFAT
/dev/sdb2       307210995   976768064   334778535    f  W95 Ext'd (LBA)
/dev/sdb5       307211058   976768064   334778503+   7  HPFS/NTFS/exFAT
ubuntu@ubuntu:~$ sudo parted -l
Model: ATA WDC WD5000AAKX-0 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
 1      1049kB  105GB  105GB   primary   ext4            boot
 2      105GB   500GB  395GB   extended                  lba
 5      105GB   483GB  378GB   logical   ntfs
 6      483GB   500GB  17.1GB  logical   linux-swap(v1)


Model: ATA WDC WD5000AAKX-0 (scsi)
Disk /dev/sdb: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type      File system  Flags
 1      1049kB  157GB  157GB  primary   ntfs         boot
 2      157GB   500GB  343GB  extended               lba
 5      157GB   500GB  343GB  logical   ntfs


Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: Can't have a partition outside the disk!                           

ubuntu@ubuntu:~$

---

### Post by Bashing-om on 2014-06-25
SUPERFITTER; OK ;

From the outputs we know that linux is installed onto that 1st hard drive, and that the partition containing the final stages of the boot code is located in partition sda1. Now we can (RE-)install grub using a number of methods. In this instance let's try:
From the liveDVD -> terminal:
Terminal commands:
```

sudo mount /dev/sda1 /mnt
sudo grub-install --boot-directory=/mnt /dev/sda
sudo umount /mnt

```

Reboot into the install, and pick up and chainload the other systems ( if that is how you want to boot) by terminal commands:
```

sudo grub-install --recheck /dev/sda
sudo update-grub

```

Reboot once more and all should be
[INDENT][INDENT][INDENT][INDENT]hunky dory
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by SUPERFITTER on 2014-06-25
ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt
ubuntu@ubuntu:~$ sudo grub-install --boot-directory=/mnt /dev/sda
Installing for i386-pc platform.
Installation finished. No error reported.
ubuntu@ubuntu:~$ sudo umount /mnt
ubuntu@ubuntu:~$ 



I got this error:
ubuntu@ubuntu:~$ sudo grub-install --recheck /dev/sda
Installing for i386-pc platform.
grub-install: error: failed to get canonical path of `/cow'.
ubuntu@ubuntu:~$ sudo update-grub
/usr/sbin/grub-probe: error: failed to get canonical path of `/cow'.
ubuntu@ubuntu:~$

---

### Post by Bashing-om on 2014-06-26
SUPERFITTER; Hey hey ,

> 
I got this error:
ubuntu@ubuntu:~$ sudo grub-install --recheck /dev/sda
Installing for i386-pc platform.
grub-install: error: failed to get canonical path of `/cow'.
ubuntu@ubuntu:~$ sudo update-grub
/usr/sbin/grub-probe: error: failed to get canonical path of `/cow'.
ubuntu@ubuntu:~$
 You were still in the liveDVD environment.

The directive was:
> 
Reboot into the install,

At this time try and boot up your ubuntu on the hard disk and run those two commands.

[INDENT][INDENT]maybe yes
[INDENT][INDENT][INDENT]could be, not so yes[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by SUPERFITTER on 2014-06-26
I tried that the first time and got a black screen that had a message about Grub 2.02 I belive. When I typed the second group of commands:
sudo grub-install --recheck /dev/sda
sudo update-grub

It did not understand sudo.

---

### Post by Bashing-om on 2014-06-26
SUPERFITTER; Yuk ..

Maybe still stuck at a grub> prompt ?
> 
It did not understand sudo.

Maybe you did not hit the enter key to select the default boot option to boot that kernel ??

OR, maybe now it seems a graphics driver issue (??).
One approach to see if it is graphics related:
Boot the install to the grub boot menu, with a non-recovery kernel entry line highlighted - most likely the top line - press to 'e' key for edit mode ->
Boot parameters screen; arrow down and across to the terms "quiet splash" and and add the term 'nomodeset' - without the quotes - ; key combo ctl+x to continue the boot process.
Do you now get to the GUI login screen, and able to log into your system ?

[INDENT][INDENT]it is fault isolation
[INDENT][INDENT][INDENT]for restoration
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by SUPERFITTER on 2014-06-26
All I get on boot is a black screen that I cannot do anything with, even if I hit enter:

GNU GRUB Version 2.02~ beta 2-9

Minimal BASH-like line editing is supported. For the first word, TAB lists possible command completions.  Anywhere else TAB lists possible device or file completions.

grub>


This is what the message says on a black screen?  If I hit TAB I get pages of commands, but I do not know what to do with them?

---

### Post by Bashing-om on 2014-06-26
SUPERFITTER; Morning .

Panic not. Just proceed in a calm and orderly fashion.
What you are seeing is grub, and not able to complete the boot process likely due to still with corrupt boot file(s). Let's go back to my post #3 and do a more in-depth (re-)install of grub with 'dpkg-reconfigure grub-pc ' . This is a lot more complex and involved, but we can do this. We are going to do a full CHange Root and execute that command in that environment.
Boot the liveDVD to a terminal:
Terminal commands:
```

sudo mount /dev/sda1 /mnt/
sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
sudo mount --bind /sys /mnt/sys
sudo mount --bind /dev/pts /mnt/dev/pts
sudo chroot /mnt/ /bin/bash
dpkg-reconfigure grub-pc

```
You are now in the install and as well you are ROOT, be very careful and sure of all commands entered ! There is no forgiveness of a mistake or error. Triple check before entering commands !
In the reconfigure grub-pc routine is a pop up window to make a selection as to where to install grub. - space-bar to select drive, tab to OK, enter to accept - You want to choose 'sda'  such that the result is '[*]' beside 'sda'.
All done and now back out of the CHange Root:

```

exit
sudo umount /mnt/dev/pts
sudo umount /mnt/sys
sudo umount /mnt/proc
sudo umount /mnt/dev
sudo umount /mnt

```

OK, done with the liveDVD, -- reboot to the hard drive -- and see if now you are able to boot ubuntu to the desk top.
Complete the (RE-)install picking up the other Operating System to add to the boot menu from the real install -> At the desk top key combo ctl+alt+t yields a terminal:
Terminal commands:
```

sudo grub-install --recheck /dev/sda
sudo update-grub

```

Once more reboot and now you should see the grub boot menu with that other Operating system as a selection in that menu.

[INDENT][INDENT]did we do well ?
[/INDENT][/INDENT]

---

### Post by sewbiz on 2014-06-26
I found this quote from someone who had the same problem I was having....found this on askUbuntu.com......CAN I DO THIS? Can someone show me how to enable Boot from USB in BIOS?

Quote:
[Thank you very much for your  thorough assistance.  Though I initially couldn't get any of your  suggestions to boot of a USB either, I, by a complete guess, found out  how I could:  I had Boot from USB enabled in BIOS and placed above the  hard drive in the boot order, but when I DISABLED booting form the hard  drive, all became peaches.  Thanks again!                 &#8211;                      [user165793]("http://askubuntu.com/users/165793/user165793")                 [Aug 2 '13 at 0:50]("http://askubuntu.com/questions/327323/grub-rescue-limbo-with-a-twist?rq=1#comment416854_327547")                                                                                                  ] end Quote

---

### Post by SUPERFITTER on 2014-06-28
I got this far, but where is the pop up window?

ubuntu@ubuntu:~$ sudo mount /dev/sdxY /mnt/
mount: special device /dev/sdxY does not exist
ubuntu@ubuntu:~$ sudo mount --bind /dev /mnt/dev
mount: mount point /mnt/dev does not exist
ubuntu@ubuntu:~$ sudo mount --bind /proc /mnt/proc
mount: mount point /mnt/proc does not exist
ubuntu@ubuntu:~$ sudo mount --bind /sys /mnt/sys
mount: mount point /mnt/sys does not exist
ubuntu@ubuntu:~$ sudo mount --bind /dev/pts /mnt/dev/pts
mount: mount point /mnt/dev/pts does not exist
ubuntu@ubuntu:~$ sudo chroot /mnt/ /bin/bash
chroot: failed to run command &#8216;/bin/bash&#8217;: No such file or directory
ubuntu@ubuntu:~$ dpkg-reconfigure grub-pc
/usr/sbin/dpkg-reconfigure must be run as root
ubuntu@ubuntu:~$

---

### Post by Bashing-om on 2014-06-28
SUPERFITTER; Hey,

Sorry 'bout that, missed a copy - paste correction:
```

sudo mount /dev/sd[color=red]xY[/color] /mnt/

```
Should be:
```

sudo mount /dev/sda1 /mnt/

```
so that the "root' directory is mounted.

I will edit my error.

[INDENT][INDENT]try try again
[/INDENT][/INDENT]

---

### Post by SUPERFITTER on 2014-06-28
I now have this:


&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508; Configuring grub-pc &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;  
 &#9474; The following Linux command line was extracted from /etc/default/grub or  &#9474;  
 &#9474; the `kopt' parameter in GRUB Legacy's menu.lst. Please verify that it is  &#9474;  
 &#9474; correct, and modify it if necessary. The command line is allowed to be    &#9474;  
 &#9474; empty.                                                                    &#9474;  
 &#9474;                                                                           &#9474;  
 &#9474; Linux command line:  

Should I put this in that Linux command line:*sda????  

Then Hit OK??

---

### Post by Bashing-om on 2014-06-28
SUPERFITTER; nope,

An empty line is acceptable .. just hit enter.

[INDENT][INDENT]one thing at a time.
[/INDENT][/INDENT]

---

### Post by SUPERFITTER on 2014-06-28
I now have  quiet splash__

In command line, should I hit OK?

---

### Post by Bashing-om on 2014-06-28
SUPERFITTER; Humm...
If you are still at that " The following Linux command line was extracted from /etc/default/grub or &#9474; " screen.

I would just leave the line empty, but I can not see any harm in having "quiet splash" as a boot parameter as it is a 'default' parameter.

carry on to the next item in the process.

[INDENT][INDENT]moving along
, one thing at a time
[/INDENT][/INDENT]

---

### Post by SUPERFITTER on 2014-06-28
Should I hit OK?

---

### Post by SUPERFITTER on 2014-06-28
Should I hit OK?

Or should I hit Enter?

---

### Post by Bashing-om on 2014-06-28
Yeah, hit OK, it is alright .. ( may have to tab/space to be able to "accept" .. my memory here is a bit hazy.

---

### Post by SUPERFITTER on 2014-06-28
I Hit OK and got this:

Package configuration                                                           
                                                                                
 &#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508; Configuring grub-pc &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;  
 &#9474;                                                                           &#9474;  
 &#9474; The grub-pc package is being upgraded. This menu allows you to select        
 &#9474; which devices you'd like grub-install to be automatically run for, if        
 &#9474; any.                                                                         
 &#9474;                                                                              
 &#9474; Running grub-install automatically is recommended in most situations, to     
 &#9474; prevent the installed GRUB core image from getting out of sync with GRUB     
 &#9474; modules or grub.cfg.                                                         
 &#9474;                                                                              
 &#9474; If you're unsure which drive is designated as boot drive by your BIOS,       
 &#9474; it is often a good idea to install GRUB to all of them.                      
 &#9474;                                                                              
 &#9474; Note: it is possible to install GRUB to partition boot records as well,      
 &#9474; and some appropriate partitions are offered here. However, this forces       
 &#9474; GRUB to use the blocklist mechanism, which makes it less reliable, and       
 &#9474;                                                                              
 &#9474;                                  <Ok>

---

### Post by Bashing-om on 2014-06-28
Hit 'OK' . We know we are going to install grub to 'sda'.

next !

---

### Post by SUPERFITTER on 2014-06-28
I hit enter and nothing happens?

---

### Post by Bashing-om on 2014-06-28
Did you 'tab' so that "OK" is highlighted ? .. Will not proceed otherwise, you get kicked back to the start of the process.

---

### Post by SUPERFITTER on 2014-06-28
I forgot about the tab key, I got this when I entered:


Package configuration                                                           
                                                                                
                                                                                
                                                                                
                                                                                
                                                                                
                    &#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508; Configuring grub-pc &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;                     
                    &#9474; GRUB install devices:               &#9474;                     
                    &#9474;                                     &#9474;                     
                    &#9474;    [ ] /dev/sda (500107 MB; ???)    &#9474;                     
                    &#9474;    [ ] - /dev/sda1 (104857 MB; /)   &#9474;                     
                    &#9474;    
[*] /dev/sdb (500107 MB; ???)    &#9474;                     
                    &#9474;                                     &#9474;                     
                    &#9474;                                     &#9474;                     
                    &#9474;               <Ok>                  &#9474;                     
                    &#9474;                                     &#9474;                     
                    &#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496;

---

### Post by SUPERFITTER on 2014-06-28
This one is in red[] /dev/sda (500107 MB; ???

---

### Post by SUPERFITTER on 2014-06-28
I hit the space bar to move te * to /dev/sda, but I still have a * in /dev/sdb

Now they both have a * infront of them

---

### Post by Bashing-om on 2014-06-28
ok ! Now we are talking.

What ya want is to as per post #13 -=> ' is a pop up window to make a selection as to where to install grub. - space-bar to select drive, tab to OK, enter to accept - You want to choose 'sda' such that the result is '[*]' beside 'sda'."

All ok now ?

---

### Post by SUPERFITTER on 2014-06-28
I was able to reboot and I'm now updating. So many things have to be updated. 

Thank You Very Much!!!!  
Bashing-om

I would never have gotten this computer to boot without your help.  

I had to ask a lot of questions, so others with this problem can follow what was typed into terminal.

---

### Post by Bashing-om on 2014-06-28
SUPERFITTER; Great !

Pleased it worked out.
Please mark this thread solved;
 aides others seeking the solution,
 helps keep the forum clean and 
precludes others miss-directing efforts to aid.

I could not have done it with out the bug report on Launchpad !

[INDENT]this is open source
[INDENT][INDENT][INDENT]all for 1 and one for all
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Paulzsen on 2014-12-06
Same happened to me. Any solution to this issue?

---

### Post by Bashing-om on 2014-12-06
Paulzsen; Hi ! Welcome to the forum .

The fix is to (RE-)install grub.
The more aggressive - and successful - method is from a full CHange Root environment ( such that the file systems are not mounted and in use ).
```

sudo fdisk -lu ##so you find/know the partition (/) where grub's files are installed##

## Change /dev/sdxY to actual partition value eg. /dev/sda1

sudo mount /dev/sdxY /mnt/
sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
sudo mount --bind /sys /mnt/sys
sudo mount --bind /dev/pts /mnt/dev/pts
sudo mount --bind /run /mnt/run
sudo chroot /mnt/ /bin/bash
dpkg-reconfigure grub-pc

```
Where " dpkg-reconfigure" starts a wizard, make sure you install grub to the hard disk's MBR sector ( i.e. sda) if ubuntu is installed on that 1st hard drive (sda).(You need to use dpkg-reconfigure grub-pc instead of grub-install directly, so that the system knows that it needs to run grub-install on that drive the next time grub is upgraded.)

Once completed - grub installed, back out of this CHange Root:
```

exit
sudo umount /mnt/run 
sudo umount /mnt/dev/pts
sudo umount /mnt/sys
sudo umount /mnt/proc
sudo umount /mnt/dev
sudo umount /mnt

```

Reboot at this time into the installed system. and check that all is well:
```

sudo update-grub

```

This is a complex operation for one not familiar with linux, feel free to express any concerns .

[INDENT][INDENT]it is doable
[/INDENT][/INDENT]

---

