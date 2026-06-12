---
title: "Uninstalled ubuntu! Wheres the windows bootloader"
date: 2008-05-15
forum: General Help
---

### Post by ATiwolf on 2008-05-15
Hello.
My friend let me borrow his laptop to try out Ubuntu on.
I had experience with patrons before and was quite confident I could edit them without problem.
I had the laptop dual booting xp and Linux.I knew I could just edit the linux patrons back to windows....
What I didn't know is that Linux took out the Windows boot loader and replaced it with grub, therefore keeping me from going back to windows after linux was gone...

How can I get the windows bootloader back without and xp disk?
I can't reinstall linux because I've resized the windows parton once and will not do it again without chkdsking because it'll corrupt the patrons. 

Please help. **??Solved??**

---

### Post by Mhurst1 on 2008-05-15
You need to use the windows repair disk and enter fixmbr

---

### Post by ATiwolf on 2008-05-15
Like I said before. I don't have an XP disk..

I could go buy one...But Will the upgrade xp disk let me goin into recovery mode?
I don't have $200 buck for the full version...

---

### Post by MaindotC on 2008-05-15
You don't have to buy XP.  Use a disc called the [Ultimate Boot CD]("http://ubcd4win.com/").  There are several utilities you can use, but the UBCD4WIN has utilities to fix the MBR and I've just used it before.  You'll see the options from the main menu when you boot from it.  Good luck!

---

### Post by ccw127 on 2008-05-15
Ultimate Boot CD will work great (I live by that CD), but if your computer has a floppy drive(*trembles at the thought), you could head over to to someone's working windows machine and make a boot floppy. If memory serves (and it may not), there is enough stuff on the boot floppy to fix the mbr.

Chris

---

### Post by MaindotC on 2008-05-15
ATi please let us know that it works out alright for you.

---

### Post by ATiwolf on 2008-05-16
will do...
Having a hard time downloading that cd....
...yeah I though i'd be able to do it with a dos floppy aswell but the laptop has no floppy:(

Thanks...you guys pwn

---

