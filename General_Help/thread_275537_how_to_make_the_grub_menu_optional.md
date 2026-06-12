---
title: "how to make the grub menu optional?"
date: 2006-10-11
forum: General Help
---

### Post by styracosaurus on 2006-10-11
I had Ubuntu installed all by itself a while ago, and as I remember when booting up it would only bring up the GRUB menu if you hit esc when prompted, otherwise it would boot Ubuntu.

Now, a few months later, I am dual booting with Windows XP (for games, what else? :-| ) and would like to get the option back. Now it goes to GRUB and gives me a choice...

Thanks!

---

### Post by .t. on 2006-10-11
Add "hiddenmenu" to the top of /boot/grub/menu.lst; you'll need root privileges to do this (ie, "sudo nano -w /boot/grub/menu.lst").

---

### Post by PriceChild on 2006-10-11
Yeah, there are several more options in there... just
```
sudo nano /boot/grub/menu.lst
```and read it. You'll see lots of examples that you can uncomment (remove the #) to try out.

---

### Post by aysiu on 2006-10-11
I believe *hiddenmenu* should already be in there commented. Just uncomment it after you paste in the command PriceChild gave.

**Commented**: ```
#hiddenmenu
``` **Uncommented**: ```
hiddenmenu
```

---

