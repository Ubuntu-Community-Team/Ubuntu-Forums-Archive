---
title: "Virtual Consoles are not working"
date: 2006-11-13
forum: General Help
---

### Post by garymansell on 2006-11-13
Hi,

I have installed the i386 Edgy Eft Release and have found that I cannot switch to a virtual text console by pressing ctrl alt [F1-F4]

Any ideas why this is not working?

Regards

Gary

---

### Post by garymansell on 2006-11-13
bumping... must be needed by people

---

### Post by Kitty on 2006-11-13
I can come from your video driver.
I had this problem with a nvidia card.

My solution was to disable the splash screen.
(must be changed in /boot/grub/menu.lst)

---

### Post by garymansell on 2006-11-13
FYI

Eradicating the splash command line option for the running kernel in /boot/grub/menu.lst worked for me also....

This must be a bug - this is not the expected behaviour !!

---

### Post by weeds86 on 2006-12-07
I am having this problem as well and I have a nVidia graphics card. Can someone please tell me exaclty how to eradicate the splash command line in the /boot/grub/menu.lst?

Cheers;)

---

### Post by garymansell on 2006-12-07
edit the file /boot/grub/menu.lst, find the line starting with kernel and remove the word splash from the end of the line of arguments

---

### Post by Azriphale on 2006-12-12
I am also having this problem (ATI x700), but will try removing the splash option now. Just listing that there is another with this problem.

EDIT: I now have my VCs back. Thanks. Only thing is, it still doesn't display of first switch to a VC, but after going to X, and switching to the VC again, it works.. odd. But it does work. Thanks for the info

---

### Post by mcduck on 2006-12-12
One thing you can also try (to get both splash and VT's) is adding line like vga=792 to the end of your kernel line in menu.lst. This fixed the problem for me (Ati x1600).

---

### Post by Azriphale on 2006-12-12
That was the first thing I tried. It worked with the Live CD (before installation), but not with the installed system. So now I do both so I have 1024x768 VCs and and no splash so that i can access them.

---

