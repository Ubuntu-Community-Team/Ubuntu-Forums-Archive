---
title: "I need a mail notification 5.0 deb file"
date: 2008-03-05
forum: General Help
---

### Post by unclesam.xu on 2008-03-05
Can anyone make a mail notification 5.0 deb for ubuntu feisty , I can only find 4.0 but 5.0 added hotmail support which I really need. thanks.

---

### Post by kellemes on 2008-03-05
Download [the newest version]("http://savannah.nongnu.org/download/mailnotify/mail-notification-5.0.tar.bz2") to your desktop.
Open the terminal and start typing..
```

cd ~/Desktop
tar xvjf mail-notification-5.0.tar.bz2
cd mail-notification-5.0
./configure
make
sudo make install
```
It should be installed.. but I can't promise it will work with Feisty.

---

### Post by webit on 2008-03-05
Not so fast. I tried install 5.0 version several times. Always with the same effect - ./configure exits with:

```
checking for GNOME... no
configure: error: unable to find the GNOME libraries

```
:confused: I'm using Gnome even in this moment :???:

---

### Post by unclesam.xu on 2008-03-06
just like what webit said. my feisty display the same thing.

---

### Post by webit on 2008-03-06
Found soulution in other [thread]("http://ubuntuforums.org/showpost.php?p=4354384&postcount=13"). 
Now i'm able to use 5.0 version :)

---

### Post by unclesam.xu on 2008-03-06
thanks , webit, 

I installed it . but after I ran it. after I set my hotmail, it said can't excute "GetLive, "

---

### Post by webit on 2008-03-08
> **unclesam.xu said:**
> 
I installed it . but after I ran it. after I set my hotmail, it said can't excute "GetLive, "

I use only Gmail and it works with 3 accounts (1 orginal gmail and 2 google hosted accounts). I think i can't help with hotmail :(

---

