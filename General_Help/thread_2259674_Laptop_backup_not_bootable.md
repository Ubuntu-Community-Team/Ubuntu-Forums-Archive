---
title: "Laptop backup not bootable"
date: 2015-01-06
forum: General Help
---

### Post by andrewniesen on 2015-01-06
Hello,

I've been backing up my Ubuntu 14.04 laptop to a USB stick using rsync.

I'm in the process of doing a fresh reinstall on my laptop but forgot to migrate one of my databases from the old install. I had thought I could just boot from the USB stick to access my old install and dump the database, but apparently the usb stick wasn't formatted for booting.

Is there any way I can create a bootable version of the data on the USB stick? 

I was hoping I could format an external hard drive for boot (not sure what this would look like in terms of partitions and disk formats) and then rsync the data from the USB stick to the external hard drive, then boot from that.

Anybody think this would work?

Thanks!

---

### Post by coldraven on 2015-01-06
I would not try to modify the USB stick that has the data on it, you may lose it.
Get another USB stick, create a persistent install on it and then copy your data to the available space.
A persistent install is a Live USB that has space to save stuff on.
Obviously you would need a working laptop to do this. You could use Unetbootin on a Windows/Linux/Mac machine if there is one around.

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by andrewniesen on 2015-01-06
@coldraven - Thanks for the response. 

I made the backup onto the USB stick so I could start over with a fresh install on my laptop, and I copied the Postgres data to my new install, but it didn't work. So I guess I have tried this approach. What I was wondering is if the new USB stick could be formatted properly as a boot disk and then copy the data (using rsync) to the properly formatted (new) USB stick so I can boot from it. Would that work? If so, what's the proper method for formatting that USB stick for boot?

---

