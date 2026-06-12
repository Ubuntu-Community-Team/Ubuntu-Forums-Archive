---
title: "USB Thumb Drive Permissions??"
date: 2007-11-29
forum: General Help
---

### Post by Krusader3z on 2007-11-29
I'm trying to run this command

sudo zcat boot.img.gz > /dev/sda1

It is the first step for the wiki I'm following that allows me to make a bootable USB drive from which i can install linux onto other computer from.

However i keep getting this dang error

bash: /dev/sda1: Permission denied



The stick doesnt have one of those write protection toggle switch. Anyone know what I am failing to do correctly?

---

### Post by navaburo on 2007-12-01
are you SURE that /dev/sda1 is the USB drive? Because if you have a sata harddisk then chances are that is your first harddisk partition and you could easily hose your system running that command.

So be careful!

That said, try using dd to copy the data over. Or try changing the permissions with chmod.

Something like:

```
sudo chmod 666 /etc/sda1
```

Also, it is possible that you want to write to the master boot record to make the drive bootable.

That would be /dev/sda not /dev/sda#


best of luck!

---

