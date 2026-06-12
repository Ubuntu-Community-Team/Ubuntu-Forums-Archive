---
title: "How to get a real console?"
date: 2007-02-02
forum: General Help
---

### Post by street spirit on 2007-02-02
Hi,

I'm running Kubuntu (dapper), and for some reason I can't get to the linux console with the usual key shortcuts of Ctrl-Alt-F[1-6]. When I press Ctrl-Alt-F1, the screen jsut goes black, and I can return to my X session with (Ctrl-)Alt-F7, but I never get to see any text (login prompt or other). Maybe a screen resolution issue (this is a Vaio laptop)?

TIA!

---

### Post by 23meg on 2007-02-02
Add a VGA modeline to your kernel boot line in GRUB in the form of "vga=*xyz*", where *xyz* is one of the values below, depending on what resolution you want.

```

Color depth      | 640x480  800x600  1024x768 1280x1024
-----------------+-------------------------------------
256        (8bit)|  769      771       773      775
32000     (15bit)|  784      787       790      793
65000     (16bit)|  785      788       791      794
16.7 Mill.(24bit)|  786      789       792      795
```

---

### Post by street spirit on 2007-02-02
Thanks 23meg!
I will try that on the next reboot.

---

