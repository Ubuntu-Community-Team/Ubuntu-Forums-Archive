---
title: "Anybody running Edgy on an Asus P5W motherboard?"
date: 2007-01-22
forum: General Help
---

### Post by mrojas73 on 2007-01-22
HI,  I bouthg this board (Asus P5W Deluxe), 2 GBs of OCZ platinum ram, and an intel Core2Duo 4600.   I can run Dapper with no problem and even install Edgy from both the lice cd or the alternate cd, the installation completes succesfully, but the syste will not boot.  It gets stuck in the ubuntu screen and after a long wait it gives an error.  I can't remember the error right now, but I will record it next time I try to boot from that hard drive.

I am just wondering if anybody has been able to run edgy on this board.

Thanks.

---

### Post by lvanderree on 2007-01-28
It runs fine for me, but only when not using the jmicron ide connector...

I disabled this in the bios.

---

### Post by alex77 on 2007-03-23
I suspect you are having the same problems as I had:

[http://ubuntuforums.org/showthread.php?t=376762]("http://ubuntuforums.org/showthread.php?t=376762")

you certainly have the same symptoms. Edgy doesnt seem to liek the jmicron driver. You could disable it if you dont have any IDE stuff attatched, but a nice chap callled temis01 told me that adding: irqpoll noapic nolapic to the kernel options works niceley.

> At install with edgy you have to add :
irqpoll noapic nolapic
before "--" to kernel options

At first boot after install when you see grub menu :
press e
select the kernel line, go to the end of it and add the same sequence
press ENTER
press b

When boot is done from a terminal or console, do :
sudo nano /boot/grub/menu.lst
edit this line :
# defoptions=ro quiet splash
so it looks like this :
# defoptions=ro quiet splash irqpoll noapic nolapic
CTRL + O
CTRL + X
then type :
sudo update-grub

Now edgy will always boot with the required sequence you added

You're done


This solved it, ubuntu installled nicely. Of course I then had issues with starting x server because my graphics card was hated, and my wireless still isnt sorted, but those are other stories...

---

### Post by xadder on 2007-03-23
Just for the record, I have an Asus P5B and Jmicron, and edgy worked fine for me first time around. That was after I had spent a month trying to get other distributions to work (including edgy).

I send this just to give hope to others that yes, edgy and Jmicron can co-exist. I don't know it works for some but not others though.

---

### Post by RapMan on 2007-03-30
I am running Edgy on P5W with disabled JMicron controller, without problems.
WiFi works with ndiswrapper installed from source files, trhe remote works with lirc 0.81pre installed also from source files. 
Feisty Herd 5 didn't boot, my system is now stable, maybe I will try the final version...

---

### Post by beeboob on 2007-03-31
But what whit us. There have are dual boot. And the JMicron? 

I will be are bad thing if i have to reinstall win. (autocad and so on) 

I there are ok way to install 7.04 and dont have to lose the other OS

---

