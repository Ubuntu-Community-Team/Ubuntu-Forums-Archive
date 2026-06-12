---
title: "backup error"
date: 2012-12-26
forum: General Help
---

### Post by fco3d on 2012-12-26
Hello everyone,
I am pretty new to Ubuntu, I just build a small server for my little Home studio, Ubuntu 12.04 LTS.
I have 2 identical 2T hard drives, I am using one to hold working files and I want to use the other one for back up, now after putting all my files one the server (around 800Gb) I tried to back up all that info using the default backup software, after dealing with some permission error it worked, but it give me an error at the end, not able to copy or backup several files.
Then I tried other software (file Backup Manager) and I had several errors.
Then I did try (Back in time) same error at the end.

I am complete new to this OS, everything seems to work fine until the very end that give me an error and skip some files or it does not copy any at all.
Is this a permission problem?

I looked online for some solutions but I can't find any similar problem
 any guidance would be appreciated.

Thank you in advance.
Fco.

---

### Post by sahabcse on 2012-12-27
Hi

Which backup software are you using and how did you mount the secondary hdd. 

Paste the o/p of

#mount -a
#fdisk -l

---

### Post by fco3d on 2012-12-27
Hi,
I did used GParted to set up the disk, created a partition, format and mounted.

at the beginning I used the default back up software that come with Ubuntu, I think it is Deja dum??
but it give me writing errors?? then I tried File Backup Manager and lastly Back in Time, both of them start to work, took forever and at the end give a error.

I afraid I do not understand when you say

"Paste the o/p of

#mount -a
#fdisk -l"

---

