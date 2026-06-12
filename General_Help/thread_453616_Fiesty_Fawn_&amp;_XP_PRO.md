---
title: "Fiesty Fawn &amp; XP PRO"
date: 2007-05-24
forum: General Help
---

### Post by JupiterMike on 2007-05-24
My Desktop has XP Pro installed.  I would like to utilize Fiesty Fawn also.  I don't wish to eliminate XP and install Fiesty Fawn.  I guess I could try a Virtual PC on the desktop. I have tried Wubi & Microsoft Virtual PC,   neither one could I get to work. I would like to try installing to a external hard drive or some other Virtual PC system.  The problem is I don't know how to do any of these. Is there any simple way this idiot can try?

---

### Post by AnRa on 2007-05-24
You can install Ubuntu and Windows on the same hard drive.
Maybe you find this useful: [https://help.ubuntu.com/community/Installation/I386](https://help.ubuntu.com/community/Installation/I386), just be careful when partitioning, also make sure that you fully understand what you are doing. ;)

---

### Post by stchman on 2007-05-24
> **JupiterMike said:**
> My Desktop has XP Pro installed.  I would like to utilize Fiesty Fawn also.  I don't wish to eliminate XP and install Fiesty Fawn.  I guess I could try a Virtual PC on the desktop. I have tried Wubi & Microsoft Virtual PC,   neither one could I get to work. I would like to try installing to a external hard drive or some other Virtual PC system.  The problem is I don't know how to do any of these. Is there any simple way this idiot can try?

If you want to install Feisty and keep XP in a dual boot configuration all you need to do is insert the Ubuntu LiveCD and boot wit CD.

Once in there fire up the Gnome Partition Manager (grapted).

I am going to assume that you have one HDD in your desktop PC and you have one big partition.  If so when you fire up gparted bring up the HDD that has XP installed on it.  Resize the NTFS (assumed) partition to about 30G smaller than it was before.

Next you need to apply the changes.  You may need to do a defrag and chkdsk /f in windows.

Leave what is left over as free space.  When you install Ubuntu tell it to use the free space.  GRUB will be installed and you will be a dual booter.

Now if you have multiple partitions in your HDD then just use disc manager to delete a partition and leave it as free space.

I hope this answers your question.

---

### Post by doogy2004 on 2007-05-24
You could try vmware server, it is free.  Check it out at [www.vmware.com](www.vmware.com).  The only thing that you need to do is request a key, which is also free.

---

