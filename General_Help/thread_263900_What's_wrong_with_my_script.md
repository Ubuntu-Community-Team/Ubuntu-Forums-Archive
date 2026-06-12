---
title: "What's wrong with my script?"
date: 2006-09-23
forum: General Help
---

### Post by Roasted on 2006-09-23
I have two drives, each SATA, each identicle, 250 gig per. Instead of setting up raid (too poor for hardware, and got a huge headache from trying to set up software) I set up an rsync script with the help of some buddies. Unfortunately, they're not online right now.

I formatted my main SATA drive that was the boot drive. Now I got it up and running but I'm trying to get the script to work again.

Here's my script. It's quite simple. 

#!/bin/sh
mount /dev/sdb2 /media/sdb2
rsync -A ~/ /media/sdb2
umount /dev/sdb2 /media/sdb2

I granted it 755 octal permissions by doing this.

sudo chmod 755 /usr/local/bin/backup.

/usr/local/bin is where my backup script is located.

When I run "sudo backup" I get this:

jason@jason-desktop:~$ sudo backup
rsync: -A: unknown option
rsync error: syntax or usage error (code 1) at main.c(1108)

What did I do wrong? Am I missing a step?

---

### Post by Roasted on 2006-09-23
nevermind. The -A was supposed to be -a. Fixed.

---

