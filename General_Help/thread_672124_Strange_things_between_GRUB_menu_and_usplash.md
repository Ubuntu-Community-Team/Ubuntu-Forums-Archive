---
title: "Strange things between GRUB menu and usplash"
date: 2008-01-19
forum: General Help
---

### Post by Michl on 2008-01-19
I have several computers running ubuntu, and normally after the
GRUB menu (where I dual boot) I get the usplash (or whatever
the screen is called with 'ubuntu" etc) and then the login
window.

On one computer I get another screen that's black with white
writing that begins with Booting root kernel and then has
about ten lines of info, including boot reload, filesystem,
and so on.  It does not last long so I don't remember much 
of it.

I would like to get rid of this and have a clean boot sequence
like on the  other computers.

I had this problelm after I reinstalleed Edgy once.

Thanks for any help!!
Michael

---

### Post by Michl on 2008-01-21
Anyone?

---

### Post by nick_h on 2008-01-22
I have the same symptoms.

In Dapper I didn't have a problem.  After selecting the grub menu entry the screen went blank.  I can't remember if there was briefly a one word of text, "Loading ..." or similar, in the top left corner of the screen but after a very short period of time the usplash screen appeared whilst Ubuntu loaded.  The loading looked good.

In Feisty, after grub finished I got a brief corrupted screen before the usplash screen started.  I added the boot option vga=791 and the corrupted screen didn't appear but I got the standard boot messages appearing (as I would expect with nosplash) instead.  I can also see the change of mode (to vga=791) as the messages print.  Then usplash appears and the rest of the boot is normal.

This doesn't really cause a problem but it is annoying, especially because it worked well in Dapper.  I suspect the problem started with Edgy.

---

