---
title: "Brasero - create .iso for windows"
date: 2013-09-11
forum: General Help
---

### Post by jaz0nj4ckal on 2013-09-11
Folks:
I am trying to create an .iso of my XP disk, so I can use it to turn up Virtual Box images fast; however, I need to create an .iso for Windows as well. Using Brasero has enabled me to create an .iso that works on Ubuntu/Linux; however, I am not able to mount the .iso via Windows 8. The latter throws an error about the wrong file type or format - due to the latter, is there a switch or method used via Brasero to make or format an .iso for Windows?

In addition, I have successfully made .iso for Linux via "DD", but cannot mount these .iso in Windows.

Thanks.
JJ

---

### Post by VMC on 2013-09-11
Is it a [COLOR=#333333][FONT=Helvetica Neue]valid ISO 9660 filesystem? What dd commands did you use?[/FONT][/COLOR]

---

### Post by jaz0nj4ckal on 2013-09-12
> **VMC said:**
> Is it a [COLOR=#333333][FONT=Helvetica Neue]valid ISO 9660 filesystem? What dd commands did you use?[/FONT][/COLOR]

At first I had no clue what ISO 9960 was; however, after reading it appears ISO 9960 is supported on Windows. Does any software, which creates iso supports ISO 9960? I thought ISO images, were standard (one size fits all); however, I am learning that is not the case.

Thanks.

---

### Post by VMC on 2013-09-12
Tactfully I though you couldn't read it from Windows, but instead you can't mount it. Your using vbox in Windows. Have your tried to convert the partition to [VDI's]("http://blog.rmartinez.co/2013/01/tutorial-resize-static-virtualbox-vdis.html")? I maybe missing your problem.

---

### Post by QIII on 2013-09-12
Hello, jaz0nj4ckal!

Could you explain what you mean by "turn up Virtual Box images fast"?

---

### Post by jaz0nj4ckal on 2013-09-12
> **jaz0nj4ckal said:**
> At first I had no clue what ISO 9960 was; however, after reading it appears ISO 9960 is supported on Windows. Does any software, which creates iso supports ISO 9960? I thought ISO images, were standard (one size fits all); however, I am learning that is not the case.

Thanks.

I will try this... thanks.

---

### Post by jaz0nj4ckal on 2013-09-12
> **QIII said:**
> Hello, jaz0nj4ckal!

Could you explain what you mean by "turn up Virtual Box images fast"?

I wanted to build an .iso that I could mount or read on Windows 8/7, or be able to mount the XP .iso via Virtual Box on an Windows host OS; however, I get format errors when doing the latter two methods. Yet, I am able to mount and read on Ubuntu - or mount the xp.iso via Vritual Box.

Thanks.

---

### Post by QIII on 2013-09-12
For installing XP in VMs or to actually run XP as a VM from the media?

---

### Post by jaz0nj4ckal on 2013-09-12
> **QIII said:**
> For installing XP in VMs or to actually run XP as a VM from the media?

I might be thinking of this silly, but I wanted to try both or at least be able to read the .iso from the Windows Host OS as well.

For another topic - but I wanted to be able to mount under the Windows Host OS, so I could use the same method to encode my Office disk into an .iso, so I could install via mounting via Windows 8 or install to my guest OS via virtual box by mounting the .iso in Virtual Box.

---

### Post by QIII on 2013-09-12
What you are suggesting here could constitute a significant violation of Microsoft's copyrights, intellectual property rights and EULAs.

Closed for staff review.

---

