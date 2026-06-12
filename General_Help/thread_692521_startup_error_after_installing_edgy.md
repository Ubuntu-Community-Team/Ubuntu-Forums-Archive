---
title: "startup error after installing edgy"
date: 2008-02-09
forum: General Help
---

### Post by hotroddude on 2008-02-09
ok i had a problem i asked about last night with my gutsy instalation, unfortunatly i didnt fix it. so i opened up vista and downloaded the edgy iso ( i wanted to do that seamless running between edgy and xp thing) so i installed edgy and i get a message saying " missing operating system " so i reinstall it a few times and nothing happens, so then i pop in my xp disk and install that oficialy getting rid of vista (thank god) and then i partition my main drive into three parts, xp edgy, and a free bsd section. i try to install edgy again and the same thing happened. i pop in the xp disk and i dont run on it and now i get a huge list of ubuntu,ubuntu,ubuntu, and a billion ubuntu's and windows xp. ( im using edgy right now) but how do i fix this so it shows my multiple os's like it did before when i had vista and a wubi install of gutsy? like where it just said

windows vista
ubuntu linux

i dont need a million different ubuntu's and an xp and i really dont want to leave my xp disk in my pc all the time.

is there anyway i can posibly get around this issue?

thanks!!!!
-steven

---

### Post by overdrank on 2008-02-09
> **hotroddude said:**
> ok i had a problem i asked about last night with my gutsy instalation, unfortunatly i didnt fix it. so i opened up vista and downloaded the edgy iso ( i wanted to do that seamless running between edgy and xp thing) so i installed edgy and i get a message saying " missing operating system " so i reinstall it a few times and nothing happens, so then i pop in my xp disk and install that oficialy getting rid of vista (thank god) and then i partition my main drive into three parts, xp edgy, and a free bsd section. i try to install edgy again and the same thing happened. i pop in the xp disk and i dont run on it and now i get a huge list of ubuntu,ubuntu,ubuntu, and a billion ubuntu's and windows xp. ( im using edgy right now) but how do i fix this so it shows my multiple os's like it did before when i had vista and a wubi install of gutsy? like where it just said

windows vista
ubuntu linux

i dont need a million different ubuntu's and an xp and i really dont want to leave my xp disk in my pc all the time.

is there anyway i can posibly get around this issue?

thanks!!!!
-steven

HI and you can edit your grub menu list and this is a good link 
[http://users.bigpond.net.au/hermanzone/p15.htm#menu.lst](http://users.bigpond.net.au/hermanzone/p15.htm#menu.lst)
You can use this command to edit the file
```
gksudo gedit /boot/grub/menu.lst
```

---

### Post by hotroddude on 2008-02-09
thanks a ton! will this also let me choose an os withought my xp disk in the tray?

i dont get exactly what im supposed to do, do i comment out all the operating systems that i dont want to be shown?

---

