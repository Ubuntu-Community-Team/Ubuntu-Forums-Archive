---
title: "Latest Kernel Update = System Borked"
date: 2006-07-12
forum: General Help
---

### Post by mrgnash on 2006-07-12
I updated to the latest kernel this morning (2.6.15.26) and encountered the message afterwards that my /boot partition was at 100% capacity... so I went back and deleted my old kernels from 25 down. Lo and behold, when I rebooted there was no GRUB entry for 26 and I couldn't use 25 for obvious reasons. In addition, when I check my /boot partition with yaREG, there appears to be NO files whatsoever. So before I do what I suspect I have to do - reinstall :( - can anyone tell me if there's any way I can possibly recover my system? I've put so much work into getting compiz running and my desktop all beautified :(

---

### Post by ericesque on 2006-07-12
although I find it easy to get everything up and running again, you're not screwed.

you can get grub back simply by throwing in an alternative Dapper install disc (I couldn't get it to work with a live cd) and going through the standard install until you get to the part where it asks you how you want to set up your disk/partitions.

select to 'edit the partition table manually'  

you can mount each partition without overwriting it.  Simply select each partition one at a time and set the mount point to what it was originally.  

*warning*
There is a line that says 'keep my current data' (or something to that effect)  hitting enter will change it to 'format this partition'.  Make sure you leave your data for each partition.
*/warning*

Once you have set the mount point for each of your partitions, select the option at the bottom that says 'Done setting up the partitions'.


It will force you to format your swap partition.  No big deal for obvious reasons.  It may complain that you haven't set up a partition to install the filesystem.  It's okay.  All we're looking to do is install grub. You may need to select an option like 'Ok'  or 'continue anyway'.

eventually, you'll end up where it will ask you if you want to install grub.  This has been our goal from square one, my advice: install it.

From there, you should at least have grub.  You may want to do a little repartitioning so that you have more space on your /boot partition.  Gparted offers a live cd that you could use to expand the space on your /boot.  I think mine is 80MB --which may be overkill, but I won't miss 20MB here or there.  And if you ever want to install new splash screens, I believe they are stored in the /boot partition.  Messed me up a while ago.

If you need more help-- or a better explaination, I know there is a thread in the How-To section.  Something about "how to fix your MBR if it's screwed up."  Maybe I'll find the gumption to actually provide links here soon.

...maybe not.

---

### Post by mrgnash on 2006-07-12
I actually still have GRUB, it's just that all the kernel entries no longer function (because the kernels aren't there to boot) -- and thre's no entry for 2.6.15.26

---

### Post by hanzomon4 on 2006-07-12
You could try this....

Boot a ubuntu live cd and enter rescue mode.

After it ask you some questions it will ask you what hard-drive/partition you what to mount. mount whatever drive your linux install is.

The next screen will be blue and will have some words in the bottom left corner. 
Press ctrl+alt+F2.

next, type > mount -tproc proc /target/proc

next, type > chroot /target

then, type > su

you should now be able to install kernels edit /boot/grue/menu.lst

---

### Post by Ramses de Norre on 2006-07-12
Could you explain a bit what you do with those commands? It interests me. I understand what those commands do but I don't see why you mount /target/proc/ and chroot into /target/. (and I'd like to learn it ;))

---

### Post by Rui Pais on 2006-07-12
> **mrgnash said:**
> I actually still have GRUB, it's just that all the kernel entries no longer function (because the kernels aren't there to boot) -- and thre's no entry for 2.6.15.26

hi,
why you don't simply edit the entry for the old .25 and replace all .25 with .26.

You can edit by choosing the old entry on grub and press letter 'E' on keyboard instead of <Enter>. 
Replace the .25 with .26 and press 'B' (for boot). 

Those changes are not permanent. So after you still need to edit menu.lst and redo the changes...

Another approach is boot from a livecd mount the boot partition and do the changes on menu.lst.

...assuming, of course, that your .26 kernel instalation was ok!

---

### Post by hanzomon4 on 2006-07-12
> **Ramses de Norre said:**
> Could you explain a bit what you do with those commands? It interests me. I understand what those commands do but I don't see why you mount /target/proc/ and chroot into /target/. (and I'd like to learn it ;))

[Link]("http://ubuntuforums.org/showthread.php?t=80811&highlight=breezy+usb+boot")

---

### Post by Ramses de Norre on 2006-07-12
> **hanzomon4 said:**
> [Link]("http://ubuntuforums.org/showthread.php?t=80811&highlight=breezy+usb+boot")
But they don't explain it there neither, I'm interested in the the reason why you have to mount /target/proc/ and chroot into /target/ and what is that target directory actually?

---

### Post by hanzomon4 on 2006-07-12
I'm not sure, I just followed the directions to install ubuntu on a usb. It changed the file system from the one on the live cd to the one on my usb ubuntu install, not sure how or why.

---

