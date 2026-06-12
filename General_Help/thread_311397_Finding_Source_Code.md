---
title: "Finding Source Code"
date: 2006-12-02
forum: General Help
---

### Post by 64mgb on 2006-12-02
Where can I find source code for individual modules?  In particular I'm looking for source for the tuner module.  I've done apt-get install linux-source but that didn't do it.

Thanks,
Rich

---

### Post by LLRNR on 2006-12-02
```
apt-get source *packagename*
```

---

### Post by Delkster on 2006-12-02
> **LLRNR said:**
> ```
sudo apt-get source *packagename*
```

As a slight correction, the *apt-get source* command doesn't normally need root privileges so you don't need sudo. In fact it's even better not to use it because if you do, the files extracted from the source archive will be owned by root (since, well, it was techically root who owned the process that extracted the files) and you won't be able to edit them.

---

### Post by 64mgb on 2006-12-02
Thanks for the quick responses guys (or gals)...I really appreciate it.

Rich

---

### Post by 64mgb on 2006-12-02
Well, ok, I responded too quickly...when I do sudo apt-get source tuner I get an error that says

"E: Unable to find a source package for tuner".

Is it part of another package maybe?

Thanks,
Rich

---

### Post by LLRNR on 2006-12-02
@ Delkster : You're right, thank you for your observation. I will correct my post.

@ 64mgb : It's possible there's no such package, but you can try to search packages like this:

```
apt-cache search *packagename*
```
or even
```
sudo aptitude install apt-file
apt-file update
apt-file search *filename*
apt-file list *packagename*
```

LLRNR

---

### Post by Delkster on 2006-12-02
Is that a kernel module or a user application?

If it's a kernel module, the source probably is included in the linux-source package you installed. However, installing the package only places a compressed archive of the kernel source code in /usr/src, and you'll have to extract the contents of the archive in /usr/src before using them, like so:
```

cd /usr/src
sudo tar -jxf linux-source-whatever.version.tar.bz2

```
Check the exact name of the file with 'ls' when in the /usr/src directory. After that you should be able to find the kernel source in /usr/src/kernel-source-whatever.version.

If it is a user application, are you sure the name of the package is 'tuner'? What are you exactly trying to find the source for?

---

### Post by 64mgb on 2006-12-02
Thanks LLRNR...I'll tinker with that.  Here's a more broad question...where can I find all source code for the kernel (which would include source for the tuner module, as well as everything else that gets compiled)?  Sorry if this is basic info...I'm a Windows convert.

Thanks,
Rich

---

### Post by 64mgb on 2006-12-02
> **Delkster said:**
> Is that a kernel module or a user application?

If it's a kernel module, the source probably is included in the linux-source package you installed. However, installing the package only places a compressed archive of the kernel source code in /usr/src, and you'll have to extract the contents of the archive in /usr/src before using them, like so:
```

cd /usr/src
sudo tar -jxf linux-source-whatever.version.tar.bz2

```
Check the exact name of the file with 'ls' when in the /usr/src directory. After that you should be able to find the kernel source in /usr/src/kernel-source-whatever.version.

If it is a user application, are you sure the name of the package is 'tuner'? What are you exactly trying to find the source for?
Thanks Delkster - I didn't see this when I responded to LLRNR...I think this is exactly what I am looking for.

I'm looking for the source for the tuner module just out of curiosity.  I'm a geek, and would like to see if I can figure out what it's doing.  I have a Diamond PVR-560 TV card that I can't get to work with MythTV...the tuner module never gets loaded, even when I try to load it manually (sudo modprobe tuner).  I've since bought a Hauppauge PVR-150 and it works great.  I guess the bottom line is I'm just a tinkerer.

Thanks,
Rich

---

