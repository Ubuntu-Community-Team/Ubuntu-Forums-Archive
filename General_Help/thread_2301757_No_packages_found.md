---
title: "No packages found"
date: 2015-11-05
forum: General Help
---

### Post by caleb165 on 2015-11-05
I was having difficulty opening any video files, so I tried to install vlc to see if that would fix it. When I tried installing it, it gave an error with package not found. This happens when I try to install from terminal or software center. I checked my sources.list and tried resetting it completely to default. Now everytime I try to install any package I get the error package not found. I'm not sure if my sources.list is messed up, or what. And yes I've already tried apt-get update.

---

### Post by howefield on 2015-11-05
Can you post your sources.list here (between code tags) ?

From terminal..

```
cat /etc/apt/sources.list
```

And copy paste back here.

---

### Post by furtom on 2015-11-05
you can try:

```
sudo cp -R /var/lib/apt/lists/* ~/lists/
sudo rm -R /var/lib/apt/lists/*
sudo apt-get update
```

This will refill /lists

---

