---
title: "apt-get error  - want to verify possible solution please."
date: 2014-05-10
forum: General Help
---

### Post by nosmadar on 2014-05-10
My system is runnning Ubuntu 12.04 and up to this point was fully updated.
Here is the error. which first appeared about 2 days ago:

robert@robert-Thor:~$ sudo apt-get check
[sudo] password for robert: 
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise_universe_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.

Here is the solution I found but am hesitant to try:

[FONT=Courier New]sudo rm /var/lib/apt/lists/* -vf  
 sudo apt-get[/FONT]

because it involves using "rm" with "-f"  

Thanks in advance.

---

### Post by slickymaster on 2014-05-10
Moved to the **General Help** sub-forum.

Please do try the following:```
sudo rm /var/lib/apt/lists/* -vf && sudo apt-get update
```

---

### Post by nosmadar on 2014-05-10
Thanks!!!  that worked.

---

### Post by slickymaster on 2014-05-10
You're welcome. Glad you got it fixed.

---

