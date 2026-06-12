---
title: "Making a new partition from within 7.10"
date: 2007-11-18
forum: General Help
---

### Post by Akira Mishima on 2007-11-18
Hi all

I am another Linux newbie, and went for Ubuntu. I have installed it as dual-boot alongside with Windows XP and everything seems to work all right. However I would like now to give /home its own partition. In this forum I found how to do that, but the problem is that from within GParted I cannot create the new partition since almost all menu commands are grayed out after selecting the partition I want to carve the new one into. Here are my questions:

1) Is it safe to create the new partition from Windows? (Partition Magic)
2) I have not completely understood yet what goes inside the /home directory apart from settings: if the various applications are installed in the main Ubuntu partition, what safe is safe to keep the /home partition?

Many thanks

Akira Mishima

---

### Post by dpar on 2007-11-18
The commands are grayed out because you can't resize a partition that is mounted. You should use the livecd to do the partition editing.

---

### Post by Akira Mishima on 2007-11-19
Thank you dpar

It was indeed like you said.

Kind regards

---

