---
title: "My computer won't boot up"
date: 2013-04-29
forum: General Help
---

### Post by ninjaondemand on 2013-04-29
Sorry if this is the wrong section.
Recently I upgraded my computer to Ubuntu 13.04. I turned it off, and when I tried to boot it back up again, the computer just emits seven blips, nothing is shown on the screen.

---

### Post by grahammechanical on 2013-04-29
You will not believe this but there is a fault with your computer. Those blips are part of the machine's Power On Start-up Tests (POST). They are happening before the machine even begins to look for an operating system to load. Do you see a Grub boot menu? Do you select to load Ubuntu? The boot process is not even getting as far as checking the boot system (MBR or EFI) for instructions as to what to do.

You need to identify what those 7 blips mean. And to do that you can look in the motherboard user guide or go on the web site of the BIOS manufacture.

[http://www.postcodemaster.com/](http://www.postcodemaster.com/)

[http://www.computerhope.com/beep.htm](http://www.computerhope.com/beep.htm)

Regards.

---

### Post by ventrical on 2013-04-29
If it's a Gigabyte MoBo and you recently tried to put in a faster processor (p4 3.0GHz and above) and it is rated for (p4 2.8GHz) then the board is toast.

goodluck.

A lot of websites will tell you it's ok to upgrade some MoBos  with faster processors but it doesn't always work and the ratings are not always accurate.

.

---

### Post by PJs Ronin on 2013-04-29
Geez, I haven't heard POST error beeps in more years than I care to remember.

To check the meaning of your beep code, look [here]("http://www.technick.net/public/code/cp_dpage.php?aiocp_dp=guide_beep_codes")

---

### Post by cariboo on 2013-04-29
Moved to General Help, as Raring has been released.

---

