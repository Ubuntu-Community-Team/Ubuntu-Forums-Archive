---
title: "ubuntu won't boot"
date: 2017-04-08
forum: General Help
---

### Post by missfortran on 2017-04-08
My acer laptop running 16.04 had a crisis this morning and now the boot up only comes up with a screen telling me  UNEXPECTED INCONSISTANCY  RUN fsck MANUALLY.  the final line is (intramfs) _  

It is waiting me to enter something and I have no idea what. The last time I had to give program instructions to a computer they were on punch cards.

I hope someone can help me here.

---

### Post by Bashing-om on 2017-04-08
missfortran; Hello:

> 
UNEXPECTED INCONSISTANCY RUN fsck MANUALLY. the final line is (intramfs)


Let's take the system's advice and run that manual file system check . As this is 16.04 (systemd) we need to run this check from grub - as a 1st approximation:
force fsck at boot time by passing fsck.mode=force as a kernel parameter. This will check every filesystem you have on the machine.
At the grub menu press the 'c' key for a command line -> Boot parameters screen -> arrow down to the line starting with linux and arrow over to "quiet splash" ; delete these terms and all after and insert - fsck.mode=force - ( without the '-' separator characters) . Ctl+x to continue the boot process.

We see if this fixes the file system; If you boot to the GUI as expected . Then reboot the machine and see if the fix is in .

[INDENT][INDENT]hey, it could happen
[/INDENT][/INDENT]

---

### Post by missfortran on 2017-04-09
found a screen headlined GNU GRUB verssion 2.02 beta2 36ubuntu3.6 

can't find a command that gets me anywhere from here

---

### Post by missfortran on 2017-04-09
the computer boots ok on 14.04 via usb so i can access files dont know if this helps

---

### Post by Bashing-om on 2017-04-09
missfortran; Hummmm, hey .. 

We want to access the hard drive install install for now .
Can you boot to the grub boot menu ?

Do you know how to ?

[INDENT][INDENT]together we can
[/INDENT][/INDENT]

---

### Post by missfortran on 2017-04-10
I'm not sure what the Grub menu is so I may not recognize it even if I did get to it. I got to the page I mentioned above where the last line of the page had the word grub then the flashing cursor waiting for me to enter something. Everything I tried gave me one of two results 1: invalid command (paraphrased) and 2: Security won't let you do that (also paraphrased).

---

### Post by Bashing-om on 2017-04-10
missfortran; Ho Kay -

2 ways to activate the grub boot menu
EFI system: as soon as the bios screen clears spam the escape key;
legacy (MBR): as soon as the bios screen clears press and hold a shift key.

Advise when you are at the grub boot menu .

[INDENT][INDENT]it is a thing
[/INDENT][/INDENT]

---

### Post by missfortran on 2017-04-10
ok there
the three options are 1.ubuntu  2.advanced options for ubuntu and 3. system setup

---

### Post by missfortran on 2017-04-10
i didn't realize it was called "The Grub Menu". booting this machine has often taken me there without me doing anything other than turning the power on.

---

### Post by #&amp;thj^% on 2017-04-10
Just for clarity:
GRand Unified Bootloader
GNU GRUB (or just GRUB) is a boot loader package that supports multiple operating systems on a computer. During boot-up, the user can select the operating system to run. GNU GRUB is based on an earlier multiboot package, GRUB (GRand Unified Bootloader).
Hope that useful.

---

### Post by missfortran on 2017-04-10
went back to your orig instruct

c for command line gives me -grub- followed by cursor

---

### Post by missfortran on 2017-04-10
e for edit gets me an editable text screen with two lines of text top line is - setparams 'System setup' - then a space line then indented - fwsetup - 

the rest of the sceen is blank with a line of instructions on the very bottom

---

### Post by Bashing-om on 2017-04-10
missfortran; Yukkie on me !

As I gave the wrong direction .. in this case we want the 'e' key for edit mode.
'e' key from the grub boot menu -> boot parameters screen.
Here now
Boot parameters screen -> arrow down to the line starting with linux and arrow over to "quiet splash" ; delete these terms and all after and insert - fsck.mode=force - ( without the '-' separator characters) . Ctl+x to continue the boot process.

