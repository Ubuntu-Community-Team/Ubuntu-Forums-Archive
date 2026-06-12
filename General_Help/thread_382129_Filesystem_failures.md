---
title: "Filesystem failures?"
date: 2007-03-11
forum: General Help
---

### Post by lungdart on 2007-03-11
I have Beryl installed via the following tutorial [http://wiki.beryl-project.org/index.php?title=Install_Beryl_on_Ubuntu_Edgy_with_nVidia&oldid=5232](http://wiki.beryl-project.org/index.php?title=Install_Beryl_on_Ubuntu_Edgy_with_nVidia&oldid=5232) (The automatic script has been since removed because the repos for them went down.) It worked beautifully, then a friend tried to burn a CD with it, and the program (gnome baker, and K3b) kept crashing. After that I noticed Totem wouldn't load, so I decided to give the system a reboot. I used quit in the system menu, and it also wouldn't load, so I got fed up and hit the old faithful reset button.

But this time around fsck check failed on hda1 which is my home mount. I wasn't sure how to fix it so I did an init 0 to restart, but it just loaded my computer normally without a home folder. So I shut my computer off for the night and decided to have a look at it the next day.

My room mate turned the computer on and it seemed to work fine. I went on and tried to put in an audio cd but it could not find the cd rom drive (hdc1) and also my public mount (hdd1)

My computer has three hard drives. a 10 gig broken into to partitions hdb1 "/"  and hdb2 "swap" Theres also an 8 gig as hda1 "/home" and a 200 gig hdd1 as "/public".  The first two drives are ext 3 and the public drive is ext2 (formated by mistake, and now theres just too much data to change on it)

My computer works perfectly. My /home is there (hda1) but I just don't have my public folder and my cd drive. They don't show up in /dev either. Any suggestions?

---

### Post by dcstar on 2007-03-11
> **lungdart said:**
> 
............
My computer works perfectly. My /home is there (hda1) but I just don't have my public folder and my cd drive. They don't show up in /dev either. Any suggestions?

If you can, boot up with the Live CD and do a manual **fsck** on all the hard drive partitions.

That may help, but the drive problems may have been caused by something else which has corrupted your install.

---

