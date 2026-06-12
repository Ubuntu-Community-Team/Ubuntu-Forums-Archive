---
title: "Delete File in UDF Iso"
date: 2018-05-07
forum: General Help
---

### Post by purebasic on 2018-05-07
Hello,

im using Ubuntu 18.04 LTS and i need to remove a file within an bootable ISO-Image containing Win7-Install.

What i have already tried:

Mount the ISO and copy the files into a folder on my HDD, remove the unwanted file (ei.cfg) in folder and create new ISO-image with k3b.
The Problem is, that the new ISO File is no more bootable in virtualbox.
There is an option "Edit Boot Images" in k3b but i have no idea what to set there.

I also tried with ISO Master but it does not support "UDF" file system. 
When i try to open the Original ISO-Image it creates only a txt file which says : "This disc contains a "UDF" file system and requires an operating system that supports the ISO-13346 "UDF" file system specification."
Latest UDF-Tools package is installed in the System.

When i try to add the files from the Folder to create new ISO it failed because my install.wim is larger than 4 GB.

Is there an easy way to delete this File within the ISO?

---

