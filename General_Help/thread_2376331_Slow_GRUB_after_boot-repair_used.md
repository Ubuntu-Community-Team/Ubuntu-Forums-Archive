---
title: "Slow GRUB after boot-repair used"
date: 2017-11-01
forum: General Help
---

### Post by allonewordalex on 2017-11-01
I had to use boot repair software on my system because GRUB wasn't recognizing my boot drive and after that, I was shown the menu to pick the operating system on the new GRUB install. I tried to remove that in the /etc/default/grub where I changed the GRUB_HIDDEN_TIMEOUT to = 0. Now the menu is gone but between my BIOS and the actual loading of my OS, there is a long delay that wasn't there before. Any ideas?

---

### Post by oldfred on 2017-11-02
Did you change timeout also?

GRUB_TIMEOUT=3

I change mine from default of 10 sec to 3 sec. 
Do not change to 0, or you will never be able to get into grub when booting. And sometime you may need to.
I find 3 sec gives me just enough time to press escape (UEFI) or shift(BIOS) key when I need grub menu.

---

