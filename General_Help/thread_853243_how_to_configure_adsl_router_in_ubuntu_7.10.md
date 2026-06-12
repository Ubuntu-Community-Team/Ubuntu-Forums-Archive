---
title: "how to configure adsl router in ubuntu 7.10"
date: 2008-07-08
forum: General Help
---

### Post by emigrant on 2008-07-08
hai there,
can anybody tell me how to configure my adsl router (speedcom) in ubuntu 7.10. i run dual boot- vista and ubuntu 7.10. in vista i have configured my connection successfully. but the same way failed to work with ubuntu. i dont know whether ubuntu detects my network card. my motherboard is asus-p5gcmx/1333.

hope i can resolve my problem here.
thanks in advance.

---

### Post by uidb4056 on 2008-07-08
If your adsl router is working properly in windows you will not need to configure anything in Ubuntu. Can you access internet from Ubuntu?

---

### Post by dentaku65 on 2008-07-08
I supposed that you must intall pppoeconf
```
sudo apt-get install pppoeconf
```
Then execute in terminal
```
sudo pppoeconf
```
Choose interface, usr/pass of your internet connection and save as automatic (better)

---

### Post by FakeOutdoorsman on 2008-07-08
[https://help.ubuntu.com/community/ADSLPPPoE](https://help.ubuntu.com/community/ADSLPPPoE)

---

### Post by emigrant on 2008-07-13
hai guys, 
my internet connection works very well on windows vista. but it doesnt always work on ubuntu. it works at time. please guys help me.

---

### Post by emigrant on 2008-07-14
still nobody saw my post,,,,,....:(

---

### Post by Sef on 2008-07-14
> still nobody saw my post,,,,,....  

Please do not bump your post until 24 hours have gone by.  Otherwise an infraction can be given to you.

Since everyone is volunteers here, it can take time to get your post answered.

---

