---
title: "apt-get/synaptic problems, problem with servers?"
date: 2005-07-16
forum: General Help
---

### Post by Magitek on 2005-07-16
Hi,
Is anyone else here experiencing problems with apt-get/synaptic? I am trying to install the mplayer-386 package, which worked fine when I installed it a few days ago, but now for some reason it's having problems intalling some of the libraries. Here's is what synaptic says:

```
W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/libg/libgii/libgii0_0.8.5-2_i386.deb
  MD5Sum mismatch


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/libg/libggi/libggi2_2.0.5-1ubuntu1_i386.deb
  MD5Sum mismatch

```

The files do exist because I have downloaded them but when I try:

```
sudo dpkg -i file.deb
```

on them, there is no luck they won't install, are they corrupt?

It is not just me who is having problems my friend said synaptic wouldn't install a package for him, it may have been alsamixergui, I can't remember. I can't see any posts announcing server problems, I am hitting my head against a wall here ](*,) , Is it just me?

Thanks in advance,
Joe

---

### Post by Dogmeat on 2005-07-16
I think indeed theres something wrong with the servers, because I've been getting MD5 errors too on some packages since last week or so.

---

### Post by Magitek on 2005-07-16
Glad it's not just me. This link helped me out with the [http://us.archive.ubuntu.com/](http://us.archive.ubuntu.com/) servers that where giving me hell, I just changed them to  [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com), seems to working now. I think this should really be mentioned in the ubuntuguide:
[http://www.ubuntuforums.org/showthread.php?t=49338&highlight=connection+refused](http://www.ubuntuforums.org/showthread.php?t=49338&highlight=connection+refused)

The backport servers aren't working mind you they never have for me: 

## Backports
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted

---

### Post by Magitek on 2005-07-16
I think I must have had to change to the UK archive because the US libraries where causing conflicts and I have ubuntu set up as UK version ??The MirrorMAx servers are having problems apparently, so I'm using these severs for now:

deb [http://mirror.brianpuccio.net/ubunt...rts-repository/](http://mirror.brianpuccio.net/ubunt...rts-repository/) hoary-backports main universe multiverse restricted

deb [http://mirror.brianpuccio.net/ubunt...rts-repository/](http://mirror.brianpuccio.net/ubunt...rts-repository/) hoary-extras main universe multiverse restricted

Seems to be working lets hope it can stay that way :p

---

### Post by t2kburl on 2005-07-16
I think it may be a sign of the rapidly increasing user base of Ubuntu  :)

---