### Post by ATiwolf on 2008-05-17
:(
Wow lots has happend since I last came here....

Well, I got an xp disk from a friend to try the recovery console...
The XP disk wouldn't run the console because it lacked drivers for the hardrive and couldn't find it....

So I found a program called ms-sys that I could run from the live cd to put the MBR back into Window's Hands. Here:
[http://www.arsgeek.com/?p=3340](http://www.arsgeek.com/?p=3340)

Well the thing looked as if it'd work but it just screwed my parton really hard. Gparted couldn't even recognize the windows patron....
I got invalid paron table error at boot up...:mad:
I freaked out and then finally used Ultimae CD thing. I went into test disk and fixed the bad boot sector and wrote a new MBR..

But now when i boot there is a flashing cursor and Xp doesn't boot. **I can access my windows data just fine** thru the unltimate CD and from the ubuntu live...whats going on?

---

### Post by MaindotC on 2008-05-17
In the [arsgeek article]("http://www.arsgeek.com/?p=3340") it asks for output.  Can you post that output please?

NM - looks like we need to see what to do w/ UBCD.  Sec.

---

### Post by Xiong Chiamiov on 2008-05-17
Personally, I'd use [SuperGrubDisk]("http://supergrubdisk.org") to see if I could boot into Windows.  If you can, then you just have to run fixmbr from a DOS prompt.

---

### Post by ATiwolf on 2008-05-17
> **Xiong Chiamiov said:**
> Personally, I'd use [SuperGrubDisk]("http://supergrubdisk.org") to see if I could boot into Windows.  If you can, then you just have to run fixmbr from a DOS prompt.

....
I used super grub disk to try and fix the MBR and it said it succeeded...When I went back and tried to boot I got this:

```
_
```

the cursor just flashes. Nothing has changed....
Then I used SGD to boot and it did all the commands like chainloader+1 and whatnot...Then after it does the boot command I get the same blank cursor...

```
Blah Blah Blah
back
set aux_hd=hd0
rootnovrtify (hd0)
chainloader +1
boot

_
```
Yep it just blinks...windows MBR is being lazy...
like I said i can still access all my files and folders from the live cd..It doesn't say Sda1 like it used to.I go into computer and select '70gb volume' and theres my window stuff....is that the problem? is there anyway I can run the grub command in terminal and set it as sda1?

omg!why!?

---

### Post by Paris Heng on 2008-05-17
> **Xiong Chiamiov said:**
> Personally, I'd use [SuperGrubDisk]("http://supergrubdisk.org") to see if I could boot into Windows.  If you can, then you just have to run fixmbr from a DOS prompt.


How to use the SuperGrubDisk, just boot it? Any how to? My GRUB showing error after i removed the Ubuntu, so now i can't get into MS Windows.

---

### Post by ATiwolf on 2008-05-17
> **Paris Heng said:**
> How to use the SuperGrubDisk, just boot it? Any how to? My GRUB showing error after i removed the Ubuntu, so now i can't get into MS Windows.

Yeah you just download the iso and burn it..It just runs...
You get error 22 right?
I have removed grub too and fixed the MBR several times and I get nothing...

Im thinking of putting a fresh GRUB back in and seeing if it will run without linux so i can run windows

Heres the SGB isos:
[URL="http://www.supergrubdisk.org/index.php?pid=5"]select open of them there mirrors
[/URL]

---

### Post by ccw127 on 2008-05-17
When you borrowed the windows CD, was it the same version as you have installed? If you have home installed, you need a home CD; pro for pro.

---

### Post by ugm6hr on 2008-05-17
GAG might allow to get back into Windows without having to do any further damage.

Once you can boot into Windows, it should be easier.

---

### Post by ATiwolf on 2008-05-17
> **ccw127 said:**
> When you borrowed the windows CD, was it the same version as you have installed? If you have home installed, you need a home CD; pro for pro.

Mrh? I have Pro and the disk if for home...I figured windows fecovery console would work anyway...it didn't detect my hard drive any way....

I played around with testdisk again and it found two patrons listed  
in the same path. One was normal and the other was in the backup sector. They both had 'D' tags for deleted..

After looking over the testdisk documentation I was relieved in finding out they they we're not actually deleted just using the same path.:confused:

Maybe thats what's keeping the MBR from booting. It's confused...

---

### Post by Seks on 2008-05-17
You may be trying to solve a little problem with a sledgehammer. 

Get an ubuntu live CD and pop it in, go to partition manager and move the "boot" flag to the windows partition. That solved an "unable to boot" issue after an unsuccessful ubuntu install for me. (Then I used unetbootin, my cd burner is trippy)

---

### Post by ATiwolf on 2008-05-18
Gparted indicates that the Windows parton is indeed wearing the boot. It should be able to run,lol.
*sigh* I'm going to go change the tags on the two twin NTFS partons or delete one..Theres no other choice. 

Re-re-re-re-re-rewrite the MBR=Fail

Reinstall Grub=Fail

Reinstall Linux=Fail(gparted errors out when I try to shrink the NTFS parton to allow space for ubuntu)

---

### Post by Cap'n Skyler on 2008-05-18
> **ATiwolf said:**
> Gparted indicates that the Windows parton is indeed wearing the boot. It should be able to run,lol.
*sigh* I'm going to go change the tags on the two twin NTFS partons or delete one..Theres no other choice. 

Re-re-re-re-re-rewrite the MBR=Fail

Reinstall Grub=Fail

Reinstall Linux=Fail(gparted errors out when I try to shrink the NTFS parton to allow space for ubuntu)
when i have had various hard drive issues and linux distros go crap on me and then nothing will start or come up enuff for me to fix it,i go find a different linux or windows and re install that and then it overwrites everything and then later come back and re install your fave linux.
 try the live cd's for linux...perhaps thru that you can then get to do some hard drive partioning?
try ubuntu 
puppy
fedora
dsl
slax
any of these live cd's should get you access to the HD

---

### Post by ATiwolf on 2008-05-18
yeah, I know. I've being using the 7.10 live cd this whole time trying to either fix the MBR or to parton and reinstall linux(and inevitably GRUB).
> 
any of these live cd's should get you access to the HD
yep. I can get to all my pictures and college notes but NOoo windows refuses to boot. Thanks though

---

### Post by Cap'n Skyler on 2008-05-18
> **ATiwolf said:**
> yeah, I know. I've being using the 7.10 live cd this whole time trying to either fix the MBR or to parton and reinstall linux(and inevitably GRUB).

yep. I can get to all my pictures and college notes but NOoo windows refuses to boot. Thanks though

from all my tries i do know they all are just a little bit different.can you try a windows boot cd/floppy?

---

### Post by ATiwolf on 2008-05-18
Negative,Ghost Rider.

The laptop is a modern one, and therefore came standard with its floppy bay circumcised.

I have,however, used the ***ULTIMATE BOOT CD  *** and it's plethora of recovery programs to try and fix the MBR 

Every Attempt to get this bad boy to boot is always meet with the obnoxious blinking of that darn boot cursor....Grr :x

---

### Post by ugm6hr on 2008-05-18
> **ATiwolf said:**
> Re-re-re-re-re-rewrite the MBR=Fail

Reinstall Grub=Fail

Reinstall Linux=Fail(gparted errors out when I try to shrink the NTFS parton to allow space for ubuntu)

Have you tried GAG?
[http://www.users.bigpond.net.au/hermanzone/p18.htm#GAG_Boot_Manager](http://www.users.bigpond.net.au/hermanzone/p18.htm#GAG_Boot_Manager)

A different bootloader that doesn't need to be installed.

If that doesn't work either, you might be best off backing up files you can get to (if you didn't pre-messing about) and reinstalling.

---

### Post by ATiwolf on 2008-05-18
> **ugm6hr said:**
> Have you tried GAG?
[http://www.users.bigpond.net.au/hermanzone/p18.htm#GAG_Boot_Manager](http://www.users.bigpond.net.au/hermanzone/p18.htm#GAG_Boot_Manager)

A different bootloader that doesn't need to be installed.

If that doesn't work either, you might be best off backing up files you can get to (if you didn't pre-messing about) and reinstalling.

Heh. I have small stack of recovery/live/OS CDs in front of me right now. Probably enough to rival a computer technician's collection.
I'm totally out of Blank CD-RWs thanka to this situation. 
I'll try to use gaG tomorrow if I find another cd in my house that I'd been using for backup. 

I might have to go buy more and a sharpie so I can label these things.

---

### Post by ugm6hr on 2008-05-18
> **ATiwolf said:**
> Heh. I have small stack of recovery/live/OS CDs in front of me right now. Probably enough to rival a computer technician's collection.

Important thing is to resist trying to write to the HD repeatedly, since you can currently access your HD files - which may not be the case if you repartition.

Did you back-up before all this started?

---

### Post by ATiwolf on 2008-05-18
Nope.
I kept putting off reinstalling ubuntu and just did it one day...
I was surprised when got the grub error 22 and wished I had just left it alone.

It's lame when you're confident and **think** you can do something(**with** or without relevant experience) and then get **slapped** down by reality. Your always learning and mistakes are **necessary**.:(

I didn't/Don't have the means or know how to make or restore any entire Parton table or what ever. I can grab any files I need from the windows parton if I fear any sort of imitate disk failure...Which is a constant threat...

---

### Post by ATiwolf on 2008-05-18
I don't know whats going on but GAG give the same results as all past boot attempts...a flashing cursor and thats it.

Why do I keep getting that. It's Just like and older computer I had with a blank hardrive...like its trying to boot from nothing...but I know that data is there...

---

### Post by mahuyar on 2008-05-18
> **ATiwolf said:**
> I don't know whats going on but GAG give the same results as all past boot attempts...a flashing cursor and thats it.

Why do I keep getting that. It's Just like and older computer I had with a blank hardrive...like its trying to boot from nothing...but I know that data is there...

Also make sure you have the following files in your C:\  -
boot.ini
NTDETECT.COM
NTLDR

While you're at it, can you post the contents of boot.ini also?

This Microsoft's KB [article]("http://support.microsoft.com/kb/318728") might be useful.

EDIT:  Can you also post your "sudo fdisk -l" result if not too much trouble?  Thanks.

---

### Post by ATiwolf on 2008-05-18
Yeah they are all in there boot.ini goes:
[PHP][boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect[/PHP]:confused:


brb to post linux results....live CDs are slow but not as slow as the ultimate disk...
thanks btw to everyone who still sticking with this

---

### Post by ATiwolf on 2008-05-18
[PHP]Disk /dev/sda: 80.0 GB, 80026361856 bytes
240 heads, 63 sectors/track, 10337 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0xc59ec59e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9565    72311368+   7  HPFS/NTFS
/dev/sda2            9566       10337     5836320    c  W95 FAT32 (LBA)
[/PHP]

The sda2 is the recovery partition that IBM place on the Hdd of the laptop...
If i tried to instigate that recovery process it will reformat the PC completely...Not an option...:(

---

### Post by Commodore13 on 2008-05-18
I'm having a similar problem, but not the exact one.
I'm a major noob in the this stuff so I really need somebody to walk me through this please!
I was really exited about the Wubi feature in 8.04 and I thought that it would be a good alternative to managing an entirely seperate partition. I had the idea to delete my Ubuntu partition and install Wubi inside of Vista Premium instead. I went to diskmgmnt.msc and deleted the partition, when I went to restart and install wubi, I realized that I had erased GRUB!! it came up with the err message 17. I'm currently typing this from my emergency DSL-N CD I have in my toolbox. Please help me!

I'm sorry for intirupting this current thread, please email me help at [email]commodore.J13[at]gmail.com[/email]

---

### Post by mahuyar on 2008-05-18
Thanks.  ATiWolf, can you join the ubuntu's irc?  It's at irc.ubuntu.com.  Channel is #ubuntu

EDIT:  We will post the solution here if things go successful.

---

### Post by ATiwolf on 2008-05-18
I went into the live CD pidgen thing and connected to irc.ubuntu.com
how do I go to the ubuntu channel....:confused:

---

### Post by Commodore13 on 2008-05-18
Click on the join chat button and type in #ubuntu
I think....

---

### Post by MaindotC on 2008-05-18
You need an irc client - it's like a chatroom.  Try the package called xchat.

---

### Post by mahuyar on 2008-05-18
> **strAlan said:**
> You need an irc client - it's like a chatroom.  Try the package called xchat.

Thanks, we got it.  Trying to help there now.  We'll post back the solution if we ever come up with one.  :D

---

### Post by ATiwolf on 2008-05-19
mahuyar and I have found an interesting issue with the ms-sys program's readme file:

Apparently, when using the linux 2.6 kernel, the program will write incorrect Partition Geometry.:confused:

Beyond that, all attempts to get windows booted again have failed...

---

### Post by mahuyar on 2008-05-19
> **ATiwolf said:**
> mahuyar and I have found an interesting issue with the ms-sys program's readme file:

Apparently, when using the linux 2.6 kernel, the program will write incorrect Partition Geometry.:confused:

Beyond that, all attempts to get windows booted again have failed...

ms-sys program's -p switch is buggy at best.  I guess we should avoid using its -p switch side of the story.

When you have a chance, try [MbrFix]("http://www.ambience.sk/fdisk-master-boot-record-windows-linux-lilo-fixmbr.php") tool.  I came across it while googling for a solution.  It sounds like a right tool for us.  You'll have to boot with your Ultimate Boot CD and run the program from there.

Let me know how it goes.

---

### Post by ATiwolf on 2008-05-19
No, No, mahuyar.
I've tried everything on the UBCD.
It has to be because the Geometry is incorrect...

Another Friend of mine has the exact same laptop and I had also installed ubuntu on his. I went over there just about and hour ago and:
1.Booted from ubuntu live cd(with the dreaded 2.6 kernel)
2. unmouted and killed both the ext3(linux) and linux swap file partitions.
3.Feed the windows NTFS partion the corpse of both linux partitions.
4. Booted into The UBCD and Ran checkdisk then that Mbrfix program.
5.Backed up his MBR and saved it in C:\
6.[COLOR="YellowGreen"]SMASHED[/COLOR] the Grub with a Windows Boot....loader...

It was [COLOR="YellowGreen"]messy[/COLOR] but it worked.Windows booted and there was no error
The Only mistake I made on MY laptop was using that darn ms-sys program without reading the readme...Stupid 2.6 kernel doesn't know how to Calculate Partition geometry.:mad:

---

### Post by ibuclaw on 2008-05-19
Hmm... All that trouble?

I got rid of my GRUB and restored the Windows MBR with **two commands under Linux**.

No Windows CD needed!

[Read Here.]("http://ubuntuforums.org/showthread.php?t=799895")

The way I think it works (As I actually did it by accident) is that SYSLINUX (An alternative Bootloader to GRUB, except made for USB Drives) erases the MBR and just marks the hard-drive as "BOOTABLE", then when the BIOS reads the MBR, it just boots straight off the first disk.

If that disk is Windows, then you'll boot straight into Windows! No GRUB, no configuration!

Boot back into your LiveCD and give it a try!

Regards
Iain

---

### Post by ccw127 on 2008-05-19
Srry about taking two days to get back here... been quite busy; I just finished getting all caught up on this thread... so are you good ati? I figure I should ask before chiming in with anything new (cause I have a couple of thoughts in the case that you are not).

Chris
[email]hololight@gmail.com[/email]

---

### Post by ATiwolf on 2008-05-19
Um...I no longer have the laptop. 
I just gave it back to the college as-is.
I instructed the staff to let the computer technicians know the the Patition Geometry is not acurate and needs adjusting. 
The staff doesn't know diddly-squat about computers except for maybe one, individual. 
They didn't make a big fuss...

They Probably would have though I erased the disk if I they tried to boot it without a term-filled explanation to confuse them :lolflag:

The problem is pretty much solved...
The solution?:
[SIZE="4"]Don't Use MS-SYS with any variation of the 2,6 kernel...Or you and your hard drive are boned[/SIZE]

---

### Post by ibuclaw on 2008-05-19
+1

here, here...

---

### Post by mahuyar on 2008-05-20
> **ATiwolf said:**
> No, No, mahuyar.
I've tried everything on the UBCD.
It has to be because the Geometry is incorrect...

Another Friend of mine has the exact same laptop and I had also installed ubuntu on his. I went over there just about and hour ago and:
1.Booted from ubuntu live cd(with the dreaded 2.6 kernel)
2. unmouted and killed both the ext3(linux) and linux swap file partitions.
3.Feed the windows NTFS partion the corpse of both linux partitions.
4. Booted into The UBCD and Ran checkdisk then that Mbrfix program.
5.Backed up his MBR and saved it in C:\
6.[COLOR="YellowGreen"]SMASHED[/COLOR] the Grub with a Windows Boot....loader...

It was [COLOR="YellowGreen"]messy[/COLOR] but it worked.Windows booted and there was no error
The Only mistake I made on MY laptop was using that darn ms-sys program without reading the readme...Stupid 2.6 kernel doesn't know how to Calculate Partition geometry.:mad:

So... That MbrFix program fixed your friend's laptop?  Well, I wouldn't exactly say *fixed*, since nothing was wrong on that laptop, but MbrFix restored Windows boot loader on it?  If we had time to use it on the laptop you gave back, we probably could've saved it with that program.  :-k

Terrible experience with ms-sys for us.  I just can't believe it did not even warn us at least, that it could screw up the partition tables with the -p switch.  ](*,)

---

