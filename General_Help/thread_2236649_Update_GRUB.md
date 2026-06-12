---
title: "Update GRUB?"
date: 2014-07-28
forum: General Help
---

### Post by Mike_Walsh on 2014-07-28
Morning all.

Plenty of 'Update grub' threads on the forum, but can't find one quite like my query...

Basically, I've gone from having three OSs on my PC back to just the one (Ubuntu 14.04), and would like to update the grub menu to reflect this. In other words, to return it to the state where it no longer appears, which it shouldn't with a single OS.

How can I accomplish this, please? Any advice will be welcome, and remembered for future exploits!


Regards,

Mike.

---

### Post by claracc on 2014-07-28
I don't understand very well your question since if you have installed grub2 and you have not any other operating system in your computer but ubuntu 14.04, then as the documentation states:[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2) :

"If no other operating system is detected GRUB 2 will boot straight into the default operating system and no menu will be displayed"

So, to get rid of boot menu you need to uninstall all the other OSs that you don't want, and grub itself will do the work to not show the boot menu.

---

### Post by ajgreeny on 2014-07-28
> **claracc said:**
> I don't understand very well your question since if you have installed grub2 and you have not any other operating system in your computer but ubuntu 14.04, then as the documentation states:[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2) :

"If no other operating system is detected GRUB 2 will boot straight into the default operating system and no menu will be displayed"

So, to get rid of boot menu you need to uninstall all the other OSs that you don't want, and grub itself will do the work to not show the boot menu.
You will, however, need to run ```
sudo update-grub
``` in your one remaining linux OS or the menu will still show all the old OSs.

That sentence shown by claracc is true only after grub has been updated, until then it will remain the same.

---

### Post by Mike_Walsh on 2014-07-28
Thanks, AJ; that's what I was after.

I knew I'd come across the command at some point in the last few months since I switched to Ubuntu.....but for the life of me I COULD not remember it!

It was just quicker to ask here on the forums, rather than trawl thru the 'net again.

It's sorted now, anyway, so.....I'll mark this as solved.

Cheers!

Regards,

Mike.

---

