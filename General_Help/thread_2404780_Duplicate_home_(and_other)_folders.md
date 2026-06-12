---
title: "Duplicate /home (and other) folders"
date: 2018-10-28
forum: General Help
---

### Post by Nick Hopton on 2018-10-28
I had my desktop PC nicely set up with the system files (Ubuntu 18.04) on an SSD drive and my data on a separate 1 TB hard drive. A problem with a power supply unit that failed left me with a system that would not boot and I thought that the answer would be to disconnect the hard drive (to protect the data) and reinstall Bionic on the SSD. Of course, what I now have is system with two /home folders, which is causing me some pain. There are of course other folders that are duplicated too.

What I'd like to do is set the /home folder on the hard disk to be my home folder. Is there a relatively simple way of doing this? I should mention that I am pretty ancient and don't know much about the internals of Linux, even though I've been using it for a number of years.

Failing a fix, would I better off going back to where I started and reinstalling Bionic in a way that would get round the problem? If so, some pointers would be appreciated, the data on the hard disk is mainly backed up, but I'd still rather not risk losing it.

---

### Post by vanadium on 2018-10-28
Because you reinstalled the same system, you can reuse your original /home on the 1 TB hard drive without problem. You can mount the home folder on the 1 TB drive to the new installation by adding a line in /etc/fstab. You can find various howo's  such as this one: [https://www.maketecheasier.com/move-home-folder-ubuntu/](https://www.maketecheasier.com/move-home-folder-ubuntu/). Your case is more simple: you already have the separate partition, you do not need to copy your home over. You essentially only need step 1, finding out the UUID of your 1 TB hard drive, and step 4, creating a new line in /etc/fstab.

This assumes that the contents of your home folder is in the root folder of the 1 TB drive.

---

### Post by Nick Hopton on 2018-11-04
Thanks for this. In fact trying to find the BUUID of my 1 TB hard disk produced results that didn't appear to make sense, so in the end I backed up the data (again), reformatted the disk and reinstalled 18.04. There was, I'm sure, something wrong with the disk and my system is now running much, much faster.

---

