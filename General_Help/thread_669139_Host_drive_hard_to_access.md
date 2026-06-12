---
title: "Host drive hard to access"
date: 2008-01-16
forum: General Help
---

### Post by jaddi27 on 2008-01-16
Hi,

I recently installed the latest Gusty version of Wubi (rev 386) on my laptop. 

I had a few installation problems. Wubi installed fine on Vista, but after the restart, the Ubuntu installation would keep stopping at a different % and then had to be restarted. I got the install to work by plugging in my external USB hard drive (no, wubi wasn't installed to this) - I don't know what this did but the install went right through first time with it plugged in. I'm now posting this from ubuntu wubi.

My problem is that it is hard to access the host drive, as it is not mounted under /media/host, instead it is under /host. Also, /host is not r/w by everyone, making it hard to copy files to it.

I can mount the host drive under somewhere such as /media/windows with full read write access using ntfs-3g. However I would like it to display in the 'Computer' view in nautilus and, if possible, on the desktop.

Any help with this would be much appreciated.

Thanks for such a great program,

Joel

---

### Post by ago on 2008-01-17
The /host drive is a bit delicate since it hosts your virtual hard disks
Having that in /media/host would create a problem if for instance you unmount it by accident. 
That would be equivalent to rip off your hard disk...

You may try to chown/chmod a folder in there and symlink that to a more convenient location

---

### Post by gsrkashyap on 2008-01-31
i have 2 windows dirves (c&d) d drive is rw accessible but where as c drive is not can you help me .  when i access from nautilis it creats  a folder disk in /media folder and when i try to change the permissions both chown/chmod with root privileages.

---

### Post by ago on 2008-01-31
you need to have administrator right to write to /host

sudo cp /file/to/copy /host/target/folder

---

### Post by polmir on 2008-01-31
type i terminal
```
gedit /etc/fstab
```
and post out of it

---

