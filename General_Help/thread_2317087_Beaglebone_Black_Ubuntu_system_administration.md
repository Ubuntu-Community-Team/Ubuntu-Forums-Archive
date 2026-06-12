---
title: "Beaglebone Black Ubuntu system administration"
date: 2016-03-13
forum: General Help
---

### Post by phil95 on 2016-03-13
I am new to this forum, so I don't know which section this should be posted in.  If someone has a suggestion, please let me know.

I have a Beaglebone Black (embedded linux) and have loaded Ubuntu on to the onboard 4GB flash memory.  Everything is running fine.  I am working on building some OpenCV applications and would like to have a full desktop environment on the BBB.  However, the packages available won't fit on the onboard memory.

I have a 64GB sd card in the slot.  I have figured out how to partition and mount the card for storage.

Here are the things I would like to know:

1.  Is there a way to put the new packages i install (apt-get install...) onto the sd card and have them run properly without moving the entire operating system onto the card?  I don't want to move everything to the card for safety reasons and I figure the onboard emmc will be faster than the card.

2.  Should I setup a swap partition on the card?  I have read about it, but don't fully understand if it is necessary or advantageous, nor how to set it up.

3.  What other directories would it be good to move to the card and how do I move them?

Thanks for any help.

---

### Post by bab1 on 2016-03-13
> **phil95 said:**
> 
Here are the things I would like to know:

1.  Is there a way to put the new packages i install (apt-get install...) onto the sd card and have them run properly without moving the entire operating system onto the card?

There is no method for the end user to select the install location of APT packages.  The typical locations are in a subdirectories of /usr.
> 
2.  Should I setup a swap partition on the card?  I have read about it, but don't fully understand if it is necessary or advantageous, nor how to set it up.

If you move the swap to the SD card you will have that space available on the 4GB card.  You will have to make a partition on the SD card for the swap area.
> 

3.  What other directories would it be good to move to the card and how do I move them?

You can't pick and choose what individual directories you want on either the 4GB flash or SD card.  The file system (FS) is one hierarchical tree that starts at / (the root of the FS).  You would have to create a partition for each branch of the FS that you wanted to locate on the SD card. It is possible to have multiple partitions on the SD card. For example, if you wanted to locate the /var branch on the SD, you would create a partition and format the partition as EXT4.  Then you mount this partition at /var.  You would have to transfer all the data that resides on the 4GB card for /var to the new partition.  This is just an example of how it works.  I'm not suggesting that you actually do this.  What I am saying is you can't do what you have move individual directories and have things work.

It isn't practical to create a partition for /usr after the install of Ubuntu.  I suggest that you backup the data you have and reinstall the OS with the SD card partitions you create available to the installer.  Most of the tutorials for this will use /home as the example, but you can do the same thing for /usr.  This will put all the APT installed programs on the SD card.  A typical Unity DE will be about 4GB to 6GB in size.  I would also store all the data at /data, but this can be done after the OS is reinstalled.

---

### Post by phil95 on 2016-03-14
Thanks for the response.  You wrote:

"If you move the swap to the SD card you will have that space available  on the 4GB card.  You will have to make a partition on the SD card for  the swap area."

I have a swap partition on the SD card and have formatted it as a swap partition.  How do I tell Ubuntu to use that as swap?

Also, if I move directories (i.e. /home) to a directory on the SD card (i.e. /media/my-sdcard/home) and then setup a link from the /home to point to the one on the SD card, that should accomplish what I want.  Correct?  I should be able to do the same with the /usr directory.  Is there a problem with that?

---

### Post by grahammechanical on 2016-03-14
I think that bab1 is making a good point. It is best to do this during installation of Ubuntu when using the Something Else option. Then we can select partitions & chose their use and give them a mount point. Look at the images in sections 4 & 5 of the wiki page

[http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation](http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation)

When we set Use As a file system (ext4) we then set a mount point. The mount points are listed in the drop down menu activated by clicking the down pointing arrow

/  = Ubuntu OS
/home = Home folder
/usr = usr folder

And so on.

We can set mount points to partitions for nearly all the system folders in Linux. This is how it was done in the very old days. It is not necessary now because hard disk space is very cheap. But it can still be done.  And in this way we can put /home on a partition of its own and even on a different hard drive. 

Regards.

---

### Post by bab1 on 2016-03-14
> **phil95 said:**
> Thanks for the response.  You wrote:

"If you move the swap to the SD card you will have that space available  on the 4GB card.  You will have to make a partition on the SD card for  the swap area."

I have a swap partition on the SD card and have formatted it as a swap partition.  How do I tell Ubuntu to use that as swap?

