---
title: "Ubuntu stalls on startup when looking for mystery ata2 port."
date: 2007-07-21
forum: General Help
---

### Post by TygerTung on 2007-07-21
I'm having issues with ubuntu stalling on startup for no aparent reason why is looks for a mystery ata2 port.

ATA0 and ata1 are the ide ports for my hard drives and optical drives or somthing, I don't know what ata2 is though.

It gets all upset for a while while it probes them but then after a while it just gives up and loads anyway.

It just a bit anoying having to wait about three minutes while it spits a dummy before it realises it's just wasting it's time while it starts up.

Here is what the error message looks like:

[ATTACH]38750[/ATTACH]

Any idea what the matter could be?

---

### Post by fluteflute on 2007-07-24
I am getting this too. It is very fustrated waiting all the extra time upon bootup.

---

### Post by bobbob1016 on 2007-07-25
I get the same on one of my laptops.  Not sure what the issue is either though.

---

### Post by TygerTung on 2007-07-26
It seems it doesn't like one of my optical drives for some reason, I have tried many things!!!!

I had two hdd on one ide channel, and two optical drives on one channel, so what I have done is put a hdd and an optical drive on each channel but it hasn't made any difference.

---

### Post by bobbob1016 on 2007-07-26
Someone gave me the answer on the Ubuntu IRC channel, here is the link I was given: [http://bbs.archlinux.org/viewtopic.php?pid=265646](http://bbs.archlinux.org/viewtopic.php?pid=265646)
Basically, I edited my grub menu.lst file, and removed the "ro" option, and added "legacy_ide earlymodules=sis" without quotes.

---

