---
title: "Grub after Update"
date: 2005-10-31
forum: General Help
---

### Post by hodgemanU on 2005-10-31
I updated my HP nc6000 laptop from 5.04 to 5.10 using the online method.
(changed the repositiories from hoary to breezy, and updated w/apt)

Worked/is working great, but the grub loader didn't get updated to the new graphic version that is available with 5.10.
I have the new bootsplash stuff, it works fine.

Any Ideas on how to fix this? (Sorry I am a linux newb, but learning fast)

HM

ps. My reason for not doing a clean install to 5.10 was because I used the HP laptop version of 5.04, didn't want the hardware hassels :D

Thanks in advance

---

### Post by SilentCacophony on 2005-10-31
> Worked/is working great, but the grub loader didn't get updated to the new graphic version that is available with 5.10.

I've got a fresh install of 5.10, and there is no 'graphic version' of grub. Grub has had the option to allow a bootsplash image for quite some time, though you have to set that up yourself.

> I have the new bootsplash stuff, it works fine.

I'm not clear on what you're talking about there. Breezy comes with a package called **usplash** installed, which has an 'ubuntu' image with a progress bar, while running the bootup steps between grub and gdm. You may also have a 'bootsplash' image set up for grub, if you choose to set one up.

If it's usplash that you're missing, you should be able to simply install it:

**sudo apt-get install usplash**

---

### Post by hodgemanU on 2005-11-02
Thanks, got a bit confused, the USplash is working fine.
I (for some reason) thought that the Grub Menu was different too.

Must be the drugs :D

---

