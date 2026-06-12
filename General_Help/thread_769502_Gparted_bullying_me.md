---
title: "Gparted bullying me"
date: 2008-04-26
forum: General Help
---

### Post by CorruptNoob on 2008-04-26
So I've been 'appending pending operations' for near an hour now, it's currently at the "real resize" stage, and I have no idea what's going on.

Apparently canceling the operation can cause SEVERE DISK ERRORS!!!! So I'm a bit worried right now, any help?

---

### Post by logos34 on 2008-04-26
If you're resizing the left boundary of the partition, it takes a LOT longer, so be patient.

---

### Post by adult swim on 2008-04-26
youve just got to wait it out!  one time i got the bright idea to shrink some partitions and then  move them all around.  i think it took over 4 hours to finally finish!

---

### Post by CorruptNoob on 2008-04-26
If you meant the block to the far left.. yes it's being resized.. a question, is it best to have..



[Windows][/home][/]

or

[Windows][/][/home]


Windows will be mounting /home, does it matter where it's positioned?

---

### Post by imtheguru on 2008-04-26
It is a batch tool. Keep the operations simple and they'll complete quicker with reduced probability of failures.

---

### Post by adult swim on 2008-04-26
if you will be accessing home from windows i would throw home in the middle so it is right next to either windows or /

---

### Post by CorruptNoob on 2008-04-26
Great so not only do I have to wait for this 2hour partitioning process but.. due to my poor judgement I have to do it again and re-order them

Thank you, let's talk about something more interesting, like how can I have seperate wallpapers for each monitor using Twinview?

---

### Post by adult swim on 2008-04-26
i wouldnt worry about doing it again, its not really going to speed up anything.  if you really want the windows | /home | /  and you can back up your /home partition on an external drive i would just delete all of your linux parttions and click apply.  then create the partitions you will be using for /home and / and then reinstall ubuntu.  i cant help you with your monitor issues.

---

### Post by CorruptNoob on 2008-04-26
I'm quite confused by your reply.. you want me to have my /home partition externally?

---

### Post by adult swim on 2008-04-26
> **CorruptNoob said:**
> I'm quite confused by your reply.. you want me to have my /home partition externally?
sorry about that.  if i were you i wouldnt do it all over again.  the performance increase is only negligible.  my suggestion was for if you wanted to have it set up  as windows /home / .  after you backed up your /home externally and deleted your linux partitions like the earlier post says, once everything was reinstalled you would copy your /home backup to your new /home partition.

---

### Post by CorruptNoob on 2008-04-26
Hmm, all my partitions except the windows one are fresh. My ubuntu and home partitions have nothing in them (aka clean install, new linux user)

so I don't need to back up /home! 


However, I have a question, I've apparently deleted dells diagnostic partition, what the hell is that :d

thanks

---

### Post by adult swim on 2008-04-26
the internets tell me that it isnt that important.  i have a dell and wiped the whole drive including the diagnostic partition.  i dont think i ever used it and i saw somewhere that all of the tools on the diagnostic partition are on your dell recovery cd that came with your computer.

---

### Post by CorruptNoob on 2008-04-26
Cool, hey thanks a lot for your help and time, I really appreciate it :)

---

### Post by CorruptNoob on 2008-04-26
So, I deleted my Recovery and Diagnostic partitions

ended up with


NTFS Windows
EXT3
EXT3

(reserved for / and home)


I restart to make some final adjustments to my windows partition (backing up a few files etc)

turns out windows won't boot, my PC just keeps restarting...


Uhoh!

---

### Post by adult swim on 2008-04-26
what windows?
post the output of ```
sudo fdisk -l
```

---

### Post by CorruptNoob on 2008-04-27
Device Boot      Start         End      Blocks   Id  System
/dev/sda1            7650       18182    84606322+  83  Linux
/dev/sda2           18183       19387     9679162+  83  Linux
/dev/sda3   *           1        7649    61440561    7  HPFS/NTFS

Partition table entries are not in disk order



WindowsVista... it's dead!

---

