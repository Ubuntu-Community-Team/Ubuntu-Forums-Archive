---
title: "How to completely uninstall Ubuntu 8.04 ?"
date: 2008-05-21
forum: General Help
---

### Post by whitesands on 2008-05-21
I have a dual boot set up with ubuntu 8.04 and Windows Vista...I would like to do a completely remove ubuntu and restore Visa..I tried using the GNome partition editor to do this but some of the partitons are locked...How do I unlock these partitions and also identify which ones are for ubuntu ?

---

### Post by StooJ on 2008-05-21
Gnome partition editor should be able to do this just fine.

The partitions may be locked because you are using Ubuntu. Try downloading the gparted livecd (very small download) and boot from that. Then delete the Ubuntu partitions and resize your vista partition to recover the space.

[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

Obviously; please do not steal software.

---

### Post by overdrank on 2008-05-21
> **whitesands said:**
> I have a dual boot set up with ubuntu 8.04 and Windows Vista...I would like to do a completely remove ubuntu and restore Visa..I tried using the GNome partition editor to do this but some of the partitons are locked...How do I unlock these partitions and also identify which ones are for ubuntu ?

And to add
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)

---

### Post by pdwerryhouse on 2008-05-21
The partitions will be locked because you're using them; boot the system off your ubuntu cd and use Gparted from there...

---

### Post by bodhi.zazen on 2008-05-21
This thread is a step-by-step guide :

[http://ubuntuforums.org/showthread.php?t=508927](http://ubuntuforums.org/showthread.php?t=508927)

---

### Post by whitesands on 2008-05-22
Thank you for the responses...

 If I have a back up Vista CD is it possible to just boot up the gparted live CD and delete the ubuntu partitions...Then load the Vista cd ?

 Wouldn't that remove ubuntu and restore vista and the MBR without issues ?

 Thank you....

---

### Post by StooJ on 2008-05-22
No. The step-by-step guides are your way to go. Follow them and you'll get sorted.

---

### Post by ronaldv2li on 2008-09-10
What about GRUB?

---

### Post by bodhi.zazen on 2008-09-10
> **ronaldv2li said:**
> What about GRUB?

What about it ?

The link I posted reviews exactly how to remove grub if that is what you are asking.

---

### Post by ronaldv2li on 2008-09-10
Yeah, that's it. But my problem was that I deleted ubuntu partitions and then was unable to boot. I used Super Grub. It's another bootloader. [http://forjamari.linex.org/frs/?group_id=61&release_id=499]("http://forjamari.linex.org/frs/?group_id=61&release_id=499") Just had to download an .iso file, then create a bootable CD.

---

