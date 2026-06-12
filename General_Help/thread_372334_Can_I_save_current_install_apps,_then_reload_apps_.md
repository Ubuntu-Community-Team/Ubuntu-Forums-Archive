---
title: "Can I save current install apps, then reload apps on another system?"
date: 2007-02-28
forum: General Help
---

### Post by grahams on 2007-02-28
I know apt-get understands what is currently installed on my system. Can this data be used to load the same set of apps on another system and/or fresh install? 

I've tried synaptic and it looks like I can create scripts to copy pending installs, but not what I already have installed. I can't see a reference to this in man pages for apt-get or apt-config, anyone know if it is possible?

---

### Post by 23meg on 2007-02-28
Check out APTonCD.

[http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)

---

### Post by grahams on 2007-02-28
Thanks for the reply, APTonCD looks very cool and looks like it can do what I'm looking for if I hadn't be so good about cleaning up after myself. APTonCD will only load what if finds in /var/cache/apt/archives/ and after an apt-get clean that is wiped out. Do you know of a way to force a re-download of all my installed apps without re-installing them?

---

### Post by etank on 2007-02-28
Try ```
sudo aptitude --download-only **somepackage**
```

---

### Post by bodhi.zazen on 2007-02-28
> **grahams said:**
> I know apt-get understands what is currently installed on my system. Can this data be used to load the same set of apps on another system and/or fresh install? 

I've tried synaptic and it looks like I can create scripts to copy pending installs, but not what I already have installed. I can't see a reference to this in man pages for apt-get or apt-config, anyone know if it is possible?

It is easier then that ;)

Argh ... The link is broken, sorry :(

Try this one : [http://yordan.wordpress.com/2006/09/20/ubuntu-package-list/](http://yordan.wordpress.com/2006/09/20/ubuntu-package-list/)

---

### Post by grahams on 2007-02-28
Cool, thanks for the link

dpkg --get-selections | grep -v deinstall > ubuntu-files (this is exactly what I was looking for).

I'll give it a try.

---

### Post by grahams on 2007-02-28
Quick note on APTonCD.

By using synaptic and marking all my installed packages (takes a long time), and then creating a download script I was able to downland all the .debs into /var/cache/apt/archive. After that I created an ISO image via APTonCD and install the packages on my new system.

---

### Post by grahams on 2007-02-28
Quick note on APTonCD.

By using synaptic and marking all my installed packages (takes a long time), and then creating a download script I was able to downland all the .debs into /var/cache/apt/archive. After that I created an ISO image via APTonCD and used it to install the packages on my new system.

---

