---
title: "Ubuntu won't let me login"
date: 2008-02-14
forum: General Help
---

### Post by mooseman089 on 2008-02-14
Hello I just noticed that ubuntu requested I restart my system so I did but after rebooting I get to the login screen and type in my login and I see the nvidia logo and hear the login sound but then it returns me to the login screen with no error and I tried other accounts on the system with the same results.

---

### Post by taurus on 2008-02-14
Get to another console with <Ctrl><Alt>F2 and see if you can log in with your username and password.  Then, perhaps check to make sure you disk is not full.

```
df -h
```

---

### Post by mooseman089 on 2008-02-14
Wow you are right somehow my 640Gb raid 5 array is full according to df -h my /dev/md0 has Avail: 0 and use: 100%.  I have no idea how it got this full is there any apps that can help me find large directories and files?

---

### Post by taurus on 2008-02-14
Look in /var to make sure nothing is filling up the space in there.  

```
sudo du -h /var
```

You can also clean out the cache to buy you some space so you can log in from GUI login screen again with

```
sudo apt-get clean
df -h
```

---

### Post by mooseman089 on 2008-02-14
I was able to delete an old backup folder that was 80gigs which freed up space to login but /var is only using 420megs.

Edit: I just noticed that in firefox my entire history is completely gone I'm not sure if there is anything else missing yet.

---

