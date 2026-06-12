---
title: "Guidance on 'Using &quot;Backup&quot; in Ubuntu 12.10'"
date: 2012-12-04
forum: General Help
---

### Post by felkar on 2012-12-04
I have recently installed "Ubuntu 12.10 and signed up for "Ubuntu One".

I note that Ubuntu One has a default entry called "deja-dup" and that this  has to do with the backup routines used by the (installed) "duplicity" package.

I also note that "duplicity" has a man-page entry that is [COLOR="Red"]1100[/COLOR] pages long.  As I am an amateur (and geriatric) Linux user, I find this discouraging.

If there are introductions to "backup" routines, that are written for raw novices, I would welcome being pointed to them.

felkar

---

### Post by ibjsb4 on 2012-12-04
First narrow it down a bit.  Do you want on-line backup, HDD, synchronize, clone?  

I use on-line backup just for personal files, to try to upload my complete system would just be to time consuming for me.

I find backing up my entire system to a second HDD much faster.  So I can just clone the whole thing.

[http://clonezilla.org/](http://clonezilla.org/)

For keeping files up to date, either locally or remote you can sync a backup.  I use rsync for this.  Rsync is part of the default Ubuntu install, but is a terminal only app.  So to give it a frienly face (GUI) you can add something like grsync or luckybackup to it.  Both are in the software center.

[http://en.wikipedia.org/wiki/Grsync](http://en.wikipedia.org/wiki/Grsync)

[http://www.howtoforge.com/creating-backups-with-luckybackup-on-an-ubuntu-9.04-desktop](http://www.howtoforge.com/creating-backups-with-luckybackup-on-an-ubuntu-9.04-desktop)

I don't use deja-dup so don't know how easy it is to use.  Just know that the ones I use are.

---

### Post by felkar on 2012-12-05
> **ibjsb4 said:**
> First narrow it down a bit.  Do you want on-line backup, HDD, synchronize, clone?  

SNIP

For keeping files up to date, either locally or remote you can sync a backup.  I use rsync for this.  Rsync is part of the default Ubuntu install, but is a terminal only app.  So to give it a frienly face (GUI) you can add something like grsync or luckybackup to it.  Both are in the software center.

SNIP

I don't use deja-dup so don't know how easy it is to use.  Just know that the ones I use are.


It looks as though I need to do some "background" reading!

In the past (on Debian) I used the "snapshot" package to run weekly updates of crucial directories (e.g. /home, /etc and /usr). I have also used "rsync" to copy the whole system (before attempting a "Debian Update to a later version" routine).

Now that I have switched to Ubuntu, I thought there was merit in learning to use the supplied "deja-dup" package.  But I have failed to find a "beginner's guide" to "deja-dup".

The "Ubuntu Software Centre" - which does not list "snapshot" - does list "Back in Time".  From the description and the "users comments", this appears to do the same as the (Debian) snapshot package.

The  listed "user comments" - with **one** exception - were all very favourable; almost all users gave it a "5 star' rating.

What more could anyone ask.

Thanks you for your advice and the pointers.

felkar

---

### Post by felkar on 2012-12-06
> **felkar said:**
> It looks as though I need to do some "background" reading!

SNIP.

The "Ubuntu Software Centre" - which does not list "snapshot" - does list "Back in Time".  From the description and the "users comments", this appears to do the same as the (Debian) snapshot package.

The  listed "user comments" - with **one** exception - were all very favourable; almost all users gave it a "5 star' rating.

What more could anyone ask.


felkar

Follow-Up
=========

Contrary to the posted info, "Back in Time" needs some additional tweaks in a Ubuntu 12.10 environment.

And the suggested package described in:

 [http://www.howtoforge.com/creating-backups-with-luckybackup-on-an-ubuntu-9.04-desktop](http://www.howtoforge.com/creating-backups-with-luckybackup-on-an-ubuntu-9.04-desktop)

may need the same tweaks.

My aim is to "backup selected directories" (i.e./home/, /etc/ and /usr) to a USB-drive.

Currently, when I plug a USB drive into Ubuntu 12.10, it is mounted automatically (in my "/media" directory) and opened.  

But "Back in Time" does not appear to regard this address as valid.

Assuming that I have correctly understood the advice of the "Back in Time" maintainers, the preferred routine is to add an entry to "/etc/fstab" and point "Back in Time" to the selected "mount-point".

If this is correct, I need guidance on the syntax of "/etc/fstab" entries that Ubuntu 12.10 accepts as valid.

felkar

---

