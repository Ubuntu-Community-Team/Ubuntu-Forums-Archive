---
title: "HELP: Abnormal BIOS Boot Entry"
date: 2024-05-12
forum: General Help
---

### Post by ddoubleuc on 2024-05-12
Hi Gang,

This [IMG]https://ubuntuforums.org/attachment.php?attachmentid=293759&stc=1[/IMG] has suddenly appeared in my BIOS boot order list ... any idea what it is or how I can establish what it is?

---

### Post by grahammechanical on 2024-05-12
The first character is the Latin capital A with OGONEX. In hexadecimal it is u + 104. In decimal it is 260

Libreoffice writer>special characters>Latin-1

What the two characters represent in your BIOS and why they are there, I have no idea. Have you added a new drive or storage device?

Regards.

---

### Post by him610 on 2024-05-13
It is a logo, probably from the motherboard manufacturer.

If you had rather not see it, go into the BIOS setup where it can be turned it off/on.

I found *Full Screen Logo* under the BIOS Boot sub-menu where it can be (en/dis)abled.

---

### Post by ddoubleuc on 2024-05-13
Hi Graham … thanks for assisting … I recently ran nvme-cli sanitize on the only internal SSD then reloaded OS … sometimes I’ll have Ubuntu Live on USB flash and I access BIOS to change boot order but the logo I refer to above is a more recent entry to all I’ve just explained

---

### Post by ddoubleuc on 2024-05-13
Thanx Him610 … I’ll have a poke around BIOS for such option

---

