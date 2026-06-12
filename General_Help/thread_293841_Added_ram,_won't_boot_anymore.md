---
title: "Added ram, won't boot anymore"
date: 2006-11-05
forum: General Help
---

### Post by stuffelse on 2006-11-05
Hi all,
First post here. Installed 6.06 Dapper x64 on my Turion 64 laptop. I installed it at stock specs for the machine (2x256 PC2700), dual-booted with XP Pro, it worked great. I installed a 1GB PC2700 ram stick in place of a 256 earlier today, and dapper no longer wants to load. Windows XP works better than it did before, so the ram is not suspect. It will go through the GRUB, start the boot screen with the loading bar, when it gets to the last "text i can't remember [OK]" type of line, it slows down DRASTICALLY. I waited about 5 or more minutes, and it eventually spit out about 1 loaded line per minute. I've tried it twice, both times I grew impatient and powered it down. I'm currently running a memtest just for kicks.

Has anybody else experience anything similar?

---

### Post by pdub on 2006-11-05
RAM quite often has to be installed in pairs. I know that my notebook had 2x256 and I had to install 2x1024. Did you check your users manual to ensure that you can mix the RAM sizes?

---

### Post by ReaderRat on 2006-11-05
Are you running the 1Gig stic along with a 256 Meg stic? Some computers won't do this....they have to have two identical stics.

---

### Post by stuffelse on 2006-11-05
yeah i've got a 1024 stick and a 256 stick, both are pc2700. the reason i didn't suspect that is that it worked perfectly in windows, so i dont think it's a hardware issue.

---

### Post by stuffelse on 2006-11-05
*bump* sorry...

anyway I got a chance to boot the laptop again, it's currently sitting at the Ubuntu load screen with the progress bar, and it's sitting at "Loading Manual Drivers..." and has been there for WAY longer than it ever did before. 

it is now VERY slowly scrolling the images and text off the screen. and by slowly i mean it took 30 seconds for the "ubuntu" image and progress bar to scroll away.

Is there a command for Ubuntu that performs a file system check that is safe for a dual boot setup?

---

