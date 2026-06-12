---
title: "ubuntu is not installing on hard drive please some help"
date: 2013-02-02
forum: General Help
---

### Post by larry3d on 2013-02-02
hello everyone  i have a problem trying to install ubuntu in one of my oldest computer i  dont have a good  knowledege but i can learn very easy if you explain step by step what do i need to do . ok here is   

error : file not found
grub rescue > ls
(hd0)  (hd0,msdos5) (hd0,msdos1)
grub rescue > ls (hd0,1)/
./ ../ lost+found/ pinguy_32 bit.iso [BOOT]/ casper/ isolinux/ preseed/ md5sum.
txt README.diskdefines ubuntu


i hope some help please i need this computer working for my uncle

---

### Post by speartip on 2013-02-02
When you say "my oldest computer" what are the specs & how old is it?
As much info as possible will allow the maximum amount of help.

---

### Post by larry3d on 2013-02-02
motherboard
**[SIZE=3]msi MS-6577 ver 2.1[/SIZE]**

primary master [ST3160021A]
primary slave  [none]
secondary master  [none]
secondary slave  [none]

memory slot 1  512 mb ddr sdram
memory slot 2 256 mb  ddr sdram

BIOS Core Version    v6.0
BIOS Revision  3.09 12/11/2002


hard drive barracuda 160 gb   product of china 



 i hope this help  thank you

---

### Post by speartip on 2013-02-02
Ubuntu will run but more ram would help.
You would probably do better with the 12.04lts xubuntu version from here:
[http://xubuntu.org/getxubuntu/](http://xubuntu.org/getxubuntu/)
burn to disc & see if that fires up.

---

### Post by larry3d on 2013-02-02
i had before on this machine ubuntu (pinguy) but than i switch many times with diferent platforms on this computer but now is refusing to install again ubuntu  , i only want the 32 version running on this machine and pinguy is not using unity

---

### Post by larry3d on 2013-02-02
i think all this problems started when i format the hard drive using a usb adapter conected to the usb of my other computer, making the format inside ubuntu 

compatible with all system (FAT)

than after that i took it  back to my motherboard and when i start the machine with the cd inside i saw the message

 error : file not found
grub rescue >

it works fine with another hard drive but has windows xp , but i hate windows xp because my uncle love to open all his emails and most has virus , so better for him is linux so i need again ubuntu running on this machine

---

### Post by speartip on 2013-02-02
You could try using the live gparted cd & format the hard drive again to ext4.

---

### Post by larry3d on 2013-02-02
speartip can you tell me please how can i do that ?  you mean i have to connect again the hard drive through the usb adapter to my other computer and install this gparted on ubuntu and format my hard drive ? is that what you mean  ? and what is ext 4 ?

---

### Post by Calinou on 2013-02-02
Pinguy is not Ubuntu and it's not supported here.

---

### Post by speartip on 2013-02-03
Reading your posts again, i'm not sure we have hit the problem.
Do you have an ubuntu live cd/usb?
When you put it in the machine you wish to install to, is it set to boot from the cd or the hard drive?
The message you posted:
error : file not found
grub rescue >
tells me your booting from the hard drive not the cd, hence the "file not found" message, because your hard drive is blank.
Please tell us exactly what you are doing, & what medium you are using, & as the last poster said are you using Ubuntu or Pinguy?

---

