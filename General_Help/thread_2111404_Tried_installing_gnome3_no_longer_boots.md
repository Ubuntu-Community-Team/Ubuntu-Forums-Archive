---
title: "Tried installing gnome3 no longer boots"
date: 2013-02-01
forum: General Help
---

### Post by sayhey69 on 2013-02-01
Hi I just got a computer with Ubuntu 12.04 today and decided to install gnome shell. I ended up adding the ricotz/testing ppa as well as the gnome3-team/gnome3. not sure where i went wrong but now i cant get past the ubuntu splash screen on reboot. using ctrl+alt+f1 i have poked around and found unity/ubuntu-desktop are no long installed and i cant reinstall them. ive removed both of the previously mentioned ppas and tried to purge/clean as much of them as possible.

when i try to install unity or lightdm i get this error:

unmet dependencies...
Depends: libglib2.0-bin

when i try to install libglib2.0-bin i get this error:
Depends: libglib2.0-0 (= 2.32.3-0ubuntu1) but 2.34.1-0ubuntu1~12.04~ricotz0 is to be installed



ive tried everything i can think of to fix broken packages and nothing seems to work. since its a new computer i have 0 stuff on it that i need to keep. i also looked up ways to completely reset ubuntu but none of those did anything. any help would be appreciated

---

### Post by zealibib slaughter on 2013-02-01
have you tried 
```
sudo apt-get install ubuntu-desktop
```

---

### Post by sayhey69 on 2013-02-01
yes. it lists packages ubuntu-desktop needs including lightdm and unity and says it cant install those 2 and stops

---

### Post by zealibib slaughter on 2013-02-01
32 or 64 bit?

---

### Post by steeldriver on 2013-02-01
how exactly did you remove the ppas? it seems like it is still trying to install ricotz0

---

### Post by sayhey69 on 2013-02-01
64

---

### Post by zealibib slaughter on 2013-02-01
ok then do this
```
wget http://security.ubuntu.com/ubuntu/pool/main/g/glib2.0/libglib2.0-bin_2.32.1-0ubuntu2_amd64.deb 
```then 
```
sudo dpkg -i libglib2.0-bin_2.32.1-0ubuntu2_amd64.deb
```then
```
sudo apt-get update && sudo apt-get install ubuntu-desktop
```


if errors happen on installing the deb package then do
sudo apt-get -f install

---

### Post by sayhey69 on 2013-02-01
> **steeldriver said:**
> how exactly did you remove the ppas? it seems like it is still trying to install ricotz0

ya it does seem like that.


sudo ppa-purge ppa:ricotz/testing
sudo add-apt-repository --remove ppa:ricotz/testing

i did both of these commands for each ppa and got messages when doing sudo add-apt-repository --remove that the ppa didnt exist. which seems to make sense since afaik ppa-purge should remove the ppa

---

### Post by sayhey69 on 2013-02-01
> **zealibib slaughter said:**
> ok then do this
```
wget http://security.ubuntu.com/ubuntu/pool/main/g/glib2.0/libglib2.0-bin_2.32.1-0ubuntu2_amd64.deb 
```then 
```
sudo dpkg -i libglib2.0-bin_2.32.1-0ubuntu2_amd64.deb
```then
```
sudo apt-get update && sudo apt-get install ubuntu-desktop
```


if errors happen on installing the deb package then do
sudo apt-get -f install

i get errors when trying to install the deb package.

libglib2.0-bin depnds on libglib2.0-bin (=2.32.1-0ubuntu2); however:
version of libglib2.0-0 on system is 2.34.1-0ubuntu~12.04~ricotz0

doing sudo apt-get -f install says it will remove libglib2.0-bin.

---

### Post by zealibib slaughter on 2013-02-01
ok give the output of cat /etc/apt/sources.list 

or sudo nano /etc/apt/sources.list and look for any repository that shouldn't still be there
btw have you done a sudo apt-get update

---

### Post by sayhey69 on 2013-02-01
i have done sudo apt-get update.

the repositories are only the defaults.

---

### Post by zealibib slaughter on 2013-02-01
ok now thats weird 
try this
```
wget http://mirror.pnl.gov/ubuntu//pool/main/g/glib2.0/libglib2.0-0_2.34.0-1ubuntu1_amd64.deb
```

then install with dpkg -i and try to install unity. maybe just maybe

---

### Post by sayhey69 on 2013-02-01
dpkg: warning: downgrading libglib2.0-0_2.34.0-1ubuntu1_amd64.deb from 2.34.1-0ubuntu1~12.04~ricotz0 to 2.34.0-1ubuntu1.
dpkg:regarding libglib2.0-0_2.34.0-1ubuntu1_amd64.deb containing libglib2.0-0:
libglib2.0-0 breaks glib-networking (<< 2.33.12)
glib-networking (version 2.32.1-1ubuntu2) is present and installed.
dpkg: error processing libglib2.0-0_2.34.0-1ubuntu1_amd64.deb (--install):
installing libglib2.0-0 would break glib-networking, and
deconfiguration is not permitted (--auto-deconfigure might help)
Errors were encountered while processing:
libglib2.0-0_2.34.0-1ubuntu1_amd64.deb

---

### Post by zealibib slaughter on 2013-02-01
ok now sudo apt-get -f install

or maybe add --auto-deconfigure to the dpkg command

the problem seems to be that  2.34.1-0ubuntu1~12.04~ricotz0 to 2.34.0-1ubuntu1is installed and is conflicting with the other packages

---

### Post by sayhey69 on 2013-02-01
i got libglib2.0-0 to install now by removing glib-networking. there were a few more dependency issues but i ended up downgrading a few more packages and now it is supposedly installing ubuntu-desktop. fingers crossed it works

---

### Post by sayhey69 on 2013-02-01
i got it to up and running again. thanks for the help. in the end "just" took removing or downgrading any package that gave an error at any point.

---

