---
title: "Gnome Baker locking up"
date: 2007-08-06
forum: General Help
---

### Post by Ianman on 2007-08-06
Hi all,

Every time I try to burn an ISO image everything seems to go fine except that when the burning starts, I can hear the DVD burner spinning and the LED flashes as I would expect but nothing happens. Whats more, the systems seems to go into super slomo. Moving the mouse is impossible as I move it and wait to see where the cursor ends about 15 seconds later. I can't even get to a console to logout or halt the system.

Has anyone else seen this?
Thanks!

---

### Post by bogolisk on 2007-08-06
> **Ianman said:**
> Hi all,

Every time I try to burn an ISO image everything seems to go fine except that when the burning starts, I can hear the DVD burner spinning and the LED flashes as I would expect but nothing happens. Whats more, the systems seems to go into super slomo. Moving the mouse is impossible as I move it and wait to see where the cursor ends about 15 seconds later. I can't even get to a console to logout or halt the system.

Has anyone else seen this?
Thanks!

It has nothing to do with gnome-baker. It's a kernel problem that plagued many Feisty installation. Not sure if it will be fixed in gutsy. Your best bet is probably downgrading to Edgy or Dapper. Other things you can try, assuming you have an IDE dvd drive and it is  hdd:
```

   sudo rmmod ata_generic
   sudo rmmod sr_mod
   sudo pkill -f 'hald-addon-storage: polling /dev/hdd'
   sudo hdparm -u0 /dev/hdd

```
then burn at 8x speed (instead of 16x.)

---

### Post by Ianman on 2007-08-06
Ok thanks for that! Sure hope they can fix it for the next release.

---

### Post by stchman on 2007-08-06
> **Ianman said:**
> Hi all,

Every time I try to burn an ISO image everything seems to go fine except that when the burning starts, I can hear the DVD burner spinning and the LED flashes as I would expect but nothing happens. Whats more, the systems seems to go into super slomo. Moving the mouse is impossible as I move it and wait to see where the cursor ends about 15 seconds later. I can't even get to a console to logout or halt the system.

Has anyone else seen this?
Thanks!

I have never used Gnomebaker.  Use K3B, the best burning program for Ubuntu.

---

### Post by bogolisk on 2007-08-06
> **stchman said:**
> I have never used Gnomebaker.  Use K3B, the best burning program for Ubuntu.

It wouldn't make any difference in this case because neither  K3B nor gnome-baker can do the actual burning.  They are just graphical front-ends to growisofs. Both will call growisofs to do the actual burning. The problem is in the kernel.

---

