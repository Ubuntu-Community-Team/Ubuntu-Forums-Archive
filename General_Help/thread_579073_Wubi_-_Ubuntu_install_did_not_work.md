---
title: "Wubi - Ubuntu install did not work"
date: 2007-10-17
forum: General Help
---

### Post by Wingsfree on 2007-10-17
I get the bcm43xx_microcode5.fw message.

Unfortunately, when I tried to go in the login as I wrote it down is not working.

I don't suppose there is a bypass.

Otherwise I guess my only alternative is to uninstall and start over.

---

### Post by PGHammer on 2007-10-17
What's the hardware and OS setup?
How much hard drive space was free on the target partition?

I can say this much; this has easily been the easiest install of a non-Windows OS since BeOS 5 Personal Edition (like Wubi, it installed from Windows).  I've done most of my posts about Wubi from within Wubi (talk about eating the dogfood). Since installing Wubi, I've installed 142 updates, added twenty applications, and upgraded the graphics drivers for my ATI X1650 card (not to mention completely changed the way I think about Linux, which is *entirely* due to Wubi).

I did my Wubi from within Vista Ultimate, on older hardware, and I'm having no trouble whatever.  I can access files on the Windows partition with ease (my current wallpaper, for example, is from the Windows partition; I have no trouble playing MP3s with Totem, or opening documents written using Word in OpenOffice.org Writerm either).

To put it succinctly, Wubi's a keeper.

---

### Post by ago on 2007-10-18
> **Wingsfree said:**
> I get the bcm43xx_microcode5.fw message.

Unfortunately, when I tried to go in the login as I wrote it down is not working.

I don't suppose there is a bypass.

Otherwise I guess my only alternative is to uninstall and start over.

Yeah you can replace "quiet splash" with "single" in menu.lst
That will boot in recovery mode, then you can type

passwd wingsfree

---

