---
title: "computer won't boot"
date: 2006-12-15
forum: General Help
---

### Post by notatoad on 2006-12-15
not really a ubuntu problem i don't think, but people here seem to know their stuff, so i'll ask anyways:

ubuntu updated itself yesterday, i didn't even look at what it was updating. it told me i had to restart, so i restarted this morning, and now it won't boot. i don't even get into grub, it just stalls at the pci device listing. i will post a picture of the screen here later.

anybody know what's wrong? i'm thinking maybe ram?

---

### Post by Nersis on 2006-12-15
It seems to be a hardware problem. BIOS' sound is correct? Post the picture please, surely it shows the error.

---

### Post by notatoad on 2006-12-15
not really an error, just this
[IMG]http://img149.imageshack.us/img149/6022/2hv5.jpg[/IMG]

i can't even think what i would change in bios.  i've got absolutely no clue what's wrong

---

### Post by zgornel on 2006-12-15
Restore BIOS Defaults. If that does not work, reset the bios settings from the motherboard  jumper. Check temperatures and voltages. Something might be fried. :(

---

### Post by wpshooter on 2006-12-15
You say the update told you to restart the computer, yet you say "so I restarted this morning".

Did you restart the computer **immediately** after the update was applied as per the **prompt** and if not, why not ?

My guess is that the O/S is not being found on the hard drive.

Try to go into the BIOS and make sure the hard drive is being recognized there and that the hard drive is in the boot sequence.

If that does not work see if you can boot to the Ubuntu DESKTOP installation CD.

---

