---
title: "I can't login in"
date: 2017-03-02
forum: General Help
---

### Post by jjherg3344 on 2017-03-02
So I have a compaq presario v3614au. It's got some old AMD Turion X2 64 processor, 2 gigabytes of ddr2 memory and Nvidia GeForce Graphics. 

When I first installed ubuntu onto this machine, I had serious graphics glitching problems. I solved this issue by installing the graphics driver by booting ubuntu with "nomodeset"

It now doesn't login in and gives me another error. [ATTACH=CONFIG]273953[/ATTACH]


Does anybody know how to solve this problem?

---

### Post by howefield on 2017-03-02
Not seeing the error image.. perhaps you could use the edit post button and then the paperclip icon to attach it to your post ?

---

### Post by jjherg3344 on 2017-03-02
ok

---

### Post by mörgæs on 2017-03-02
Are you able to get to a terminal, for example by selecting recovery mode from the boot menu?

---

### Post by ajgreeny on 2017-03-02
Looks to me as if this is an LVM problem of some sort from the original post's image, but unfortunately that is not much help to me as LVM is not something I have used.

Can you please type the full text of that error if you can not get into Ubuntu to copy and paste it here.

---

### Post by jjherg3344 on 2017-03-02
yes in reply to [mörgæs]("https://ubuntuforums.org/member.php?u=939075")[COLOR=#000000]  [/COLOR]

---

### Post by ajgreeny on 2017-03-02
> **jjherg3344 said:**
> yes
Please be a bit more helpful.
What are you answering with this post; that you are using LVM, or that you will try to type the full error, rather than show an image?

---

### Post by jjherg3344 on 2017-03-02
> **ajgreeny said:**
> Looks to me as if this is an LVM problem of some sort from the original post's image, but unfortunately that is not much help to me as LVM is not something I have used.

Can you please type the full text of that error if you can not get into Ubuntu to copy and paste it here.

ivactad is not active yet, using direct activation during sysinit
/dev/napper/ubuntu--vg-rot: clean, 188954/7233536 files, 1497488/28920832 blocks

---

### Post by mörgæs on 2017-03-03
Why do you use LVM? Isn't it a lap computer with a single harddisk? 

Let's see the hardware details. Please run ```
sudo lshw -sanitize > lshw.txt
``` and post lshw.txt in CODE tags.

---

