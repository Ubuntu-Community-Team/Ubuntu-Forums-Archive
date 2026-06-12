---
title: "fix permissions?"
date: 2006-10-23
forum: General Help
---

### Post by scudellari on 2006-10-23
I messed up some of the permissions on my machine.  I ran:

sudo find / -type d -exec chmod 775 {} \;

I realized what I did pretty quickly and killed the command.  But now, every once in a while I try to run something, and it gives me a permissions error. I can fix it quickly and move on usually, but I want to fix EVERYTHIng. Is there someway to do this using the install CD? Some tool that can fix my permissions?

Thanks.

---

### Post by kidders on 2006-10-24
Hi there,

Those permissions you set are pretty open! It surprises me that you encounter problems, since not many directories are likely to require world write permission. My biggest concern is security-related.

I don't think there is a way to put your permissions back they way they used to be :-( If your box is not a personal PC, I would re-install Ubuntu _immediately_.

---

