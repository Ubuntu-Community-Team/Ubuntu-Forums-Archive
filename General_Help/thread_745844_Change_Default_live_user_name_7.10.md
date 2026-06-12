---
title: "Change Default live user name 7.10"
date: 2008-04-04
forum: General Help
---

### Post by pawnrocket on 2008-04-04
I am among other things trying to change the name of the default live user on the 7.10 livecd. I hame mounted initrd.img-2.6.22-14-generic and I am unable to find any references to "ubuntu" using the grep command 

grep -R "ubuntu" * 

does anyone know the location of the Default User Name on the 7.10 live cd?

---

### Post by bodhi.zazen on 2008-04-04
did you try /etc/passwd

I think you are best off :

deleting ubuntu and making a new user though, easer then changing stuff

Just watch your groups, make sure the new user is in the same groups as ubuntu

---

### Post by pawnrocket on 2008-04-04
Does your method work for altering the livecd? I am trying to make the live cd boot with another user name, One that is not "ubuntu" ... I have the whole livecd mounted as well as the initrd.img. So far I have learned that it is in initrd.img somewhere. But I don't know where. How would I delete the user "ubuntu" ? With chroot?

---

### Post by pawnrocket on 2008-04-04
I will restate my question... 

Somewhere on the livecd in the initrd.img (in a script I think) is 

USERNAME=ubuntu
HOST=ubuntu
USERFULLNAME="Ubuntu LiveCD User"

Does anyone know the path 'on the livecd, inside the initrd.img' to the script where USERNAME, HOST, and USERFULLNAME are present?

---

### Post by bodhi.zazen on 2008-04-04
I think all those things are in the various config files in /etc

/etc/hosts and /etc/hostname for host name (change both or you will loose sudo access).

username is in /etc/passwd and /etc/shadow and /home ...

As far as the user, I think making a new one, make sure it works, delete the old one would be easiest. If you want you can then change /etc/passwd and change the uid.

---

### Post by pawnrocket on 2008-04-05
Thank you Bodhi, you are correct, /etc/casper.conf 


I will check the others, as I said I am remastering a live cd - I will look in the other areas for any relevant  info... Thanks again. :popcorn:

---

