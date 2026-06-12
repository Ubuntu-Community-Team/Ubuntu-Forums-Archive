---
title: "btrf input/output error"
date: 2020-12-15
forum: General Help
---

### Post by daves00 on 2020-12-15
Hi,

I am running the desktop version of Ubuntu 18.04.5, using the system as a media server.
I have btrfs raid 1 on my media partition

 I had a powerfail and this has left a couple of errors in two specific sub-directories. All other files/folders are intact and function perfectly

1. Ran btrfs scrub - this gave 2 unrecoverable errors
2. from using ls - it looks like 2 directories are corrupt 
3. I am happy to loose these 2 directories - I have backed up of the important data in these directories and have moved that data out of the directory and stored on a different machine.
4. I have tried using rm * to delete the files that are supposedly remaining in these directories - i get cannot remove,  "Input/output error"
5. I have tried rm -R ./folder/*  i receive the same "Input/output error"

I have a backup, but would rather not reformat the partition and restore 2 TB of data from my USB external drive if at all possible.

What is the best way of killing these 2 directories/repairing the filesystem?

is 'btrfs -repair' a sensible route to try?

Thanks in advance
Dave

---

