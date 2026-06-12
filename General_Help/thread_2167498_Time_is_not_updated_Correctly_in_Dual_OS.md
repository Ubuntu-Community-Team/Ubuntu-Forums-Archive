---
title: "Time is not updated Correctly in Dual OS"
date: 2013-08-13
forum: General Help
---

### Post by nachinew on 2013-08-13
Hi,

I installed Dual OS are Ubuntu and Windows 8, when ever I using this OS simultaneously or not simultaneously both the OS time is not up to date. Please guide me how to fix this small  issue and what is the root cause of this issue.

---

### Post by Slug71 on 2013-08-13
You probably did not set your location when, at least on Ubuntu, when you did the install.

Just clock on the time at the top right of your Ubuntu Taskbar and click "Time and Date Settings". you can choose your correct time zone there.
If i remember correctly, It's the same with Windows. Just click on the time and you can change your settings.

---

### Post by tgalati4 on 2013-08-13
Sometimes there is a setting in your computer's BIOS to set the time to UTC (universal time).  Also, there is a switch within Windows to set time to UTC, but you will have to search for it.  Linux uses UTC as the time base and offsets it with your timezone to display the correct time.  

If you log into Windows and local time base is used then when you shut down the local time base is stored to BIOS time.  When you then boot into linux, the local time is read and treated as UTC which then incorrectly displays your time as + or - your timezone offset.  Annoying but fixable.

---

### Post by nachinew on 2013-08-14
> **tgalati4 said:**
> Sometimes there is a setting in your computer's BIOS to set the time to UTC (universal time).  Also, there is a switch within Windows to set time to UTC, but you will have to search for it.  Linux uses UTC as the time base and offsets it with your timezone to display the correct time.  

If you log into Windows and local time base is used then when you shut down the local time base is stored to BIOS time.  When you then boot into linux, the local time is read and treated as UTC which then incorrectly displays your time as + or - your timezone offset.  Annoying but fixable.

I did not get U. How to Fix, please guide how to update this in BIOS setting.
I already selected my Home Country in Ubuntu and Windows 8. But I did not find out where the problem raised.

---

### Post by Slug71 on 2013-08-14
Just enter your BIOS and look around if there is a way to edit the time.

---

### Post by Mark Phelps on 2013-08-14
Change Ubuntu to use localtime.

To make the change in Ubuntu, edit edit /etc/default/rcS and change

UTC=yes to no, like this:

```
# assume that the BIOS clock is set to UTC time (recommended)
UTC=no
```

---

### Post by nachinew on 2013-08-14
> **Mark Phelps said:**
> Change Ubuntu to use localtime.

To make the change in Ubuntu, edit edit /etc/default/rcS and change

UTC=yes to no, like this:

```
# assume that the BIOS clock is set to UTC time (recommended)
UTC=no
```

Thanks for your help.

---

