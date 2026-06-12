---
title: "Unison for syncing files"
date: 2008-01-01
forum: General Help
---

### Post by mlho on 2008-01-01
My old, physically infirm, but otherwise normal functioning laptop has, for some time now, served as a desktop.

Now have a new laptop. Wanting to sync various directories. rsync is uni-directional, so have been trying out Unison.

Unison does what is supposed to, but needs a bit of guidance for conflicts and very slow as under default settings, it checksums every single file.

Using the **-fastcheck true** option forces it to use time stamps instead, so considerably faster, but having problems syncing between a NTFS directory and a FAT32 directory.

rsync has the option of **-modify-window=1** which allows a little bit of leeway for timestamps to make allowances for minor differences in the way different file systems store time stamps.

Can't seem to find an option on Unison, but I may have missed it. Can anybody help?

Mark

---

### Post by paxmark1 on 2008-03-14
here is an old post I put up awhile back which allows me to use the command line version of unison with vfat usb stick.  Still waiting on a reply.  Hope this helps you.  I really do like rsync and unison, bit of a learning curve.

side issue.

I had problems with unison between puter and USB, but got it to work in the text mode via appending

-perms=0


How can I get that set up for the graphical GTK version of unison?

peace

---

