---
title: "Password issue"
date: 2013-01-01
forum: General Help
---

### Post by bobipod on 2013-01-01
[http://www.linuxuser.co.uk/features/raspberry-pi-media-centre-tutorial](http://www.linuxuser.co.uk/features/raspberry-pi-media-centre-tutorial)

I'm trying to download and install the program for my Raspberry Pi from the link above. 

I get to step 3 and it keeps asking for my password.  Everytime i enter the password it says it's wrong but i know for sure it isn't.

Can i disable or change the password to get around this problem?

I'm running the latest update on ubuntu 12.10

---

### Post by bobipod on 2013-01-01
[http://www.upubuntu.com/2012/09/how-to-reset-lost-user-password-on-pc.html](http://www.upubuntu.com/2012/09/how-to-reset-lost-user-password-on-pc.html)

*I've tried this but i just get an error when i re enter the new password and it says nothing changed??*

---

### Post by chadk5utc on 2013-01-01
ok what version of linux are you using on your pi?
And are you able to boot it to terminal #

---

### Post by bobipod on 2013-01-01
I'm not using anything on Pi yet.  I am trying to download the program onto the sd card.  The problem i have is that my ubuntu laptop (which i'm using to get the program onto the sd card)  will not recognise or change/remove my password and will just not allow me to download the program.

---

### Post by chadk5utc on 2013-01-01
Ok I understand now and have had this happen once long ago heres a link that should help
[https://help.ubuntu.com/community/LostPassword](https://help.ubuntu.com/community/LostPassword)

---

### Post by bobipod on 2013-01-01
> **chadk5utc said:**
> Ok I understand now and have had this happen once long ago heres a link that should help
[https://help.ubuntu.com/community/LostPassword](https://help.ubuntu.com/community/LostPassword)

On this link using the first method i go through all the steps but get the message:

passwd: authentication token manipulation error
passwd: passwd unchanged

The Other Way
I hold shift and it just gives the option of normal boot or boot to recovery mode.  Recovery mode doesn't have any options with kernel n it. I assume i must be in the wrong place?

---

### Post by steeldriver on 2013-01-01
try this link - in particular make sure you remount the root filesystem with read-write permissions

[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by bobipod on 2013-01-01
> **steeldriver said:**
> try this link - in particular make sure you remount the root filesystem with read-write permissions

[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

perfect that's done it for me.

---

### Post by chadk5utc on 2013-01-01
Good glad to hear one of them worked.

---

