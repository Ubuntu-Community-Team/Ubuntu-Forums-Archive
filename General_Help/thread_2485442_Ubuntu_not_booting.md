---
title: "Ubuntu not booting"
date: 2023-03-29
forum: General Help
---

### Post by mahassani on 2023-03-29
I am getting prompt to grub rescue - I have looked to general solution like set boot and set prefix not working. 
I did a boot repair and got [http://paste.ubuntu.com/p/rNpfnMnyFZ/](http://paste.ubuntu.com/p/rNpfnMnyFZ/) 
Any help is welcome to boot on the computer and fix it Thank you

---

### Post by yancek on 2023-03-30
The obvious question is did this install ever work?  Or is it a new install which has not booted?
See Line 31 in boot repair.  It says "0 OS detected"
Line 15 shows sda1 which is LVM.
Starting at Line 88, there is information on LVM.  I don't use LVM but it is my understanding that LVM with encryption requires a separate boot partition which you do not have.
See the link below for more information.

[https://gist.github.com/superjamie/d56d8bc3c9261ad603194726e3fef50f](https://gist.github.com/superjamie/d56d8bc3c9261ad603194726e3fef50f)

---

### Post by mahassani on 2023-03-30
[SIZE=3]Unfortunately, it did not and I am still stuck to log in and retrieve some of the data.:(
When I reboot, prompt to grub rescue with error: attempt to read or write outside of disk 'hd0' 
The ext2 is in lvm/ubuntu--vg-root, the other are hd0, hd,msdos1 and lvm/ubuntu--vg-swap_1. Also, when looking at the setting, I see cmdpath=(hd0)[/SIZE]

---

### Post by MAFoElffen on 2023-03-30
> **yancek said:**
> [COLOR=#ff0000]The obvious question is did this install ever work?  Or is it a new install which has not booted?[/COLOR]

See the link below for more information.
[https://gist.github.com/superjamie/d56d8bc3c9261ad603194726e3fef50f](https://gist.github.com/superjamie/d56d8bc3c9261ad603194726e3fef50f)

This question was never answered...

I have more questions. This looks to me as a recent Lenovo computer, where it has UEFI BIOS, but is installed and the boot from the LiveUSB was via Legacy/CSM. Is there a reason for that? What is the BIOS set to boot as?

Noted that that is a very good set of instructions as a reference.

---

### Post by yancek on 2023-03-31
> [SIZE=3]Unfortunately, it did not and I am still stuck to log in and retrieve some of the data[/SIZE] 

Does that mean it never booted successfully?  If that is the case, I don't understand your reference to retrieving data.  If it never booted, what data are you referring to?

 Since boot repair did not detect any OS (line 31 of boot repair) you need to install again.  My limited understanding of LVM and encryption is that you need a separate /boot partition so when you reinstall make sure you create a separate boot partition.  Good luck.

---

### Post by mahassani on 2023-03-31
[SIZE=4]Thanks a lot, I did not understand the output of the boot repair. I think my option now is to re-install :(
I missed to mentioned, I guess important, this machine had LTS 18. and after an upgrade to LTS 20 this issue happened. It did after shutdown due battery low! 
The error I ger is "ERROR: attempt to read or write outside of disk 'hd0'. Entering rescue mode... grub rescue >" In grub, tried defining set boot and set prefix then [insmod]("https://www.linuxfoundation.org/blog/blog/classic-sysadmin-how-to-rescue-a-non-booting-grub-2-on-linux") but same error I get. 
I booted the machine from live usb LTS 18 and tried to re-partition drive to install the boot in there (100 mib), but run out of space. Then installed boot repair and tried to repair and got the message that shared in here. [/SIZE]

---

### Post by ActionParsnip on 2023-03-31
So you attempted to upgrade an OS from LTS to the next LTS on battery power....? Is this what you are saying?

---

### Post by mahassani on 2023-03-31
Not, it did upgraded and booted - but kept running on low battery till shut down. From there, this issue started

---

### Post by yancek on 2023-04-01
Do you have a 'live' USB of Linux you can use to mount and attempt to view what data is on the device?  If so, are the boot files of Grub on sda1? Do they show a grub.cfg file with a menuentry pointing to Ubuntu which is also on sda1?  As asked before, is your drive (sda1) encrypted?  Did you have a separate boot partition previously?  It looks to me as if the entire drive is taken up by the Ubuntu (OS) partition and the swap so you would need to decrease the size of the main partition to create a separate /boot partition.  I don't know how to do that with LVM so wait for someone else to respond.  Have you tried using the Ubuntu 18.04 USB to access the drive to copy data from it to another drive?

---

### Post by mahassani on 2023-04-01
Thank you for inputs, I will see whether I could find some suggestions on how to create the /boot on LVM. 
I do have 18.04 USB, as for whether is in Grub or sda, I am not sure, neither the other questions. Not expert in this matter. 
sda1 is not encrypted. Have not tried to copy the data from anther drive, but will look for it- Thanks a lot!

---

