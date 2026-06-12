---
title: "[SOLVED] Boot Help Needed. Triple Boot Setup"
date: 2008-05-01
forum: General Help
---

### Post by one4house on 2008-05-01
I am having a little problem with my boot settings.  FIrst I will go into the background story. I have an Acer Aspire 5920 that has the original HD in it with Windows Vista Home Premium.  I have hosed this install a couple of times, but have restored back to the stock 4 partitions that came on the drive when I bought it.  This part of the install I have no problems with.  Vista runs fine, but I am not able to boot directly into Vista. That is where the problems come in.

     For sick fun I decided that I wanted to load Mac OS X on my PC.  After a couple of failed attempts at partitioning my HD (remember, it is already broken into 4 partitions by Acer) I decided to get an external HD and HD docking station.

     With the help of these peices I was finally able to get OS X (Leopard) to install and run.  This was not enough and I broke that drive into 2 partitions and loaded OS X and Ubuntu. 

     I put the OS X on first because it allowed me to go into the Disk Utilities and partition it the way I wanted.  I broke the disk (The external one) into two 40 gig partitions and loaded OS X on partition 2.  After that I installed Ubuntu on partition one of that drive.

     My problem is that  GRUB wrote over the MBR of my Vista disk.  I am only able to chose between Vista and Ubuntu, in GRUB, if I have the external drive connected to my computer on boot.  Kinda takes the "portable" part out of my laptop.  What I am needing is a way to get it to where I can boot into Vista normally and still somehow get to Ubuntu when I have the external drive connected.

     Anyone have any ideas on how I might do this?  I am at a loss as of now.  I am not in a big hurry to figure it out.  I do know how to fix the MBR of the Vista install if it comes to that, but then I would lose access to one of my 3 operating systems.

---

### Post by one4house on 2008-05-01
Also, it has been a while since I have been on this forum.  If I am posting this topic in the wrong place would you let me know so I can move to the right area of the forum?  I would hate to get little or no response because I misplaced my thread.

---

### Post by deadABuser on 2008-05-01
How bout reinstall GRUB on the internal hardrive?

"A key feature of GRUB is that it can be installed without being attached to an operating system, although it needs a copy of a Linux image for such an installation. Working as a stand alone system it is virtually a mini system in its own right and able to boot all the installed major operating systems by a method known as Chain loading."

