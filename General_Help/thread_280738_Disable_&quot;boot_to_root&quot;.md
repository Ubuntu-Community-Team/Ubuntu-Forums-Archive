---
title: "Disable &quot;boot to root&quot;"
date: 2006-10-19
forum: General Help
---

### Post by encompass on 2006-10-19
How can I disable the recovery mode, or better... require a password for it.
It is common knowledge that when you install ubuntu and you want to reset the password, you just boot to recoverymode and do so.
With the setup of a test computer lab of ubuntu computers this next month at my school, I want to disable that so people can't hope on as root and change settings that they shouldn't.
Any ideas?

---

### Post by Dr. Nick on 2006-10-20
not sure how to a password it,but editing the /boot/grub/menu.lst you can remove the recovery mode from it. If you look at that file their may be a way to protect it, possibly a uid setting?; if not you may be able to delete the boot option for recovery mode if you know you will never want/need it.

That would work in theory, but I have never tested it so I would do it on a fresh install that wasnt important just to be safe.

---

### Post by aysiu on 2006-10-20
Just type ```
passwd root
``` when you're in recovery mode.

Of course, you may also want to create a password for the BIOS and make sure the students don't have physical access to the screws that hold the computer together.

---

### Post by Zeddicus on 2006-10-20
You could also remove the recovery option from the list and password protect GRUB.

I used to use these instructions to do so:

[http://www.gentoo.org/doc/en/security/security-handbook.xml?part=1&chap=2#doc_chap2](http://www.gentoo.org/doc/en/security/security-handbook.xml?part=1&chap=2#doc_chap2)

---

### Post by glotz on 2006-10-20
Introduce a GRUB password
[http://www.gnu.org/software/grub/manual/html_node/password.html#password](http://www.gnu.org/software/grub/manual/html_node/password.html#password)
[http://makuchaku.info/amnesty/#changegrubpasswordforgotten](http://makuchaku.info/amnesty/#changegrubpasswordforgotten)

and lock the recovery option
[http://www.gnu.org/software/grub/manual/html_node/lock.html#lock](http://www.gnu.org/software/grub/manual/html_node/lock.html#lock)

Also make sure your boot order is HD before CD. And BIOS is password protected. :)

---

### Post by encompass on 2006-10-20
Woah! Thanks for all the ideas on that one... I had the grub passworded... but figured there were other ways.  Thanks everyone.

---

