---
title: "My clock is overclocked!"
date: 2006-07-02
forum: General Help
---

### Post by Tosa on 2006-07-02
It does sound silly, but the clock in the panel goes ahead something like half an hour per day! I don't know when it began behaving like that. Maybe it was a couple of days ago when I installed the k7 kernel. *Set date and time automatically* is on, but it doesn't affect the clock at all. I'm aware that it's not the major problem, but it's annoying...
Another annoying thing that I'm sure popped up with the k7 kernel is that I can't change *Switch monitor off after* value. Actually I can, but when I turn my computer on it's back to its default!

---

### Post by woedend on 2006-07-02
its annoying...there are multiple possible fixes.  try this one to start

kdesu kate /boot/grub/menu.lst

find the line "kernel" from the first section(not the recovery mode section)
it might look something like
kernel /boot/vmlinuz26 root=/dev/hda1 ro splash

add noapictimer to the end like
kernel /boot/vmlinuz26 root=/dev/hda1 ro splash noapictimer

then save and reboot.  If it doesnt work let me know ill go dig up the thread of fixes

---

### Post by victor_c26 on 2006-07-02
I also have the same problem, but my clock is a lot faster. It goes 4 hours ahead in around half an hour.

I think I put noapic in the wrong section though. I put "noapic=true" in the default option section of the menu.lst file.

It seemed to work in Ubuntu, but when I boot back to my Windows install, the clock is off by about 12 hours.

---

### Post by victor_c26 on 2006-07-02
Double posted message

---

### Post by Tosa on 2006-07-04
[QUOTE=woedend]... If it doesnt work let me know ill go dig up the thread of fixes[/QUOTE]

Thanks! It seems it works. The clock still shows correct time! :cool:

---