[http://www.troubleshooters.com/linux/grub/grub.htm]("http://www.troubleshooters.com/linux/grub/grub.htm") might help.

---

### Post by one4house on 2008-05-01
Thank you for the link. I am looking into that now.

---

### Post by one4house on 2008-05-01
bump

---

### Post by danwood76 on 2008-05-01
Are you able to boot from the USB on your laptop?
Eg, can you press a button at the start that allows yout to boot from HD, CD, Floppy, USB?

---

### Post by one4house on 2008-05-01
> **danwood76 said:**
> Are you able to boot from the USB on your laptop?
Eg, can you press a button at the start that allows yout to boot from HD, CD, Floppy, USB?

Yes, that is how I get into the OS X install now.  I have f12 set up on boot to allow me to choose what disc (CD, Flash Memory, Which HD) to start if need be.

There is a little more to this story now.  I threw in my Vista install cd and fixed the MBR of Vista.  I now want to know how to get GRUB onto the vista partition so that I can add an entry for the Linux in the boot options?  I tried throwing in the Ubuntu Live CD and going to terminal and doing:
Sudo grub
root (hd0,2) <--------This is the CD and Partition my Vista install is on
setup (hd0) <---------At this point it errors and says "Partition is unreachable" or something like that.

LOST!

---

### Post by danwood76 on 2008-05-01
You cant install grub to just the MBR and so you wont be able to stick it on your vista partition.
What you can do is install it to the external HD.

That way you will always boot vista by default, but if you want ubuntu or OSX you can press F12 and select it.
You can boot OSX from Grub btw, the same way you boot vista (chainloading)

---

### Post by one4house on 2008-05-01
> **danwood76 said:**
> You cant install grub to just the MBR and so you wont be able to stick it on your vista partition.
What you can do is install it to the external HD.

That way you will always boot vista by default, but if you want ubuntu or OSX you can press F12 and select it.
You can boot OSX from Grub btw, the same way you boot vista (chainloading)

Cool, sounds great.  How do I go about loading GRUB onto the external HD?  Right now when I hit F12 I can only load into Darwin.  It does not see the Ubuntu as being loaded on the disk.

---

### Post by one4house on 2008-05-01
bump

---

### Post by danwood76 on 2008-05-01
Well first boot into ubuntu, either from the hard disk or CD, it doesnt matter.

Then you need to find out which hard disk ubuntu is on, if you post the output of this I will try and talk you through the rest:

```

sudo fdisk -l

```

---

### Post by one4house on 2008-05-01
Thanks for helping.  PM sent.

---

### Post by -Zeus- on 2008-05-01
> **one4house said:**
> Thanks for helping.  PM sent.

Post is not equal to PM.  Please post it in the thread so others can benefit.  Also, your bumping frequency is excessive.  Bumping after 6 hours with no reply is OK; waiting only 1hr is not.

---

### Post by one4house on 2008-05-02
> **-Zeus- said:**
> Post is not equal to PM.  Please post it in the thread so others can benefit.  Also, your bumping frequency is excessive.  Bumping after 6 hours with no reply is OK; waiting only 1hr is not.

I will post in the thread when I do find a solution.  In a forum with as much traffic as this one, bumping after 1 hour means getting from the 4th page to the 1st page.  Are you a moderator? If not, then harass someone else my friend.

---

### Post by one4house on 2008-05-03
Have not heard back from the person who was going to help.  He is probably busy with something else.

Anyone know the basics of chain-loading 2 OS's?  He had mentioned that my OSX86 could be chainloaded with linux.  I have no idea what this is all about.  I will be booting into the Linux / OS X drive by f12 ing on boot and choosing the drive.  My drive extensions from f-disk are as follows:

THe fdisk list my 2 drives

sda <-----Vista
sdb <Linux and Mac

sda is listed 

sda1
sda2 (Actual Vista Patition)
sda3
sda4

partitions 1 and 4 are for acer's recovery tool. 3 is just a storage patition.

sdb is listed as

sdb1 Linux swap partition
sdb2 (it list this as unknown in linux) but it is Mac OS X
sdb3 Linux


Hope someone can help.

---

### Post by one4house on 2008-05-03
can a mod change the title of this to reflect new help needed?

---

### Post by DaddyX3 on 2008-05-03
I would simply install Start-Up Manager 
```
sudo apt-get install sum
```
and edit your boot options with that. It is much much easier and you have the option to completely bypass the GRUB menu all together or set it on a short timer and auto load your OS (your selection) after a few seconds or none at all.

---

### Post by one4house on 2008-05-03
Problem is that I can't get into my install of linux at the moment.  When I fixed the MBR of my vista partition it killed the GRUB link to Linux.  Right now when I hit f12 to tell my computer which disk to boot from, Linux does not come up as  an option. It goes straight to OS X when I choose the external disk.  

This might be fixed by  reinstalling Linux, but I do not want it to take over and load GRUB again.  Catch 22.  Loading Linux messed up my boot options in the first place.

---

### Post by danwood76 on 2008-05-04
I just had good fun with this, wrote an entire guide and managed to close firefox and loose it, its quite early.
Sorry I didnt reply earlier, I have been home for a visit and have been catching up with friends and family.

Ok so to start off boot the live CD up, lets install grub to the USB disk.

Once in the live CD open a terminal and type this command:
```

sudo grub

```
Next we have to make sure we know which partition grub is on (this will be your linux partition)
```

find /boot/grub/stage1

```
this should give you back something like this:
```

(hd1,2)

```
(This is my guess on the output based on the info above but your hard disk number may be different, if it is change the number in all the commands below otherwise it wont work)

Ok so now we know where grub is we have to first set the root to be that partition then install it to the drive.
So:
```

root (hd1,2)

```
Then install it:
```

setup (hd1)

```
it should dump some output like this:
```

Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/fat_stage1_5" exists... yes

```
and end with succeeded and then  done.
so thats done, we quite grub:
```

quit

```
Now your system will be able to boot back into ubuntu.
So restart and press F12 choose the USB disk and it should then load grub, select ubunut and we will go about setting up OSX in the grub bootloader.

so from a terminal type this command:
```

sudo gedit /boot/grub/menu.lst

```
My guess is you will need to add an entry like this on the bottom:
```

Title OS X
Root (hd1,0)
make active
chainloader +1

```
So scroll to the bottom of the file and paste the above.
Save the file and reboot to test it.

If you reboot and this doesnt load OSX post your menu.lst so I can check it.
There is another way of booting OSX which I have read a lot of people having success with.

---

### Post by one4house on 2008-05-04
Thanks for getting back with me.  I am quit busy today and tomorrow.  I will get back to you with my success as soon as I can.

---

### Post by one4house on 2008-05-05
I did everything you said to reinstall GRUB.  Everything went as you thought it would.  Then I went to restart and try to  get into Ubuntu, all I get after selecting Linux from the GRUB menu is ERROR 17: Cannot Mount Selected Partition.

Should I direct it to install GRUB on hd1,3 since that is the partition with linux on it?  This is just a guess.  I will continue to mess around and see what I can get. 

Odd thing I did figure out is that if I select Vista from the GRUB menu it loads into OS X.  It must just be loading into whatever OS it can find?

---

### Post by danwood76 on 2008-05-05
I think your menu.lst file is configured wrong.
This does prove that you can chainload OSX though which is good.

Can you post it?
Boot the live CD up and mount your linux partition, navigate to /boot/grub and post the menu.lst file thats in there.

hd1,2 is your linux partition, the counting starts from 0 so 2 is partition 3.

---

### Post by one4house on 2008-05-06
Sorry it took me so long.  I had a final project due for one of my classes.  Had to get that out of the way.

	
title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=80f2104e-fcd5-481a-b262-468c077dfe91 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=80f2104e-fcd5-481a-b262-468c077dfe91 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd1,2)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista/Longhorn (loader)
root		(hd0,1)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda4
title		Microsoft Windows XP Embedded
root		(hd0,3)
savedefault
makeactive
chainloader	+1

