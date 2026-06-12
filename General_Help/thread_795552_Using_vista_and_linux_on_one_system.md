---
title: "Using vista and linux on one system"
date: 2008-05-15
forum: General Help
---

### Post by zoner1 on 2008-05-15
So the other day I decided to install linux.  I partitioned my drive to allow myself to install Linux as an operating system alongside Vista.  As I understood, during the installation of Linux (I might mention that I have installed Ubuntu) I would be given an option to set up some sort of a dual boot, where I would receive an option about which operating system I would like to use when I start my computer.  This never happened. At this point, I am simply frustrated and want to be able to use Vista.  I am really unconcerned about the fate of my Linux operating system.  Thus, I am open to any suggestions at this point; how can I use Vista?  Thank you in advance for your help.

---

### Post by herteljt on 2008-05-15
If your install was succesful you should have a grub boot menu when you start up the pc.  It should give you an option to start windows.  During the install Ubuntu should have told you it detected windows and thus it would be an option in the boot menu.  

Can you boot into Ubuntu?

---

### Post by bodhi.zazen on 2008-05-15
did you install Ubuntu on the entire hard drive ?

Can you post the output of :

```
sudo fdisk -l
```

---

### Post by adult swim on 2008-05-15
> **~Nightingale~ said:**
> HAHAHAHAHAHA, FAIL!!! Thats what you get for using windows:lolflag::lolflag::lolflag::lolflag:
necessary?  if you read his post this is what he got for wanting to try out linux.  

to the op, when you installed linux and it was asking where to install did you choose the partition you set aside for ubuntu?

---

### Post by proalan on 2008-05-15
> **~Nightingale~ said:**
> HAHAHAHAHAHA, FAIL!!! Thats what you get for using windows:lolflag::lolflag::lolflag::lolflag:
How rude

---

### Post by zoner1 on 2008-05-15
Awesome, lots of responses.  I guess I wasn't too clear earlier.  I partitioned 15% of my hard drive for Linux and left the the rest reserved for windows.  That was my first choice pertaining to partitioning-related activities.  However, I was later asked which partitions I would like to reserve for different functions.  I was not quite sure what I was doing here, and I believe this might be where I messed up.  In the end, I looked online and copied a similar layout to someone else's.

I am currently using said computer we are talking about; however thankfully, I do have others.  I am able to use Linux perfectly.  I actually like the operating system; I just need a book or something to demystify its nuances.  When I start my computer, somewhere a Grub program is mentioned, but it never gives me the choice of which operating system I would like to log into.  Is there a key that I need to press at a certain point?  So, anyways, what are my options looking like?  As I understand, this isn't the simplest process in the world.

nick@nick-laptop:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18701   150215751   83  Linux
/dev/sda2           18702       19457     6072570    5  Extended
/dev/sda5           18702       19457     6072538+  82  Linux swap / Solaris


I don't see windows in there.  This is scaring me...  Thank God I backed up my entire hard drive

---

### Post by mario-182 on 2008-05-15
Hey everyone. I have the same problem as this guy. The first time I tired installing Ubuntu, I remember choosing about 50% of my harddrive to be partitioned. That didn't work because it froze at 15% of the installing system process. So the second time I installed it, I accidentally left the 'automatic' option ticked (not the manual one), so now when I boot my laptop, the GRUB loader doesn't have the Windows option..
I'm really worried and want to know if there's a way to find out whether my Vista partition is still there, and whether I can somehow access it..
Thanks
Mario

---

### Post by badfish591 on 2008-05-15
> **zoner1 said:**
> nick@nick-laptop:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18701   150215751   83  Linux
/dev/sda2           18702       19457     6072570    5  Extended
/dev/sda5           18702       19457     6072538+  82  Linux swap / Solaris


I don't see windows in there.  This is scaring me...  Thank God I backed up my entire hard drive

there is no windows partition in there man, it would show up as HPFS/NTFS under system it is a good thing you backed up your files...... sorry.

@mario-182 post the result of the same command and we can see about yours, but i'm gueesing your probably in the same boat.


oh yeah @nightingale   your a douchebag

---

### Post by zoner1 on 2008-05-15
So now that I know I deleted windows, what should I do to go about restoring it.  I ask because windows came installed on my computer.  I do not believe a disc was included.  There is a recovery drive that is used when the computer is formatted to restore windows and the computers original settings.  Unfortunately, I have no idea how to access this from Linux.  Any thoughts about what to do?

---

### Post by adult swim on 2008-05-15
i dont know if you can recover a whole installation from the recovery partition. i dont even see the recovery partition in your fdisk output.  you may try asking around to see if any of your friends have a vista disk you could borrow and then use your activation key when asked for it.

---

### Post by badfish591 on 2008-05-15
well it seems odd that there is no disc, but if you have some kind of restore drive than maybe you can access it from your bios or something?

---

### Post by zoner1 on 2008-05-15
I take that back.  I do have a disc.  I have no idea what that recovery drive is for then.  So, what is the procedure here?  will it simply ask me if I want to format when I insert the disc?

---

