---
title: "Installing ubuntu on a Usb pendrive"
date: 2008-05-01
forum: General Help
---

### Post by SpirituZ on 2008-05-01
Hello.. how are you all?....well heres my problem

i have bought a 4 Gb pendrive.. i've read several tutorials on how to install/run ubuntu on a pendrive but it doesnt seems to work ( i've been trying to ubuntu 8.04 aswell with 7.10 ...

i've tried copying all the files from the iso into the pendrive aswell, changed the bios settings to removable (which means usb) and it doesnt even boot 

-----------------------------------------------------------------
sooo what i need is a good working tutorial that lets me run ubuntu on a pendrive 


sorry for my english tho =/

---

### Post by agim on 2008-05-01
I believe the problem is that you haven't installed grub on the usb.  
here is a good looking tutorial. I haven't been able to get around to trying it, but it looks legit.

[http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/](http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/)

---

### Post by SpirituZ on 2008-05-01
i tried the tutorial  from that site but the version 8.04

---

### Post by iSplicer on 2008-05-01
> **SpirituZ said:**
> i tried the tutorial  from that site but the version 8.04

I think it will still work

---

### Post by agim on 2008-05-01
I don't mean to insult your level of knowledge, but did you read the part about installing grub or lilo to the usb? 

Quote:
Note: If your having trouble getting Ubuntu to boot, your memory stick may have a corrupted MBR. To repair the MBR of your USB device, at the terminal type sudo apt-get install lilo then type lilo -M /dev/sdx (replacing x with the letter of your flash device)

---

### Post by agim on 2008-05-01
I don't mean to insult your level of knowledge, but did you read the part about installing lilo to the usb? 

Quote:
Note: If your having trouble getting Ubuntu to boot, your memory stick may have a corrupted MBR. To repair the MBR of your USB device, at the terminal type sudo apt-get install lilo then type lilo -M /dev/sdx (replacing x with the letter of your flash device)

---

### Post by reb0rn on 2008-05-01
I managed to install ubuntu 8.04 on kiggston 4GB flash... BUT
I paritioned USB from live CD also i put GRUB on Usb and than i select USB to be primary devece in bios it booted, only porblem was that Grub stated its HD1,0 but it should be HD0,0 i edited and managed to boot Ubuntu 8.04 but looks like there is more problems with it..... whan i enter my data in login screen system does never show Gnome interface it just stop there i only see desktop with no interface.........
I also find more ppl here had the same problem!

---

### Post by SpirituZ on 2008-05-01
ok i just woke up, and thank for these usefull information ill try them.

---

### Post by Keith5698 on 2008-05-01
> **reb0rn said:**
> I managed to install ubuntu 8.04 on kiggston 4GB flash... BUT
I paritioned USB from live CD also i put GRUB on Usb and than i select USB to be primary devece in bios it booted, only porblem was that Grub stated its HD1,0 but it should be HD0,0 i edited and managed to boot Ubuntu 8.04 but looks like there is more problems with it..... whan i enter my data in login screen system does never show Gnome interface it just stop there i only see desktop with no interface.........
I also find more ppl here had the same problem!

I'm brand new to Ubuntu, and I am also having this same problem.  I followed the instructions for installing Ubuntu on a flash drive from [http://www.pendrivelinux.com/2008/04/14/ubuntu-804-usb-hard-drive-install/](http://www.pendrivelinux.com/2008/04/14/ubuntu-804-usb-hard-drive-install/) 
and everything seemed to boot properly, but after I log in, everything stops at a blank screen.  Not really sure where to go from here, so any assistance that could be provided will be appreciated!  Thanks!

---

### Post by SpirituZ on 2008-05-01
ok i tried that the lilo -M dev/sdb and it worked, it boots..

But. then i tried installing the OS itself into the  pendrive... used that lilo command but it stays trying to boot it ...

---

### Post by SpirituZ on 2008-05-01
editedd

---

