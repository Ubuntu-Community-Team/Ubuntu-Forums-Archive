---
title: "how to recover files from encrypted home folder."
date: 2014-05-14
forum: General Help
---

### Post by rizos on 2014-05-14
i have a partition for root and another for home, the partition of home had all my files after a fresh install i forgot to enable the home partition as home again, the result was that i lost the partition home and files, i created a new home partition on the same partition of the old one and recover part of my files, is there a way to copy all the other  files from old home (enrcypted, yes i have the passphrase) to the new home folder?

the old files i know they are there using the sudo ecryptfs-recover-private command.


thanx a lot.

---

### Post by HiImTye on 2014-05-15
did you back up the volume header to a file? if the answer is no, then you aren't likely to be able to recover anything.
remember, the point of encryption is to make it nearly impossible to recover without the encryption information

---

### Post by p.callan on 2014-05-15
I have a similar problem. A broken Ubuntu 13.10 on one partition and my files on another, encrypted partition.
I have two files on my desktop that I HAVE TO copy out before I format the OS partition.
In root:

cd Desktop
user/Desktop/

dir
TOR.desktop

This is completely wrong though. Why are my files not listed here? And how do I copy them to the USB stick?
If I format 13.10 and install 14.04 and install truecryt again, will I still be able to access my encrypted partition?

---

### Post by rizos on 2014-05-15
@HiImTye "the old files i know they are there using the sudo ecryptfs-recover-private command."

all my files are aviable from the tmp folder, what you talking about?.

i just wonder if there is a way to recover the account so i can use it as usual.

---

### Post by HiImTye on 2014-05-15
> **rizos said:**
> i created a new home partition on the same partition of the old one and recover part of my files

please clarify what is meant here, because it sounds like you erased your encrypted partition and made a new one.

---

### Post by rizos on 2014-05-18
sorry for the late answer.

i delete the old paritition but recovered, now from a new account i can access my files at /tmp/ecryptfs.gJgf3jrP, im wondering if there is a way to get this files and my old account in anyway besides copy to a new location as i dont have an external hard drive or space to do it on the same pc.

---

