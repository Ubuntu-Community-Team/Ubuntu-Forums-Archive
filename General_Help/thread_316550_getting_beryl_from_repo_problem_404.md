---
title: "getting beryl from repo problem 404"
date: 2006-12-10
forum: General Help
---

### Post by g3k0 on 2006-12-10
Hey i was following the guide in the sticky for beryl kinda but when I try 
sudo apt-get install beryl I get

Get:1 [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) edgy/main beryl-core 0.1.3~0beryl2 [320kB]
Err [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) edgy/main beryl-plugins-data 0.1.3~0beryl1
  404 Not Found
Get:2 [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) edgy/main beryl-settings 0.1.3~0beryl1 [110kB]
Err [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) edgy/main emerald 0.1.3~0beryl1
  404 Not Found
Get:3 [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) edgy/main beryl 0.1.3~0beryl2 [10.3kB]
Fetched 440kB in 2s (198kB/s)
Failed to fetch [http://ubuntu.beryl-project.org/pool/edgy/main/beryl-plugins/beryl-plugins-data_0.1.3~0beryl1_all.deb](http://ubuntu.beryl-project.org/pool/edgy/main/beryl-plugins/beryl-plugins-data_0.1.3~0beryl1_all.deb)  404 Not Found
Failed to fetch [http://ubuntu.beryl-project.org/pool/edgy/main/emerald/emerald_0.1.3~0beryl1_i386.deb](http://ubuntu.beryl-project.org/pool/edgy/main/emerald/emerald_0.1.3~0beryl1_i386.deb)  404 Not Found
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

---

### Post by renzokuken on 2006-12-11
weird, i did it from that repo last night and it worked fine

but isnt the proper install command

```
sudo apt-get install beryl-core beryl-plugins beryl-plugins-data emerald beryl-settings beryl-manager beryl beryl-dev emerald-themes
```

---

### Post by hikaricore on 2006-12-11
With the new beryl release it's possible that you were trying to access the ubuntu beryl packages while they were being updated.  You may want to try again today, tho I hear beryl-settings is corrupt or compiled wrong and segfaulting.  I'm sticking with the SVN builds for now:

[http://www.ubuntuforums.org/showthread.php?t=279456&highlight=beryl+svn](http://www.ubuntuforums.org/showthread.php?t=279456&highlight=beryl+svn)

---

### Post by daou on 2006-12-11
> weird, i did it from that repo last night and it worked fine

but isnt the proper install command

It's enough to install:
sudo apt-get install beryl emerald emerald-themes

the other packages are installed automatically ([http://wiki.beryl-project.org/wiki/Install/Ubuntu/Edgy/nVIDIA](http://wiki.beryl-project.org/wiki/Install/Ubuntu/Edgy/nVIDIA)[]("http://wiki.beryl-project.org/wiki/Install/Ubuntu/Edgy/nVIDIA")).

---

