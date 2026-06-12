---
title: "Which Disk setup for Ubuntu Server?"
date: 2014-04-12
forum: General Help
---

### Post by hamish3 on 2014-04-12
Hi all,

Looking for a little advise on the best way to set up Ubuntu server,


I currently have a nice shiny new SSD along with 5x WD Red HDDs that I would like to set up with ZFS.


Now I have looked around the interweb and I could do the same as a lot of people seem to and just Install the OS on the SSD, but I have heard of people using a USB thumb drive for the relatively static OS as well so Im a little confused as to the best set up.

Should I:


     1) Install the OS on SSD and ZFS the 5x HDD for media as most seem to do.


     2) Install the OS on a USB thumb drive with the Cache and other frequently changed (not sure what files would be best to move over) files on the SSD and ZFS on the 5x HDD for media

Im not looking for advice on How to set up the OS but simply which of the two disk set-ups would be better in the long run.


To start with this will be a family media/backup server streaming to Android phones/Windows PC/Laptop and Panasonic smart TV. Backing up the PC and laptops.
Eventually I would like to play around with VM's and explore Ubuntu later once the OH isnt so concerned that the new tech might lose all our photos etc. 


Thanks in advance for any suggestions or advice.


H

---

### Post by Double.J on 2014-04-12
Hi there!

Welcome to the forums!

I'm assuming the ZFS choice is for  RaidZ?

Well, Given your current hardware, I can't think of a particularly good reason to use the thumb drive. The  SSD makes perfect sense, as it gives a sizeable performance boot to the system, however the thumb drive would be a substantial performance limitation.

The SSD drive will not only use a motherboard SATA connector, whereas the USB key would use the serial USB port (even with USB3 it will be slower), but also the flash chips in the USB stick will typically have much slower read/write speeds than the SSD drive. Also SSD drives typically come with more advanced data management firmware so that as the drive ages and the number of writes left reduce, drive performance is maintained as long as possible - most SSD vendors typically quote 10's of GB in writes per day for 10-25 years. Flash key manufacturers do not, in my experience make these assessments. Finally the USB key would be external and thus more prone to accidental removal/damage.

I would say that the question should really be is it better to use the SSD for the system and the 5 disks in raidz for data, or use ubuntu's software RAID on the five disks and install the system in separate partitions on an md partition and free up the SSD? after all an ubuntu server install is pretty small ~a gig and it does mean that the system is protected against drive failure?

In essence; use the performance and additional capacity of the SSD,  or use the redundancy of the additional disks?

Jj

---

### Post by hamish3 on 2014-04-12
Hi Double.J

Thanks for welcome and the quick reply.
 
Yes I intend to set up the 5 Reds in raidz1, Ill also be backing that up to an external HDD so raidz2 shouldn't be needed. 

From what you have said I think Ill go with the performance on the SSD and use the 5 disks as the raidz1 in zfs.  
 
To be honest I made the assumption that Solid state was Solid state, whether SSD or USB, and didnt even think about the speed of the two buses. 

Im just starting out in the whole non Win world so its nice not to be judged to harshly for what was in hindsight a simple enough question to answer.

Now I just have to fit them all into the N40L sitting on the table.

Thanks

H

---

### Post by Double.J on 2014-04-12
> **hamish3 said:**
> Im just starting out in the whole non Win world so its nice not to be judged to harshly for what was in hindsight a simple enough question to answer.

Not at all. I'm a firm believer that the real strength of Linux is it's community. I have the advantage of time in that my first attempts with Linux were with Debian Potato! The first question I ever asked in on-line support (it was mostly mailing lists and IRC (took a little while to get a reply ;)) was 'I can't get through disk partitioning, what does it mean 'mountpoint /'?

Just looked up the N40l; looks like a very sweet home server box! My last build was a home server. I only needed 2x2TB in RAID1 plus SSD, So crammed it all into the [COLOR=#000000]cooler master elite 120.
[/COLOR]
Have fun with the cables!

Jj

---

