---
title: "There is no public key available for the following key IDs"
date: 2016-05-02
forum: General Help
---

### Post by marcello7 on 2016-05-02
Hi guys,

not sure if the question has been answered before but I wasn't able to find anything on the forum - I am new to Ubuntu and the forum :P.
When I run the command: ```
sudo apt-get update
```

I got this warning: ```
There is no public key available for the following key IDs: 1397BC53640DB551
```

Can anyone explain what is causing the problem and how can I fix it?

Thanks!

---

### Post by QDR06VV9 on 2016-05-02
Try add the key by way of.
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys KEY_ID 1397BC53640DB551
```
And check that it is ok by 
```
sudo apt update
```

---

### Post by marcello7 on 2016-05-02
> **runrickus said:**
> Try add the key by way of.
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys KEY_ID 1397BC53640DB551
```
And check that it is ok by 
```
sudo apt update
```


Thanks runrickus - the command resolved the issue.
 What was causing it?

---

### Post by QDR06VV9 on 2016-05-02
The key for what ever reason was not in the key ring(Trusted)...and now it is..:D
Glad it worked out for you.
Kind Regards

---

### Post by marcello7 on 2016-05-02
Thanks Again!

---

### Post by QDR06VV9 on 2016-05-02
You are Very Welcome.
And thank you for marking as solved.
Regards

---

### Post by CaptainMark on 2016-05-03
I have exactly the same key coming up as a problem. I had heard recently on a podcast that Canonical have been updating the launchpad ppa's to use a higher bit key signing process, I would assume this is linked but that is a bit of a guess

---

### Post by marcello7 on 2016-05-03
Apparently a new Google key has been released and nobody didn't know anything about it. 

forums.linuxmint.com/viewtopic.php?t=221151#p1161682

---

### Post by u1106 on 2016-05-19
I got the same error when trying to install pepperflashplugin-nonfree (for chromium-browser). However, the apt-key command given above is not enough for pepperflashplugin-nonfree, because pepperflashplugin-nonfree stores the public key in a place specific to the package. The instructions given in [http://unix.stackexchange.com/questions/279825/pepperflashplugin-nonfree-error-failed-to-retrieve-status-information-from-go/280091#280091](http://unix.stackexchange.com/questions/279825/pepperflashplugin-nonfree-error-failed-to-retrieve-status-information-from-go/280091#280091) are complete.

---

### Post by Betialai on 2017-03-23
Was this the first time you ran apt update after installing Google Earth?

---

