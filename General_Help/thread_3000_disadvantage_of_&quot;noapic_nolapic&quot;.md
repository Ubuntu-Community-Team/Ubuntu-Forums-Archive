---
title: "disadvantage of &quot;noapic nolapic&quot;"
date: 2004-11-02
forum: General Help
---

### Post by tariq on 2004-11-02
i have an amd64 with nforce3 on a shuttle motherboard. the amd64 port worked well. but i require the flash/realplayer plugins ... so i installed the 32bit ubuntu. 

however i found that theings went wring in the install (hangs, i/o errors, interrupt errors) so i had to resort to a "noapic, nolapic".

what are these? what is the disadvantage of noapic and nolapic? if any?

---

### Post by jdong on 2004-11-02
APIC is a fancy interrupt router , sending interrupts to be handled by the least busy processor in a SMP (multi processor) system. Disabling it on a uniprocessor system makes absolutely no impact on performance or anything else.


Disabling apic on a SMP system could cause lower performance under high load conditions. Of course, APIC should never break on a SMP system!

---

### Post by jdusablon on 2004-11-02
My Asus A7N8X-X has an APIC bios option, but the nForce2 chipset has never supported MP. APIC must have other reasons for being.

---

### Post by jdong on 2004-11-02
Not really. APIC is just another way of routing interrupts; a more efficient way. There was the whole theory that APIC would make uniprocessor interrupt handling more efficient, but that wasn't the case!

---

### Post by jdusablon on 2004-11-02
So in the interest of efficient resources/better compatibility, should it be on or off for a Linux/UNIX system?

---

### Post by jdong on 2004-11-02
It honestly doesn't matter on a uniprocessor system! flip a coin!

---

