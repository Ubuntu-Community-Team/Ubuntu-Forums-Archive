---
title: "Second HD with /home missing after upgrade"
date: 2007-02-14
forum: General Help
---

### Post by quincunx on 2007-02-14
I have two drives on my system a 20Gig and 40Gig.  I dedicated my 40Gig to my /home directory, but after performing one of the upgrades two days ago, it appears to be missing.

I saw the update icon appear on my desktop, and did the usual routine for installing.  After completing it said I needed to reboot to complete the changes.  After rebooting I attempted to login and got an error message saying something to the effect of:

Your directory is listed as:
'/home/me'
but does not appear to exist.
(and goes on about logging in with a failsafe terminal)

I am able to login with the failsafe terminal, and typing "dh -f" does not show me my second drive.  Now, the /home directory wasn't always on the 40Gig; a friend moved it there for me a month or so ago.  So I'm thinking there's some file somewhere that needs to be modified to let the system know it exists, or to mount on boot, or something.

Any and all help is greatly appreciated!

---

### Post by Tuna-Fish on 2007-02-14
that file is called /etc/fstab. there is some command-line util that looks the right settings for you but i quite cannot remebmer its name.

---

### Post by quincunx on 2007-02-14
> **Tuna-Fish said:**
> that file is called /etc/fstab. there is some command-line util that looks the right settings for you but i quite cannot remebmer its name.
Anyone know the name of this utility, or what I would do with the utility to get my system to see my second drive?  I would imagine there might be some troubleshooting steps involved before using this said utility, no?

---

### Post by Niamor on 2007-02-14
A quick fix would be to type in a terminal sudo mount /dev/hda* /home (/dev/hda* being your 40g partition, you can see it with sudo fdisk -l)

The proper fix would be to write this in /etc/fstab but I'm not too sure about the way to write it.

---

### Post by Keith Hedger on 2007-02-14
why not just just login via the failsafe terminal create the /home/me directory reboot to get back a desktop and look at your /etc/fstab file (I had a similar problem after an upgrade and if I remember rightly the entries in fstab had been changed from /dev/hdaX etc to uid numbers which didnt work)

you can mount the missing HD manually and either copy your old home dir back or get your mate to tell you what he did and get him to redo/undo it

---

### Post by quincunx on 2007-02-14
> **Keith Hedger said:**
> why not just just login via the failsafe terminal create the /home/me directory reboot to get back a desktop and look at your /etc/fstab file (I had a similar problem after an upgrade and if I remember rightly the entries in fstab had been changed from /dev/hdaX etc to uid numbers which didnt work)

you can mount the missing HD manually and either copy your old home dir back or get your mate to tell you what he did and get him to redo/undo it

I know I'm able to look at the fstab in the failsafe terminal, I don't know how to interpret the contents, but it didn't seem like my 40G was listed.  Since I can do that with the failsafe console, I don't see the need for creating a "/home/me" directory to get a desktop.  Is there something the desktop will give me that the console won't in terms of locating my HD?

**How would I mount the missing HD?**  Copying my home directory back to my 20G is impossible unless I want to delete everything in it first, then live with little space for my data.  

I'm trying to get a hold of my friend, but he doesn't have a phone, and I don't know when I'll be able to talk to him next.  His changes have had no negative impact, until after I performed the upgrade; even then, I'm not absolutely sure that his changes are the problem here.

If it was working before the upgrade, obviously the upgrade didn't handle itself well.  Which is something I've experienced twice with Ubuntu now.  The first one was upgrading from Badger to Drake and I lost all my settings, even some functionality.  It was while repairing that when my friend noticed the low disk space and that my 40G was untouched.  He fixed most of what the "upgrade" broke and moved my /home directory to the 40G and everything was great... until the (kernel?) upgrade a couple of days ago.

---

### Post by quincunx on 2007-02-14
> **Niamor said:**
> A quick fix would be to type in a terminal sudo mount /dev/hda* /home (/dev/hda* being your 40g partition, you can see it with sudo fdisk -l)

The proper fix would be to write this in /etc/fstab but I'm not too sure about the way to write it.

I was able to see both drives by typing "sudo fdisk -l /dev/hda" and 
again, using "/dev/hdb".  When I tried:

sudo mount /dev/hdb1 /home
I got
mount: you must specify the filesystem type

After using "sudo mount", I saw that hda1 was of type ext3.  I didn't 
see hdb listed.  So I used:

