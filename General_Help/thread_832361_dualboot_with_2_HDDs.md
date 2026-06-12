---
title: "dualboot with 2 HDDs"
date: 2008-06-17
forum: General Help
---

### Post by n.aggel on 2008-06-17
Hi guys, i have ubuntu 7.10 in my system for quite some time.

What i would like is to buy another harddrive and install there freebsd7. So that i can dual boot between ubuntu 7.1{on hard drive1} and freebsd {on harddrive 2}.

Any ideas on what problems i may face?
How can i make grub aware of the other OS {which will be on a second harddrive..}?

thanks for your time,

nicolas

---

### Post by ajgreeny on 2008-06-17
If freeBSD uses grub by default there should be no problem; simply mount that drive in ubuntu and copy the entry in the grub menu.lst file, or whatever FreeBSD uses for its grub configuration to the bottom of your ubuntu grub menu.lst file.  It should now show when you use ubuntu's grub and you can boot to it if you chose.

You will, of course, need to reinstall ubuntu's grub first, but you can do that easily with the live CD.

---

### Post by n.aggel on 2008-06-17
hi, i don't think freebsd uses grub. from what i can see here: [http://www.freebsd.org/doc/en/books/handbook/boot-blocks.html](http://www.freebsd.org/doc/en/books/handbook/boot-blocks.html)....

any ideas?

---

