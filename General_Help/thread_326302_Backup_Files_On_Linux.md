---
title: "Backup Files On Linux"
date: 2006-12-27
forum: General Help
---

### Post by moricgaut on 2006-12-27
Soon I will be getting a new computer. So that means I will need to reinstall ubuntu on that computer. I got the new ubuntu cd so that I can install that on my new computer. Now I have alot of software that I downloaded from synaptic package manager. Now when I get this new computer I don't want to download them again because i only have 256kb internet connection so it still takes awhile. So would there be a way so that I coukd backup all the software that I downloaded and installed from synaptic package manager. Thanks!

---

### Post by sgbeamer on 2006-12-27
Several ways to go:

1) tar your directories that contain softwareware or files /home /etc /usr /bin /sbin /lib, burn to a cd and untar them on the new machine (Be careful which files you duplicate in /etc because this contains most of your settings so you don't want to copy things like /network /X11, which are hardware related on the new machine).  Something like this:

       tar cjvf oldcomputerbackup.tar.bz2 home etc usr bin sbin lib

2) connect the 2 machines and copy files directly using SAMBA or NFS

3) locate the packages filename.deb on your machine and burn those to a cd and use dpkg -i filename.deb to reinstall them  

4) more recent versions of ubuntu have a simple backup function on the admin menu.

---

### Post by moricgaut on 2006-12-27
well is there any backup software or program i can use to backup files. if so what are they called.

---

### Post by OrangeCrate on 2006-12-31
> **sgbeamer said:**
> 
4) more recent versions of ubuntu have a simple backup function on the admin menu.

I've looked. Being new to Ubuntu, I'm either missing it in my search, or Dapper doesn't have it?

---

### Post by indytim on 2007-01-01
You could checkout partimage.  It allows you to backup an entire partition and restore it (so far I'm only using it for backups of my ops).  It is a shell run at command line with a gui front end.  One thing you might find of interest is that it allows you to determine the size of the partition backup file(s) (I use 4000m to fit on a dvd).

Hope this helps,

IndyTim

---