sudo mount -t ext3 /dev/hdb1 /home
and got
mount: special device /dev/hdb1/ does not exist

Does anyone know what to do from here?  I was happy to see my 40G drive 
is okay, but did my home directory get blow away?

---

### Post by Keith Hedger on 2007-02-15
I suggested you get a desktop env as you didnt gice the impression you was ok with a terminal but if u are thats fine -sorry

post your /etc/fstab file and also the output of mount (just type mount at a console) as its difficult to see what the problem with the mounting is.

No your old home dir has probably not been blown away but u wont have access to it untill the disk its on can be mounted

---

### Post by quincunx on 2007-02-15
> **Keith Hedger said:**
> post your /etc/fstab file and also the output of 
mount (just type mount at a console) as its difficult to see what the 
problem with the mounting is.


Here's my fstab, fdisk, and mount info for some reason the preview of this post is "centered", but I don't know how to fix that while using lynx-nano to make posts ;) :


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb1       /home           ext3    defaults        0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

me@abrahadabra:/$ sudo fdisk -l /dev/hda

Disk /dev/hda: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2330    18715693+  83  Linux
/dev/hda2            2331        2434      835380    5  Extended
/dev/hda5            2331        2434      835348+  82  Linux swap / Solaris
me@abrahadabra:/$ sudo fdisk -l /dev/hdb

Disk /dev/hdb: 40.0 GB, 40020664320 bytes
16 heads, 63 sectors/track, 77545 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1       77545    39082648+  83  Linux
me@abrahadabra:/$ sudo mount
/dev/hda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
/sys on /sys type sysfs (rw)
varrun on /var/run type tmpfs (rw)
varlock on /var/lock type tmpfs (rw)
udev on /dev type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
devshm on /dev/shm type tmpfs (rw)

---

### Post by Keith Hedger on 2007-02-16
well the only thing i can see that might be wrong is line 6 in your fstab :
"dev/hdb1 /home ext3 defaults 0 1 i think should read :
/dev/hdb1 /home/YOURUSERNAME ext3 defaults 0 1

where obviously replace YOURUSERNAME with your username, as your home folder is usually a sub folder of /home, so change your fstab and then try:

sudo mkdir /home/YOURUSERNAME
sudo chown YOURUSERNAME /home/YOURUSERNAME

you can then try mounting hdb1 manually with sudo mount -a if hdb1 mounts and evrything seems ok try a rebbot and see what happens

---

### Post by llamakc on 2007-02-16
> **Keith Hedger said:**
> well the only thing i can see that might be wrong is line 6 in your fstab :
"dev/hdb1 /home ext3 defaults 0 1 i think should read :
/dev/hdb1 /home/YOURUSERNAME ext3 defaults 0 1

where obviously replace YOURUSERNAME with your username, as your home folder is usually a sub folder of /home, so change your fstab and then try:

sudo mkdir /home/YOURUSERNAME
sudo chown YOURUSERNAME /home/YOURUSERNAME

you can then try mounting hdb1 manually with sudo mount -a if hdb1 mounts and evrything seems ok try a rebbot and see what happens


This is incorrect unless the OP originally had /dev/hdb1 mounting at /home/USERNAME. Most folks who keep separate /home partitions are mounting /home  and not their user directory underneath.

When mounting from the commandline, are you "in" the /home/ directory?

In your original post, you mentioned "updates". You mean the updates through Synaptic/Adept/apt-get, correct? And not a distro-release update from Dapper to Edgy, or anything of that sort?

---

