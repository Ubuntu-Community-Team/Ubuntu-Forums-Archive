---
title: "ubuntu freezes"
date: 2007-09-27
forum: General Help
---

### Post by donmor on 2007-09-27
Ubuntu 7.04 installed on a Toshiba A70 dual boot with WinXP. Every time I load ubuntu, it will freeze up and I have to shut down the power. Sometime I will play a game, sometimes I'm on Firefox, and sometimes I'm trying to get the updates like tonight. Got the notice that there were upgrades and when I went to click on the icon, nothing. Have tried both kde and genome.

Thinking of reinstalling it again but have done that twice already.

Anyone have any ideas?

Don

---

### Post by gautada on 2007-09-27
Could be bad memory.  I have had the "freezes" that a new stick of RAM curred.  I would run the memtest, Click "ENTER" when grub comes up early in the boot before the Ubuntu logo and choose MemTest86+.  Check out this [blog]("http://panela.blog-city.com/bad_memory__ubuntu_memtest86_to_the_rescue.htm").

---

### Post by donmor on 2007-09-27
Thanks, I'll try that

Don

---

### Post by donmor on 2007-09-27
Thanks to a post from se2131 I have solved me problem for now.
Was getting a clock error at boot up and added "noapic nolapic" to the kernel boot

/boot/grub/menu.lst
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=caae8c05-dc12-43d2-81e1-8805a409e1d6 ro quiet splash **noapic nolapic**
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

Hopes this helps someone else.

Don

---

### Post by gautada on 2007-09-28
Glad you found a solution.  Don't forget to mark the thread as solved using "Thread Tools".

---

