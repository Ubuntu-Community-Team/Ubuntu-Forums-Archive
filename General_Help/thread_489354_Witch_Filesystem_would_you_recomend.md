---
title: "Witch Filesystem would you recomend?"
date: 2007-07-01
forum: General Help
---

### Post by nalinde on 2007-07-01
OKi, so i have a new harddrive, 250, that i've going to use for backing up my dvd:s ~1 GB, e-books and manuscripts, larger text files. So to the question... witch Filesystem should i use? One FS that can handle large files easily an a lot of smaller text files, i would prefer. I've given ReiserFS i thought.. but i'don't know actually... else i will stick with ext3... oki.. thanks anyways :-)

---

### Post by tpg on 2007-07-01
I use ext3 on my external hard drive, and I've never had any issues. I don't know if it's the most efficient, but it's reliable.

---

### Post by BlackAnthrax on 2007-07-01
I use Ext3, but if you are paranoid for various reasons 
;)
I would suggest looking into encrypting the disk, as I do. You will see a slight slow down, but it works, and also can be mounted in Windows/Mac.
Encrypting the disk and benefits of doing so can be found here.
[http://techystuff.info/?p=28](http://techystuff.info/?p=28)

---

### Post by bodhi.zazen on 2007-07-01
+1 ext3

I have dabbled with several file systems and IMO ext3 is most stable and reliable. These are features you want if you are using the drive for backups.

---

### Post by mang on 2007-07-01
I've used ext3 for along time, and before that ext2. I've never really had a problem with either.

---

### Post by Rui Pais on 2007-07-01
I use XFS for a partition that gets big files i download from the net, like compressed source files, isos, music and films. I moved /var/cache/apt/archives to that partition too (and made a symlink to there).

Apart from that i use ext3 for all / and /home.

I used to set my /boot as ext2 (and for portage tree, when i used Gentoo), but give up use separated boot partitions.

---

### Post by nalinde on 2007-07-02
Awesome, thanks for your replies!! :-)

Well, think i will stick with ext3.. as many people say: It's stable and works really good.

Looked around yesterday and found a wiki about **ext4 **though. Whats the deal with it? is that project done or is it still under dev. ? Found a lot of people saying that is finished and stable, even supported by the kernel? but can't really find any software that supports it so i can give it a try on a partion....

@BlackAnthrax - Hehe,well i'am familiar with truecrypt. Used it ever since the Anti piracy office started to raid the university connections. Pufft.... I'am so sick at this. if the only could provide me  
with their products with out DRM and "Up haussed" prices and the possibility to use it in my GNU/Linux OS.

---

### Post by BlackAnthrax on 2007-07-02
Yes, truecrypt is great software.

---

