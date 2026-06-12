---
title: "My keyboard doesn't work in GRUB and I need to boot from CD"
date: 2007-03-29
forum: General Help
---

### Post by Skeletron on 2007-03-29
I have a Zippy EL-715 USB Keyboard.   When GRUB says to press any key to boot from CD, I press keys and nothing happens.

I have tried setting my BIOS to not look at the HDD at all and only look at my DVD, but I think GRUB overrides this (confim/deny?)

---

### Post by acormack on 2007-03-30
I think this is due to the age of your computer / bios.

A bios upgrade might work - but may be overkill - Can you borrow a keyboard from someone?

Alec

---

### Post by cowlip on 2007-03-30
Try to reset ESCD in your bios (use a different keyboard to get into your bios first)

---

### Post by Skeletron on 2007-03-30
> **cowlip said:**
> Try to reset ESCD in your bios (use a different keyboard to get into your bios first)

I will try that.  I am able to get to my bios, it's just GRUB that doesn't work.

---

### Post by Skeletron on 2007-03-31
Turning on legacy support in the bios for USB worked.

---

