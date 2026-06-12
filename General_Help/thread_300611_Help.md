---
title: "Help"
date: 2006-11-15
forum: General Help
---

### Post by bmx161x on 2006-11-15
I have a Sony Vaio FS760 laptop. I currently has Windows XP Home edition installed on it. I made recovery disks for it, and I'm looking to wipe the harddrive and install ubuntu (not dual boot) . If i do this will I be able to recover XP with the recovery disks after Ubuntu is installed if I wanted to?

Thank you for your help

---

### Post by organica on 2006-11-15
If it is like my Acer, it will have another partition probably about 4 gigs in size.  This is your recovery partition.  Don't destroy it.  Your recorvery cd pulls from that partition to recover the Vaio factory install.  Otherwise you'll have to use a purchased Windows XP cd.

---

### Post by bmx161x on 2006-11-16
i have another partition that is 6 gig. it only shows up in disk manager. if i were to chose the wipe option in ubuntu would it wipe that partition as well. im new to all of this so i have noooo idea what im doing.

---

### Post by strabes on 2006-11-16
> **bmx161x said:**
> i have another partition that is 6 gig. it only shows up in disk manager. if i were to chose the wipe option in ubuntu would it wipe that partition as well. im new to all of this so i have noooo idea what im doing.

Yes if you chose that option it would wipe your entire hard drive. Instead of choosing that option, choose the 'manually partition the disk' option. Then, delete all partitions except that 6gig one. Create one partition for the main ubuntu installation, and another for swap. The latter should be about twice as big as the amount of ram you have, so if you have 1 gig of ram make the swap partition 2048mb. The partition that you are going to install ubuntu on should take up the rest of the space on your harddrive unless you have a 250gig HDD or something. So, it should look like this: 

(6gig-restoration)(***gig linux installation)(2048mb - swap)

Trust me, you won't want to go back to windows once you try linux for 1-2 weeks. At first you're going to be like what the hell is going on but after that you'll like it way more than windows. It's good that you found this forum; it helped me a lot when I was new too. You should also check out [www.ubuntuguide.org](www.ubuntuguide.org). It has tutorials for lots of things in ubuntu. It's really useful.

---

### Post by bmx161x on 2006-11-16
i already tried to partition for dual boot, and for some reason my hard drive doesnt have any unallocated space so i couldnt partition. i have an 80 gig hdd and its not even close to full. its still totally stock so would that be a setting that vaio did or do i really not have any unallocated space? i am totally new to installing os's and partitioning drives etc. i apprecaite all of your help.

---

### Post by organica on 2006-11-16
> **bmx161x said:**
> i already tried to partition for dual boot, and for some reason my hard drive doesnt have any unallocated space so i couldnt partition. i have an 80 gig hdd and its not even close to full. its still totally stock so would that be a setting that vaio did or do i really not have any unallocated space? i am totally new to installing os's and partitioning drives etc. i apprecaite all of your help.

Try these.  A video to help you dual boot install windows and edgy.
[http://video.google.com/videoplay?docid=-6104490811311898236]("http://video.google.com/videoplay?docid=-6104490811311898236")

And your best friend after you have Ubuntu installed.
[http://ubuntuguide.org/wiki/Ubuntu_Edgy]("http://ubuntuguide.org/wiki/Ubuntu_Edgy")

Good Luck and stick with the forums.  People here will help with the learning curve.

---

### Post by bmx161x on 2006-11-16
thanks alot for all the help. i really appreciate it. i toyed with ubuntu a bit recently and it seems awesome. i think instead of dual booting i might just install ubuntu and get rid of windows all together. again i appreciate all the help, and ill be sure to post with any other questions

---

### Post by bmx161x on 2006-11-16
i also was wondering if you were able to run itunes in ubuntu. is it just a matter of installing or is there more involved

---

### Post by organica on 2006-11-21
definitly more involved.  You need to install "wine" or better yet, get a copy of CodeWeavers' CrossOver Linux [http://www.codeweavers.com/beta/cxlinux/]("http://www.codeweavers.com/beta/cxlinux/")

You can install itunes, but you can not burn audio cd's with it.  Just use the newest version of Banshee, Rhythmbox, or Songbird (coolest).

---

### Post by cantormath on 2006-11-21
> **bmx161x said:**
> I have a Sony Vaio FS760 laptop. I currently has Windows XP Home edition installed on it. I made recovery disks for it, and I'm looking to wipe the harddrive and install ubuntu (not dual boot) . If i do this will I be able to recover XP with the recovery disks after Ubuntu is installed if I wanted to?

Thank you for your help

I would suggest not using "Help" as a title.  Try to be more descriptive.
Just a suggestion.

---

