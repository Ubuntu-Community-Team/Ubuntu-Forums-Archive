---
title: "recommended file permissions"
date: 2007-11-12
forum: General Help
---

### Post by sfh1975 on 2007-11-12
dear friends,
i am on a triple boot machine (ubuntu, debian, xp) but playing with debian messed up my file permissions in ubuntu. is there any way i can return to the default permissions? i know that might not be possible but at least some recommendations for important directories and files might help. for example, what do i need to change to be able again to use pppd for using my dial up internet? and so on.
thanks in adv,

---

### Post by 1337455 10534 on 2007-11-12
How did Debain get access to your Ubuntu partition??*

Click on the internet conenction icon in the notification area and try the manual configuration/

---

### Post by sfh1975 on 2007-11-13
> **1337455 10534 said:**
> How did Debain get access to your Ubuntu partition??*

Click on the internet conenction icon in the notification area and try the manual configuration/

Well that is not difficult I guess. All you need to do is to mount the partitition/ drive that you need access to.
Re the second issue, this was just an example. There are many other applications which are crashing or dont run at all due to messed up file permissions.
thanks anyway,
Any other solutions?

---

### Post by bingoUV on 2007-11-13
Do you feel the file owners have been messed with, or just the permissions? I cannot give a way to restore default permissions, but  if you are not too much concerned with security, 755 is a good bet as permissions for all files, and still reasonably safe.
```

sudo chmod -R 755 /

```

After this, I hope most of your stuff should work

---

### Post by sfh1975 on 2007-11-13
> **bingoUV said:**
> Do you feel the file owners have been messed with, or just the permissions? I cannot give a way to restore default permissions, but  if you are not too much concerned with security, 755 is a good bet as permissions for all files, and still reasonably safe.
```

sudo chmod -R 755 /

```

After this, I hope most of your stuff should work

bingoUV, Thanks.
I guess both are messed up, though the ownership up to a lesser extent.
I will try this option but I guess it messes up the .dmrc and some other home directory files, making you unable to log in.
Thanks anyway,

---

