---
title: "why does the installer no longer give you the option to not include a swap partition?"
date: 2015-08-30
forum: General Help
---

### Post by eival on 2015-08-30
i remember this distinctly being an option in the past within the automated install method that would let you check a box to use swap just like it does now to download updates and additional third party files

now the only alternatives are the less-than-straightforward manual install process, or deleting or turning off the swap partition after we finish the install which wastes up to 16 gigs of space and if we delete and resize the main partition causes the annoying 1:30 minute "startjob" delay on each boot because its looking for that UUID which then we have to manually change system files, ect...

swap should be something manual installers deal with, if you're working hard trying to keep a 10+ year old system running, that should be more work for you, especially as SSD's are becoming more prevalent.

---

### Post by v3.xx on 2015-08-31
Last time I did this, I think was 14o4.

Use the manual partition option and create a root "/" partition.  Then close and you will be prompted to create a swap partition.  Exit the partitioner at that point and its done without swap.  I know of no check box for this.

---

### Post by efflandt on 2015-09-01
I have never really used automated install because I like to either set up partition(s) first like I want them or in some cases want to put grub somewhere other than the mbr of sda. Manual install (Other) is not that complicated. You either chose an existing partition or tell it to create a partition in unallocated space, the type of file system (usually ext4) and mount point (/ if just one partition) and to format it. There is also a drop down list at the bottom to tell it where to put grub.

I don't have swap on any of my computers because I do not hibernate my 8 GB desktop, I don't hibernate my 8 GB laptop because it boots quickly from mSATA SSD card, and I don't use my tablet PC that often which only has 1 GHz 2 core cpu, 2 GB RAM, Win7 Pro on 32 GB SSD and both Lubuntu and Ubuntu (w/common /home partition) on 32 GB SD card.

---

### Post by grahammechanical on 2015-09-01
I am confused as to what you are complaining about.

Are you complaining that the Install alongside option (or Erase disk and install Ubuntu option) will create a swap partition without asking the user if they want a swap partition? Fair enough. But then you say, "swap should be something manual installers deal with." I am confused.

Are you really recomending that the most easy method for the inexperienced person to install Ubuntu not create a swap partition? Or are you recomending that potential new users who may not know what swap is or why Linux has a swap partition be asked to make a decision on whether to have a swap partition or not?

Linux is getting a lot of new users who have working computers that came with Windows XP. These machines do not have massive amounts of RAM. Those users will need a swap partition. I think the developers have got the balance of user's needs weighed just about right.

This is not a support request.

Regards.

---

