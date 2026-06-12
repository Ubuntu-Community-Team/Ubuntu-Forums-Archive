---
title: "Can't See External HDD"
date: 2015-11-18
forum: General Help
---

### Post by shane_faulkinbury2 on 2015-11-18
I have this 1 TB external HDD that I'm unable to see in Ubuntu.  Here are some screenshots taken using Gparted of some of the unmounted portions of the HDD which I think are part of it.  There is also a screenshot of my home folder which doesn't show the drive either.  I'm wanting to format the entire drive to NTFS so I can see it both on Ubuntu and Windows.  Is the only way of doing this to use Dban first or is there a way to complete this using Ubuntu?

---

### Post by sudodus on 2015-11-18
Are there any important data on the drive, that you want to recover before wiping it?

In that case that has the highest priority.

After that, you can use [mkusb](https://help.ubuntu.com/community/mkusb). It is 'almost always' enough to wipe the first megabyte, and after that create the partition table and file system.

See these links

[mkusb#Wipe_the_first_megabyte_or_the_whole_device](https://help.ubuntu.com/community/mkusb#Wipe_the_first_megabyte_or_the_whole_device)
[mkusb#Wipe_menu](https://help.ubuntu.com/community/mkusb#Wipe_menu)

You can select

**b "Big drive: create GUID partition table with NTFS partition" **

and do it automatically.

But it is also possible to do it with ***gparted***.

---

### Post by shane_faulkinbury2 on 2015-11-18
Thanks, mkusb worked great!  Now I have my HDD back!  :p

---

