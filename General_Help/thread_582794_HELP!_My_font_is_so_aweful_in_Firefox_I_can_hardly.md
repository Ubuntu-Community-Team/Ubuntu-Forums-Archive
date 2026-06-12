---
title: "HELP! My font is so aweful in Firefox I can hardly read it! I need a quick fix!"
date: 2007-10-20
forum: General Help
---

### Post by RAV TUX on 2007-10-20
I know there is a command I can plug into the terminal but I have forgotten what it is....please help.

---

### Post by forestpixie on 2007-10-20
not sure what command you refer to - but I hope someone puts it here so I can know it too.

But - I do [this]("http://ubuntuforums.org/showthread.php?t=208396") with the xml file, and change my fonts - seems to be ok for me. Relies on msttcorefonts which I assume you have 

Sorry if it's not what you're looking for

---

### Post by WakkiTabakki on 2007-10-20
Try enabling subpixel rendering:
1. Open System / Preferences / Appearance / Fonts
2. Choose subpixel smoothing
3. Click on details and choose full hinting

If that doesn't help, try changing fonts in firefox (Edit / Preferences / Content). I use Bitstream Vera Sans, size 16.

/N

---

### Post by hugmenot on 2007-10-20
Err, Ctrl-+ ? Your fonts are just too small.

---

### Post by floke on 2007-10-20
I thought you used opera?

---

### Post by kerry_s on 2007-10-20
**sudo dpkg-reconfigure fontconfig-config**

---

### Post by Jose Catre-Vandis on 2007-10-20
> **WakkiTabakki said:**
> Try enabling subpixel rendering:
1. Open System / Preferences / Appearance / Fonts
2. Choose subpixel smoothing
3. Click on details and choose full hinting

If that doesn't help, try changing fonts in firefox (Edit / Preferences / Content). I use Bitstream Vera Sans, size 16.

/N

and untick the box in Advanced about allowing pages to choose their own fonts :)

---

