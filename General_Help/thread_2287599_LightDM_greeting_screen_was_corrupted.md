---
title: "LightDM greeting screen was corrupted"
date: 2015-07-20
forum: General Help
---

### Post by artemis86 on 2015-07-20
Hello. I tried to change greeting screen with Ubuntu-Tweak, but I got an error. When I trying to change user from my account, I got only lock screen without list of all user's. When I select from lock screen 'Change user', I got corrupted greeting screen (without transparent panel and background image). [http://funkyimg.com/i/ZjV4.jpg](http://funkyimg.com/i/ZjV4.jpg) -> this is my screen after select 'Lock/Change user', [http://funkyimg.com/i/ZjV5.jpg](http://funkyimg.com/i/ZjV5.jpg) -> this is my screen after select 'Change user' (again, from lock screen on previous image), [http://funkyimg.com/i/Zk6Y.jpg](http://funkyimg.com/i/Zk6Y.jpg) -> this is my screen after rebooting and first login to my account. When I login to my account, I got an error with 'lightdm 1.10.5-0ubuntu1.1'. Please, help!( How to fix it?

P.S. Ubuntu 14.04.2 x64 Unity

---

### Post by Vladlenin5000 on 2015-07-20
Hi and welcome.

I'm not sure it works but you can try to reinstall/reconfigure LightDM

```
sudo dpkg --reconfigure lightdm
```

---

### Post by artemis86 on 2015-07-20
Thanx :)
I tried reconfigure lightdm - it is really doesn't work

---

