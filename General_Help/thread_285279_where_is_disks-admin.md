---
title: "where is disks-admin?"
date: 2006-10-26
forum: General Help
---

### Post by lime4x4 on 2006-10-26
in dapper i had a disk manager under system-administration in edgy it's not there.Anyway to add this back? Found it use full in mounting my other hard drives.For some reason edgy only mounted my main drive and that's it

---

### Post by egd on 2006-10-26
I'm totally amazed that some dumb #@$%^%$^ thought it a good idea to remove disk-admin from Edgy.  Given Ubuntu is trying to position itself for the Desktop wtf were ppl thinking?  Gaining mindshare on the Desktop is about ease of use and tools to get things done.  disks-admin may no longer be under development but it fulfills a dire need in Ubuntu - visibility of physical hard drives and figuring out which drive is what device in Linux - crucial for someone with multiple hard drives transitioning from Windows and now no doubt left wondering where the hell their data is, hmmm, let me see, which one of the eight hard drives could it possibly be...oh, wait, perhaps it's the external raid box, but damn, I have no idea which device that is and I definitely don't want it mounted or powered up every time I use my pc.

eliminating disks-admin without providing a viable alternative was a really dumbass decision.

---

### Post by yopnono on 2006-10-26
Build it from source maybe, or use the terminal.

---

### Post by PriceChild on 2006-10-26
I've been using gparted lately to figure things out... i agree :)

*threads merged*

---

### Post by lime4x4 on 2006-10-26
that's why i liked dapper then i thought edgy would be even better it is in alot of ways but i few nifty apps are missing..Can anyone point me in the directiion of building the disk manager app from source?

---

### Post by yopnono on 2006-10-26
[http://packages.ubuntu.com/dapper/source/gnome-system-tools](http://packages.ubuntu.com/dapper/source/gnome-system-tools)

---

### Post by PriceChild on 2006-10-26
> **yopnono said:**
> [http://packages.ubuntu.com/dapper/source/gnome-system-tools](http://packages.ubuntu.com/dapper/source/gnome-system-tools)But there's also an edgy version of this package which i have installed.

---

### Post by lime4x4 on 2006-10-26
already have the edgy version installed but it's not there either

---

### Post by lime4x4 on 2006-10-26
installed pysdm and all is well with the world at the moment...lol

---

### Post by egd on 2006-10-27
> **lime4x4 said:**
> installed pysdm and all is well with the world at the moment...lol

disks-admin allowed you to initiate a browse of a drive/partition you have just mounted.  pysdm doesn't.  Gnome needs a decent tray-based tool to allow you to dynamically mount/unmount devices and initiate an "open at this mountpoint" nautilus or other file manager session at will.

For anyone wondering where/how to find and install pysdm, goto ubuntuguide.org, follow the instructions under adding additional repositories, then run System/Administration/Synaptic Package Manager, search for pysdm and install it.  It will appear as Storage Device Manager under System/Administration.

There you go, nice and simple - just what the Dr. ordered to aid people looking to move from Windows.  I am of course being sarcastic.  Imagine a Windows user with a first time install of Linux trying to figure this out without instructions.  Absolutely sh1ts me.

---

### Post by yopnono on 2006-10-28
> **lime4x4 said:**
> installed pysdm and all is well with the world at the moment...lol

Don't think pysdm support scsi drives.

---

### Post by jgeewax on 2006-10-29
I must agree with everyone on this. 

Was there a good reason to remove this great app? It seems like it was a terrible idea. I guess everyone makes mistakes.... I hope they bring this tool back.. (in some form atleast.)

---

### Post by jgeewax on 2006-10-29
I guess gparted is not as friendly as the disks-admin application, but it does work:

sudo aptitude install gparted

:)

---

### Post by lime4x4 on 2006-10-29
yeap i used gparted to format the disks then used pysdm to mount them

---

### Post by yopnono on 2006-10-29
You can use gparted to mount and unmound drives aswell.

---

### Post by IanVaughan on 2006-11-22
There are many ppl wondering (including me) where it went! 

As I posted in [an other thread]("http://www.ubuntuforums.org/showthread.php?p=1791679")), is disks-admin not in a Dapper repository (although I cant find it).

So someone removed it from a Dapper Repository, and then by default it did not get into Edgy Repository? (guessing)

So who is this wise person?
Any why was it removed?

And I totally agree with edg:-
> **egd said:**
> I'm totally amazed that some dumb #@$%^%$^ thought it a good idea to remove disk-admin from Edgy.  Given Ubuntu is trying to position itself for the Desktop wtf were ppl thinking?
...
eliminating disks-admin without providing a viable alternative was a really dumbass decision.

