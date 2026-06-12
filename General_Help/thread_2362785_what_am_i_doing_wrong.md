---
title: "what am i doing wrong ???"
date: 2017-06-01
forum: General Help
---

### Post by rob141 on 2017-06-01
Hi everyone ;)

Ok so now ubuntu 17.04 works fine.

I am trying to auto mount  on every boot a shared network HDD that is connected on my router through the usb port.

So i edited my fstab like this:   //linksys37952/backups/raspishare /home/*********/pishare/retropie ext4 username=*********,passwd=*********,nounix,noserverino,defaults,users,auto 0 0


I had copied that from my raspberrypie's fstab because this exact setup works, only it is written cifs instead of ext4 before the username part and the username and password are different but it is the same thing for the rest of that code.

Actually i had left it at first as cifs in ubuntu but then i was receiving the error: wrong FS blablabla    so i figured it meant wrong file system

so i changed it to ext4 and then it was ok.

The error i am asking help with is that now i get the error saying that the folder: //linksys37952/backups/raspishare    does not exist 

i know it does exist and i know it is the right path without miss spelling.  what is wrong in that line please ??  should i add:    smb:       before the path //linksys37952/backups/raspishare   ??

Thank you very much in advance

just to make things clear, the path //linksys37952/backups/raspishare is NOT directly on my raspberrypi, it is on my shared network HDD.   ;)    

I only want to share the same folder on both machine for easier futur file transfer between my laptop and my raspberrypi. I want to make sure it is automatically mounted at boot like it is also on my raspberrypi please.

One more thing i forgot to say is that the share kinda work because i see the drive raspishare on my desktop but it is not mounted and if i double click on it i get the same error as it cant be mounted because the folder does not exist. My second question is why is it even on my desktop since it is suposed to be in /home/*********/pishare/retropie  of my laptop ???

---

### Post by rob141 on 2017-06-01
Ok now it finally works

i have change this: [COLOR=#000000]//linksys37952/backups/raspishare /home/*********/pishare/retropie ext4 username=*********,passwd=*********,nounix,noserve rino,defaults,users,auto 0 0

for:  [/COLOR][COLOR=#000000]//ipadresse of my router/backups/raspishare /home/*********/pishare/retropie cifs username=*********,passwd=*********,defaults,users,auto 0 0

and i installed cifs-util  and now everything is ok  ;)    [/COLOR]

---

