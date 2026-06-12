---
title: "Mouse cursor gone when I play video in VLC"
date: 2013-10-18
forum: General Help
---

### Post by dankojoffrey on 2013-10-18
Hi, today I installed Ubuntu 13.10 (I had 13.04 before, bu I made clean install) and as soon as I play video in VLC my mouse cursor disappears... then I can get it back only when I turn off and then turn on my touchpad with function key on keyboard. After a second or two it disappears again... Then when I turn off VLC it's working fine again...
When I use other video player (like Totem) it doesn't happen... Only with VLC...

It's asus vivobook, with nvidia optimus card on bumblebee (nvidia-304) and it has got a touch screen(which is finally working in 13.10:P)
I did not have this problem with any other ubuntu or any other distro...

Any ideas...???

Thanks...

---

### Post by dankojoffrey on 2013-10-19
It was resolved with vlc 2.1.1 update... It's not in Ubuntu 13.10 sources... need to install from downloaded sources or custom PPA...

---

### Post by 4lex2 on 2013-10-29
Any chance the newer version will be pushed to Saucy universe, or are we locked into the current version until the next Ubuntu release?

---

### Post by dankojoffrey on 2013-10-29
why don't you add PPA to your system:
```
sudo add-apt-repository ppa:videolan/stable-daily
sudo apt-get update
sudo apt-get install vlc
```

you'll have the vlc 2.1.1

---

### Post by 4lex2 on 2013-10-29
> **dankojoffrey said:**
> why don't you add PPA to your system:
```
sudo add-apt-repository ppa:videolan/stable-daily
sudo apt-get update
sudo apt-get install vlc
```

you'll have the vlc 2.1.1

Didn't realize Videolan had an official PPA. I'll use that, thank you.

---

### Post by 4lex2 on 2013-10-31
Just wanted to add that videolan/stable-daily doesn't actually have 2.1.1 as of yet on Saucy. The highest version available is 2.0.8.

**ppa:videolan/master-daily **has up to version 2.2.0 , so you'll likely need to use that PPA until stable gets refreshed.

---

### Post by dankojoffrey on 2013-10-31
> **4lex2 said:**
> Just wanted to add that videolan/stable-daily doesn't actually have 2.1.1 as of yet on Saucy. The highest version available is 2.0.8.

**ppa:videolan/master-daily **has up to version 2.2.0 , so you'll likely need to use that PPA until stable gets refreshed.

I used this PPA and it installed version 2.1.1 on Saucy... it was like a week ago... but maybe they removed the package in meantime...

---

