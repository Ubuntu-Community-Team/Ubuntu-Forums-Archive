---
title: "No Sound With Headphones Sony"
date: 2013-02-12
forum: General Help
---

### Post by Antvinder on 2013-02-12
Hi

I have a sony E series laptop and I have only just started using Linux and have started with Ubuntu 12.10

My problem is I get sound from the speakers but when I plug my headphones there is no sound. 

I have looked for an answer on here but can not find any that solve the issue for me. 

[LIST]
[*]My headphones work in other devices
[*]Software updater says I am all upto date
[*]Made sure the volume in alsamixer is all on full and that nothing is on mute
[*]Alsa is upto date and recognises my sound cards and has them activated
[/LIST]

Thank you in advance :)

---

### Post by Antvinder on 2013-02-13
Ok... now I am extremely confused...

I spent all day and night trying to fix the headphone problem but to no luck. I have now just rebooted back to Windows 7 because the laptop is my TV my Game console and my DVD player... so the headphones not working really is a big issue for me...

On rebooting to Windows 7 I did a full clean reboot and formatted the hard drive. So Windows installed on a clean drive and has the most up to date drivers... and guess what... yerrrrp no sound from the headphones :(... I am very confused as the port was working literally 5 minutes before installing Ubuntu... but now its not working with either OS which tells me it HAS to be a hardware issue... all tho I'm not sure how something broke :-/ 

... Any suggestions? Once I know the jack is working on Windows again then I will HAPPILY go back to Ubuntu.

Thanks Again

---

### Post by fdrake on 2013-02-13
on ubuntu type into the termianl "alsamixer". When a sound output/input is highlighted and has "MM" it means left/right are muted (press m to unmute and up/down to change volume). If it is not highlited, the hardware is not recognized/available. To exit press "ctrl + c"

Do you have a sound option in your BIOS/UEFI ?

---

### Post by TOMBSTONEV2 on 2013-02-13
There is a little switch on the mother board which tells the mother board something is plugged in there. Somethimes the switch fails to make contact with the correct spot on the mother board. I have found the only way to fix this is to take it apart and unbend the actually switch so its more at its factory setting. I did this on a Hp Pavilion 6500 laptop.

Best of luck to you.

---

### Post by Antvinder on 2013-02-13
I don't have sound on my bios. 
There's nothing on mute on Alsamixer
The headphones work on other devices and have tried other headphones

And it can't be the switch on the motherboard as all the other input ports are working fine.. USB, HDMI and SD Reader are working... Its just the headphone jack that for some reason dosn't work on Ubuntu or Win 7... I have both OS installed So can try solutions for either OS

:(

---

