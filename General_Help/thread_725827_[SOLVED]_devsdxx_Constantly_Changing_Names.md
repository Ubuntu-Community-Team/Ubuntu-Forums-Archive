---
title: "[SOLVED] /dev/sdxx Constantly Changing Names"
date: 2008-03-16
forum: General Help
---

### Post by Jaymoon on 2008-03-16
I apologize if this situation I'm in seems confusing, but I'll try to explain it the best I can...

Basically my setup is this:
1 80GB drive with Ubuntu 7.10 installed (only a couple days since fresh install)
1 149GB drive with music on it
1 153GB drive with DVDs on it

My drives are setup this way internally:
80GB drive primary SATA drive
149GB drive secondary SATA drive
153GB drive primary PATA drive
DVD burner secondary PATA drive

Apparently what is happening is that my devices are switching names each time I boot.  I'll give you an example...

I have my /etc/fstab file configured to mount the Music drive to /home/jaymoon/Music.  The DVD drive is set to mount at /home/jaymoon/DVD.

Everything mounts fine.  Except that once I reboot, sda1 became sdc1.  Because of that, sdc1 becomes sdb1, and sdb1 becomes sda1.

Next time I reboot, the order is all screwed up again.

Here's a screenshot:
[IMG]http://i32.tinypic.com/2jbmkhc.png[/IMG]

Now I simply reboot without modifying anything, and here's what I get now:
[IMG]http://i27.tinypic.com/308le2x.png[/IMG]

Is there any way to tell my system to keep a device location the same every reboot?

---

### Post by louieb on 2008-03-16
If your changing the boot order in BIOS the device names are going to change. Thats why Ubuntu went to using the UUID in /etc/fstab and  /boot/grub/menu.lst. 

So just wondering are you changing the boot order with BIOS?
Are you using UUID or labels in /etc/fstab?:confused:

Might try using e2label to give your partitions a label. Then use the label in /etc/fstab to set your mount points.

---

### Post by Jaymoon on 2008-03-16
Thank you very much *louieb*, that seemed to work (for now).

I've rebooted a couple times, and the directories are mounting where they need to be.

For those that want more information on the steps I took to use e2label, I followed this:
[http://www.redhat.com/docs/manuals/linux/RHL-7.3-Manual/ref-guide/s1-filesystem-ext3-create.html#S2-E2LABEL](http://www.redhat.com/docs/manuals/linux/RHL-7.3-Manual/ref-guide/s1-filesystem-ext3-create.html#S2-E2LABEL)

---

### Post by chrisccoulson on 2008-03-16
If you're identifying filesystems in your fstab using UUID's, then this shouldn't happen. This is why UUID's are used by default.

---

### Post by Mordac85 on 2008-04-25
That was certainly frustrating.  Thanks for pointing me to the UUID's.  I have a Precision 670 where I added 2 SATA and 1 SCSI drive and it was changing on every boot!  I was listing them by name and I guess the system likes to change that on a whim b/c I didn't make any BIOS changes.

Now that I got the UUID using vol_id and sotred out fstab, all is well and seems to be stable.

---

