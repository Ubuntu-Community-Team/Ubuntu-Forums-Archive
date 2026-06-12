---
title: "fix bad sectors/blocks on NTFS hdd with dd?"
date: 2013-05-28
forum: General Help
---

### Post by MrsUser on 2013-05-28
I know how to smart-fix bad blocks on a Linux partition without reformatting the whole partition, but by specifically rewriting the sectors in question by calculating their position.  I followed this guide:
[http://smartmontools.sourceforge.net/badblockhowto.html](http://smartmontools.sourceforge.net/badblockhowto.html)
This is a quick way to get rid of pending sectors.

However, I'd like to know how to do this for NTFS partitions? Does anyone know how or can point me to an instruction?

---

### Post by Rebelli0us on 2013-05-28
You have to boot a Windows OS the check/repair NTFS partitions, Linux can't do it.

---

### Post by Mark Phelps on 2013-05-28
As an alternative, if you know someone with a Windows PC, have them download and burn the Minitool Partition Wizard Boot CD.

Then, boot from that and use the Check option against the partition in question.  That will run CHKDSK for you.

---

### Post by MrsUser on 2013-05-28
Thanks. I know about CHKDSK, but I wanted a quick way to rewrite the bad sectors. CHKDSK checks the whole partition and it'd take ages for a 3TB hdd :-/ In Linux, I can use the technique described in the link I have given. It's a very quick way with dd and I wanted to know if there is an equivalent for NTFS partitions, so that I can specificially only rewrite those bad sectors instead of having to run a maintenance on the whole partition.

---

### Post by SuperFreak on 2013-05-28
Not meaning to hijack this thread, but
> **Mark Phelps said:**
> As an alternative, if you know someone with a Windows PC, have them download and burn the Minitool Partition Wizard Boot CD.

Then, boot from that and use the Check option against the partition in question.  That will run CHKDSK for you.

I downloaded and burned MiniTool   Partition Wizard Boot CD  in Ubuntu and burned the image with K3B. I am able to boot to this disk and it seems functional. I ran a "Surface Test" on an external NTFS disk, but the option to Check the disk for errors (this presumably is chkdsk) is grayed out and unavailable.

EDIT: Minitool disk says that partition must have a letter designation to run "Check the Disk". It provides an option to change letter designation but unfortunately that option is greyed out also and is unavailable

---

### Post by MrsUser on 2013-05-29
Hello, thanks for all the replies. Meanwhile, I decided to backup my data and reformat the hdd to ext4 for easier handling in the future. Currently, I am transfering back my data from the backup. Happy to be 100% Linux now :)

---

