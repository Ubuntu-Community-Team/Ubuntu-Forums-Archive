---
title: "Can't boot Ubuntu"
date: 2007-09-22
forum: General Help
---

### Post by Prizo on 2007-09-22
Well, hello there. I really need help with booting Ubuntu, Seems like no matter what I try I always get error/lockup.
When I try to boot in normal mode my PC locks-up with:

EIP: [<c011c706>] Native_apic_write_atomic+0x6/0x10 SS:ESP 0068:f134ba98    And then I can only restart my pc...

But with noapic nolapic and other parameter's I get random error's

I've already tried almost everything Including bios updating, and still the same...
I hope there's a way to fix it some how.

Thanks for any help.

---

### Post by Arwen on 2007-09-22
Hello,I think I've seen somewhere in this forum this kind of problem before but I don't think I've seen a solution,you can search a bit if you want.Maybe you should try the Alternate CD?

---

### Post by Prizo on 2007-09-22
Well, I've already searched everywhere but still nothing helps
And I installed with Wubi because LiveCD wont boot too...
But I could boot Ubuntu few months ago when my PSU died and I had to replace it.

---

### Post by Prizo on 2007-09-22
Bump.

I guess there is no way to fix it? :(

---

### Post by jwcgator on 2007-09-22
Is that all the screen says and no actual ERROR message? Try pressing Ctrl+alt+delete. It made my Ubuntu continue to boot, maybe it will help you.

---

### Post by Prizo on 2007-09-23
Well, It doesn't work because it's locked up...
But I remember I used noapic nolapic and made my pc loop error or sometimes restart, Anyways I'll try it.

---

### Post by banewman on 2007-09-23
As another option try - at the " start or install " part of the live cd pressing F6 and typing - acpi=off noapic nolapic pnpbios=off pci=bios. Might be what you need...:)

---

### Post by Prizo on 2007-09-23
> **banewman said:**
> As another option try - at the " start or install " part of the live cd pressing F6 and typing - acpi=off noapic nolapic pnpbios=off pci=bios. Might be what you need...:)

Hmm, It doesn't work with LiveCD, But does work with Wubi installed Ubuntu.
Now the only thing I'm getting is this error:

Alert! /media/host/wubi/install/install.virtual.disk does not exist. dropping to a shell!

/bin/sh: cant acces tty; Job control turned off. :mad:

---

