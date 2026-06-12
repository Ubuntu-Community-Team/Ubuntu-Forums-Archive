---
title: "apt-get errors (unable to update)"
date: 2008-02-11
forum: General Help
---

### Post by b00tl3g on 2008-02-11
Hey everyone getting this error when trying to do anything with apt-get. 

I have tried sudo apt-get update, tried sudo apt-get upgrade, sudo apt-get autoclean 


Nothing just keeps spitting this out. Can someone please help>?


andre@IT-DEV:~$ sudo apt-get upgrade
Reading package lists... Error!
E: Problem parsing dependency Pre-Depends
E: Error occurred while processing slapd (NewVersion1)
E: Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_gutsy-updates_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.

---

### Post by apetresc on 2008-02-11
> **b00tl3g said:**
> Hey everyone getting this error when trying to do anything with apt-get. 

I have tried sudo apt-get update, tried sudo apt-get upgrade, sudo apt-get autoclean 


Nothing just keeps spitting this out. Can someone please help>?


andre@IT-DEV:~$ sudo apt-get upgrade
Reading package lists... Error!
E: Problem parsing dependency Pre-Depends
E: Error occurred while processing slapd (NewVersion1)
E: Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_gutsy-updates_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.

Could you post the contents of your /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_gutsy-updates_main_binary-i386_Packages file?

---

### Post by b00tl3g on 2008-02-11
its quite large I don't think i should copy pate it here... its 1044kb large.


I've also noticed that i can't open the file with gedit, only can do a cat on it.
when trying to open with gedit i get the:

gedit has not been able to detect the character coding.
Please check that you are not trying to open a binary file.
Select a character coding from the menu and try again.

error

---

### Post by b00tl3g on 2008-02-11
anyone???

---

