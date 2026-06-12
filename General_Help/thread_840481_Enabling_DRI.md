---
title: "Enabling DRI"
date: 2008-06-25
forum: General Help
---

### Post by tatoniss on 2008-06-25
I have an old computer but i am pretty sure it can handle some graphics, i use to on windows. but when i checked it i don't think dri is enabled. Im new to ubuntu and i don't know a lot about this but i would like it to work because i may be able to use some simple desktop effects and games, would it also make videos run smoother?

Anyway thank you if you can help

I have hardy 8.04

My card is a  3D Rage LT Pro AGP-133 [1002:4c42] (rev dc)

---

### Post by tatoniss on 2008-06-25
Maby my card is not enabled because i ran compiz check and this is what i got, I am not using a laptop but is says there is a battery error

```
 ./compiz-check

Gathering information about your system...

 Distribution:          Ubuntu 8.04
 Desktop environment:   GNOME
 Graphics chip:         ATI Technologies Inc 3D Rage LT Pro AGP-133 (rev dc)
 Driver in use:         ati
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...FATAL: Error inserting battery (/lib/modules/2.6.24-19-generic/kernel/drivers/acpi/battery.ko): Operation not permitted
           [ OK ]

```

---

### Post by Forlong on 2008-06-25
ATI Rage cards are too old to support Compiz, sorry.

---

### Post by tatoniss on 2008-06-25
But can i still enable it, it did work when i used windows.

here is my info

---

### Post by tatoniss on 2008-06-25
here is the xinfo after running the code you made

---

### Post by mcurran on 2009-10-29
Compiz is supported by this card:

ATI 3D RAGE LT PRO AGP 4MB

I had compiz working on Linux Mint 4 "Daryna"; however, I just recently started looking to see if I can get Compiz or direct rendering working with the newer releases (Karmic Koala).  I have not had any success, but I would assume it's possible, since it worked before.

Even though it worked, my computer was very slow when it was working, but it was still cool to see the desktop cube and other effects working with this old legacy card.

---

