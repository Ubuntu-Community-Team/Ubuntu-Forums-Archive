---
title: "my pc switches itself on"
date: 2008-01-31
forum: General Help
---

### Post by den81 on 2008-01-31
hi all, i have a minor problem!!

at approx 2 am every morning my pc decides it wants to be on so boots all by itself.

i have been running xp for years and recently decided to dual boot with ubuntu (which rocks ).

this has only happened since my ubuntu install and if im using xp last thing before i switch off for the night it dosent happen, only when im using ubuntu does this problem occur.

i solved it temporarily by just flicking the switch on my power supply after shutdown but would like to find out whats causing it

any help much appreciated 

den

---

### Post by jaytek13 on 2008-01-31
It could be a BIOS settings. I would traverse through the options and check if you have any "wake on" options turned on.

---

### Post by skymera on 2008-01-31
you could unplug it.

but check the BIOS said above.

theres usually and auto-on setting.

---

### Post by den81 on 2008-01-31
i checked bios and coulsnt find any settings for wake or auto start, unless these setyting have some sort of computer jargon name that i dont know about

---

### Post by ocwo92 on 2008-01-31
This is a hack, but it may work for your purposes. The idea is that you tell your PC to wake up in 2030, which should keep it from waking up automatically for a while.

sudo sh -c "echo '2030-01-01 01:01:01' > /proc/acpi/alarm"

Edit: on my own computer, for some reason the above sets the wake-up date to January 1, 2008, but then again, presumably the computer will regard that as history.

---