### Post by adult swim on 2008-05-16
when you boot from your disc youll get to a point where it asks you where to install windows, it may tell you that it will automatically format your whole drive if doesnt see any ntfs, which it wont.  if you dont care to get rid of ubuntu, i would just delete all of your partitions from the windows partition editor and then install vista on the whole drive.  if you want to try ubuntu again (and i hope you do) it is easier to install it after windows rather than to install ubuntu and then windows.

---

### Post by zoner1 on 2008-05-16
I really do want to try Ubuntu again.  From the short introduction that I've had, I've really come to appreciate the operating system.  I'm just realizing that to fully utilize the system's capabilities I'm going to need to buy a book.  The old click and see what happens method that I grew up using to learn how to operate Vista just doesn't seem to work any longer. 

So you recommend I trash Linux for now and try reinstalling it again after Vista is operational?  I think I'll be back on this page within the next few days for complete instructions about how to partition my drive so I don't need to go through this ordeal again.

---

### Post by mario-182 on 2008-05-16
Holy crap :(
I now hate Ubuntu.. I'm guessing I'll get the same result. Where abouts do I put in that command?
So I'm guessing if Windows *is* deleted, there's no way of using it's System Restore?
I'll be losing so much.. There's NO way of recovering my documents/programs??
Goddammit.. Who wouldn't to delete Windows and *only* use Linux :(

---

### Post by adult swim on 2008-05-16
i would definitely wipe the drive and start all over with windows first.  when you are ready it only takes like 10 minutes to install ubuntu so its not that big of a deal!

---

### Post by jjthomas on 2008-05-16
Since everything is back up, I would do the following:
1) If you can get Partition Magic, use it partition your hard disk out as follows (If not use Knoppix or simuliar.  The goal is to lay out your partitions first then install the OS'es):  
   100GB NTFS for Windows
    54GB Linux for Ububntu
     6GB for Linux Swap
It looks like you have an 6GB Partition for Swap.  I would make the swap file 2x your installed RAM. 

Install Vista first.  Then install Ubuntu. 

Vista does mark partitions with its own header information.  You might google Vista and Linux to see what all the steps are, as well as anything you need to get these two OS'es to coexist.  I finally dedicated one machine to Vista and the other to Linux.  

I did have Vista and Ubuntu Studio running at one time on the same computer, but not any longer...  so I know it's doable. :)

-JJ

---

### Post by mario-182 on 2008-05-16
Can someone tell me where I went wrong?
I still don't see where I screwed up, causing Windows to be erased..
All I did was follow the instructions on the CD, and it *never* said anything about erasing my current OS :confused:

EDIT: These were my results :(

[i]mario-182@himynameismario:~$ sudo fdisk -1
[sudo] password for mario-182:
fdisk: invalid option -- 1

Usage: fdisk [-b SSZ] [-u] DISK     Change partition table
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s)
       fdisk -s PARTITION           Give partition size(s) in blocks
       fdisk -v                     Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors[/i]

---

### Post by SEMW on 2008-05-16
> **mario-182 said:**
> These were my results :(
[i]mario-182@himynameismario:~$ sudo fdisk -1
[sudo] password for mario-182:
fdisk: invalid option -- 1

The 'l' in 'sudo fdisk -**l**' is a lowercase L (for **L**inux), not the numeral 'one'.

---

### Post by mario-182 on 2008-05-16
> **SEMW said:**
> The 'l' in 'sudo fdisk -**l**' is a lowercase L (for **L**inux), not the numeral 'one'.

My bad:
[i]Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xdffc408c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18701   150215751   83  Linux
/dev/sda2           18702       19457     6072570    5  Extended
/dev/sda5           18702       19457     6072538+  82  Linux swap / Solaris[/i] :confused::(

So I'm guessing there's no Vista.. Does this also mean I have wiped my documents, programs, etc.?
A quick answer would help, so I can move on and format my laptop :(
Thanks

---

### Post by adult swim on 2008-05-16
weird, you have the exact same fdisk output as the other guy.  either way unfortunately your windows is gone.  i have read about software that will recover files and such that you have formatted over with ext3.  i have never used these programs so i cant really give you much information.  maybe google recover ntfs partition?

---

### Post by mario-182 on 2008-05-16
Thanks nevertheless

Does anyone have any info on recovering my files? 
This is the first time I've really dealt with dual booting or installing other OS. Really I just though the Ubuntu CD would've been more helpful
There's a lot of Uni work, programs, photos, etc.. Just stuff I can't reproduce, so it'd be extremely helpful if I can somehow recover these before formatting :(

---

### Post by kesman on 2008-05-16
You should've read what the install CD told you while partitioning. There were options for manual partition, fully automatic which partitions the whole hard disk for linux, and a guided partition using the largest empty space available. At every point, it warns you about loss of data on the formatted partition.
For data recovery, it costs a lot of money to get even a tiny bit back :F
From the output of fdisk, your windows is definately gone. Insert your windows install media and reinstall it. Then if you want to try out ubuntu, insert the ubuntu cd WHILE in windows and select the wubi-windows-linux-installer-whatever to install ubuntu side by side with windows.

---

### Post by mario-182 on 2008-05-16
The CD did have the manual, guided, etc. options, but never did it say "this crappy OS will now erase your perfectly functional current OS and all your important documents"
Sorry but I'm in the worst mood right now..
Thing is, I actually wanted to use ***Unix***.. Now I'm just gonna restore it

To hell with Linux :D

EDIT: So it can be confirmed that there's no way of recovering my files without wasting more money, right?
Thanks

---

### Post by mario-182 on 2008-05-16
.. so I think it *actually* got worse..
I'm trying to restore factory settings on my laptop by tapping ALT+F10 at the Acer splash screen, but I've realised that it seems that it can't run the eRecovery application, if my drive got wiped.. :(
Holy.. Seriously, what the hell

---

### Post by mario-182 on 2008-05-16
> **mario-182 said:**
> .. so I think it *actually* got worse..
I'm trying to restore factory settings on my laptop by tapping ALT+F10 at the Acer splash screen, but I've realised that it seems that it can't run the eRecovery application, if my drive got wiped.. :(
Holy.. Seriously, what the hell
Please

---

### Post by nzadLithium on 2008-05-16
eRecovery seems to be a windows program? If it is then when you wiped your harddisk you will have deleted it. 

You might be able to recover any important documents with an ntfs data recovery program. maybe this one? [http://www.download.com/DiskPatch/3000-2086_4-10063613.html?part=dl-DiskPatch&subj=dl&tag=button](http://www.download.com/DiskPatch/3000-2086_4-10063613.html?part=dl-DiskPatch&subj=dl&tag=button)
i think this has to be run from a windows installation so you would have to take your harddisk out and put in another pc with windows installed. Then install that program on it and use it to recover files. If your confident you can do that then go for it. I take no responsibility for any damages.

If you dont feel confident to do that you could try looking for some sort of linux ntfs recovery program but i think it will be a difficult hunt and keep in mind the longer the computer is on the more data you are likely to lose (when your browsing web etc it will be sticking data onto your disk which could overwrite any data left over from the ntfs partition).

I actually fail to see how you can recover a deleted partition it seems if you repartition it, it would write over the whole disk? but these programs say they can recover though so maybe thats not what happens. Maybe someone who knows a little more about this than me could help out?

---

### Post by mario-182 on 2008-05-16
Thanks for the info, but I've pretty much given up on recovering my data..
On top of it all, I have a laptop, which would be extremely difficult to remove the HDD without causing more damage
All I want at the moment is to just format my laptop, but I can't even do that, since the Acer apps were deleted.. :(
I'm so lost. Guess I'll have to contact the re-seller and see what they can do, cos I don't think there's many other options

---

### Post by Joeb454 on 2008-05-16
You can still format it, though if you want Windows back on there, you will need a Windows Vista install disk :)

Also I know it's irrelevant now, but the option both yourself and the O.P were looking for was Guided (Use Largest Continuous Free Space). I'll admit that it can be a little confusing with the 2 Guided Options there.

---

### Post by bryncoles on 2008-05-16
@mario-182

if you use your computer, run it from the ubuntu cd. i know you havent had the best start with ubuntu, but putting the cd in the drive and booting up is called a 'live session', and it means that nothing is written to your drive (is that right, more experienced linux people?)

...and you might yet recover some data (but dont quote me on that). 

there is a linux program called testdisk (read and acquire here: [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)). its also in the ubuntu repositories, but i think you'd have to fiddle with some settings to get it there. 

you'll need an external hard drive at least as big as your laptops drive, to put the recovered data on. test disk says it can recover partitions, but ive only ever used it to recover a few photos from a digital camera, so im afraid i cant help you with using the program. read the info on the link i posted, and see if you want to try that (from the ubuntu live (boot) cd). 

sorry about your computer. hope it can be fixed.

---

### Post by mario-182 on 2008-05-16
Thanks a lot. I'll give that a try
Yeah I've got my 320gb external

If anyone can provide more help with TestDisk, it'd be appreciated
Thanks again

---

### Post by kesman on 2008-05-17
> **mario-182 said:**
> Thanks a lot. I'll give that a try
Yeah I've got my 320gb external

If anyone can provide more help with TestDisk, it'd be appreciated
Thanks again

[http://www.cgsecurity.org/wiki/TestDisk_Livecd](http://www.cgsecurity.org/wiki/TestDisk_Livecd)
I think this would be easies solution. You only download an .iso-file, burn it to a cd and boot with it in. It then starts up just like ubuntu liveCD did, but with testdisk and some other rescue applications this time.

---

### Post by nzadLithium on 2008-05-17
on the page kesman provided:
The knoppix link looks hopeful. I think you should download knoppix and burn to cd (follow links on that page) and then read the "hints about testdisk usage" on that page as well. Maybe print it out. 

Upon booting knoppix you need to find the terminal. You can then follow what it says on the page about "hints about testdisk usage"

I expect from reading that page you will have to find out what your harddisk is called. /dev/(something)
It gives you instructions how to find out in the section below "Identifying an HDD's Linux device"

Then you will have to run sudo -s
then type testdisk and hit enter. Go through what it says.

I hope this helps if you were having any trouble.

---