You set the swap in the /etc/fstab file.  Here is an example (yours will have a different UUID)```
# swap was on /dev/sdb2 during installation
UUID=12219fad-3c0c-4a00-bbe6-245024fd39d3 none            swap    sw              0       0

```
> 
Also, if I move directories (i.e. /home) to a directory on the SD card (i.e. /media/my-sdcard/home) and then setup a link from the /home to point to the one on the SD card, that should accomplish what I want.  Correct? 

I wouldn't do that.
> 
 I should be able to do the same with the /usr directory.  Is there a problem with that?
Yes.  You want the entire branch mounted seamlessly.  The /usr branch holds all the system tools.

Both @ grahammechanical and I have told you what you should do.  Bite the bullet, reinstall it with the /usr branch on the SD card.

---

### Post by mastablasta on 2016-03-15
do you really need a desktop or can you do with windows manager such as for example IceWM or jwm? they need a lot less disk space and RAM to run.

---

### Post by phil95 on 2016-03-16
I'm running on a Beaglebone Black.  I installed it from an image loaded on an SD card that flashes the OS to the internal emmc.  I wasn't given any options as to where to put anything.  Therefore, I now have the OS loaded into the emmc and am working from that perspective.

My purposes for this system at this point are:

1.  Learn about Linux
2.  Explore the BBB
3.  Setup the BBB for robotics
4.  Setup the BBB for other external control

Really, I don't really need a full desktop because I don't see the point in trying to replace my MacBook with a BBB.  However, with only 4GB available, I believe that, as I load more and more packages for future experiments (i.e. OpenCV), I will eventually run out of space (I am already at 47%).

When I asked about moving my /home directory to the SD card and putting a link to the new location, "bab1" says "I wouldn't do that".  No other explanation is given.  Please tell me why this is not a good idea.

I appreciate the response.  Please help me learn.

---

### Post by bab1 on 2016-03-16
> **phil95 said:**
> 
When I asked about moving my /home directory to the SD card and putting a link to the new location, "bab1" says "I wouldn't do that".  No other explanation is given.  Please tell me why this is not a good idea.

You didn't ask about moving any specific directory initially.  You asked how to move sections of the OS (how do I make programs install on the SD card?).  This is all on the /usr branch of the file system.  The problem is with the ownership and permissions of all the files and directories.  Most likely you will screw that up and have to reinstall the OS.  This has nothing to do with moving your data to a new location.  It only has to do with applications at /usr that expect to be in a specific location with the proper ownership and permissions.

You have been warned by 2 experienced users, do as you wish.

---

### Post by mastablasta on 2016-03-16
/home only holds user data such as user's config files and data files - not much else. programs are mostly elsewhere. if you use it without desktop (e.g for robotics) then 4 Gb should be enough.

---

### Post by phil95 on 2016-03-16
Ok, warning taken.  I'll wait until I run low on storage to mess with the SD card.  Maybe by then I'll have a bit more understanding of the system.

Thanks for the help.

---

### Post by mastablasta on 2016-03-16
yes, but if you use ext file system you should worry already when you reach  90% capacity.

still like i said if this is only experiemental and if you need a desktop interface, then try to use Windows mangers, they take up a lot less space and resources in general. e.g. jwm takes about 50, 60 Mb RAM on boot, compare that to about 400 -500 MB RAM for modern dekstops.

you also have tabed interfaces such as i3 for example. explore a bit yourself and learn ;)

---

### Post by phil95 on 2016-03-17
Thanks, some more suggestions.

At this point I have decided to re-flash the emmc for the Beaglebone, and start over.  However, since I have made that decision, I can do some experimenting before I go there.  Maybe I'll learn a few new things!

---

### Post by mastablasta on 2016-03-17
since you struggle with hard disk space this guide might come in handy: [http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

screens might be somewhat different but the process is very similar.

---

### Post by bab1 on 2016-03-17
> **mastablasta said:**
> since you struggle with hard disk space this guide might come in handy: [http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

screens might be somewhat different but the process is very similar.

Bear in mind that if you want to use the SD card space, you will need to partition the SD to use that space during install.  To do this you need to manually create and select the partitions during the install process that the OS will use for the various branches of the file system (e.g. /usr or /home or something else)..  The default install scheme will not work for the installation that we have been talking about (i.e.  using the SD card for parts of the OS file system).

You might want to read [**this**]("http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation").  Ask questions if it isn't clear what you should do.

I would find a good Ubuntu system administrator guide to read up on the basics.  A Google search reveals this slightly older [**Ubuntu admin guide**]("http://www.svecc.com/SLUG/slug_pdf/The%20Official%20Ubuntu%20Book,%207th%20Edition.pdf").

---

