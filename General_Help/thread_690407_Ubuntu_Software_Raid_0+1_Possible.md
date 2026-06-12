---
title: "Ubuntu Software Raid 0+1 Possible?"
date: 2008-02-07
forum: General Help
---

### Post by MacBookBuntu on 2008-02-07
I've read a lot about setting up software raids in Ubuntu, but none of them address a software Raid 0+1 configuration.  Is this possible?  (and if so, any tips?)

A little background:

I'm working with a Dell Powervault 725N with 4 IDE drives and NO hardware Raid controller.  I've got it booting the basic Gutsy netboot install via PXE.  I'd like the first two drives to be a raid 0 stripe, and the second two to be a Raid 1 clone of the first two.

I'm a bit of a noob - at least when it comes to Raids, so I thank you for your patience in advance.

-Tim

---

### Post by danwood76 on 2008-02-07
heres a guide on setting up a RAID10 array (which is what you want)
[http://www.mythtv.org/wiki/index.php/RAID#Setup_.28Software_RAID.29](http://www.mythtv.org/wiki/index.php/RAID#Setup_.28Software_RAID.29)

regards,
Danny

---

### Post by djamu on 2008-02-07
hey.

This is an easy one -aside from wondering why'd you prefer this instead of the striped redundancy of raid5 / raid6- in case of raid 5 ( 4disks ) which gives you more ( 1disk ) space of the otherwise mirrored disk... 

Raid 0+1 better known as raid 10 is pretty easy to setup.
as the name suggests there are 2 routes > the mirrored stripe / striped mirror
the first requires you to create 2 stripes which are mirrored / the other are 2 mirrors which are striped...

Another thing is that there another route one can take for striping - striping is splitting up data across HD's, for example a 2 disk stripe will split up bytes ( 8bit ) into nibbles ( 4bit ) and write each nibble to a disk. While for single file / single user access this can theoretically double your data throughput... it is generically a not so smart thing to do on servers with lots of users ( as disks work simultaneously  in sync for each request ). Better is then to use linear raids which enlarges your volume without striping.. ( just adding the volume of 2nd disk etc. .. to the previous ). This has a major advantage as disks might work independent ( in case the data of 2 requested files are physically on different disks,.. ) resulting in better overall performance; as multiple files can be fetched simultaneously..  ( just take into account that HD's have seek times )

In short, if this is a workstation / video frameserver whatever.. for a single user > use stripe
if it's a mailserver / fileserver ( lots of small files / lots of users ) > use linear raid 

then mirror this...

just give me some more info on intended usage & I'll guide you ):P


**EDIT:**

> **danwood76 said:**
> heres a guide on setting up a RAID10 array (which is what you want)
[http://www.mythtv.org/wiki/index.php/RAID#Setup_.28Software_RAID.29](http://www.mythtv.org/wiki/index.php/RAID#Setup_.28Software_RAID.29)

regards,
Danny

**I've found things there which are definitely false, the info on custom chunk sizes might get you in trouble ... use the standard 64kb ( don't specify chunk size ) **

Just for your info...

[QUOTE=Performance Expectations

There are many 'opinions' on what RAID level is best for performance, since it can vary greatly depending on many factors, but with all things being equal, here's the facts about the most common RAID levels:

    * RAID 5 is the slowest*
    * RAID 1 is in the middle (speed is equivelent to not using RAID)
    * RAID 0 (and RAID 0+1, 10, 1+0, etc) is the fastest 

And here's why:
[edit]
RAID 5

RAID 5 (striping with parity) is the slowest because your computer has to calculate parity for every write operation and then write that parity to disk. This can be considerable overhead with software RAID or budget RAID controllers. Parity is the distrubed data that allows you to lose any hard drive but still not lose data. Read speads are very good, better than RAID 1. *You can significantly increase RAID 5 performance, sometimes even get it faster than RAID 1 performance, if you do the following:

    * Use hardware RAID solution
    * Use a Battery-Backed Write-back Cache, or BBWBC (only available on high-end RAID controllers). These only help data bursts, up to the size of the cache (typically 16-256 MB), not extended write operations.
    * Add more disks 

In general, unless you have server-class hardware and SCSI disks, you can always expect RAID 5 writing to be slower than RAID 1 or 0. Reading is very fast, can be similar to RAID 0. ]
[/QUOTE]