---

### Post by yopnono on 2006-11-22
True that is crap that it was removed, but still, you can use GParted to mount and format etc,etc.

---

### Post by nrayever on 2006-11-23
hi everyone:

disks-admin was a great app. maybe with some bugs or what ever. but it let me format a usb flash memory that had some issues! it was full of no files!! :confused: :confused: 
believe it or not!! if i tried to move any file to the memory, an error window appears telling me that the memory was full. so disks-admin let me format the memory. this kind of apps are a most & need to have!!

we should make a request to developers to add it again in feisty fawn and on the next releases and that it should not be removed of ubuntu never!! a good app that i'm really missing. :( :( 

why developers sometimes remove great and usefull apps as disks-admin?? ](*,) ](*,)  can someone explain me??

nrayever

---

### Post by IanVaughan on 2006-11-23
I agree with previous comments on GParted, it is quite good.

But, firstly, neither disks-admin or GParted come in the standard Edgy distribution,  whereas disks-admin was part of Dapper.

So at least out-of-the-box ppl had something to use.

There needs to be a GUI shipped with the distro to make it complete and to compete!

Secondly, its one thing to remove something from the distro, but to remove it completely from all repositories as well is a separate issue.
Perhaps there is a very big problem (crash/security) with disks-admin, and thats why it was removed? That has to be the only reason?

Any devs reading? Care to comment?

---

### Post by The Grum on 2006-11-23
I agree completely. Disks-admin was great when using the Dapper live cd to grab stuff from unbootable Windows systems. 

Found the reason, though:

