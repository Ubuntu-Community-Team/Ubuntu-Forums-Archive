---
title: "How do I edit the source?"
date: 2007-05-27
forum: General Help
---

### Post by oldcpu on 2007-05-27
I have installed something using aptitude.  But I did not like something in the application.  I would like to edit it.

It is not optional.  So the only way is to edit the source.  I have searched, and there is no source.

I take it that the *deb package in /var/cache/apt/archives/ is it?

Now, how do I go about editing the package or source?

I know what to do, but I do not know how to do it.  Please help.

---

### Post by Ventrue on 2007-05-27
You must download a source code of this program from program author website ;)

---

### Post by Bachstelze on 2007-05-27
Or download the source package with apt-source.

---

### Post by christhemonkey on 2007-05-27
If the program is from the repositories then you can get the source easily by doing:
```
sudo apt-get source *yourprogram*
```

(but for every deb entry in your /etc/apt/sources.list you must have a deb-src)

---

### Post by oldcpu on 2007-05-27
Thanks for replying everyone.

I have edited the source.  But during the configuration, it tells me
```
configure: error: Bad GTK+ version
```
I do not know how I can get a bad GTK+ version.  I installed it fine with aptitude.  Anyone know how I can fix this?

---

