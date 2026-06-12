---
title: "Erm I lost /usr/bin/ and I need some help getting it back"
date: 2007-06-22
forum: General Help
---

### Post by jeffisawesome on 2007-06-22
I did something stupid using the mv command and I lost /usr/bin/ is there a way to get it back using my live CD or am I hosed?  I can get to all my files and stuff, but I'd rather not have to reinstall.

---

### Post by Bachstelze on 2007-06-22
*"There are two types of *nix sysadmins : those who have already done a big blunder with the root account, and those who will do one very soon."*

Congrats, you've moved to the upper category, now you're in for a reinstall :)

---

### Post by jeffisawesome on 2007-06-22
I was afraid of that.  Though I do say that if ubuntu didn't have this screwy sudo stuff going on then GUI dependent newbs like myself wouldn't screw up trying to do stuff from terminal.

Well, at least I didn't lose anything except a bit of pride.  Thanks anyway.

---

### Post by NeoLithium on 2007-06-22
Depending on how you partitioned, you may not lose your files. Di d you have a seperate /home partition when you set it all up, or was it the 'Use entire Disk' and let Ubuntu do it's thing.  Should you have seperate partitions, you can just install the / partition and leave the /home and any other storage you have, the way it is and choose not to format.

---

### Post by Silenus on 2007-06-22
what do you mean screw sudo stuff, sudo had nothing to do with you moving your directory. Why were you mv'ing around as root anyway ;), curiosity killed the cat. But a reinstall or follow the steps listed above will fix it.

---

### Post by jeffisawesome on 2007-06-22
Too late I already dumped the files onto my flash drive using the Live CD and formatted the hard drive, but that's ok same difference.

I was trying to mv a couple things into /usr/bin/ but I guess I got the command backwards.

Anyways posting from my brand new Ubuntu install.  Gotta love an OS that takes 20 mins to install and like 5 mins to run updates. :p

Thanks guys!

---

### Post by NeoLithium on 2007-06-22
> **jeffisawesome said:**
> Too late I already dumped the files onto my flash drive using the Live CD and formatted the hard drive, but that's ok same difference.

I was trying to mv a couple things into /usr/bin/ but I guess I got the command backwards.

Anyways posting from my brand new Ubuntu install.  Gotta love an OS that takes 20 mins to install and like 5 mins to run updates. :p

Thanks guys!

I know what you mean. When I first started Ubuntu, I reinstalled like 12x or something, it actually makes it not so bad to do a full reinstall, though I am sure now to have a seperate /home partition and a seperate /data for my files.

---

### Post by jeffisawesome on 2007-06-22
Heheh I'm clever... "sudo nautilus" solves my little problem command line mental block problem kinda cheating though huh?  I take back all that bad stuff I said about sudo :D

---

