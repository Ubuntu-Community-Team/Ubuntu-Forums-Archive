---
title: "why doesn't &quot;make&quot; work for me?"
date: 2006-10-24
forum: General Help
---

### Post by leveliv on 2006-10-24
hi I am in my terminal trying to install lighttpd-1.4.13 and It calls for me to configure it so I do with ./configure and it does its thing...next I'm told to use "make" so I do and this is what I get: ```
goodwhite@ChrisRoom:~/Desktop/lighttpd-1.4.13$ make
bash: make: command not found
goodwhite@ChrisRoom:~/Desktop/lighttpd-1.4.13$

```
any ideas as to why it won't work for me?

---

### Post by picpak on 2006-10-24
Try running

```
sudo apt-get install build-essential
```.

---

### Post by leveliv on 2006-10-24
I beleive that worked, thank you very much

---

### Post by begone77 on 2006-10-26
I get this

E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
begone77@begone77-desktop:~/stuff2/wine-0.9.23$ sudo apt-get install build-essential
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

---

### Post by moffa on 2006-10-26
> **begone77 said:**
> I get this

E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
begone77@begone77-desktop:~/stuff2/wine-0.9.23$ sudo apt-get install build-essential
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

You have adept / synaptic or some other package manager open. You have to close them all.

---

