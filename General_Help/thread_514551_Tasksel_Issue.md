---
title: "Tasksel Issue"
date: 2007-07-31
forum: General Help
---

### Post by chadwick359 on 2007-07-31
And at the end of the day, I still don't have LAMP.

I just bought a new VPS plan with VPSLink, but whenever I try to install LAMP with tasksel, it just hangs and spits this at me. 

```
tasksel: aptitude failed (100)
```

I've found no mention of this on the forums, and google gives me nothing. Has anybody else run into this, or is it an issue with my VPS image? As usual, any help would be appreciated.

---

### Post by nitro_n2o on 2007-07-31
i tried to do this lately (to save my self some time) but it didn't work i couldn't even wait to see the image it  just hangs, so i installed everything on it's own by apt-get and works fine :) 
```
sudo apt-get install mysql-server apache2 php5 libapache2-mod-php5 openssh-server openssl
```
one command nice and easy

---

### Post by chadwick359 on 2007-07-31
Thanks a lot, I got it figured out. Turns out  that apache was a bit misconfigured and was eating so much RAM that I couldn't launch MySQL correctly, but i got it now, thanks for the quick reply!

---

### Post by Maltalossewen on 2007-08-05
I just ran into this and I was certain that it had worked last evening (I'm reinstalling now in a VMWare session).
And then it occured to me it was after I had performed a package update.
After performing following steps, I now have my LAMP-server up and running:

sudo apt-get update
tasksel install lamp-server

---

