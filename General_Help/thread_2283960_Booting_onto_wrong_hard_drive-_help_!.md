---
title: "Booting onto wrong hard drive- help !"
date: 2015-06-26
forum: General Help
---

### Post by Tim036 on 2015-06-26
I run Ubuntu 14.04 64 bit fully updated.

Its got two drives

1st on the first sata port SSD drive

2nd 1TB Western Digitial 1TB for data

both have a booting version of Ubuntu on them.

For a year or more it booted from the SSD drive.

Suddenly it started to boot from the Western Digital drive.

As they are in cradles when I close down I pull out the drive 2  only the SSD drive is left in.

When I start it up, once I have the desktop, I push drive 2 in.  Works OK but not that elegant.

So the question is:-  Is there part of the OS I can look at and correct the order of booting?

Many thanks in advance,

A very puzzled,

Tim

---

### Post by dino99 on 2015-06-26
set grub2 only in one place

> sudo apt-get purge grub*
sudo grub-install /dev/sda
(replace sda by what you want if needed)

---

### Post by Tim036 on 2015-06-26
Many thanks for replying,

I'll try that.

:  )))

Tim

---

### Post by Tim036 on 2015-06-26
Well that resulted with both drives in their cradles, neither booted.

I'll try that on the second drive on its own with just the first line.

:  )

Tim

---

### Post by Tim036 on 2015-06-26
Solved

I swapped the cradle positions and the 2nd drive booted.

I replaced the cradles positions and it all works fine.

I don't understand it but hey !  it works.

( the second drive did not seem to have grub installed originally)

So I'm happy now !

Many many thanks for your support !

:  )))

Tim

---

### Post by Tim036 on 2015-06-26
nm

---

### Post by ajgreeny on 2015-06-26
I have marked this thread as **SOLVED** from the Thread Tools menu at the top.

I am aware that you have edited the final post's title but that does not show in any thread listings, so it will not be obvious to those searching for information that you have managed to find an answer.

---

