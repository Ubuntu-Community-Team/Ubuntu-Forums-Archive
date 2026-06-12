---
title: "Reinstall system - how to handle the zfs pool?"
date: 2020-12-29
forum: General Help
---

### Post by mattiash on 2020-12-29
I have my storage server running Ubuntu server 20.10 with an zfs pool (consiting of 5 vdevs and in total 10 disks). 
I need to reinstall the system.

What is best way to do that?
1) Blow the current SSD and reinstall Ubuntu and do a zfs import -f pool?
2) Install new system on a another SSD and do and export from the old system and then do an import on the new?
3) Are you mad? Keep the old system, fix it instead, dont take this risk with the pool!

To be clear I do want the pool to be intact and keep all the data. Pretty much I want the install a new system and reconnect the pool to that.

---

### Post by TheFu on 2020-12-30
Do whatever you like, just be 100% certain you have a disconnected backup tat can be restored before beginning for any files you can't lose.  20.10 is NOT an LTS release. IMHO, all software is beta on non-LTS releases. 

Good luck.

---

