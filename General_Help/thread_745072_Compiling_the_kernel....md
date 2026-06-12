---
title: "Compiling the kernel..."
date: 2008-04-04
forum: General Help
---

### Post by POW R TOC H on 2008-04-04
I'm compiling the new 2.6.24.4 linux kernel. The problem is, I have less than 900Mb free space left in my root directory (yes, I know, it's stupid). Compiling the kernel requires me (according to some tutorials, I'm new at this) to untar it to my /usr/src dir, and configure, then 'make'. The problem is, there isn't enough space... I'm sorry if this is a newbie question, but is it safe and possible to compile the kernel somewhere in my /home directory, and them 'make install' it regularly? After this (if everything is OK) I can erase my old kernel, and free some space...

---

### Post by danwood76 on 2008-04-04
you can recompile it in your home directory without any issues.
Infact its safer to recompile in your home than in /usr/src as that requires root access.

I normally build the kernel (and all my software) in a folder called build in my home directory and ive never had any issues.

---

### Post by POW R TOC H on 2008-04-04
Thank you. And I have one more question... If I want to mount a partition to a specific non-empty directory in my root dir, is there a way to get the same files on the mounted partition that were there before mounting?
Specifically, what I want to do is mount a new partition (about 10 Gb) to /usr/src so I can have space for multiple kernel sources (I want to learn a bit of module programming, so I think it's wise to have another kernel to roll back to in case of an emergency...)
I was thinking of booting up my LIVE GParted distro, so I can safely copy the files from /usr/src to the new partition, and then mount it as /usr/src... Is this safe, and can you tell me of any bad thins that might happen?

---

### Post by danwood76 on 2008-04-04
To be honest its easier if you leave those folders alone and just use a seperate partition.
You can make sym links from the /usr/src to wherever you build your kernels.

So for example if I have a partition /mnt/kernels and in it I have kernel-2.6.25.
I can create a symlink in the /usr/src dir to it and then I can compile as if it was actually in that directory.

So cd /usr/src/kernel-2.6.25 would cd to my extra partiton but the address would still read /usr/src/kernel-2.6.25

I hope I made that clear.

---

### Post by POW R TOC H on 2008-04-04
Yes, in fact, you did. You also solved my problem. Thank you very much!

---

### Post by brian_p on 2008-04-04
> **danwood76 said:**
> Infact its safer to recompile in your home than in /usr/src as that requires root access.

As a matter of interest, there is the fakeroot package.

---

### Post by POW R TOC H on 2008-04-04
> **brian_p said:**
> As a matter of interest, there is the fakeroot package.

What is that :O ?

---

### Post by brian_p on 2008-04-04
> **POW R TOC H said:**
> What is that :O ?

It basically provides for package building and installation by pretending to be root.

The full description will be in your package manager. Or do

apt-cache show fakeroot

in a terminal.

---