I see a couple of entries that I could change up.  Everything looks good as far as the lines that tell GRUB to load Linux.  I have no ide what is causing the mount problems.


EDIT:  After looking things over, I think that we need to change root of Ubuntu to be (hd0,2)

When we are trying to load into Linux, I do not think that it sees the HD that is in the laptop and it wants to consider the external drive hd0.  

The only problem is that I do not have permission to edit the menu.list file while I am booting from the live cd.  Is there a way around this problem?

---

### Post by one4house on 2008-05-07
Finally got it working.  When you boot from the external drive, it no longer sees the external drive as a secondary drive.  It only sees the external, so I had to change the menu.lst file to hd0,2 to get GRUB to see my Linux partition.  While I was there I removed the references to Vista and XP and edited to show a boot option for OS X86.  Now my menu.lst file looks like this:

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=80f2104e-fcd5-481a-b262-468c077dfe91 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=80f2104e-fcd5-481a-b262-468c077dfe91 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root





# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Mac OS X86
root		(hd0,1)
savedefault
makeactive
chainloader	+1



This took care of my problems with the hard drive.  I am now fully operational with all three operating systems.  I want to thank danwood76 and bodhi.zazen ([http://ubuntuforums.org/showthread.php?t=784068](http://ubuntuforums.org/showthread.php?t=784068)) who both gave me the pieces I needed to get everything set up.  Very much appreciated.

---

### Post by danwood76 on 2008-05-07
No problem, and well done.

Could you mark the thread as solved in the thread tools so that anyone searching the topic can get help on this subject?

regards,
Danny

---

### Post by one4house on 2008-05-07
I tried to mark it as solved, but it does not seem to be an option under my "Thread Tools".  Can a mod moark this one as solved, please?

Again, thanks for the help.

---

### Post by herger on 2008-05-07
Ciao. Thanks for the solution: I have a similar problem.
I have 2 hd's: the first with XP and Fedora and the 2nd (new) with Ubuntu.
When I finished installing Ubuntu, Fedora was not seen in the GRUB any more. I will try with Your solution.
By the way, could You please tell me how did You had MAC OS X running on Your Acer? I would really appreciate.
Thanks and regards

Herger

---

### Post by one4house on 2008-05-07
> **herger said:**
> 
By the way, could You please tell me how did You had MAC OS X running on Your Acer? I would really appreciate.
Thanks and regards

Herger

That is a whole other can of fun.  Do a search for hackint0sh or OS X86.  You will find all the info you need and much more.  If you are good at torrents, search for leo4all.  This should be enough to get you on your way.

---

