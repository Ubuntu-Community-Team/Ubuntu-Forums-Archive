---
title: "Are these updates OK to install?"
date: 2006-09-19
forum: General Help
---

### Post by BackInTimeMan on 2006-09-19
My update notification includes a couple for an older version of the kernal as well as the new one. Do I need to install these?

Please see attachment.

Cheers.

---

### Post by madmetal on 2006-09-19
i think its normal and ok.
i have download the updates you mention.

---

### Post by BackInTimeMan on 2006-09-19
> **madmetal said:**
> i think its normal and ok.
i have download the updates you mention.

OK, thanks. I'll backup first and then let them loose.

---

### Post by Ramses de Norre on 2006-09-19
They are perfect. But you'll need to reinstall things like proprietary video drivers because it's a kernel upgrade.

---

### Post by David Corrales on 2006-09-19
> **Ramses de Norre said:**
> They are perfect. But you'll need to reinstall things like proprietary video drivers because it's a kernel upgrade.

If you're using the repository drivers, they will be auto-updated.

---

### Post by PriceChild on 2006-09-19
> **BackInTimeMan said:**
> My update notification includes a couple for an older version of the kernal as well as the new one.

I only see one kernel there...

I've got that installed and all is fine :)

EDIT

BTW i noticed you cropped your screenshot.... If you hold the ALT key, then press the screenshot key, i think it should simply s/c the active window.

Very handy :)

---

### Post by BackInTimeMan on 2006-09-19
> **Ramses de Norre said:**
> They are perfect. But you'll need to reinstall things like proprietary video drivers because it's a kernel upgrade.

OK, thanks. I have a Matrox card and the drivers were already installed in Ubuntu so I'm hoping they will be fine after the upgrade. If not, then I may be back for some help...

---

### Post by BackInTimeMan on 2006-09-19
> **David Corrales said:**
> If you're using the repository drivers, they will be auto-updated.

I certainly hope so! :)

---

### Post by BackInTimeMan on 2006-09-19
> **PriceChild said:**
> I only see one kernel there...

I've got that installed and all is fine :)

EDIT

BTW i noticed you cropped your screenshot.... If you hold the ALT key, then press the screenshot key, i think it should simply s/c the active window.

Very handy :)

Oh yes, I see where I made the mistake, I thought 2.6.15-27.28 referred to a new kernal, not noticing the 2.6.15 written above it. The other two entries that mention the kernal seem the same except one calls itself a kernal image and the other a complete kernal. I'm new to Linux and don't know what the distinctions are but as long as the upgrade goes OK (doing it later) I'll be happy.

Thanks for the tip about taking a screenshot, just tried it and it works as you said. :)

---

### Post by PriceChild on 2006-09-19
> **BackInTimeMan said:**
> Oh yes, I see where I made the mistake, I thought 2.6.15-27.28 referred to a new kernal, not noticing the 2.6.15 written above it. The other two entries that mention the kernal seem the same except one calls itself a kernal image and the other a complete kernal. I'm new to Linux and don't know what the distinctions are but as long as the upgrade goes OK (doing it later) I'll be happy.

linux-386 is a metapackage which always depends on the latest kernel and associated packages... meaning you keep up to date.

linux-image-2.6...... is the actual kernel.

linux-image-386 is like linux-386 except that it only depends on the latest actual kernel, not much more.

Restricted modules are those with surprisingly restricted use and not necessarily free such as hardware drivers. You can probably guess what each of those now means if you use the same idea as above.

Pricey

---

### Post by BackInTimeMan on 2006-09-19
> **PriceChild said:**
> linux-386 is a metapackage which always depends on the latest kernel and associated packages... meaning you keep up to date.

linux-image-2.6...... is the actual kernel.

linux-image-386 is like linux-386 except that it only depends on the latest actual kernel, not much more.

Restricted modules are those with surprisingly restricted use and not necessarily free such as hardware drivers. You can probably guess what each of those now means if you use the same idea as above.

Pricey

Thanks for the information. Updated now and all is well :)

---

