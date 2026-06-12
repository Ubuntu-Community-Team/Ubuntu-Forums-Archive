---
title: "timeshift wont start"
date: 2019-02-19
forum: General Help
---

### Post by bobsone on 2019-02-19
Hi
I have a new install Mate 18.04 and have attempted to include Timeshift.
The install completed successfully but Timeshift won’t start, the enter password window comes up and accepts the password but nothing else happens after that.
I tried launching from the terminal with sudo timeshift-gtk but this only returns;
[Warning] Deleted invalid lock
**
ERROR:arraylist.c:1199:gee_array_list_real_get: assertion failed: (index
< _size)
Aborted

My net searches found some posts where people had problems starting Timeshift but I haven’t found anything where Timeshift won’t even launch from the terminal.

Any help appreciated...

Regards.

---

### Post by rbmorse on 2019-02-19
How did you install Timeshift?  

I used the teegee2008 ppa as the source for my install in Cosmic and didn't have any trouble.

---

### Post by bobsone on 2019-02-20
Thanks for the reply

I tried installing/uninstalling via the Synaptic Package Manager and from the terminal with
```

sudo apt-add-repository-y ppa:teejee2008/ppa
sudo apt-get update 
sudo apt-get install timeshift 

```
A little more info:
I have two (laptop and desktop) Mate 18.04 systems successfully running Timeshift, the current install is a desktop  Core2Duo E6750, and an Asus   Maximus II Formula motherboard.

---

### Post by rbmorse on 2019-02-20
Thanks for verifying the install source. That looks correct. 

Thanks also for the equipment profile.  From what I see on [https://teejeetech.in/timeshift/](https://teejeetech.in/timeshift/) Timeshift doesn't run on equipment of that vintage.  It requires an EFI system using the GRUB2 bootloader.

---

### Post by bobsone on 2019-02-21
Oh... :oops:
Thanks for your effort to identify the issue, it is appreciated

It never occurred to me to check if it is EFI!

---

