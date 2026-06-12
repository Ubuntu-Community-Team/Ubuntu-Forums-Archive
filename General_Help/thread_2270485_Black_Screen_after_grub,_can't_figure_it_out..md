---
title: "Black Screen after grub, can't figure it out."
date: 2015-03-23
forum: General Help
---

### Post by Patrick_Costa on 2015-03-23
I'm new here so please bear with me.

Ubuntu 14.04.2 64 bit
Dell e6320

I've had my system running great for a few months.  I installed updates yesterday and then shut down my system.  When I turned it on this morning I saw the grub screen and then afterwards the screen went black.  Ive been reading the forums all morning and trying different things.  Nomodeset fix, reinstalling desktop...nothing.  I did notice that if I remove "quiet splash" in the grub menu I can boot into tty.  Other than that I'm stumped.  


Any suggestions (be gentle, I'm still learning).  Thanks

---

### Post by oldfred on 2015-03-23
Removing quiet splash you see boot process, do you see any errors or warnings?
It does scroll by quickly.

Can you boot recovery mode or second line in grub menu for same kernel or older kernel?

---

### Post by Patrick_Costa on 2015-03-23
Thanks for the response.  I finally figured it out.  I narrowed it down to xorg but that gave me all kinds of trouble.  After a lot of looking I discovered that there is a bug in 14.04.2 and 12.04.5 with the updating of fglrx.  I updated them manually and was finally able to get my gui back.  Should I share the link here (it's to another forum) for others?  I'm new to the forums

---

### Post by oldfred on 2015-03-23
I do not think we are as particular as some other forums. And we like to see/know solutions, so we can pass them along.

---

