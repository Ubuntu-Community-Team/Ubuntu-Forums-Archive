---
title: "Error 18: Selected cylinder exceeds maximum supported by BIOS"
date: 2008-02-13
forum: General Help
---

### Post by darvasi on 2008-02-13
Hi All,

I must tell you my story to **prevent you spending hours** looking for a solution.
Today I wanted to boot in windows xp which is in the same disk (hdd) with the ubuntu.
Both of the system have been working fine next to each other so far.
So today before I logged of from ubuntu I let the update manager to finish the updates.
Then when I wanted start the xp I've got the message:  Error 18: Selected cylinder exceeds maximum supported by BIOS
I have spent nearly the hole day searching a solution and I almost gave it up.
There are a lot of different issues about this message but none says what to do exactly in my situation.
One says to refresh the BIOS. Bullsh..t! The last I'd advice considering it's a dangerous manoeuvre.
I do not know what exactly caused this to me BUT simple **reinstalling GRUB** using "grub-install /dev/hda" is worked. How?

1.Go to terminal
2. Type in: '[COLOR="Black"]**_sudo grub-install /dev/hda_**[/COLOR]'
That's all.
After it booth of the boot must be working again.

Regards, AD

---

