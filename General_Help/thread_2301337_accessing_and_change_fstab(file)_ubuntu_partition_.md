---
title: "accessing and change fstab(file) ubuntu partition from windows"
date: 2015-11-01
forum: General Help
---

### Post by neuber on 2015-11-01
Hi guys

I am trying everything but not to managing the file /etc/fstab of the ubuntu without ubuntu

the error started because I changed the file: / etc improperly and now my ubuntu 14  not access.

In windows 8.1 I tried ext2explore-2.2.71 and Ext2Fsd-0.62 with adm but I can't change, delete fstab or rename fstab_backu2 to back fstab

---

### Post by yancek on 2015-11-01
Use the installation medium you used to install Ubuntu or any Linux Live CD to do that.  Boot the Live CD, create a mount point for root filesystem partition, mount it and make the changes.

---

### Post by neuber on 2015-11-01
[[COLOR=#000000]yancek[/COLOR]]("http://ubuntuforums.org/member.php?u=1928724")

I do this but don't worked



sudo mkdir /media/neuber
sudo mount /dev/sda3  /media/neuber
cd /media/neuber
ls (THE file fstab list (one) is not a original fstab and not fstab_back2 created by me
nano fstab
THE file fstab Is not a fstab original

---

### Post by tturrisi on 2015-11-01
boot from a live ubuntu usb or dvd and edit/rename the files.

---

### Post by neuber on 2015-11-01
[COLOR=#000000]I do this but don't worked[/COLOR]



[COLOR=#000000]sudo mkdir /media/neuber[/COLOR]
[COLOR=#000000]sudo mount /dev/sda3 /media/neuber[/COLOR]
[COLOR=#000000]cd /media/neuber[/COLOR]
[COLOR=#000000]ls (THE file fstab list (one) is not a original fstab and not fstab_back2 created by me[/COLOR]
[COLOR=#000000]nano fstab[/COLOR]
[COLOR=#000000]THE file fstab Is not a fstab original[/COLOR]

---

### Post by yancek on 2015-11-01
Did you do this using the installation disk/flash drive? When you used the mkdir and mount commands, did you get any output?  If not it should have worked.  When you do:  cd /media/neuber you are a normal user and can't modify the file.  After mounting, use:  sudo nano /media/neuber/etc/fstab  OR, you can replace nano with gedit if you are more familiar with it.

---

### Post by neuber on 2015-11-02
Tank's yancek, that's worked. Now I can back to my original problem. [http://www.vivaolinux.com.br/topico/UbuntuBR/MicroSD-Somente-Leitura](http://www.vivaolinux.com.br/topico/UbuntuBR/MicroSD-Somente-Leitura)
With you can help me I appreciate

---

### Post by neuber on 2015-11-02
My problem now is: Format SD CARD protected ([COLOR=#545454][FONT=arial]/[/FONT][/COLOR][COLOR=#6A6A6A][FONT=arial]**dev**[/FONT][/COLOR][COLOR=#545454][FONT=arial]/[/FONT][/COLOR][COLOR=#6A6A6A][FONT=arial]**mmblkp01 and **[/FONT][/COLOR][COLOR=#545454][FONT=arial]/[/FONT][/COLOR][COLOR=#6A6A6A][FONT=arial]**dev**[/FONT][/COLOR][COLOR=#545454][FONT=arial]/[/FONT][/COLOR][COLOR=#6A6A6A][FONT=arial]**mmblkp02)  in ubuntu using gparted**[/FONT][/COLOR]

---

### Post by tturrisi on 2015-11-02
Start a new thread re the sd cards.

---

### Post by yancek on 2015-11-02
What did you do in GParted and what was the result?  You need to post more details and be sure to unmount any partition before you try to format it.  I'd agree to start a new thread because this is pretty unrelated to your title.

---

