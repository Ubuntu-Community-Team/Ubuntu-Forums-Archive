---
title: "Urgent: Root partition has changed name. Cannot boot."
date: 2007-02-26
forum: General Help
---

### Post by Loffe_ on 2007-02-26
Hello!

I fiddled a little with my partition tables and now Edgy wont start correctly.

Partition table before:

sda1 ntfs winxp
sda2 extended
sda5 ntfs win data
sda6 ntfs nothing
sda7 ext3 root
sda8 swap
sda9 ext3 data

I removed the sda6 since it was unused and it rendered in this new table:
sda1 ntfs winxp
sda2 extended
sda5 ntfs win data
sda6 ext3 root
sda7 swap
sda8 ext3 data

As you can see the linux partitions changed shifted one step and when I rebooted grub couldn't "mount /dev/sda7 on /" Not weird because sda7 now was swap

By pressing e in the grub menu I could change the root entry to the right device and I could boot into Edgy again. :) 

The problem now is that a lot of things don't work: networking, sound, etc...

Also if I install a new kernel the grub menu is updated to the old partition again, and I have to edit it from sda7 to sda6 again...

Is there a way to fix this annoying problem?

Or is it easier to add the removed partiotion again?

---

### Post by Tesiph on 2007-02-26
Use ```
sudo gedit /boot/grub/menu.lst
``` and edit the part that says
```
## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,5)

```Edit the last line to the correct device, probably (hd0,4) in your case. Don't remove the #. That will fix your kernel update problem.

I'm not sure about the other problem. Editing you partition table should not have any effect on the rest of the system.

---

### Post by Yoooder on 2007-02-26
What utility did you use to edit your partition table?  I don't know of any that will move partitions when one is removed.

It is *possible* that you might have lost a lot of data as a result of this.  Would you be good enough to post the name of the utility and your end-results from this once you get your machine back up and running?  It would be handy for the community to know.

---

### Post by Loffe_ on 2007-02-26
**Tesiph:**
Your code was not *exactly* the one I needed but it helped me find a solution. I have grub on a secondary drive together with the /boot partition on (hd0,0) or hdc1, and that one is still the same...

I just had to change this &#8595; in /boot/grub/menu.lst
# kopt_2_6=root=/dev/sda6 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

I also made a "sudo dpkg-reconfigure linux-image-2.6.17-11-generic" to rebuild the menu.

After a reboot it worked. When GDM showed up the usual sound was heard and when I logged on I realized that the network was working too :D


**Yoooder:**
There seem to be no data lost at all. 
I used a live cd called SystemRescueCD with the well known program GParted.
Could the reason of the name changes be that this was inside an extended "lba" partition?


/Loffe
Back on track :D

---

