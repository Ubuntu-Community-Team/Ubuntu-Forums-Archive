---
title: "Ubuntu freezes"
date: 2006-12-01
forum: General Help
---

### Post by rexio8 on 2006-12-01
I've installed Ubuntu 6.10 and have some problems with it. The thing is that it crashes a lot of times. The system just freezes and you can't do anything. The only thing left is to press the reset button. Those crashes appear regardless of what I do and at no particular time. My computer spec.:
Pentium 4 2,4 HT, 2 x 512 MB DDR Kingmax in Dual, Gigabyte I8PE1000-L, Fic Radeon 9500 PRO, one network card, 80GB Seagate(with Ubuntu only), 200GB Seagate, Nec 3520A DVD-RW.
I've checked the cd for errors - everything ok. Memtest86+ shows no errors also. What is more I have a Windows XP on the same machine and it works fine. The ubuntu booted from the live cd hangs too. What could it be? The temperatures seem fine, Voltage also...Could it be some sort of driver malfunction or what?
Thanks for any help. 

P.S. I've run fsck from the live cd. The disk is clean of errors.

---

### Post by aidanr on 2006-12-01
can you check the logs for anything that might help, system->administration->system log

i had problems before with the computer locking up, turned out to be the psu

---

### Post by wpshooter on 2006-12-01
My first guess would be that it may be related to the setup of your Radeon 9500 video card.

---

### Post by rexio8 on 2006-12-02
I just can't believe it. I've tried to install fglrx but with no efect. So I've decided to format the disk and try to install ubuntu once more to have a clean start. But no I can't even install it because my pc hangs while copying files or even right on the start when you input the user name etc. Could a "broke" graphic card cause things like this? (on windows everything is fine.. I also don't remember to have such problems with dapper). What is more I've recorded the iso-image with egdy on a second cd. And still nothing changes so I think that the image, recorder and cd's are good.

P.S. Nothing interesting in the syslog.

P.S.2 I've managed to install ubuntu... Somehow it just didn't hang. But still fighting with it.

---

