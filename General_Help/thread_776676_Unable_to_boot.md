---
title: "Unable to boot"
date: 2008-04-30
forum: General Help
---

### Post by Duroon on 2008-04-30
I have been using Hardy for a few weeks now and when I got home from work my laptop wouldn't boot. I should say it doesn't get to the login screen I guess. It was working fine at work, I shut it down to come home and now once it gets past the progress bar on the splash screen all I get is a black screen. I am in serious need of help with this I am afraid.

---

### Post by Monicker on 2008-04-30
> **Duroon said:**
> I have been using Hardy for a few weeks now and when I got home from work my laptop wouldn't boot. I should say it doesn't get to the login screen I guess. It was working fine at work, I shut it down to come home and now once it gets past the progress bar on the splash screen all I get is a black screen. I am in serious need of help with this I am afraid.

Did you try the recovery mode option from the boot menu?  That might display some information about where a problem is occurring.

---

### Post by Duroon on 2008-04-30
I did and there was a bunch of stuff that flew by rather quickly. I guess what I really need to know is how to reset my xorg config from the command line as root. Most of the errors seemed to have to do with x.

---

### Post by Monicker on 2008-04-30
> **Duroon said:**
> I did and there was a bunch of stuff that flew by rather quickly. I guess what I really need to know is how to reset my xorg config from the command line as root. Most of the errors seemed to have to do with x.

dpkg-reconfigure xserver-xorg

---

### Post by Duroon on 2008-04-30
Well I tried that and still no go. I am using the live cd to at least copy all of my files to my server here at home. If all else fails I will just redo the laptop with a fresh install I guess.

---

### Post by anars on 2008-05-10
I think I'm suffering from this too. The error is periodical.

The progress bar when booting up just moves from side to side. It hangs just after loading ata_piix, and then this keeps repeating:

```
ata1.00: qc timeout (cmd 0x27)
ata1.00: failed to read native max address (err_mask=0x4)
ata1.00: revalidation failed (errno=5)
```

And then later:

```
ata3.00: status: {DRDY}
ata3: soft resetting link
ata3.00: configured for UDMA/66 (shifts to "UDMA/33" later on")
```

Any ideas, people?

EDIT: Moving this to another thread :-)

---

