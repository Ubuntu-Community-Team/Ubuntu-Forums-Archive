---
title: "Backup entire root partition"
date: 2006-12-08
forum: General Help
---

### Post by zba78 on 2006-12-08
If I booted up using a live CD (Slax/knoopix etc.) and mounted my Kubuntu root partition, would I simply be able to use TAR to  backup the entire distro to my external hard-disk?

eg. if I do ```
tar cvvf /mountpoint/ieee1394disk1/kubuntu-backup.tar /dev/hda?/
```

Reason is I'm tempted to give Suse 10.2 a go but want to be able to return to Kubuntu if I'm not keen on it but can't be bothered to set everything up again.

---

### Post by linuchsan on 2006-12-08
Don't forget the -p and -P options

---

### Post by zba78 on 2006-12-08
Of course, tar cvvpPf ......

But if I decide to untar it all back in the future to the same partition would I be able to boot as I can now (of course making sure that Grub is setup correctly)

---

### Post by chrisccoulson on 2006-12-08
Have you seen [this]("http://www.ubuntuforums.org/showthread.php?t=81311") thread?

And yes, you will be able to restore the archive and boot from it later on, should you wish to do so. I have had to restore my whole system from a tar archive once already. The howto suggests that you shouldn't exclude /dev from the backup. However, I did exclude /dev without any issues, as well as other virtual folders (/proc, /sys, /var/run, /var/lock). Just remember to recreate the excluded folders if you restore the system.

---

### Post by zba78 on 2006-12-08
> **chrisccoulson said:**
> Have you seen [this]("http://www.ubuntuforums.org/showthread.php?t=81311") thread?

And yes, you will be able to restore the archive and boot from it later on, should you wish to do so. I have had to restore my whole system from a tar archive once already. The howto suggests that you shouldn't exclude /dev from the backup. However, I did exclude /dev without any issues, as well as other virtual folders (/proc, /sys, /var/run, /var/lock). Just remember to recreate the excluded folders if you restore the system.

That's lovely, just what I was after. Thank you

---

### Post by bodhi.zazen on 2006-12-08
I do not know if this helps, but you can copy an entire partition with gparted (I use the gparted live CD). This will copy your root partition to a new partition and you then modify menu.lst and update fstab to the new partition.

---