### Post by Keith Hedger on 2007-02-16
wasnt aware of that :( 
yes when i tried out a upgrade to edgey my fstab entries got changed to UIDs and nothing got mounted I sorted it out among other problems and then when back to dapper as edgy was pretty poor at the time.

the other problem i had was the ownership of my home folder got changed and untill i changed it back couldnt login maybe thats the problem is if not im afraid i cant help sorry:( :(

---

### Post by quincunx on 2007-02-16
> **llamakc said:**
> This is incorrect unless the OP originally had /dev/hdb1 mounting at /home/USERNAME. Most folks who keep separate /home partitions are mounting /home  and not their user directory underneath.

When mounting from the commandline, are you "in" the /home/ directory?

In your original post, you mentioned "updates". You mean the updates through Synaptic/Adept/apt-get, correct? And not a distro-release update from Dapper to Edgy, or anything of that sort?

The update was through the auto-notification (orange icon in the "task tray"), which I think uses Synaptic.  And you are correct, this isn't a distro-release update, although, I believe it was a kernel update of sorts.  It did require me to reboot to complete the upgrade, after that I could not login.

When I login using the failsafe terminal, I do notice a directory called "home", but I don't know if this is created temporarily since the original one couldn't be found.  That does seem to be the case as there were a few other directories under "/home" that don't appear in the failsafe login.

---

### Post by Keith Hedger on 2007-02-16
have u tried mounting hdb1 manually to somwhere place other than /home and if so does it mount rw or read only? if its mounting read only it may need repair silly question i know but have u run fsck on hdb1?

---

### Post by quincunx on 2007-02-17
> **Keith Hedger said:**
> have u tried mounting hdb1 manually to somwhere place other than /home and if so does it mount rw or read only? if its mounting read only it may need repair silly question i know but have u run fsck on hdb1?

Yesterday when I would type "sudo mount -t ext3 /dev/hdb1 /home" I get:

mount: special device /dev/hdb1 does not exist
Today I got:

me@abrahadabra:/$ sudo mount -t ext3 /dev/hdb1 /home
mount: /dev/hdb1 already mounted or /home busy

Here's what I get running fsck:

me@abrahadabra:/$ sudo fsck -V
fsck 1.38 (30-Jun-2005)
Checking all file systems.
[/sbin/fsck.ext3 (1) -- /] fsck.ext3 /dev/hda1 
e2fsck 1.38 (30-Jun-2005)
/dev/hda1 is mounted.  

WARNING!!!  Running e2fsck on a mounted filesystem may cause
SEVERE filesystem damage.

Do you really want to continue (y/n)? no

check aborted.
[/sbin/fsck.ext3 (1) -- /home] fsck.ext3 /dev/hdb1 
e2fsck 1.38 (30-Jun-2005)
/home: clean, 14394/4889248 files, 8542872/9770662 blocks


I did "ls /dev/hdb1" and it did find the file.  So it's there and not 
there for some reason.

---

### Post by llamakc on 2007-02-17
Try mounting it somewhere else.

sudo mkdir /mnt/hdb1

sudo mount -t ext3 /dev/hdb1 /mnt/hdb1

---

### Post by Keith Hedger on 2007-02-18
try fsck /dev/hdb1 (when hdb1 is not mounted!) to just check hdb1 otherwise fsck will try and check all drives (not a good idea on mounted systems) hence the warning u got.

stilll sounds to me like an ownership/permisuins problem with /home.

---

### Post by quincunx on 2007-02-18
> **Keith Hedger said:**
> try fsck /dev/hdb1 (when hdb1 is not mounted!) to just check hdb1 otherwise fsck will try and check all drives (not a good idea on mounted systems) hence the warning u got.

stilll sounds to me like an ownership/permisuins problem with /home.

Okay, here's what I got using fsck on just /dev/hdb1.  Big surprise, 
same results.  Below that is where I mounted to somewhere other than 
/home.  Same result there as before.

me@abrahadabra:/$ sudo fsck /dev/hdb1
Password:
fsck 1.38 (30-Jun-2005)
e2fsck 1.38 (30-Jun-2005)
/home: clean, 14394/4889248 files, 8542872/9770662 blocks
me@abrahadabra:/$ sudo mkdir /test
me@abrahadabra:/$ sudo mount -t ext3 /dev/hdb1 /test
mount: /dev/hdb1 already mounted or /test busy
me@abrahadabra:/$ 

I think I'm done with Ubuntu.  I've used it a little over a year, and 
while some of it has been great, this really sucks.  An update should 
never end this drastic.  I haven't been able to use my computer for two 
weeks now (other than Lynx).  In all the years that I had used Windows I 
never had anything this bad happen.  It seems like I can't get to my 
data, and the one person helping me likes to assume that this is a 
permissions issue (like the one he had) rather than using 
troubleshooting techniques to find out what is really going on.  I mean, 
I am thankful that someone has been showing me what commands to type to 
get the info.  I had just expected that a Linux expert would have chimed 
in by now and given me a few steps toward actually solving this.

Where are the expert Linux users for Ubuntu?

---

### Post by llamakc on 2007-02-18
Are you offering a bounty to fix your problem? Hired help is easy to find.

Why don't you use a LiveCD and see if you can mount the drive that way?

"mount: /dev/hdb1 already mounted or /test busy"

--that line? That means you may already have mounted the disk. Do this:

`umount /dev/hdb1` and see if you get something like:

umount: it seems /dev/hdb1 is mounted multiple times

---

### Post by quincunx on 2007-02-18
> **llamakc said:**
> Are you offering a bounty to fix your problem? Hired help is easy to find.

Why don't you use a LiveCD and see if you can mount the drive that way?

"mount: /dev/hdb1 already mounted or /test busy"

--that line? That means you may already have mounted the disk. Do this:

`umount /dev/hdb1` and see if you get something like:

umount: it seems /dev/hdb1 is mounted multiple times


Here's what I get with umount:
me@abrahadabra:/$ sudo umount /dev/hdb1
umount: /dev/hdb1: not mounted

---

### Post by llamakc on 2007-02-18
Okay, now try with a LiveCD. See if you can locate your data.

---

### Post by quincunx on 2007-02-18
> **llamakc said:**
> Okay, now try with a LiveCD. See if you can locate your data.

What program would I use to burn to a cd?

Since the error message says "mounted OR busy", what would be the cause 
of "/home" being busy?

me@abrahadabra:/$ sudo mount
/dev/hda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
/sys on /sys type sysfs (rw)
varrun on /var/run type tmpfs (rw)
varlock on /var/lock type tmpfs (rw)
udev on /dev type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
devshm on /dev/shm type tmpfs (rw)
me@abrahadabra:/$ sudo mount -t ext3 /dev/hdb1 /home
mount: /dev/hdb1 already mounted or /home busy
me@abrahadabra:/$ sudo umount /dev/hdb1
umount: /dev/hdb1: not mounted

---

### Post by llamakc on 2007-02-18
Use the CD you installed with.

---

### Post by quincunx on 2007-02-18
> **llamakc said:**
> Use the CD you installed with.

I don't think I have the CD anymore.  I'm pretty sure I lent it to someone last year.
I do have some other distro's that I downloaded before I found Ubuntu, maybe I'll see if one of those is "Live".

---

### Post by llamakc on 2007-02-18
Good luck with your data.

---

### Post by quincunx on 2007-02-18
> **llamakc said:**
> Good luck with your data.


You don't know a command-line program for burning a CD?

Or where I could find out which one to use?

---

### Post by llamakc on 2007-02-19
Are you familiar with searching in Synaptic or on the commandline with apt-get? There are plenty of programs. I use "cdrecord" from the command line, but the easiest way would be to probably search the wiki at ubuntu.com.

[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

---

### Post by quincunx on 2007-02-19
> **llamakc said:**
> Are you familiar with searching in Synaptic or on the commandline with apt-get? There are plenty of programs. I use "cdrecord" from the command line, but the easiest way would be to probably search the wiki at ubuntu.com.

[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

The URL you gave me doesn't describe how to burn an image using the 
command line.  I tried looking at cdrecord, but the help didn't make 
much sense to me.  I saw where options for the device are.  I'm 
assuming it would start with "cdrecord (option) /cdrom", but I couldn't 
see where a filename would go.  What would be required for buring an ISO image to my CD?

---

### Post by llamakc on 2007-02-19
> **quincunx said:**
> The URL you gave me doesn't describe how to burn an image using the 
command line.  I tried looking at cdrecord, but the help didn't make 
much sense to me.  I saw where options for the device are.  I'm 
assuming it would start with "cdrecord (option) /cdrom", but I couldn't 
see where a filename would go.  What would be required for buring an ISO image to my CD?

It is in the man page for 'cdrecord'. Googling for "how to use cdrecord burn iso" would lead you to many pages that explain this.

Type:

sudo cdrecord dev=/dev/hdX -data /path/to/nameof.iso

where "/dev/hdX" represents your burner.

---

### Post by quincunx on 2007-02-20
> **llamakc said:**
> It is in the man page for 'cdrecord'. Googling for "how to use cdrecord burn iso" would lead you to many pages that explain this.

Type:

sudo cdrecord dev=/dev/hdX -data /path/to/nameof.iso

where "/dev/hdX" represents your burner.

Google is being Lynx unfriendly, so I can't search for anything there.  
If anyone knows of a good text-based-browser-friendly search site, 
please let me know.

Here's what I get when I use cdrecord:

me@abrahadabra:/$ sudo cdrecord dev=/dev/hdc -data 
/ubuntu-6.10-desktop-i386.iso 
cdrecord: No write mode specified.
cdrecord: Asuming -tao mode.
cdrecord: Future versions of cdrecord may have different drive dependent defaults.
cdrecord: Continuing in 5 seconds...
Cdrecord-Clone 2.01.01a01 (i686-pc-linux-gnu) Copyright (C) 1995-2004 Joerg Schilling
NOTE: this version of cdrecord is an inofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.

cdrecord: Warning: Running on Linux-2.6.19.1-rt15
cdrecord: There are unsettled issues with Linux-2.5 and newer.
cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
scsidev: '/dev/hdc'
devname: '/dev/hdc'
scsibus: -2 target: -2 lun: -2
Warning: Open by 'devname' is unintentional and not supported.
Linux sg driver version: 3.5.27
Error: Cannot gain SYS_RAWIO capability.Is cdrecord installed SUID root?
: Operation not permitted
Using libscg version 'debian-0.8debian2'.
cdrecord: Warning: using inofficial version of libscg (debian-0.8debian2 '@(#)scsitransp.c      1.91 04/06/17 Copyright 1988,1995,2000-2004 J. Schilling').
Device type    : Removable CD-ROM
Version        : 0
Response Format: 1
Vendor_info    : 'ARTEC   '
Identifikation : 'WRR-4848        '
Revision       : '1.00'
Device seems to be: Generic mmc CD-RW.
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-2 SWABAUDIO BURNFREE FORCESPEED 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R96R
Error: Cannot gain SYS_RAWIO capability.Is cdrecord installed SUID root?
: Operation not permitted
Starting to write CD/DVD at speed 48 in real TAO mode for single session.
Last chance to quit, starting real write    0 seconds. Operation starts.
Turning BURN-Free off
cdrecord: Success. write_g1: scsi sendcmd: no error
CDB:  2A 00 00 00 41 83 00 00 1F 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: F0 00 05 00 00 41 99 0C 00 00 00 00 10 02 00 00
Sense Key: 0x5 Illegal Request, Segment 0
Sense Code: 0x10 Qual 0x02 (id crc or ecc error) [No matching qualifier] Fru 0x0
Sense flags: Blk 16793 (valid) 
cmd finished after 0.032s timeout 40s
write track data: error after 34347008 bytes
cdrecord: A write error occured.
cdrecord: Please properly read the error message above.


I'm not sure which of the errors it is referring to, it does ask if it's 
been installed with a root ID.  Is there a way to re-install it with the 
right privs, or can I just change permissions somewhere?

---

### Post by quincunx on 2007-02-20
Here's something else I've found.  I don't know if this is missing for 
the same reasons my drive seems to be?



me@abrahadabra:/$ sudo cdrecord -scanbus
Cdrecord-Clone 2.01.01a01 (i686-pc-linux-gnu) Copyright (C) 1995-2004 
Joerg Schilling
NOTE: this version of cdrecord is an inofficial (modified) release of 
cdrecord
      and thus may have bugs that are not present in the original 
version.
      Please send bug reports and support requests to 
<cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this 
version.

cdrecord: Warning: Running on Linux-2.6.19.1-rt15
cdrecord: There are unsettled issues with Linux-2.5 and newer.
cdrecord: If you have unexpected problems, please try Linux-2.4 or 
Solaris.
cdrecord: No such file or directory. Cannot open '/dev/pg*'. Cannot open 
SCSI driver.
cdrecord: For possible targets try 'cdrecord -scanbus'.
cdrecord: For possible transport specifiers try 'cdrecord dev=help'.
cdrecord: 
cdrecord: For more information, install the cdrtools-doc
cdrecord: package and read /usr/share/doc/cdrecord/README.ATAPI.setup .

---

### Post by quincunx on 2007-02-21
So, it appears that after my upgrade I have:

1. Lost one drive (appears to be not mounted, but system claims that it is)
2. Lost write access to my CDROM (it appears to write something to the disk, but fails with a message about cdrecord being installed as root).
3. Lost my /home directory (which is on the drive mentioned in #1), so I can only login with the failsafe terminal

Using the failsafe terminal, I have to browse the web with Lynx and I am not able to use Google (says browser made a bad request).

Am I totally screwed at this point?  Is there anything else that I can try to see if I can get my system working again?

---

### Post by quincunx on 2007-02-21
I was able to get a li

---

### Post by quincunx on 2007-02-21
I got a live CD and was able to mount my old /home directory!  Yea!  I 
couldn't do much else with the live CD after that, giving me errors 
about the /home dir.

So how do I get that to happen when logging in to my HD?  Is there a way 
to use the CD burner with the live CD?

---

### Post by llamakc on 2007-02-22
> **quincunx said:**
> I got a live CD and was able to mount my old /home directory!  Yea!  I 
couldn't do much else with the live CD after that, giving me errors 
about the /home dir.

So how do I get that to happen when logging in to my HD?  Is there a way 
to use the CD burner with the live CD?

Do you have more than one cd drive? If not, then no. How much data is in your /home directory? Are we talking MB or GB of stuff?

---

### Post by quincunx on 2007-02-22
> **llamakc said:**
> Do you have more than one cd drive? If not, then no. How much data is in your /home directory? Are we talking MB or GB of stuff?

Just one CD drive, and data would be measured in Gigs.

---

### Post by llamakc on 2007-02-22
Do you have diskspace on the other partition or hard drive that IF you had access to the data missing on /home, you could copy it over?

If so you can mount the target (on a different partition than the fubar'd /home) while using the livecd with something like:

1. Make a place to mount your good partition. (This is in the LiveCD session)

sudo mkdir /media/hdZ

2. Mount your good partition.

sudo mount -o remount,rw /dev/hdZ /media/hdZ

3. Make a directory INSIDE of that

sudo mkdir /media/hdZ/MYOLDHOME

(the above will appear in the root (/) of your partition that you mounted.)

4. Mount your old home (I don't remember if it was hdb1)

sudo mount /dev/hdb1 /mnt

5. Change directory into /mnt and start moving stuff to /media/hdZ/MYOLDHOME

Of course some caveats: 1) I don't remember if the LiveCD automounts existing partitions. If it does, you'll still want to 'remount' where you would be copying data TO, not from. 2) My guesses at your partition numbers are only guesses. Think through what you are doing before following my advice. 

What I can tell you is that it is very possible to get data off of your old home with a LiveCD, and to write it to your hard drives provided you remount with the 'rw' flags. I really hope you figure this out. 

If somebody else reads this and sees an error in the above, please correct me. Thanks.

---

### Post by quincunx on 2007-02-22
> **llamakc said:**
> 
2. Mount your good partition.

sudo mount -o remount,rw /dev/hdZ /media/hdZ


In this case, would "hdZ" be exactly that, or something else like "hda" or "hda1"?

---

### Post by llamakc on 2007-02-22
> **quincunx said:**
> In this case, would "hdZ" be exactly that, or something else like "hda" or "hda1"?

Your intuition is correct. I don't remember your hard drive layout. Is your fstab posted in this thread? EDIT: There it is.

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb1       /home           ext3    defaults        0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
```


So in my example above, /dev/hdZ would be replaced with /dev/hda1 and /media/hdZ would be /media/hda1. 

HTH.

---

### Post by quincunx on 2007-02-22
> **llamakc said:**
> So in my example above, /dev/hdZ would be replaced with /dev/hda1 and /media/hdZ would be /media/hda1. 
HTH.

I typed:
ubuntu@ubuntu:/$ **sudo mount -o remount,rw /dev/hda1 /media/hda1**

and got:
```
ubuntu@ubuntu:/$ sudo mount -o remount,rw /dev/hda1 /media/hda1
mount: you must specify the filesystem type
ubuntu@ubuntu:/$ man mount
Reformatting mount(8), please wait...
ubuntu@ubuntu:/$ sudo mount -t ext3 -o remount,rw /dev/hda1 /media/hda1
mount: /media/hda1 not mounted already, or bad option
ubuntu@ubuntu:/$ 
```

Here is my **fstab** while using the **Live CD**:

```
unionfs / unionfs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
```

and "**sudo mount**" looks like this:```

ubuntu@ubuntu:~$ sudo mount
unionfs on / type unionfs (rw)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.17-10-generic/volatile type tmpfs (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
```

If I use the CD menu option to mount to the "First HD", I get the same results as without the CD.

---

### Post by llamakc on 2007-02-22
And this is after you made the directory to mount to, correct? 

Which LiveCD are you using?

---

### Post by llamakc on 2007-02-22
Here's what I can tell you: I used the method I wrote above to save data from a bad drive. I did so by booting a LiveCD, remounting where I would be writing to, and copying the data.

I sent you a PM.

---

### Post by quincunx on 2007-02-26
> **llamakc said:**
> And this is after you made the directory to mount to, correct? 

Which LiveCD are you using?

Yup, this was after creating the /media/hda1 directory.  I'm using the 6.10 Live CD, just burned it from the Ubuntu website after your suggestion.

---

### Post by llamakc on 2007-02-26
Have you remounted /dev/hda1 and made a directory to store stuff yet?

---

### Post by quincunx on 2007-02-26
> **llamakc said:**
> Have you remounted /dev/hda1 and made a directory to store stuff yet?

When I attempted the "remount" is when I got:

```
mount: /media/hda1 not mounted already, or bad option
```

Since this all started, there has been only one point at which I could see the contents of my old home directory.  That was after booting with the LiveCD and mounting /dev/hdb1 to /home, but that broke all (most?) functionality with the LiveCD for that session.

---

### Post by llamakc on 2007-02-26
> **quincunx said:**
> When I attempted the "remount" is when I got:

```
mount: /media/hda1 not mounted already, or bad option
```Since this all started, there has been only one point at which I could see the contents of my old home directory.  That was after booting with the LiveCD and mounting /dev/hdb1 to /home, but that broke all (most?) functionality with the LiveCD for that session.

Correct, you should have mounted it to a NEW place, one that you made, or somewhere like /mnt (when you were in the LiveCD). 

Knoppix will auto-mount those partitions for you.

---

### Post by quincunx on 2007-02-26
> **llamakc said:**
> Correct, you should have mounted it to a NEW place, one that you made, or somewhere like /mnt (when you were in the LiveCD). 

In your instructions:
> 1. Make a place to mount your good partition. (This is in the LiveCD session)
sudo mkdir /media/hdZ
2. Mount your good partition.
sudo mount -o remount,rw /dev/hdZ /media/hdZ
3. Make a directory INSIDE of that
sudo mkdir /media/hdZ/MYOLDHOME
(the above will appear in the root (/) of your partition that you mounted.)
4. Mount your old home (I don't remember if it was hdb1)
sudo mount /dev/hdb1 /mnt
5. Change directory into /mnt and start moving stuff to /media/hdZ/MYOLDHOME

I only made it to step 2, I didn't have a chance to get to step 4 where I mount at /mnt.  So, I currently have a /media/hda1 directory that I created.  Do I need to create a /mnt directory to do "**sudo mount -t ext3 -o remount,rw /dev/hda1 /media/hda1**"?

---

### Post by llamakc on 2007-02-26
No. Remount /dev/hda1 with:

```

sudo mount -o remount,rw /dev/hda1 /media/hda1

```

Now, you must create a NEW directory on your hard drive's primary partition. You're going to create that with:

```

sudo mkdir /media/hda1/MYOLDHOME

```

When this is all said and done, and you boot normally without the livecd the data we save/move will be in /MYOLDHOME

Now you're ready to mount your /dev/hdb1 (old home partition)

```

sudo mount /dev/hdb1 /mnt

```

If you get this far with no errors, do this:

cd /mnt && ls

You will now be INSIDE your old, missing directory. Start copying stuff over to /media/hda1/MYOLDHOME.

---

### Post by quincunx on 2007-02-26
Right, I understand that, but when I get to here:

> **llamakc said:**
> ```

sudo mount -o remount,rw /dev/hda1 /media/hda1

```


...is when I get the error, "**mount: /media/hda1 not mounted already, or bad option**".  I don't see how creating a directory afterward is going to change that.  Unless I'm supposed to just ignore the error message and continue with steps 3-5?

If I don't use the "-t ext3" option I get "**mount: you must specify the filesystem type**".

---

### Post by llamakc on 2007-02-26
I misunderstood you. I thought you had already remounted.

Since I'm not in front of a system with the same error, perhaps you could try

sudo mount -t ext3 -o remount,rw /dev/hda1

Also, are you still using the Ubuntu LiveCD or the Knoppix cd?

---

### Post by quincunx on 2007-02-26
> **llamakc said:**
> I misunderstood you. I thought you had already remounted.

Since I'm not in front of a system with the same error, perhaps you could try

sudo mount -t ext3 -o remount,rw /dev/hda1

Also, are you still using the Ubuntu LiveCD or the Knoppix cd?

I haven't been able to get the Knoppix CD, might be able to do that tomorrow.  I actually got to copy from one drive to the other by doing this:

```

sudo mount -t ext3 /dev/hda1 /media/hda1
sudo mkdir /media/hdb1
sudo mount -t ext3 /dev/hdb1 /media/hdb1
sudo mkdir /media/hda1/ddrive_stuff
sudo mkdir /media/hda1/ddrive_stuff/NOTES
sudo cp -r /media/hdb1/home/me/NOTES/* /media/hda1/ddrive_stuff/NOTES

```

However, I still get the error using cdrecord when I boot to the hard-drive (and only one CD player/burner).  Should I make a new thread for that, or is it better to solve that in this thread?

---

### Post by llamakc on 2007-02-26
> **quincunx said:**
> I haven't been able to get the Knoppix CD, might be able to do that tomorrow.  I actually got to copy from one drive to the other by doing this:

```

sudo mount -t ext3 /dev/hda1 /media/hda1
sudo mkdir /media/hdb1
sudo mount -t ext3 /dev/hdb1 /media/hdb1
sudo mkdir /media/hda1/ddrive_stuff
sudo mkdir /media/hda1/ddrive_stuff/NOTES
sudo cp -r /media/hdb1/home/me/NOTES/* /media/hda1/ddrive_stuff/NOTES

```However, I still get the error using cdrecord when I boot to the hard-drive (and only one CD player/burner).  Should I make a new thread for that, or is it better to solve that in this thread?

So you DID get your stuff off of the drive? Awesome. 


```

me@abrahadabra:/$ sudo cdrecord dev=/dev/hdc -data 
/ubuntu-6.10-desktop-i386.iso 
cdrecord: No write mode specified.
cdrecord: Asuming -tao mode.
cdrecord: Future versions of cdrecord may have different drive dependent defaults.
cdrecord: Continuing in 5 seconds...
Cdrecord-Clone 2.01.01a01 (i686-pc-linux-gnu) Copyright (C) 1995-2004 Joerg Schilling
NOTE: this version of cdrecord is an inofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.

cdrecord: Warning: Running on Linux-2.6.19.1-rt15
cdrecord: There are unsettled issues with Linux-2.5 and newer.
cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
scsidev: '/dev/hdc'
devname: '/dev/hdc'
scsibus: -2 target: -2 lun: -2
Warning: Open by 'devname' is unintentional and not supported.
Linux sg driver version: 3.5.27
Error: Cannot gain SYS_RAWIO capability.Is cdrecord installed SUID root?
: Operation not permitted
Using libscg version 'debian-0.8debian2'.
cdrecord: Warning: using inofficial version of libscg (debian-0.8debian2 '@(#)scsitransp.c 1.91 04/06/17 Copyright 1988,1995,2000-2004 J. Schilling').
Device type    : Removable CD-ROM
Version        : 0
Response Format: 1
Vendor_info    : 'ARTEC   '
Identifikation : 'WRR-4848        '
Revision       : '1.00'
Device seems to be: Generic mmc CD-RW.
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-2 SWABAUDIO BURNFREE FORCESPEED 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R96R
Error: Cannot gain SYS_RAWIO capability.Is cdrecord installed SUID root?
: Operation not permitted
Starting to write CD/DVD at speed 48 in real TAO mode for single session.
Last chance to quit, starting real write    0 seconds. Operation starts.
Turning BURN-Free off
cdrecord: Success. write_g1: scsi sendcmd: no error
CDB:  2A 00 00 00 41 83 00 00 1F 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: F0 00 05 00 00 41 99 0C 00 00 00 00 10 02 00 00
Sense Key: 0x5 Illegal Request, Segment 0
Sense Code: 0x10 Qual 0x02 (id crc or ecc error) [No matching qualifier] Fru 0x0
Sense flags: Blk 16793 (valid) 
cmd finished after 0.032s timeout 40s
write track data: error after 34347008 bytes
cdrecord: A write error occured.
cdrecord: Please properly read the error message above.
```

I'm not sure what the problem is with the burner. A new thread may help others too.

---

### Post by llamakc on 2007-02-26
BTW, have you tested the burner using the "-sao" option?

---

### Post by jorgepeixoto on 2007-03-26
Has this problem already been solved? 

I haven't had the patience to read the entire thread, but some things have captured my attention:

1) It seems that the guy has been advised to "remount" hdb1, but he can only "remount" hdb1 if it has already been mounted!
Why has this "remount" suggestion been made? Why not a normal mount? 

2) Until now, it seems that the guy has not tryed to mount in another place (that is, not /home).

3) If I were the guy, I would copy the contents (except for large files like video) of hdb1 to hda so that I could use the system. I would copy everything except the biggest files (normally, a coupe of files (like some videos, or some music) occupy most space.

---

### Post by jorgepeixoto on 2007-03-26
One question: when running the Ubuntu live CD, what is your fstab?

---