Raid5 is NOT the slowest, I know because I'm running a couple of 15 disk raid5 / raid6 arrays. ( soft raid's )
I know for a fact that a 4 disk stripe (raid0) almost runs equally fast as a 5 disk raid5 
The parity calculation is just a simple XOR operation & hardly affects performance ( cpu's are running at a much higher speed then IDE / SCSI bridges )
Raid5 is just a stripe with parity..
Although it's true that windows based soft raid5 is just a joke .. > the info on this site is probably biased because of this...

That info on battery backed write back cache is just plain nonsense.... It doesn't help anything for performance, it's means is to properly flush cache on a sudden power down, and by doing so minimizes the possible effects of the power surge.... But since where talking Linux with state of the art file system journaling... there's no need for that.... If you really want to be on the safe side, just use a UPS.

some more gibberish..

> 
# mdadm -v --create /dev/md0 --force --chunk=32 --level=raid5 \
      --spare-devices=0 --raid-devices=3 /dev/sda1 /dev/sdb1 /dev/sdc1


Do not use --force  
Do not use --chunk=32
no need to use the -v flag


And that info IDE vs SCSI is just completely outdated... ( seems from before the DMA era )
most recent linux distributions use a scsi bridge for the IDE bus, aside from that info that states one shouldn't place disks on both channels of an IDE controller... tssktssk ... IDE busses are much faster then disk thruput... so there's no point in not doing ( if he would say not to place a cdrom I'd understand )


There's a couple of posts from me on the forum regarding RAID stuff... so I'm not going in detail here why you shouldn't use those flags... just don't use them..


Jan

---

### Post by MacBookBuntu on 2008-02-07
Danny-
Thank you for the link -- it's actually very  helpful in getting all this sorted out.  I think the issue for me is I'm trying to get the raid setup using Ubuntu's partitioning utility prior to installation of the OS.

Djamu-
This server is not a file server, nor anything mission critical or heavy.  We'll probably end up throwing Nagios and a couple other server utilities, maybe even a corporate wiki (using phpwiki).  My boss seems set on a 10 (or 01) combination, though from what I've read now 10 seems the way to go.  Can I set this up from Ubuntu's partition utility during install?

Thanks!

-Tim

---

### Post by djamu on 2008-02-07
No don't use the gnome ( gparted) partitioner...

first install the mdadm package ( apt-get install mdadm or using synaptics )
reboot:
because mdadm needs to be started at boot time.

use the shell ( command line ) to  partition the disks using > cfdisk  ( not fdisk ), which is easy to use
although strictly there's no need to partition the disks ( mdadm doesn't need them ), it's still good practice to do so.... some OS's ( think M$ ) write data on disks ( initialize ) regardless of your wishes if they don't have partitions....

then use that mdadm command without the --force & --chunk & -v flag.... ( I've edited my previous post after reading that page... so you might want to reread it ...

---

### Post by MacBookBuntu on 2008-02-07
djamu,

Thanks for the tips -- I'll get back to you soon on this.  I need to do a PXE boot to a command line, as I can't create RAIDs utilizing the same disk I booted from.  However, it doesn't look as frightening as I once thought.

-Tim

---

### Post by djamu on 2008-02-07
> **MacBookBuntu said:**
> djamu,

Thanks for the tips -- I'll get back to you soon on this.  I need to do a PXE boot to a command line, as I can't create RAIDs utilizing the same disk I booted from.  However, it doesn't look as frightening as I once thought.

-Tim

huh? :confused:

---

### Post by MacBookBuntu on 2008-02-08
> **djamu said:**
> huh? :confused:

lol, sorry to be confusing, I'm a noob, so I don't mean to confuse others!

All I meant is -- If a software raid is going to contain the boot volume for the server, then I need to first setup the raid, and second install the operating system, right? (not the other way around)

Specifically, I want to make a software raid from /dev/sda, /dev/sdb, /dev/sdc, and /dev/sdd, so I cannot install Ubuntu on /dev/sda1, boot from it, and subsequently incorporate /dev/sda into the raid, correct?

In any case, I'm trying to find a way of setting up the Raid on the server prior to installing the operating system.  (The Ubuntu Installer utility only creates 0, 1 & 5 raids, not 10 or 01)

Is that any clearer?  Hopefully I'll have it up and running today.

---

### Post by danwood76 on 2008-02-08
You cant load the boot loader off a software raid volume.
Its simply impossible as software is needed to initialise the array, so there is no way to load the info off the /boot partition or the MBR for that matter.

You will need to have the /boot partition on another drive, as you can load enough into the initramfs to be able to boot from a sw raid.

---

### Post by djamu on 2008-02-08
> **MacBookBuntu said:**
>  If a software raid is going to contain the boot volume for the server, then I need to first setup the raid, and second install the operating system, right? (not the other way around)


set up raid during install ( I'll clarify further in the post )

> 
Specifically, I want to make a software raid from /dev/sda, /dev/sdb, /dev/sdc, and /dev/sdd, so I cannot install Ubuntu on /dev/sda1, boot from it, and subsequently incorporate /dev/sda into the raid, correct?

In any case, I'm trying to find a way of setting up the Raid on the server prior to installing the operating system.  (The Ubuntu Installer utility only creates 0, 1 & 5 raids, not 10 or 01)

Is that any clearer?  Hopefully I'll have it up and running today.

K here we go.

There's only 1 type of raid a system can boot from, and that's a raid1. Simply because every disk contais the same info. A prequisite of a bootable system is that it must be able to boot from it ( obviously ). In order to do so it must find a legitimite bootsector & bootpartition ( to load any drivers > mdadm for example,  best practice is using initramfs -which comes standard and loads anything the system might need to continue booting - ... because only raid1 has that, all -other types are a kind of stripes- do the following while installing...

Create a small 100MB primary partition ( so no automatically generated partitions ) on every disk ( all 4 ).
make that a raid 1 (dev/md0) labeled as /boot format ext3... 
This partition will hold all boot data, grub + initramfs 
(i'm just assuming you want a full redundant system ).
Since the contents of this 100MB partition is identical for all 4 disks, the system will be able to boot regardless of the condition of the disks and raid status .. So this small partition won't become raid10 / 01

**after final install, use CFDISK to make all 4 disks bootable as only 1 will have a bootflag**

alternatively you could do this for the complete system partition /   use a larger partition then :)  
I'm not sure which mount you'll be using to hold you data... but most likely it will be /var/www since you where talking nagios ?

just keep in mind that following  pittfall might arise.. ( despite what the mdadm manual claims there's no need to use the mdadm.conf ). you have to make sure the 2 raid0 arrays gets assembled before joining them into a raid1 ... I got some time left now, I'll check some things on Gutsy ( which I assume you'll be using 


Jan

---

### Post by djamu on 2008-02-08
> **danwood76 said:**
> You cant load the boot loader off a software raid volume.
Its simply impossible as software is needed to initialise the array, so there is no way to load the info off the /boot partition or the MBR for that matter.

You will need to have the /boot partition on another drive, as you can load enough into the initramfs to be able to boot from a sw raid.


that's wrong... i'm booting my servers of a raid1

---

### Post by MacBookBuntu on 2008-02-08
djamu,

Your instructions and clarifications are nothing short of awesome.  I totally understand what's happening now.  I feel like I totally owe you a pie or pizza or something.

Here's where I'm at:

/dev/md0 is a Raid1 200mb Ext3 across all four drives with mount point /boot  (more space than I need, I know)

/dev/md1 is a Raid1 1.5gb Swap across all four drives (I assume I need swap on all 4, just like /boot)

/dev/md2 is a Raid0 236gb of /dev/sda3 & /dev/sdb3 -- not given a mount point yet
/dev/md3 is a Raid0 236gb of /dev/sdc3 & /dev/sdd3 -- not given a mount point yet

Now, where do I assign my / mount point?  If I assign it to /dev/md2, can I still make a RAID1 of md2 to md3 using mdadm once the install is finished?

Thanks...

-Tim

---

### Post by MacBookBuntu on 2008-02-08
Scratch that, I found a workaround...

/dev/md0 is a Raid1 200mb Ext3 across all four drives with mount point /boot (more space than I need, I know)

/dev/md1 is a Raid1 1.5gb Swap across all four drives (I assume I need swap on all 4, just like /boot)

/dev/md2 is a Raid1 118gb of /dev/sda3 & /dev/sdb3 -- set for use with LVM
/dev/md3 is a Raid1 118gb of /dev/sdc3 & /dev/sdd3 -- set for use with LVM

LVM merges md2 and md3 into a single volume on which I mounted /

Is this insane, or does it make sense?

-Tim

---

### Post by djamu on 2008-02-08
no it isn't but that's not a raid 10 :lolflag: because stricly speaking lvm is not a stripe

lvm = linear raid better known as disk spanning ( re-read my first post )

BUT: that will solve the pitfall of forcing the assemble sequence...
> /dev/md2 + dev/md3 need to be assembled before concatenating either /dev/md4 or the lvm volume...

i'm currently checking the assemble workaround on a vmware image ( every distro has it's quirks, so just to make sure )..

I'll be back with you in 15 min.

---

### Post by djamu on 2008-02-08
> **MacBookBuntu said:**
> djamu,

Your instructions and clarifications are nothing short of awesome.  I totally understand what's happening now.  I feel like I totally owe you a pie or pizza or something.

-Tim

mmm that's all ? :popcorn:

k the results of my fiddling, while the system / ( whole space exept /boot as raid1 ) can be installed from CD as raid01 ( the last mirrored assembly has to be done manually ) one can't install a system from cd as a RAID10.
It can be done but that's not for the feint of heart... and since lvm is not stripe....

Another much easier route that won't cost much in HD space is to put the entire system on the boot partition ( it's a server yes ? so it won't take that much ), meaning instead of creating a small 100MB primary raid1 as /boot ext3 > create a larger 2GB raid1 ext3 mount = / solely for the system... and use the remaining space as a true raid10 with mount /media/data  /var/www whatever. ( no need for a seperate /boot then )...
This space can only be reserved but not mounted thru the installer > meaning just create 2 large md raid1 devices without mount point ( the ones that get striped once the system is up and running ). Once the system is up & running create the final md raid0 device ( made up out of those 2 unmounted raid1's ) format it ( reiserfs is good for that, allows quota & what not..  ) & mount it... 

you might need a small script to assmble this final stripe on boot as on boottime the system will be unable to mount it ( can depend on device nr... assemble speed .... ) whatever..  I'll provide you one ( real easy ) that has to be put in the rc folder...

just ask when done... & give me the disk info then i'll write a tailored script & where to put it..

good luck


Jan

---

### Post by MacBookBuntu on 2008-02-08
Awesome, I'm playing with the various ways of configuring the RAID now -- and I'll let you know how it ends up -- and if I'll need a script for a final mount.  You're probably the single most helpful person on a forum ever!  Is that your website in your signature?

---

### Post by djamu on 2008-02-08
> **MacBookBuntu said:**
> Awesome, I'm playing with the various ways of configuring the RAID now -- and I'll let you know how it ends up -- and if I'll need a script for a final mount.  You're probably the single most helpful person on a forum ever!  Is that your website in your signature?

yes that's what I do for a living ( this is my personal stuff )

---

### Post by danwood76 on 2008-02-09
> **djamu said:**
> that's wrong... i'm booting my servers of a raid1

Yeah sorry, with the exception of RAID1 as this needs no software to boot the drive as it has no complex striping.
I was talking about the more complex versions of RAID.

---

### Post by bbarrons on 2008-03-14
Djamu,
 I read thru this thread and found it to be very helpful.I had a server to setup. I was able to get it up and running and I would like to know if what I did makes sense.
 Here is what I have and how I setup.
 I bought a used server from ebay.....dual processor, 4 scsi drives, no cdrom.
I setup to install over network with pxe. Got that connectin fine and went at a gutsy server install
I partitioned the 4 drives this way:
100mb partition on ea drive. created raid 0  dev/md0 with the 4 partitions and formatted as ext3 and made a boot partition.
then then took the balance of drives a & b and created dev/md1
and then repeated for drives c&d and created dev/md2
I then created a logical group from those 2. and partition that into 3 volumes /root /opt /home
 It boots, it runs, and seems fine......What I did......did I waste my time or does it make sense?
 thanks for your opinion.
 Bill

---

### Post by djamu on 2008-03-14
> **bbarrons said:**
> Djamu,
 I partitioned the 4 drives this way:
100mb partition on ea drive. created raid 0  dev/md0 with the 4 partitions and formatted as ext3 and made a boot partition.
then then took the balance of drives a & b and created dev/md1
and then repeated for drives c&d and created dev/md2
I then created a logical group from those 2. and partition that into 3 volumes /root /opt /home
 It boots, it runs, and seems fine......What I did......did I waste my time or does it make sense?
 thanks for your opinion.
 Bill

K seems fine, should run flawless :)... just check that all 4 first partitions have the bootflag ( use cfdisk )
If it's a server I wouldn't have made a seperate /home.. any specific reason for the /opt ?
What Fs did you use ? quota ?
Although not necessary in some cases a swap comes in handy ( streaming Lamp webserver / lots of other processes )
if its's a pure mailserver you might benefit from formatting with small chunks... ( doesn't affect the array so leave that @ 64k )...

As an extra I usually mail on regular intervals the contents of the /var/log to another server ( every 5 min ), as a precaution. ( mirror over iscsi is a good idea to > seperate nic ).. 
Even with the legendary security of linux, security breaches are mostly caused by social engineering, ( from the inside out ) so keeping your logs intact might prove valuable.  
A local vmware server image with Monowall / Pfsense as a routing firewall package is a good idea too if it's a webthing... ( & easier then running these chrooted ) just route your traffic thru these... 
( main server local adress > pfsense/monowall > internet IP...
Since Monowall / Pfsense is FreeBSD, it's much harder to exploit shared distro weaknesses ( if any :-) )




Anything else ?
Mind to share some configs ? 

cheers.. :popcorn:

---

### Post by bbarrons on 2008-03-14
Thanks for the reply.
I created a home because even though it was a server I like to have a gui....so I install kubuntu.
 IT will be in a private school so I will also use it to show others how to care for it.
/opt is where  zimbra ( email suite) stores its mailboxes. I will also have to backup that to another server.
 I forgot to mention I used 1 gig per drive for swap.
 I have 2 of these servers to setup. The second one is going to be setup with squid and dansguardian. I have never used these before but they seem to be failry easy to setup and get a basic config going. Right now the school installs net nanny on ea computer....seems to be a terrible waste of resources.
Bill

---

### Post by djamu on 2008-03-14
> **bbarrons said:**
> Thanks for the reply.
I created a home because even though it was a server I like to have a gui....so I install kubuntu.
 IT will be in a private school so I will also use it to show others how to care for it.
/opt is where  zimbra ( email suite) stores its mailboxes. I will also have to backup that to another server.
 I forgot to mention I used 1 gig per drive for swap.
 I have 2 of these servers to setup. The second one is going to be setup with squid and dansguardian. I have never used these before but they seem to be failry easy to setup and get a basic config going. Right now the school installs net nanny on ea computer....seems to be a terrible waste of resources.
Bill

looking at what your doing.. might I suggest looking at this [SME-server]("http://www.smeserver.org/") site doesn't look that fancy... but it's quite powerfull ( squid mail & whatnot )
That Zimbra suite looks nice, i'll check it.. 
Firewall ? Never used Dansguardian but doesn't seem to be a firewall (should block traffic both ways if it's a school ) Pfsense has some squid modules. both Monowall & Pfsense can be embedded ... on [these]("http://www.pcengines.ch/alix.htm") ( i'm not affiliated just a happy customer) as dedicated firewall / router

Good luck

---

### Post by bbarrons on 2008-03-14
I played with SME for a few years. I had trouble keeping it stable. It seemed like I was always messing with it to keep it running. OF course it might have been the pc I installed it on for testing. I came back to this project about 6 months ago and decided to give ubuntu server a try. I had been ising ubuntu on a desktop since dapper release and loved it. SO, I started to look for a email and calander system I could put on ubuntu. I decided on zimbra. Easy to install and didnt take alot of configuring to get it up and running.
Dansguardian is really just for web filtering. The school uses a netgear router as their firewall.
pfsense really looks like the ticket for us. I have much more research to do. thanks for the tip.
 bill

---

### Post by djamu on 2008-03-14
> **bbarrons said:**
>  thanks for the tip.


that goes both ways... Zimbra looks really cool... i'm surely going to test it... 

:lolflag:

---

