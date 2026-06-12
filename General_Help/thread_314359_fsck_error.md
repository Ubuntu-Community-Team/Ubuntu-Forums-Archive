---
title: "fsck error"
date: 2006-12-07
forum: General Help
---

### Post by cacharreo on 2006-12-07
Hi people
Yesterday I did hibernate my computer for first time. Today I have had the surprise that two different HD's cannot be mounted. I have checked  the *chekfs* Log file of  generated but I don't know how to fix this problem.](*,) ](*,) ](*,) 
Can somebody help me with this?:-D 
Following you'll find the text from the *chekfs* Log file

[B]fsck -C -R -A -a 
Thu Dec  7 18:54:30 2006

fsck 1.39 (29-May-2006)
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
/dev/hda1: 71713 files, 4886217/5110723 clusters
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
/dev/hda2: 29 files, 264300/3602322 clusters
fsck.ext3: Unable to resolve 'UUID=3b895f8e-8d45-4496-b542-20407846bf78'

fsck died with exit status 8

Thu Dec  7 18:54:41 2006
----------------

[/B]
Thank you in advance  ](*,) ](*,)

---

### Post by esaym on 2006-12-07
Perhaps try loading the live cd and checking the file systems from that?  If they are in a clean state you will have to force it with -f command

---

### Post by cacharreo on 2006-12-07
SOLVED !! :p

---

### Post by esaym on 2006-12-07
> **cacharreo said:**
> SOLVED !! :p

Using my advice or what? :confused:

---

