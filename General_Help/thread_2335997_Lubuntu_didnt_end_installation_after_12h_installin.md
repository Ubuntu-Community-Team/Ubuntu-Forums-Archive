---
title: "Lubuntu didnt end installation after 12h installing"
date: 2016-09-03
forum: General Help
---

### Post by aaddaamm on 2016-09-03
Hi guys, im new in the forum and not very good in english so im sorry about the mistakes i could have.

So a yesterday i started the installation of Lubuntu in a lil bit old PC, with 1GB RAM and a AMD athleon 3500+.
All was going right, but the installation has stucked since yesterday and it only displays this message :

Detecting Filesistem

Lbuntu CRON [23142]: (root) CMD ( cd / && run-parts --report /etc/cro.hourly)
Lbuntu CRON [23282]: (root) CMD ( cd / && run-parts --report /etc/cro.hourly)

I dont know if i should stop installation or idk really what i have to do.

---

### Post by mörgæs on 2016-09-03
Hi, welcome to the fora.

12 hours is a sign that something is wrong. Which release of Lubuntu did you try to install?

---

### Post by aaddaamm on 2016-09-03
Lubuntu 16.04 LTS.
Thanks for fast reply :)

---

### Post by Bucky Ball on 2016-09-03
Are you trying to dual-boot this with Windows or install Lubuntu only? A a new or old drive if Lubuntu only?

Can you boot from the install media (the Ubuntu disk or USB) and choose the option 'Try Lubuntu'? What happens?

---

### Post by aaddaamm on 2016-09-03
Ive done all at Try Lubuntu without installing, the PC had Win XP before that, but i wanted to erase all the disk.

---

### Post by TheFu on 2016-09-03
I don't have the answer, but [https://askubuntu.com/questions/117744/how-can-i-install-on-a-non-pae-cpu-error-kernel-requires-features-not-present](https://askubuntu.com/questions/117744/how-can-i-install-on-a-non-pae-cpu-error-kernel-requires-features-not-present) seems relevant.

---

### Post by mörgæs on 2016-09-03
We know that the processor is an Athlon, hence no PAE problems here.

Aaddaamm, if you meant 16.04.0 then please try 16.04.1 in stead. 

If you want to use Google Chrome then you should pick the 64 bit version, if you prefer Chromium and/or Firefox then I would recommend 32 bit for this hardware.

---

### Post by Bucky Ball on 2016-09-03
> **aaddaamm said:**
> Ive done all at Try Lubuntu without installing, the PC had Win XP before that, but i wanted to erase all the disk.

You've tried all that and it can boot to 'Try Ubuntu'??? You didn't answer that clearly and that's what I was asking.

If you can, install Gparted from the package manager there, Synaptics, then open it. Delete all partitions from your disk and then go to 'Devices'. Choose 'Create new partition table'. That should leave you with a clean disk. Now reboot and try installing Lubuntu again.

---

### Post by RobGoss on 2016-09-03
You might want to try a lighter distribution of Ubuntu you don't have enough Ram to handle **16.04** it requires more and will not run as it should

A clear indication when booting in to the live session if it's not running as intended then the odds that it will run efficiently is not likely. The installation does not take 12-hours that's a sign there's something wrong with the installation. I recommend trying other flavors of Ubuntu and see if there's any that will work correctly on that old machine stick with the lighter versions

---

### Post by Bucky Ball on 2016-09-03
> **RobGoss said:**
> You might want to try a lighter distribution of Ubuntu

They are: Lubuntu. And Lubuntu 16.04 should be ok on that machine. Next step would be the Ubuntu minimal install or something outside of the Ubuntu flavours. :)

---

