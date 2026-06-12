---
title: "Mirroring Selected Ubuntu Repo's."
date: 2007-04-21
forum: General Help
---

### Post by ikonia on 2007-04-21
Hi,

I have a lot of projects mirrored on a Redhat machine.

I've decided due include the ubuntu repo's into my local mirror to aid with constand re-installs and mass deployment.

I mirror for example the redhat, fedora and centos mirrors using rsync.

I only mirror the previous 2 versions through to current.

so for example fedora 4 5 and 6, i'll drop 4 when fc7 is released. (just as an example).

For ubuntu i'd like to mirror the 6.0.6.1 rpeo's and the 7.04 and drop edgy.

For the redhat based mirrors I just use the "rsync --exclude" option 

eg: rsync --exclude 1/--exclude 2/ --exclude 3/

When FC7 is released i'll add --exlucde 4/

This works due to the layout of the redhat based repo's.

Is there way I can use rsync to mirror the ubuntu repo's I desire. 
i've tried a few methods, but I still end up with warty content for example.

Input is appriciated.

---

### Post by heimo on 2007-04-21
Some of these may be helpful:
[http://packages.ubuntulinux.org/feisty/net/debmirror](http://packages.ubuntulinux.org/feisty/net/debmirror)
[http://packages.ubuntulinux.org/feisty/net/debpartial-mirror](http://packages.ubuntulinux.org/feisty/net/debpartial-mirror)
[http://packages.ubuntulinux.org/feisty/net/apt-mirror](http://packages.ubuntulinux.org/feisty/net/apt-mirror)

---

### Post by ikonia on 2007-04-21
A fair few of them I'd read, and I was trying to avoid the debian based tools such as apt-mirror due to the fact that I'm mirroring from redhat.

However, I suppose I should stop dodging the bullet and start biting it and port it to redhat and fedora.

Thanks for the input.

---

