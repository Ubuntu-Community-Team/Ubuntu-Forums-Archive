---
title: "Ubuntu 16.04 doesnt boot after trying to enter as root"
date: 2018-09-08
forum: General Help
---

### Post by jfcastello on 2018-09-08
Hello everyone , i've been stuck trying to recovery my ubuntu 16.04.

i was trying to log as root using 
"vi /etc/lightdm/lightdm.conf. " 
as is explained here "http://www.byclouder.com/help/recovery/mobile/pro/how-to-recover-mobile-phone-file.html" (i was trying to easy recover data from my oldest androids)

but, when i reboot system ubuntu doesnt load and i get a black screen with a blinking line where i cant write anything. so i just tryied a few things:

1. was to enter an usb with ubuntu 14.0 and i selected an option that says some like " search for damage files in disk" . then it appears after the system finished to "search" that it found two files damage and press any key to reboot. but... it doesnt work for mi, after reboot nothing happends

2. i also tryed using boot-repair in the "use ubuntu 14.02 without install it", but i get an error.

3. desesperated i went to grub commands, starting EFI general disk on bios and pressing "e". but it is chinense for my...

aditional i dont find the option "advances option" that here says: 
"https://wiki.ubuntu.com/RecoveryMode"
 i have many photos, python packages, apps,arduino proyects , and very important data that i dont want to lose :( :( , for that reinstall is not an option.


thanks if you can help me!!.

---

### Post by Impavidus on 2018-09-08
> **jfcastello said:**
> Hello everyone , i've been stuck trying to recovery my ubuntu 16.04.

i was trying to log as root using 
"vi /etc/lightdm/lightdm.conf. " 
as is explained here "http://www.by...-recover-mobile-phone-file.html" (i was trying to easy recover data from my oldest androids)
That guide offers some really dangerous advice. Never enable root login for the GUI. Never. Don't even enable the root password.

> but, when i reboot system ubuntu doesnt load and i get a black screen with a blinking line where i cant write anything. so i just tryied a few things:

1. was to enter an usb with ubuntu 14.0 and i selected an option that says some like " search for damage files in disk" . then it appears after the system finished to "search" that it found two files damage and press any key to reboot. but... it doesnt work for mi, after reboot nothing happends

2. i also tryed using boot-repair in the "use ubuntu 14.02 without install it", but i get an error.

3. desesperated i went to grub commands, starting EFI general disk on bios and pressing "e". but it is chinense for my...

aditional i dont find the option "advances option" that here says: 
"https://wiki.ubuntu.com/RecoveryMode"
I don't know how much damage you have caused by now. Using the live disk, you should be able to access the files of your installed system. Try to undo the changes to /etc/lightdm/lightdm.conf. With a bit of luck, you can get in again. Then disable the root password with```
sudo passwd -d root
```If you can't get in, I don't know what other damage you did. Best to reinstall in that case. Take the opportunity to move to 18.04. You should be able to access your files using the live disk and make backups on external media.
 > i have many photos, python packages, apps,arduino proyects , and very important data that i dont want to lose :( :( , for that reinstall is not an option.


thanks if you can help me!!.
If you have backups, you won't lose any documents. If you've got no backups, you'll lose your documents some day. Maybe not today, but it will happen. But with a live disk, you should still be able to create those backups now, even with the system messed up, as long as the filesystem is in reasonable shape.

---

### Post by jfcastello on 2018-09-08
thanks for responding
on my live usb ubuntu 14.02  i opened the terminal and put next direction

> cd /media/ubuntu/8a62147c-57d6-493a-9866-47ae7684a87b/

with that i got into my ubuntu 16.04, so here i purged and reinstalled lightdm, and go to the directories, and restore ligthtdm with 

> sudo service lightdm restart

and reboot

.. it didnt work

so, i went again to the grub mode and when i try to start the rescue mode by commands I get an error saying that the file "/casper/ vmlinuz.efi" was not found.

effectively, I went to ubuntu live disk and searched the casper fodler in my mount unit of ubuntu 16.04 but i didnt find anything!, so i copied (very idiotically) the archive from the ubuntu live disk, but obviously it didnt work.

so... any ideas?  :(

if all this dont work, 
how can i do the backup for all my datas, especially my pythons packages and photos?

thanks

---

### Post by HermanAB on 2018-09-09
You need to stop making changes to the system and make a backup of your data!

Boot a live USB disk, use the file manager to open the HDD, insert another USB widget and copy the data, then keep the widget safe while you are faffing around with your system.  Otherwise you will progressively get more and more unhappy...

---

### Post by QIII on 2018-09-09
A few lessons here:  

If you google it randomly and it says to muck around with system files without first backing them up, it's wrong.  

If you break something and don't go straight to some place like UF or Ask Ubuntu before your start pulling out random parts and throwing them on the garage floor, you are just asking for a significant emotional event.

Back up your important data frequently -- to a device other than the machine it is on.  To two places if you can.  

Don't monkey around with system files unless you know what you are doing.  

And I will give a huge +1 to ***stopping what you are doing*** and backing up your important data before you do anything more.

---

