---
title: "Wine"
date: 2006-12-29
forum: General Help
---

### Post by DougieFresh4U on 2006-12-29
I have removed wine as I was having what** "wine desktop"** called **HTML rendering disabled**(trying to run simple games) and after 3 days of posting on forum no responses on getting html (alot of other advice not pertaining html) any way, my question, is there a way for me to try and install wine or wine tools although I am using **Feisty version**?

---

### Post by pianoboy3333 on 2006-12-29
2 options, compile from source at [http://www.winehq.org/](http://www.winehq.org/)

OR
add the repository/ies:
deb [http://repository.debuntu.org/](http://repository.debuntu.org/) edgy multiverse
# deb-src [http://repository.debuntu.org/](http://repository.debuntu.org/) edgy multiverse

---

### Post by hikaricore on 2006-12-30
You do realize that fiesty fawn is a pre alpha testing version not to be used unless you're fully aware that things can and will go wrong right?  You'd be better off using edgy IF for some reason dapper doesn't work with your hardware.

---

### Post by DougieFresh4U on 2006-12-30
> **hikaricore said:**
> You do realize that fiesty fawn is a pre alpha testing version not to be used unless you're fully aware that things can and will go wrong right?  You'd be better off using edgy IF for some reason dapper doesn't work with your hardware.

Yes I am aware as I have** THREE** machines and this particular one I use to play around with Feisty as I did the same with Edgy. I should most likely start my threads stating such info so I don't get the Feisty is yada yada yada yada  and expect breakage yada yada yada yada!!!

---

### Post by pay on 2006-12-30
Add this to your sources list "deb-src [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) edgy main" ```
sudo nano /etc/apt/sources.list
```and then```
sudo aptitude update
sudo aptitude install build-essential
sudo apt-get build-dep wine
sudo apt-get --build source wine
```

---

### Post by hikaricore on 2006-12-30
> **DougieFresh4U said:**
> Yes I am aware as I have** THREE** machines and this particular one I use to play around with Feisty as I did the same with Edgy. I should most likely start my threads stating such info so I don't get the Feisty is yada yada yada yada  and expect breakage yada yada yada yada!!!

Sorry about that, I've just seen you posting quite a bit on various sections of the forums and wanted to make sure you knew.  :)   I won't bug ya about it again hehe.

---

### Post by DougieFresh4U on 2006-12-30
Thanks for reply 'pay' this is what terminal is spitting out :::                   dougie@DougiesToyBox:~$ sudo apt-get build-dep wine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Could not open file /var/lib/apt/lists/wine.budgetdedicated.com_apt_dists_edgy_main_source_Sources - open (2 No such file or directory)

---

### Post by DougieFresh4U on 2006-12-30
> **hikaricore said:**
> Sorry about that, I've just seen you posting quite a bit on various sections of the forums and wanted to make sure you knew.  :)   I won't bug ya about it again hehe.

No problem, just that so many members respond starting out with a lecture about distribution being new and all that crap that goes with it and don't really know what others motives are for using said distros. Thanks for reply any way :)

---

### Post by pay on 2006-12-30
> **DougieFresh4U said:**
> Thanks for reply 'pay' this is what terminal is spitting out :::                   dougie@DougiesToyBox:~$ sudo apt-get build-dep wine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Could not open file /var/lib/apt/lists/wine.budgetdedicated.com_apt_dists_edgy_main_source_Sources - open (2 No such file or directory)Did you update first?```
sudo apt-get update
```

---

### Post by DougieFresh4U on 2006-12-30
Yes I did. Any Idea what is wrong?

---

