---
title: "cannot play dvds with totem"
date: 2008-05-22
forum: General Help
---

### Post by freespire on 2008-05-22
Hello!

i just can't get my totem to play dvds.although it has updated the gstreams it gives me an error message .any idea of what should i do?
thank u!!!

---

### Post by kshane on 2008-05-22
> **freespire said:**
> Hello!

i just can't get my totem to play dvds.although it has updated the gstreams it gives me an error message .any idea of what should i do?
thank u!!!

Have you installed "ubuntu-restricted-extras"?

Kevin

---

### Post by freespire on 2008-05-22
no...:)

how can i do it?do you know the command lines?or shall i have to install it from synaptic manager?

---

### Post by werries on 2008-05-22
should be just 

```
sudo apt-get install ubuntu-restricted-extras
```

or just use VLC media player

---

### Post by freespire on 2008-05-22
no..it didn't work.the same error message...

---

### Post by strabes on 2008-05-22
DVD playback is not included in ubuntu-restricted-extras for legal reasons. Please open a terminal (Applications > Accessories > Terminal) and enter the following commands. To easily enter commands, simply select them (with a triple click) and then middle click in the terminal. It will automatically paste the selection.
```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list
sudo aptitude update && sudo aptitude install -y medibuntu-keyring
sudo aptitude update && sudo aptitude install -y w32codecs libdvdcss2
```

Restart totem and you should be good to go. I prefer VLC for playing videos anyway. To install it simply run ```
sudo aptitude install vlc
```

---

