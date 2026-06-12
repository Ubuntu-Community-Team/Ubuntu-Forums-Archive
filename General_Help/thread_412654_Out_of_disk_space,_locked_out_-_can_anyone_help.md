---
title: "Out of disk space, locked out - can anyone help?"
date: 2007-04-18
forum: General Help
---

### Post by Jaylon on 2007-04-18
Hi. 

I'm currently unable to login to Ubuntu 6.10 at all. It's because I've completely run out of disk space on the boot partition.

Do you know how I can get access so I can delete some of the files? I've tried booting from the live CD, but I don't seem to be able to find my hard drive.

---

### Post by Wim Sturkenboom on 2007-04-18
With *sudo fdisk -l* in a terminal you should be able to see all HDs.

Further you can try to login from the commandline instead of the graphical interface.

---

### Post by akshaysrinivasan on 2007-04-18
You can boot into the Terminal , this one doesn't need much of hard disk space.Try the key combination 
left ctrl+left alt+F1.Login to your account and remove files with rm and rmdir commands.then after you have freed enough space try startx.Maybe you can resize your partition ,but i don't know much on that ,you can know more by trying 'man resize'.

---

### Post by earobinson on 2007-04-18
> **akshaysrinivasan said:**
> You can boot into the Terminal , this one doesn't need much of hard disk space.Try the key combination 
left ctrl+left alt+F1.Login to your account and remove files with rm and rmdir commands.then after you have freed enough space try startx.Maybe you can resize your partition ,but i don't know much on that ,you can know more by trying 'man resize'.
This is the correct answer.

---

### Post by Oki on 2007-04-18
Can&#8217;t it help if he boots into the terminal and run the
sudo apt-get clean
?

---

### Post by earobinson on 2007-04-18
sudo apt-get clean is a great command to run (it removes all the installer files that you downloaded to do updates) for more info use man apt-get

---

### Post by Jaylon on 2007-04-18
Thanks guys - I'll give it a go at home

---

### Post by ububaba on 2007-04-18
> **earobinson said:**
> sudo apt-get clean is a great command to run (it removes all the installer files that you downloaded to do updates) for more info use man apt-get

Suddenly I have started the problem of shortage of space (98% of the disk is free). 
Can't download even mail in **Evolution.** Can't access **gdparted** except after having 
changed permission. This "permission" lasts for the maximum of a minute. Twice
 **sudo apt-get clean** has helped but that too has now gone on strike. Any tricks to get
back to normalcy? Thanks in advance.

---

### Post by earobinson on 2007-04-18
remove some files you dont need?

rm is the remove command fyi

---

### Post by silverglade00 on 2007-04-18
Another place to check is the .Trash folder in both /root and your /home folders. It's easy to let a lot of junk build up in there. ISOs on my computer, mostly :)

---

### Post by ububaba on 2007-04-18
> **silverglade00 said:**
> Another place to check is the .Trash folder in both /root and your /home folders. It's easy to let a lot of junk build up in there. ISOs on my computer, mostly :)

Have emptied the trash. There is about 280Gbs still unused on my HDD. Restart did not help at
all.

---

