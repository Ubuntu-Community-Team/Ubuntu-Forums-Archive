---
title: "names for codec packages"
date: 2008-02-06
forum: General Help
---

### Post by steve196 on 2008-02-06
I do not know if this is the right forum for that (is there an alpha forum?).
I am using hardy alpha and the automatic codec package downloader crashes, so i want to get the codec packages with Synaptic. Can you tell me the names of the packages?
Thanks!

---

### Post by aquavitae on 2008-02-06
There is a hardy forum, I think its under development.

As for your query... I can only say what they were in gutsy, I doubt the'd have changed.  I assume you're using gnome? Do a search in synaptic for gstreamer and you should get gstreamer-good, bad and ugly (possible libgstreamer, can't remember) I think those are the packages you need to install.  Make sure you have the universe repo available first.

---

### Post by steve196 on 2008-02-06
Thank you.
I have already installed the good/bad/ugly gstreamer stuff but it gave me no video, only sound on mpeg, xvid and nothing on wmv videos. I am using the default player (totem). I guess i am just experiencing some of the alphaness of the alpha. Since this is not my main system, i think, i will just wait a bit.

---

### Post by aquavitae on 2008-02-06
I had the same problems in gutsy (and feisty).  I got around it by using totem-libxine instead of totem.  You can select it in synaptic, it will require removing totem, but the xine engine works much better for me. You'll probably need to install the xine codecs though and I can't remember what they are... libmad is one I think.  It might say if you right click on it and see what's recommended.

---

### Post by zvacet on 2008-02-06
If you have all repos open 

```
sudo apt-get install ubuntu-restricted-extras
```

for KDE

```
sudo apt-get install kubuntu-restricted-extras
```

for Xubuntu

```
sudo apt-get install xubuntu-restricted-extras
```

---

