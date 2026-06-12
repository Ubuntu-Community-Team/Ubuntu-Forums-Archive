---
title: "How do I restore the original usplash theme"
date: 2007-01-24
forum: General Help
---

### Post by Athanasius on 2007-01-24
Can some body help me to restore the original usplash theme?  I installed the edubuntu theme and it is giving me the usplash theme for edubuntu and I do not want it.

---

### Post by energiya on 2007-01-24
You could try
```

sudo aptitude install usplash-theme-ubuntu

```
Hope it works.

---

### Post by youthforlinux on 2007-01-24
try this [http://www.ubuntuforums.org/showthread.php?t=343452]("http://www.ubuntuforums.org/showthread.php?t=343452")

---

### Post by heathenx on 2007-01-24
three ways...

sudo update-alternatives --config usplash-artwork.so

or

sudo dpkg-reconfigure usplash

or

sudo apt-get install gnome-splashscreen-manager

(splash screens found in /usr/lib/usplash dir)

---

### Post by kesomir on 2007-03-01
sudo aptitude reinstall usplash-theme-ubuntu

---