We see if this fixes the file system; If you boot to the GUI as expected . Then reboot the machine and see if the fix is in .

hey, it could happen

---

### Post by missfortran on 2017-04-10
The only two lines are as above . No line with Linux

---

### Post by Bashing-om on 2017-04-10
missfortran; Regrets - but

> **missfortran said:**
> e for edit gets me an editable text screen with two lines of text top line is - setparams 'System setup' - then a space line then indented - fwsetup - 

the rest of the srceen is blank with a line of instructions on the very bottom

I am lost here as I have never encountered this screen . encryption ??

Can you provide us a screen shot ?

[INDENT][INDENT]I just do not know 
[/INDENT][/INDENT]

---

### Post by missfortran on 2017-04-10
I can't get the screen shot to work but I will take a few shots with my tablet and get those posted asap

---

### Post by missfortran on 2017-04-10
Well don't seem to able to post photos at least not from this tablet BUT when I tried to boot comp again I got the same screen using e ingrub menu with much more content and now there are 15 lines of text and line 14 starts with Linux and ends with quiet splash $vt_handoff. Then line 15 starts with united  and ends with generic.

---

### Post by Bashing-om on 2017-04-10
missfortranl Wellll ..


Do you see similar ?
> 
linux /boot/vmlinuz-3.2.0-24-generic root=UUID=dbd69ed2-530c-4409-8f5a-a3f1ea41fc67 ro quiet splash $vt_handoff  <--- linux kernel boot line

where 3.2.0-24 and dbd69ed2-530c-4409-8f5a-a3f1ea41fc67 will be different .

Then the above applies . remove quiet splash $vt_handoff and insert fsck.mode=force.
key combo ctl+x to continue the boot process  and to also run a file system check at that boot .

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by missfortran on 2017-04-10
Good try but no cigar haha 
After going through a checking process we ended with the same unexpected inconsistent requiring a manual fsck 
The last line on the screen (initramfs)_ the underline is flashing waiting for a command and the line above it tells me that entering "help" will give me a list of built in commands.

I'm thinking I might need to simply get my files off it and reinstall Ubuntu but I have admitting defeat to a machine

---

### Post by Bashing-om on 2017-04-10
missfortran; Well ... 

Like this . Given time and effort (and sometimes a liveDVD) ubuntu is always fixable.
However, that nuclear solution of a RE-install is faster - but we learn little in taking that option.

Presently we do not know if grub is failing or if there is a fault in the file system .

We can boot a liveDVD(USB) and get a better idea of what is not taking place .

Ya want to take the time and effort to learn ?

[INDENT][INDENT][INDENT]we can do that
[/INDENT][/INDENT][/INDENT]

---

### Post by missfortran on 2017-04-10
Can't complain I've been 100% Ubuntu since 2008 and this is the first time it looks like I might have to reinstall. Windows had me doing it at least every 18 months

---

### Post by Bashing-om on 2017-04-10
missfortran; Hey !

Major reason why I have the 'buntu knowledge I have is that I have many times in the learning stages borked the system to the points that I did take that nuclear solution MANY times . I have not in the longest time ! --- We do learn !

It is your time, and effort -
If ya want to keep at this and find out the why and the fix ......

Boot up a liveDVD(USB) and post back:
```

sudo parted -l
sudo fdisk -lu

```
and we take another poke at a file system check . From the live environment you can post the results for our inspection .

[INDENT][INDENT]inquiring minds want to know
[/INDENT][/INDENT]

---

### Post by missfortran on 2017-04-10
Ubuntu has my primary os for 9 years, 3 desktops and 6 laptops and this is the first time it looks like the machine might beat me.

---

### Post by missfortran on 2017-04-10
Booting USB 14.04 on the laptop, will shut down this toy (my kids tablet)

---

### Post by missfortran on 2017-04-10
ok on laptop now booted with 14.04 on usb flash drive

---

### Post by Bashing-om on 2017-04-10
missfortran;

