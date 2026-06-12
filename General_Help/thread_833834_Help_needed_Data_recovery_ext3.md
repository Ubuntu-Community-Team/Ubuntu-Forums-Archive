---
title: "Help needed: Data recovery ext3"
date: 2008-06-19
forum: General Help
---

### Post by jooyapril on 2008-06-19
I am using Ubuntu 8.04 installed via Wubi on Windows Vista Basic on Lenovo R61e. I installed Ubuntu 8.04 via Wubi. I deleted a the users home folder "/home/mark/" on my system after backing up the home user directory with HUBackup. Later I realized the backup failed :( and now I need to recover the deleted folder.  so I have tried Stellar Phoenix Linux Recovery but it does not seem to recognize the ext partition is this because it is actually installed on top of the Longhorn partition?:confused:

At any rate will someone please help me figure out how to recover the deleted folder. 

Thank you!:KS

---

### Post by greco8523 on 2008-06-19
These tools listed in this article might work:

[http://www.datarecoveryadvice.org/data_recovery_linux_recover_utilities_tools.html](http://www.datarecoveryadvice.org/data_recovery_linux_recover_utilities_tools.html)

you might want to add e2undel to you programs to try too. 

What kind of partition does wubi form within I assume the NTFS partition? if Windows is the host operating system. You might be able to mount the ubuntu wubi partition as a virtual drive and then scan it with stellar phoenix. Or even load the tools in the above link into your current ubuntu and scan the partition that way.

---

### Post by jooyapril on 2008-06-19
I want to try and use this stellar tool which is already installed on my Windows Vista BASIC system. How would I mount my Wubi Ubuntu 8.04 installation as a virtual disk in Windows Vista BASIC?:confused:

---

### Post by avtolle on 2008-06-19
Wubi installs a "virtual" partition on top of the NFTS partition, formatted (IIRC)ext3. As to mounting, the Wubi install will be within the VISTA partition, as a folder with at least one very large file contained therein. Check the Wubi Forum to see if there's any helpful information there for you.

---

