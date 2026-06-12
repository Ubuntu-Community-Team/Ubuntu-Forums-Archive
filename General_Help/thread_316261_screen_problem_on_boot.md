---
title: "screen problem on boot"
date: 2006-12-10
forum: General Help
---

### Post by dennis1200 on 2006-12-10
When booting, things normally go fine, but if something goes wrong, I have an even harder time fixing it. Here's the deal. I have an Acer Aspire laptop (correctly configured in ubuntu to have 1280x800 resolution). On boot, the text only appears in the left fourth of the screen; everything right of that is just black. So if there's an error message and I need to edit a text file (recently happened, sort of guessed my way through vim and /etc/fstab) or type commands, I can't see them (the image is cut off about root@root-lapt|). Any ideas on getting Ubuntu to recognize the screen correctly from the get go, not just once I get into GNOME? Maybe something I could do in BUM?

---

### Post by DaveBorealis on 2006-12-10
> **dennis1200 said:**
> On boot, the text only appears in the left fourth of the screen; everything right of that is just black.

Hello,

I believe your problem can be fixed by setting a proper resolution for vga in your /boot/grub/menu.lst'.  Use the following table:
[FONT="Courier New"]
```

                       640x480 800x600 1024x768 1280x1024 1600x1200
---------------+-------+-------+--------+---------+---------
256 (8 bit)       |  769     771     773       775       796
32,768 (15 bit)|  784     787     790       793       797
65,536 (16 bit)|  785     788     791       794       798
16.8M (24 bit) |  786     789     792       795       799

```
[/FONT]
and you can try various vga values, as example:
```
kernel          /boot/vmlinuz-2.6.15-27-386 root=/dev/hda1 ro quiet splash vga=775
```

HTH,
Dave

---

### Post by dannytherocker on 2006-12-10
> **dennis1200 said:**
> When booting, things normally go fine, but if something goes wrong, I have an even harder time fixing it. Here's the deal. I have an Acer Aspire laptop (correctly configured in ubuntu to have 1280x800 resolution). On boot, the text only appears in the left fourth of the screen; everything right of that is just black. So if there's an error message and I need to edit a text file (recently happened, sort of guessed my way through vim and /etc/fstab) or type commands, I can't see them (the image is cut off about root@root-lapt|). Any ideas on getting Ubuntu to recognize the screen correctly from the get go, not just once I get into GNOME? Maybe something I could do in BUM?

I have an Acer laptop as well, try vga=771 in grub. Should work!
hope this helps

---

### Post by dennis1200 on 2006-12-11
Awesome - this is exactly what I needed. I know where I get my answers (forum), but where does all of this come from? Is there documentation somewhere outlining syntax for all possible files?

---