Post #22 :
Post the results - Between code tags - of terminal commands :
```

sudo parted -l
sudo fdisk -lu

```
code tag tutorial:
[https://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](https://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

And I tell ya the specifics to run that file system check/repair from the liveUSB.

[INDENT][INDENT]small steps end a long journey
[/INDENT][/INDENT]

---

### Post by missfortran on 2017-04-10
```
ubuntu@ubuntu:~$ sudo parted -l
Model: ATA ST1000LM024 HN-M (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start   End     Size    File system     Name                  Flags
 1      1049kB  538MB   537MB   fat32           EFI System Partition  boot
 2      538MB   992GB   991GB   ext4
 3      992GB   1000GB  8465MB  linux-swap(v1)


Model: Lexar JumpDrive (scsi)
Disk /dev/sdb: 15.7GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  15.7GB  15.7GB  primary  fat32        boot, lba


ubuntu@ubuntu:~$ sudo fdisk -lu

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0xbf415fad

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1  1953525167   976762583+  ee  GPT
Partition 1 does not start on physical sector boundary.

Disk /dev/sdb: 15.7 GB, 15703474176 bytes
255 heads, 63 sectors/track, 1909 cylinders, total 30670848 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0002d40f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048    30670847    15334400    c  W95 FAT32 (LBA)
ubuntu@ubuntu:~$
```

---

### Post by missfortran on 2017-04-10
the tutorial link didn't go anywhwere

---

### Post by Bashing-om on 2017-04-10
missfortran; Ho Kay !

Let's run:
```

sudo e2fsck -C0 -p -f -v /dev/sda2

```
from the liveUSB.

See what the file system check has to relate .

[INDENT][INDENT]of it ain't one thing, it's another
[/INDENT][/INDENT]

---

### Post by missfortran on 2017-04-11
ubuntu@ubuntu:~$ sudo e2fsck -C0 -p -f -v /dev/sda2
/dev/sda2:                                                                      Inodes that were part of a corrupted orphan linked list found.  

/dev/sda2: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.
    (i.e., without -a or -p options)
ubuntu@ubuntu:~$

---

### Post by missfortran on 2017-04-11
Took the instruction in brackets literally and ran without -p. This is result

ubuntu@ubuntu:~$ sudo e2fsck -C0 -f -v /dev/sda2
e2fsck 1.42.9 (4-Feb-2014)
Pass 1: Checking inodes, blocks, and sizes
Inodes that were part of a corrupted orphan linked list found.  Fix<y>? yes    
Inode 29361227 was part of the orphaned inode list.  FIXED.
Deleted inode 29362511 has zero dtime.  Fix<y>? yes
Inode 29363861 was part of the orphaned inode list.  FIXED.
Inode 29364310 was part of the orphaned inode list.  FIXED.
Inode 29364915 was part of the orphaned inode list.  FIXED.
Inode 29367406 was part of the orphaned inode list.  FIXED.
Inode 29369233 was part of the orphaned inode list.  FIXED.
Inode 29371261 was part of the orphaned inode list.  FIXED.
Inode 29371596 was part of the orphaned inode list.  FIXED.
Inode 29371988 was part of the orphaned inode list.  FIXED.
Inode 29372220 was part of the orphaned inode list.  FIXED.
Inode 32506122 was part of the orphaned inode list.  FIXED.                    
Pass 2: Checking directory structure                                           
Pass 3: Checking directory connectivity                                        
Pass 4: Checking reference counts                                              
Pass 5: Checking group summary information                                     
Block bitmap differences:  -187820583 -(187820597--187820604) -(193861154--193861161) -(193964550--193964564) -193965075 -(193965099--193965105) -193985040 -193985091 -(193985093--193985100)
Fix<y>? yes
Free blocks count wrong for group #17 (11647, counted=11694).                  
Fix<y>? yes
Free blocks count wrong for group #90 (14189, counted=14277).
Fix<y>? yes
Free blocks count wrong for group #5731 (24165, counted=24174).
Fix<y>? yes
Free blocks count wrong for group #5916 (14218, counted=14226).
Fix<y>? yes
Free blocks count wrong for group #5919 (27531, counted=27564).
Fix<y>? yes
Free blocks count wrong (226614297, counted=226614482).
Fix<y>? yes
Inode bitmap differences:  -29361227 -29362511 -29363861 -29364310 -29364915 -29367406 -29369233 -29371261 -29371596 -29371988 -29372220 -32506122
Fix<y>? yes
Free inodes count wrong for group #3584 (1, counted=7).                        
Fix<y>? yes
Free inodes count wrong for group #3585 (1, counted=6).
Fix<y>? yes
Free inodes count wrong for group #3968 (7900, counted=7901).
Fix<y>? yes
Free inodes count wrong (60163448, counted=60163460).
Fix<y>? yes

/dev/sda2: ***** FILE SYSTEM WAS MODIFIED *****

      342652 inodes used (0.57%, out of 60506112)
        3218 non-contiguous files (0.9%)
         349 non-contiguous directories (0.1%)
             # of inodes with ind/dind/tind blocks: 0/0/0
             Extent depth histogram: 293671/649/3
    15377966 blocks used (6.35%, out of 241992448)
           0 bad blocks
           4 large files

      236050 regular files
       41086 directories
          55 character device files
          25 block device files
           0 fifos
          39 links
       65424 symbolic links (48238 fast symbolic links)
           3 sockets
------------
      342682 files
ubuntu@ubuntu:~$

---

### Post by Bashing-om on 2017-04-11
missfortran; Ouch !

We need to go deeper.
I am leery as can be to work on a 16.04 (systemd) system with 14.04 (upstart) tools.

How bout setting up a 16.04 liveUSB ?
And we do that.

[INDENT][INDENT]safety is no accident
[/INDENT][/INDENT]

---

### Post by missfortran on 2017-04-11
That will take a little while on my internet I think I need to download a copy of 16.04 to put on the stick.

---

### Post by missfortran on 2017-04-11
I need to run my wife and kids to the bus depot, I'll get back to this in 30 -40 minutes.

This is fun back soon

---

### Post by Bashing-om on 2017-04-11
missfortran;

Well, as ya " Took the instruction in brackets literally and ran without -p. " .. 
Reboot into the install and let's see what is now .

could be
[INDENT][INDENT]finer than a frog's hair
[/INDENT][/INDENT]

---

### Post by vasa1 on 2017-04-11
> **missfortran said:**
> the tutorial link didn't go anywhwereWe'll fix that in a while but for now here's a little, possibly incomplete, write-up:
CODE TAGS
Please use **[noparse]```
[/noparse]** and **[noparse]
```[/noparse]** tags to enclose *terminal output*. The reason is that terminal output (usually) uses a fixed-width font so that columns are properly aligned and spaced.

[LIST]
[*]*If you start a new thread*, just select the text you've pasted and click on the **[SIZE=4]#[/SIZE]** icon above the text box _or_ first click the **#** icon and then paste the terminal output between the code tags.
[*]*If you reply to a post by clicking the large **+Reply to Thread** below the last post in a thread*, the same process applies.
[*]*If you reply to any post by clicking on "Adv Reply" or "Reply With Quote"*, the same applies.
[*]However, *if you click on "Quick Reply"*, you'll see fewer icons above the text area and the **#** icon will be missing. In that case, either type in the [noparse]```
[/noparse] and [noparse]
```[/noparse] tags yourself for each bit of terminal output or click on "Go Advanced" to give you all the editing options the forum provides including the **#** icon.
[/LIST]

---

### Post by missfortran on 2017-04-11
OK, Back on board. Computer booted up well. It might have been a little slower but no glitches so far. Maybe we fixed it properly or maybe we jury-rigged a little, either way it works for now.  What I probably should do it run some sort of check on the root files or something in order to tell which one. What would you suggest?

---

### Post by Bashing-om on 2017-04-11
missfortran; Good deal :)

16.04 - systemd - does a file system verification at boot up . I expect that is good 'nuf for our use case.
If the system detects a fault it will tell you ( as you are now well aware ).

Use the system and see that all is now fine.

[INDENT][INDENT]that's what I think
[/INDENT][/INDENT]

---

### Post by missfortran on 2017-04-11
Thank You Bashing-om for sharing your knowledge. It is great to have my machine up and running again without having to do a full re-install of OS. Kudos, have a great day

---

### Post by vasa1 on 2017-04-11
You could mark the thread [SOLVED]: [https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

