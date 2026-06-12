---
title: "Ubuntu 18.04 LTS freezing during boot up"
date: 2020-09-24
forum: General Help
---

### Post by swarup on 2020-09-24
I am using Ubuntu 18.04 LTS as a guest OS in VM Ware workstation 15 player on a Win 10 laptop. I had the maximum size of the HD set to 40 GB. The current size has reached 39.4, i.e. it filled the virtual HD, and today the OS will not boot up. It tries to when I give the command, but is unable to complete the process of booting and freezes up. Please see the attached screen print to see where it reaches. I thought it was likely due to lack of space, so I created a copy of it on my external HDD and expanded the size of the virtual HD from 40 to 46 GB. But still it is getting stuck during boot up at the same place. I do not have any backup of this and it contains important material, so I need to get it running. Help will be deeply appreciated. 

Is there any way to boot into safe mode in vmware?

---

### Post by CelticWarrior on 2020-09-25
Increasing the size of the virtual drive does not increase the size of the partition inside. From a live session booted from the ISO min the VM we can do the usual operations with Gparted. That said I'm really not sure that's a solution.

---

### Post by swarup on 2020-09-25
Ultimately I got a temporary solution yesterday: In my original virtual machine, the one in my laptop, at the time of boot, by pressing and holding the left shift key I was able to get the Ubuntu boot menu (Grub) to show. And by that I was able to (1) fix defective files needed for boot, and (2) clean the virtual machine and thereby create some space. After doing both these I was able to boot up the virtual machine, and it is working fine (the OS is not using the whole virtual screen, probably something related with vmware tools for linux, but that is not my main concern right now).

So I am going to increase the virtual drive size now. Once that is done, can I install GParted within the virtual drive and have it increase its partition size to match the virtual drive size? Or will I have to run GParted from outside the the virtual drive? (If so, that sounds a bit complex as we are talking about using a boot disc to boot the virtual vmware drive.) Was hoping to manage it from within the virtual OS if possible.

---

### Post by CelticWarrior on 2020-09-25
You need a live session for managing any partition that will be in use when running the system. There's no difference between a VM and bare metal in that regard.

---

### Post by swarup on 2020-09-25
Ok so in that case I will need to use a boot-up disc to boot from, rather than booting into my Win 10 OS? And once I boot using the bootup disc, I will have to look inside the Win OS for my documents folder, and therein the virtual machines folder, and therein my virtual machine called Ubuntu 18.04 LTS. Once I open Gparted in the live boot, how will I see virtual disc and the Ubuntu partition inside it? All I have is that vmware .vmdk file called "Ubuntu 18.04 LTS.vmdk". How will Gparted see the partition and do its work?

---

