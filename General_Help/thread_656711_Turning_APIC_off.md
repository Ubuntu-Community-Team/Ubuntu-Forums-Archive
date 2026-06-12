---
title: "Turning APIC off"
date: 2008-01-02
forum: General Help
---

### Post by Taters on 2008-01-02
I've been trying to upgrade to Gutsy for a while, but an I/O APIC error has been preventing me for a while.

I've found that this line from the file menu.lst (/boot/grub/menu.lst) can help me:
[B]
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=d7aaf2d2-5afc-4904-9229-9d53ae46a6ce ro single[/B]

Do I just have to add this to the end of it?
[B]
apic=off[/B]


I don't want to mess up my system again, as I've gotten it to a comfortable stage. Help please.

---

### Post by dcstar on 2008-01-03
> **Taters said:**
> I've been trying to upgrade to Gutsy for a while, but an I/O APIC error has been preventing me for a while.

I've found that this line from the file menu.lst (/boot/grub/menu.lst) can help me:
[B]
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=d7aaf2d2-5afc-4904-9229-9d53ae46a6ce ro single[/B]

Do I just have to add this to the end of it?
[B]
apic=off[/B]
.......

Possibly, I use "**noapic**" myself (and you have listed the "Recovery" boot string, not the normal boot string).

My APIC error was because I have a single core CPU on a multi-core M/B, so switching this off just prevents Ubuntu trying to use features that don't apply to my hardware.

---

### Post by ~LoKe on 2008-01-03
I've used noapic as well, and as far as I can tell, it works.

---

### Post by adam.tropics on 2008-01-03
Same here, although other than the actual error message, I noticed no actual problem with the error there, nor any noticeable improvement without.

---

### Post by Taters on 2008-01-03
That kind of killed my computer.

It loads until 3-4 bars are filled. Then it freezes there. Command line works though.

Also, I went to change back the menu.lst file, but it lacks any changes. (Thus it is the very same)

What can I do to repair my system? Ask for information on my system if needed. (ubuntu 7.04, Celeron d proccessor 2.99 ghz)

---

### Post by adam.tropics on 2008-01-03
Edit Grubs boot parameters back at boot time temporarily, then make them permanent....read [howto]("http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html") here.

---

