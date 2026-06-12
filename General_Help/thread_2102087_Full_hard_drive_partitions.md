---
title: "Full hard drive partitions"
date: 2013-01-06
forum: General Help
---

### Post by maartenpeels13 on 2013-01-06
My operating system is Windows 7.
I recently tried installing Ubuntu, without succes. Two times it almost worked, but I got an error message at the end and my laptop crashed. I am not looking for tips for installing, my real problem is that afterwards my memory was almost full. Before installing i Had used around 65 Gigabytes, afterwards more than 140! My total memory is 145 gig. What happened? Can it be fixed?

---

### Post by bhaveshnande on 2013-01-06
Windows 7 does not detect Linux partition formats like ext(which is used by Ubuntu). As you have installed Ubuntu but it failed, your Windows system won't show the space used for installing Linux. 
You can use [EasUS Partition Manager]("http://download.cnet.com/Easeus-Partition-Master-Home-Edition/3000-2248_4-10863346.html") to view all partitions and delete linux ones. 

Later you will need a Windows 7 installation CD to repair your MBR (If you delete the partition where Ubuntu was installed)

Alternatively you can boot into Ubuntu Live USB/DVD, install gParted on it and manage your partitions.

---

### Post by maartenpeels13 on 2013-01-06
> **bhaveshnande said:**
> Windows 7 does not detect Linux partition formats like ext(which is used by Ubuntu). As you have installed Ubuntu but it failed, your Windows system won't show the space used for installing Linux. 
You can use [EasUS Partition Manager]("http://download.cnet.com/Easeus-Partition-Master-Home-Edition/3000-2248_4-10863346.html") to view all partitions and delete linux ones. 

Later you will need a Windows 7 installation CD to repair your MBR (If you delete the partition where Ubuntu was installed)

Alternatively you can boot into Ubuntu Live USB/DVD, install gParted on it and manage your partitions.
I installed and ran the program, but how can I see if it's a Linux Or Windows partition?

---

### Post by offgridguy on 2013-01-06
> **maartenpeels13 said:**
> I installed and ran the program, but how can I see if it's a Linux Or Windows partition?
Can you get a screenshot, and post it here. ?  Use paperclip icon to attach.

---

### Post by maartenpeels13 on 2013-01-06
> **offgridguy said:**
> Can you get a screenshot, and post it here. ?  Use paperclip icon to attach.

Here[ATTACH]229671[/ATTACH]

---

### Post by Impavidus on 2013-01-06
The ones labeled "other" are linux partitions, the ones labeled "NTFS" are windows partitions.

---

### Post by oldos2er on 2013-01-06
Memory and hard disk space are two different things; fixed thread title.

---

### Post by offgridguy on 2013-01-06
Hello, your total HD space is 298 gb.  Your windows partition is getting full as windows
works best with about 30% free space.
 Since you are not interested in reinstalling ubuntu, you can expand your existing windows partition to whatever you like.

---

### Post by maartenpeels13 on 2013-01-07
> **Impavidus said:**
> The ones labeled "other" are linux partitions, the ones labeled "NTFS" are windows partitions.

It says that I have to buy the full version to delete the partitions. Is that really neccary?

---

### Post by oldfred on 2013-01-07
What software are you talking about and what are you doing. In Windows they often give you partial versions to get you started but then want you to pay for the full version or upgrade every year.

Of course with most things Linux there is no charge. There may now be new games that will charge and some very highend software in Linux that has fees.

---

### Post by maartenpeels13 on 2013-01-07
> **oldfred said:**
> What software are you talking about and what are you doing. In Windows they often give you partial versions to get you started but then want you to pay for the full version or upgrade every year.

Of course with most things Linux there is no charge. There may now be new games that will charge and some very highend software in Linux that has fees.

I meant this [http://www.easeus.com/download.htm]("http://www.easeus.com/download.htm")

---

### Post by oldfred on 2013-01-07
I believe in general it is better to use Windows tools for Windows & Linux tools for Linux. But since I am a Linux user, I use gparted for partitioning.

---

### Post by maartenpeels13 on 2013-01-09
> **offgridguy said:**
> Hello, your total HD space is 298 gb.  Your windows partition is getting full as windows
works best with about 30% free space.
 Since you are not interested in reinstalling ubuntu, you can expand your existing windows partition to whatever you like.

How do I do that?

---

### Post by FuzzyFeat on 2013-01-09
I would reccomend using the live UBUNTU CD and GPARTED to delete and resize the partitions.

---

