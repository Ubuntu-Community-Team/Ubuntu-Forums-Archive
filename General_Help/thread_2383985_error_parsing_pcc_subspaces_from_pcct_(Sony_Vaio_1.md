---
title: "error parsing pcc subspaces from pcct (Sony Vaio 13&quot; Pro)"
date: 2018-01-31
forum: General Help
---

### Post by p-dimo on 2018-01-31
Hi all, i have the above laptop computer which at one stage had windows 8.1 then windows 10 pro. It was running completely fine but i have upgraded my machine and want to use this for a version of linux.

The problem i have is it has installed but i get the above error message when i installed. I have tried UEFI Bios and legacy. When i got the error message i rebooted and tried again and now i cant get out of the bios (as it keeps going there) unless i reinstall Ubuntu (or windows for that matter).

Im guessing Sony has inbuilt code to overwrite anything that is not windows? Any help appreciated.

Peter

---

### Post by mörgæs on 2018-02-01
Hi, welcome to the fora.

It's correct that Sony is far from linuxfriendly but I don't think it's the problem this time. Have you disabled fast boot, restricted boot and other strange boot settings as discussed in the following link?

[https://askubuntu.com/questions/670509/error-parsing-pcc-subspaces-from-pcct-acpi-pcc-probe-failed](https://askubuntu.com/questions/670509/error-parsing-pcc-subspaces-from-pcct-acpi-pcc-probe-failed)

---

### Post by p-dimo on 2018-02-05
Thanks for the reply. I have changed a few things in the BIOS for anyone who is interested. AT (anti theft from Intel has been disabled and booting into legacy mode). My bios is very basic, there isnt anything for "fast boot" etc... Though this lappy was classed as a 6 seconds windows boot at the time (fastest at the time?)

---

### Post by mörgæs on 2018-02-05
In recent releases of Windows the default action when turning on the computer is in reality a wake-up from hibernating. If you want to measure the time for a real boot you have to click 'restart'.

---

