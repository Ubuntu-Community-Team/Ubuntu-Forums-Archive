---
title: "How do I mount a FATX partition?"
date: 2006-11-18
forum: General Help
---

### Post by Junx on 2006-11-18
I have a USB thumbdrive that's formatted as FATX by an Xbox console, and I'd like to mount it in Ubuntu.  How would I do this?

The original patches sent to Linux adding support for fatx were sent 4 years ago, yet mounting the drive with -t fatx gives no helpful information, and modprobe fatx doesn't do anything either.

---

### Post by koenn on 2006-11-19
what is the unhelpful information that mount -t fatx  gives ?

---

### Post by dajhorn on 2006-11-26
The fatx driver is not bundled with Ubuntu Edgy.

  $ sudo mount -t fatx /dev/sda /mnt
  mount: unknown filesystem type 'fatx'

---

### Post by kahlil88 on 2008-07-10
Is there a FATX driver for Ubuntu, and where might I get it?

---

