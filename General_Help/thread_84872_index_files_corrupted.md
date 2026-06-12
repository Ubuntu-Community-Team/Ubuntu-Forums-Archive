---
title: "index files corrupted"
date: 2005-11-01
forum: General Help
---

### Post by kuap on 2005-11-01
Hello,

A week ago I decided to upgrade my hoary to breezy and results were great.

However, today I did a apt-get update + upgrade and I got the following error message:

E: The package index files are corrupted.

I took the same sourceslist found in the upgrading_to_breezy howto thread.

Any suggestions?

---

### Post by Xian on 2005-11-01
Does it not list another line in the error msg that begins, "No Filename:"?

---

### Post by newbie2 on 2005-11-01
can you try again ... it was for a while for me too , but now it is fixed for me with another try ;)

---

### Post by jdong on 2005-11-01
Have you tried **sudo apt-get clean; sudo apt-get update**?

This may be a nasty one....

---

### Post by kuap on 2005-11-05
Yes I've tried apt-get clean + apt-get update + apt-get upgrade

and I still get the following error:

Reading package lists... Done
Building dependency tree... Done
The following packages will be upgraded:
  khelpcenter konsole libgda2-3 libgda2-common libgl1-mesa libgl1-mesa-dri
  libglu1-mesa nvidia-kernel-common sudo
9 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
E: The package index files are corrupted. No Filename: field for package nvidia-kernel-common.


Even though it says "No filename:" error for package nvidia-kernel-common, some days ago I was receiving the same error on a different package.

---

