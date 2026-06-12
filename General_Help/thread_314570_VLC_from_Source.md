---
title: "VLC from Source"
date: 2006-12-07
forum: General Help
---

### Post by russoc4 on 2006-12-07
My friend is installing ubuntu on an old desktop that doesn't have any internet connection.

Where can he find the VLC source and how can he compile it? I don't remember how to compile things, as I don't do it often.

---

### Post by brottman on 2006-12-07
I think it would be a much better idea to download the .deb files for vlc from your computer and then give them to him on CD.

```
sudo apt-get install vlc -d
```

The packages will be downloaded to /var/cache/apt/archives

---

### Post by taurus on 2006-12-07
If you want to build it from source, you first need to install build-essential package.  It so happens that it is on the CD so insert the CD into the drive and at the prompt, do

Applications -> Accessories -> Terminal
```
sudo apt-cdrom add
sudo aptitude update
sudo aptitude install build-essential
```

[http://www.videolan.org/vlc/download-sources.html](http://www.videolan.org/vlc/download-sources.html)

---

### Post by russoc4 on 2006-12-08
i'll probably use mine to download the .deb and get it to him. thanks for your help. i didnt even think of that.

---

