---
title: "Firefox + wireless  help"
date: 2008-02-13
forum: General Help
---

### Post by Newbi on 2008-02-13
I installed gutsy yesterday night.. today while configuring it.. i've got follwing problems.


i installed at plugins of fire fox at the administrator account. Those plugins are not being enabled by default in other user accounts. (except stumble upon) . How do i get these activated????

The wireless network i was catching. is not being caught suddenly.. do u think there is a problem with ubuntu ???

thanks

---

### Post by comandrei on 2008-02-13
Firefox stores it's data in ~/.mozilla. That means each user can have a different profile and different extentions. They must manually install the extentions they need, or you can just copy your profile to their folder.
It's should be something like this:
```

 cp -R ~./mozilla /home/user/.mozilla
chown -R user /home/user/.mozilla

```
With the wireless problem, I suggest you upgrade your kernel with the hardy one.

---

### Post by Newbi on 2008-02-13
thanks bro..

but how do i update the kernel???

---

### Post by Newbi on 2008-02-13
also there's no such directory in my home 

how do i work around the problem??

---

