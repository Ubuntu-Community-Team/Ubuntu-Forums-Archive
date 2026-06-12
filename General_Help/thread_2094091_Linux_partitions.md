---
title: "Linux partitions"
date: 2012-12-12
forum: General Help
---

### Post by arunkumargoge on 2012-12-12
when i install ubuntu server in partitoon disk screen i got 4 option
1.Guided- Use entire disk
2.Guided- Use entire disk and set up lvm
3.Guided- Use entire disk and set up encrypted lvm
4.Manual
Which one should i choose? What is the advantage over the other choice? have to know everything about it pls help me..

---

### Post by offgridguy on 2012-12-12
This depends on how you want to set it up.
  Maybe give us some idea of what your plans are.

---

### Post by chadk5utc on 2012-12-12
> **arunkumargoge said:**
> when i install ubuntu server in partitoon disk screen i got 4 option
1.Guided- Use entire disk
2.Guided- Use entire disk and set up lvm
3.Guided- Use entire disk and set up encrypted lvm
4.Manual
Which one should i choose? What is the advantage over the other choice? have to know everything about it pls help me..

Each has advantages and as asked before really depends what you want to do with it?
If security is important Id go with encrypted lvm the only downside to this is that it requires someone to enter a password if the machine is restarted. But again it does make it more secure. As for using the entire Disk(s) this also depends if you want it to be the only OS on the drive or are you planning to setup a Dual boot Linux/Windows or some other OS?

---

### Post by Wim Sturkenboom on 2012-12-13
I would always choose manual partitioning. That way I can create the partitions as I want them, not as what Ubuntu has in mind. Separate /, /var and /home. Depending on needs a dedicated partition for mysql.

For my webservers, I don't use /var/www and /var/lib/mysql. That way a runaway log file that fills up /var does not affect e.g. mysql.

The advantage of lvm is that you can easily add extra space to a logical volume when you run out of diskspace. I however don't use it as it, in my opinion, adds an additional layer that can break; I might have that wrong however, but I'm of the careful and conservative type.

---

