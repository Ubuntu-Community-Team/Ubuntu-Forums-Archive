---
title: "Repair Ubuntu Installation"
date: 2006-07-05
forum: General Help
---

### Post by krazykirk on 2006-07-05
Is there any way to do a "repair" installation on ubuntu? I somehow deleted most of my packages by accident [http://ubuntuforums.org/showthread.php?t=209372](http://ubuntuforums.org/showthread.php?t=209372)

I don't want to do a reinstall, becuase i would like to keep my configuration (if thats even possible if my packages got removed)

Thanks!

---

### Post by raldz on 2006-07-05
Try this in your terminal:

```
sudo apt-get install --fix-broken
```

edited:thanks Ramses, for noticing

---

### Post by Ramses de Norre on 2006-07-05
I think you mean ```
sudo apt-get install --fix-broken
```

---

### Post by krazykirk on 2006-07-05
hmm... it didn't work... is there anything else i can do?

maybe a way to back up my settings (theme etc) then i reinstall?

---

### Post by Ramses de Norre on 2006-07-05
Most settings are in your home folder (in hidden folders) and system wide configuration files are in /etc/ (you'll only need to backup files from /etc/ which you edited yourself).
If you backup these you should be able to reset most of you're current settings in your new install.

---

### Post by krazykirk on 2006-07-05
So if i use a program in windows to access my linux partition then copy all the files in my home directory and in the /etc folder and just copy them over in the new installation would it work?

---

### Post by raldz on 2006-07-05
opps.. it was a fast reply, sorry I forgot..

---

### Post by pixelized on 2007-06-24
> **Ramses de Norre said:**
> I think you mean ```
sudo apt-get install --fix-broken
```

it work for me, but it says run apt-get update to correct problems..

---

### Post by al4ie on 2008-01-14
I'm having the same problem, when I run the above in terminal, I get this:

E: Archive directory /var/cache/apt/archives/partial is missing.


Any ideas?

---

### Post by martinolsson84 on 2008-01-20
> **raldz said:**
> Try this in your terminal:

```
sudo apt-get install --fix-broken
```

edited:thanks Ramses, for noticing

I tried this and got: 

“Segmentation fault (core dumped)”
as a result!?

My problem is: 
Add/remove applications - craches upon start.
Update manager - chraches upon start.
Synaptic - craches upon start.

Also Firefox hangs up and Ubuntu does not shut down properly some times.

---

### Post by capink on 2008-01-20
> **al4ie said:**
> I'm having the same problem, when I run the above in terminal, I get this:

E: Archive directory /var/cache/apt/archives/partial is missing.


Any ideas?

Try recreating the directory:

```
sudo mkdir -p /var/cache/apt/archives/partial
```

---

### Post by sports fan Matt on 2008-01-20
I had the same thing happen to me...that fix worked!

---

