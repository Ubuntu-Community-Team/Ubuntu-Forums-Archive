---
title: "ACPI options are causing troubles on new MSI laptop"
date: 2018-04-22
forum: General Help
---

### Post by goudin on 2018-04-22
Hi everyone, i've got several problems concerning boot options with my new msi GS63-7RD laptop.
When i got it 2 months ago i had troubles with nvidia drivers etc, but i finally got something stable and usable. But a few days ago, i tried to reboot it and i got ACPI errors at booting sequence, and the pc just gets stuck on ubuntu loading points.

My friend google told me to try a bunch a stuff in grub menu by editng booting options, and several made possible the booting:

 apic=off, but the system lacks a lot of this like sound managing via buttons, battery infos etc.
pci=noacpi, this one is the one i'm using as i write this message. But the pc still lacks some features, for exemple i cannot reboot, the pc juste gets stuck right after i click turn off or reboot.
Also, if i close the pc, instead of sleep mode that i could before get out of just by opening it back, the pc just continues to run, fans are running etc. And i have a battery life that is in average divided by two when i use on battery.

I tried to update my bios, but nothing changed. So i went for the "utlimate" solution, get back on a fresh install. And surprise, on a fresh install (that i put on an other partition of my ssd) i don't have acpi problems, i don't need to put special options on grub for booting. BUT, i cannot reboot or shutdown, it always gets stuck right after i click and i need to do it manually...

If anyone has an idea that might help, i'm all ears, as a freelance developer it's really bothering me for my work, as i have to shut down the pc every day (really bothering to have to restart all the servers and configurate all the environment), and the battery life has become so low..

Thx in advance and long life to linux :)

---

### Post by kerry_s on 2018-04-22
what version of ubuntu?

since you got a newer laptop i'd recommend the new 18 which is due for release in 4 days.
[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

maybe even pop!_os cause they have a installer with nvidia.
[https://system76.com/pop](https://system76.com/pop)

---

### Post by goudin on 2018-04-23
thx for the response :).
Version 16.04.4 LTS. Yesterday i tried something with an interesting result. I removed the intel-microcode, because an update some weeks ago was about this. Now i'm able to reboot correctly, but i still need, on of my partition, to have the pci=noacpi mention.

What i'd like is to keep this partition because i have a lot of things installed and configurated for my job that i'd rather not go through again.

---

