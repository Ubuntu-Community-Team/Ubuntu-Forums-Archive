---
title: "Radeon 7000VE and DRI support?"
date: 2006-11-07
forum: General Help
---

### Post by diamondsw on 2006-11-07
Does anyone know if the open source ATI/Radeon driver supports DRI on the Radeon 7000VE PCI card? Last time I checked (nearly a year ago), it tended to freeze the system on a fairly consistent basis.

Where should I go to find out the current status of said driver?

---

### Post by ReaderRat on 2006-11-07
Here is their driver page...
[**ATI Radeon 8500 & Higher Video cards**](https://support.ati.com/ics/support/default.asp?deptID=894&task=knowledge&folderID=27)

EDIT: I just noticed that you have a 7000 card...sorry I can't help.

---

### Post by ReaderRat on 2006-11-08
Check out here:
**[http://www.die.net/doc/linux/man/man4/radeon.4.html](http://www.die.net/doc/linux/man/man4/radeon.4.html)**

---

### Post by diamondsw on 2006-11-08
Found it:
[https://bugs.freedesktop.org/show_bug.cgi?id=707](https://bugs.freedesktop.org/show_bug.cgi?id=707)

Looks like it was fixed upstream a couple of months ago. How can I tell if this is in Edgy or not?

---

### Post by lazyart on 2006-11-08
Here's some help: [http://www.ubuntuforums.org/showthread.php?t=221672&highlight=2d+performance](http://www.ubuntuforums.org/showthread.php?t=221672&highlight=2d+performance)

It works well, though I have problems with the screensaver locking up with Hyper-Z enabled.

---

### Post by diamondsw on 2006-11-08
Or... maybe not. Ran glxgears and BAM! Frozen hard.

---

### Post by eXisor on 2006-11-08
I run the agp version of this card on Edgy. (I use Beryl/aiglx/radeon and have DRI enabled without any fiddling).

The same card froze Dapper when DRI was enabled, so give it a go on Edgy.

Performance is good in 16 bit color depth.

---