[https://blueprints.launchpad.net/distros/ubuntu/+source/gnome-system-tools/+bug/61728]("https://blueprints.launchpad.net/distros/ubuntu/+source/gnome-system-tools/+bug/61728")

---

### Post by laachlaan on 2006-11-24
Did it not occur to the person that removed disk-manager that the live CD is also a rescue tool?

My upgrade to edgy went sideways (boot freezes at kjournald starting), and I wanted to use the live CD to boot up and figure out what went wrong. It was insult added to injury that the disk-manager was removed. Now I'll have to dig out an old dapper CD, or perhaps resort to tomsrtbt to fix things.

---

### Post by ShadowVlican on 2006-11-25
if these are the kinds of decisions made to ubuntu releases, i don't faith that it's going to succeed in the desktop market

MAKE IT EASY FOR PEOPLE... i shouldn't have to get into forums to figure out:

where is my secondary BLANK hard drive
how do i partition, format, mount it?

i had to search this JUST because GParted (A GREAT APPLICATION I MUST SAY, coming from a WINDOWS USER, YOUR TARGET AUDIENCE.) wasn't included in Edgy

so i followed this code provided from a fellow user
```
sudo aptitude install gparted
```

bingo! installed! appeared by itself in "System>Administration>GNOME Partition Editor" THAT is the way that installation should go (heck, you can rename it to "GNOME Hard Drive Manager" and even novices will have an idea what it's about, since they may not know what PARTITION means, but surely anyone purchasing a computer has heard of HARD DRIVE)

---

### Post by joplass on 2006-11-29
gparted could not mount my second drive.  It can see it but does not provide the option to mount.  unmount is there but can't be used either ](*,) yiks

---

### Post by mgmiller on 2006-11-29
> believe it or not!! if i tried to move any file to the memory, an error window appears telling me that the memory was full.  so disks-admin let me format the memory.

What probably happened is that you just tried deleting the files from the USB drive.  This puts them in a trash file on the usb drive.  You can't see them any more, but they are still there taking up space.  To get rid of them totally plug in the USB drive and hit ctrl-h to show hidden files and then delete the file called .Trash.

To avoid this problem in the future, instead of just deleting files from the USB drive, which just moves them to this .Trash file, you want to erase them completely.  Got to System>Preferences>File Management and click the behavior tab.  Towards the bottom will be a section labeled **Trash** Just put a check in the box that says "include a delete command that bypasses trash".

Now when you right click a file or directory, you will have 2 delete choices, one of which will erase the file without putting it in the trash bin.

---

### Post by nrayever on 2006-11-30
> **mgmiller said:**
> What probably happened is that you just tried deleting the files from the USB drive.  This puts them in a trash file on the usb drive.  You can't see them any more, but they are still there taking up space.  To get rid of them totally plug in the USB drive and hit ctrl-h to show hidden files and then delete the file called .Trash.

To avoid this problem in the future, instead of just deleting files from the USB drive, which just moves them to this .Trash file, you want to erase them completely.  Got to System>Preferences>File Management and click the behavior tab.  Towards the bottom will be a section labeled **Trash** Just put a check in the box that says "include a delete command that bypasses trash".

Now when you right click a file or directory, you will have 2 delete choices, one of which will erase the file without putting it in the trash bin.

mgmiller:

thanks for the advice. but as a song says: "i'm not stupid as you think!!" (island groove - not stupid). i had checked the ~/.trash directory. this memory is of a friend of mine, she uses ubuntu too. and i have check the memory on my laptop, not on her computer. the trash was empty. i don't know if it was like a bug or something. or maybe it was just full of 1 bits. but it was weird. so that's why i was looking for the great disks-admin and it had disappeared in edgy eft. :( :( 

then i mount it on her computer, that still has dapper, and i have used disks-admin to clean it! and it worked again.

again thanks for the advice mgmiller. maybe i will use it with my usb memory. but the case i had wrote it's completely different.

nrayever

---

### Post by muadda on 2006-12-22
> **nrayever said:**
> hi everyone:

disks-admin was a great app. maybe with some bugs or what ever. but it let me format a usb flash memory that had some issues! it was full of no files!! :confused: :confused: 
believe it or not!! if i tried to move any file to the memory, an error window appears telling me that the memory was full. so disks-admin let me format the memory. this kind of apps are a most & need to have!!

nrayever

Your USB key has no issue. It is an Ubuntu bug that cause an USB key to be unusable after some use. See:
[https://launchpad.net/distros/ubuntu/+source/nautilus/+bug/12893](https://launchpad.net/distros/ubuntu/+source/nautilus/+bug/12893)

---

### Post by nrayever on 2006-12-29
> **muadda said:**
> Your USB key has no issue. It is an Ubuntu bug that cause an USB key to be unusable after some use. See:
[https://launchpad.net/distros/ubuntu/+source/nautilus/+bug/12893](https://launchpad.net/distros/ubuntu/+source/nautilus/+bug/12893)

hi muadda:

again, as i said on my earlier post (not the first). i had checked that the usb memory was really empty and i mean that i had erased/removed/deleted (using shift + supr to delete the files from the memory and not just to store them in a hidden folder know as .Trash-your-user) as root to all the hidden directories and files. even after that operation the memory was full of nothing. so using disks-admin was useful to formatting it.

i hope that now anybody understands what i'm saying. :D :D 

nrayever

---

### Post by infodroid on 2007-01-17
> **lime4x4 said:**
> in dapper i had a disk manager under system-administration in edgy it's not there.Anyway to add this back? Found it use full in mounting my other hard drives.For some reason edgy only mounted my main drive and that's it

I found another program that has similar features called **linHDD**. Check out some screenshots ([link]("http://www.pcbypaul.com/software/linHDD.html")) on its web site.

```
apt-get install linhdd
```

Unfortunately I can't do anything useful with it as root at the moment, since I get the following errors:

```
user@computer:~$ gksudo linHDD 
Traceback (most recent call last):
  File "/usr/bin/linHDD", line 534, in ?
    main()
  File "/usr/bin/linHDD", line 529, in main
    DriveWin()
  File "/usr/bin/linHDD", line 387, in __init__
    self.frac = float(self.perc.rstrip("%")) / 100
ValueError: empty string for float()
```

---

### Post by Curdsy on 2007-02-27
Thanks to all who posted to this thread - I agree 100% that it was foolish to remove disks-admin, especially as it is still listed in the official Ubuntu guide as the means to view and mount Windows partitions.  After wasting half a day trying to find/install disks-admin I found this thread on the forum and installed gparted which it seems to do the job. Thanks for all the help.

---

### Post by coolcalt on 2007-03-05
I'll claim the spot of the new to ubuntu user.

I first installed dapper last wednesday.  I learned that I should prolly have installed Edgy.  So I installed it again.   I am an experianced windows user, I have 8 hardrives crammed into a mid tower.  I've installed linux before so I disconnected all my drives except the master I wanted to hold linux.  

Add me to the list of people led astray by the help system, which is very good.  

I'm just started getting to know GParted.  

Hopefully it'll be able to let me play some of my music now.  I'm on day 3 of no windows!!  

I found the installer super easy.  I got my girlfriend to do one of the installs, she works as a tech for AOL, and she was impressed, please no comments on that topic, lol.  (insert sarcasm as desired)

We should remember that this is the pointy end of the ubuntu stick.  It sometimes breaks, and the guys are obviously aware of it now, and starting to fix it.

---

