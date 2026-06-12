---
title: "HELP PLEASE: DEJA DUP : First USB stick is full, what now ????"
date: 2018-02-18
forum: General Help
---

### Post by vroemm on 2018-02-18
Hi..

I asked this question before, nobody answered.

It would be very helpful if i go the answer to this :


DEJA DUP has filled its first usb stick with backups.

If i put the second usb stick in, deja dup does not continue with incremental backups.

Instead it first makes a backup of every thing, which takes a lot of space on the second usb stick.

How can i continue directly with incremental backups on a second usb stick ?

Thanks.
Super thanks for who gives the answer.

Vroemm.

---

### Post by DuckHook on 2018-02-18
My answer is bound to be incomplete. I do not use *Déjà Dup*. I use *rsync*. However, you may find the following useful.

*Déjà Dup* is just the graphical version of *Duplicity*, which, like many Linux apps is where the real versatility and power is because it is a command line app. *Duplicity* is not installed by default. If you want to use it, you will have to do: ```
sudo apt install duplicity
```
*Déjà Dup* is designed to be easy to use for newbies. Therefore, it has very limited options. It does not continually make incremental backups. It will make a new full backup on occasion. This is done to avoid broken restores should an incremental backup be corrupted, which is a danger whenever a long chain of incremental backups is relied upon. I don't know what algorithm *Déjà Dup* uses to determine when a full backup is done. It would not surprise me if a switch in media triggers such an event.

*Duplicity*, on the other hand, allows very fine grained control. Here is *Duplicity's* man page: [http://duplicity.nongnu.org/duplicity.1.html](http://duplicity.nongnu.org/duplicity.1.html)
Note that you can specify with either the *full* or *incr* switch whether you want a full or incremental backup. There are a wealth of other options and switches. The man page is complicated enough to show why many prefer the simplicity of *Déjà Dup*.

What you are asking for is essentially fine-grained control. This is not possible with *Déjà Dup*. You will have to use *Duplicity*.

A further note on good backup practice: *Déjà Dup* behaves the way it does for good reason. Periodic full backups are needed because it is not a good idea to rely too heavily on incremental backups. Your backup is only as good as your ability to restore, and incrementals are fragile. They form a chain of dependencies that can easily mislead you with a false sense of security when any one increment is corrupted or unrestorable. Since high-capacity USB sticks/drives are so cheap these days, you may wish to re-examine your desire to only do incrementals and just let *Déjà Dup* make full backups when it wants.

---

### Post by HermanAB on 2018-02-19
Only run Dejadup if the target device is big enough for everything.  One way is to use a USB hub and configure multiple sticks into a one or two terabyte JBOD.  Glue/tape/wire them down, or mount it in an enclosure, so that the JBOD cannot be disturbed.

---

