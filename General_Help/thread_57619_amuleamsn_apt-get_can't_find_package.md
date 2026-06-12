---
title: "amule/amsn apt-get can't find package?"
date: 2005-08-17
forum: General Help
---

### Post by donnysrx on 2005-08-17
hi all

if I type in "sudo apt-get install amule" in console it says "cant' find package":(

and yet "apt-get update" works fine

What am I doing wrong, apart from this, the linuxbox is working fine, using now in fact

thanks for any help:)

---

### Post by cloudr on 2005-08-17
you need to edit /etc/apt/sources.list
and add the following lines:


## Backports - package version from a newer release build to work on the current## no guarantees on working - not enabled by default
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary-backports universe multiverse

## The source packages
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary-backports universe multiverse

## hoary-extras-the most widely used source for packages not includded in Ubuntu## no guarantees on working - not enabled by default
deb [http://public.planetmirror.com/pub/ubuntu-backports/](http://public.planetmirror.com/pub/ubuntu-backports/) hoary-extras main universe multiverse restricted



Then you will be able to install amsn

---

### Post by donnysrx on 2005-08-17
ok re-edited sources.list, adding the above lines,but cant replace file due to not being logged in as root I suspose, and I don't know the password either

during install I don't remember setting a root password!!!!!!!!!!!!!!!!

will I have to reinstall ubuntu and see if I can enter a root password?

---

### Post by donnysrx on 2005-08-17
this explains it


[http://ubuntuforums.org/showthread.php?t=51641&highlight=root+pasword](http://ubuntuforums.org/showthread.php?t=51641&highlight=root+pasword)

---

