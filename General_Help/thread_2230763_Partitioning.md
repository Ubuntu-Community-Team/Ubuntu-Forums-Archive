---
title: "Partitioning"
date: 2014-06-20
forum: General Help
---

### Post by DrTaylor on 2014-06-20
I am having trouble getting my active partition resized. I've been trying to use fdisk and parted but it doesn't seem to allow me to do this. Has anyone had experience with this? How did you solve it?

---

### Post by LastDino on 2014-06-21
You can't partition/resize partitions which are mounted. You will need to boot in to live USB/DVD mode of Ubuntu. That is; ''Try Ubuntu''.

Then use Gparted there. 

Word of caution and a question: This could very much cause data loss or OS corruption, which partitions are we talking about and why are you trying to resize them?

---

### Post by Bucky Ball on 2014-06-21
> **LastDino said:**
> You can't partition/resize partitions which are mounted. You will need to boot in to live USB/DVD mode of Ubuntu. That is; ''Try Ubuntu''.

Then use Gparted there. 



^^^
This. But prior to this and while you're there, backup anything you don't want to lose before you do anything else, then fire away.

---

