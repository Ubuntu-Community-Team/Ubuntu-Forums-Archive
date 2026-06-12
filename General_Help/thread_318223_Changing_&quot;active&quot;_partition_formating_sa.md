---
title: "Changing &quot;active&quot; partition formating: safe this way?"
date: 2006-12-13
forum: General Help
---

### Post by celsofaf on 2006-12-13
Hey, I have Kubuntu installed on hda5, which is ext3-formated. However, I'd like to experiment with XFS a bit. I have an unused hda6 and my hda5 data would fit on it. Is it safe to, for example, from some LiveCD (perhaps Kubuntu itself) mount both hda5 and hda6, transfer my hda5 data to hda6, format hda5 to XFS, then transfer the data back to hda5? Would I need to do anything else to make it working?

Perhaps two things to consider: I have no personal data in hda5 (I could easily "loose it" without any headache), and my /boot is mounted to hda2.

---

### Post by bodhi.zazen on 2006-12-13
Well, you are half way home .....

With XFS as a root partition you will need a /boot partition.

Ij you do not mind it may be just as easy to install onto XFS just to check it out. 

If you like you can migrate your current root ext3 to XFS. I would use tar rather then copy.

See here: [Copy a partition](http://ubuntuforums.org/showpost.php?&p=1628330&postcount=7)

And this: [Backup a partition](http://doc.gwos.org/index.php/Backup_restore_system)

HTH

---

### Post by celsofaf on 2006-12-13
Oh yes... I forgot: I also need to have the /etc/fstab updated accordingly. ;) Seems like I had some foresight when I last installed Kubuntu when I put /boot on a separate partition then. :D

I will check the links. Thank you very much!

---

### Post by bodhi.zazen on 2006-12-13
If you need help with fstab just ask....

---

### Post by celsofaf on 2006-12-13
OK, it worked fine! ;) This is what I did, gonna post it here so other people can do it themselves if needed... Note: hda5 is my Kubuntu partition, hda6 (also ext3) is the empty one.

(1) Loaded Kubuntu (Edgy) LiveCD
(2) Opened a terminal and gone superuser (dangerous! but I did it): sudo su
(3) mkdir /media/kubuntu /media/rescue
(4) mount -t ext3 /dev/hda5 /media/kubuntu
(5) mount -t ext3 /dev/hda6 /media/rescue
(6) cd /media/kubuntu
(7) cp -ax * /media/rescue
(8) cd /media/rescue
(9) umount /dev/hda5
(10) Loaded QTParted and formated hda5 to XFS (yes... could also have used the terminal)
(11) mount -t xfs /dev/had5 /media/kubuntu
(12) cp -ax * /media/kubuntu
(13) nano /media/kubuntu/etc/fstab (to edit the fstab; just look for the / partition entry and replace ext3 by xfs)
(14) rebooted to Kubuntu on the hard drive... and prayed... ;)

I didn't delete my hda6 files at the time "just in case", but it worked realy fine. :D Now I know I can free my hda6 partiition again.

Thank you all for the help!

---

