---
title: "Trying to recover ZFS disk from a failed FreeNAS"
date: 2015-07-04
forum: General Help
---

### Post by tony-richmond-ii on 2015-07-04
Hello all. I posted for some help on the FreeBSD forum after not being able to find any workable solutions via search. It was suggested that I try a Linux forum.  Here is the story..

I have some zfs disks I need to get into. 
I had a bunch of old computer parts laying around a couple years ago and  put together a box with FreeNAS. After our move, the box wouldn't turn  on, so I pulled my disks and scrapped it. 

Using zfs on linux, I can find the disk and get a pool id, and get a  warning that it was last accessed on a different machine, but on trying  to import I'm told it's unavailable. 

The data isn't critical, but it would SURE be nice to have.

A response:

"You could try booting from a FreeBSD install image, dropping to a shell,  attempt to import the pool, and if successful copy the data to an  external disk(s) pre-setup with a zpool on Linux. This would be done at  your own risk of course."

Are there any other tools or techniques I should be aware of? Any step by steps to make sure I don't screw it up? Obviously, I got in over my head and put too much stock in the "It's so easy I don't know why EVERYBODY doesn't do it"-camp. Lesson learned, please save any admonishment.  I've gotten plenty from my wife ;). 

Thanks in advance.

---

### Post by tgalati4 on 2015-07-05
Why can't you boot with a freenas USB stick which you made a config backup of (right?) and then inspect the zfs pool for integrity, perform a scrub, and perhaps a polish, then transfer the data to other pools on your Linux machines.  Trying to resurrect a freenas zfs pool in linux should be possible in theory, but in practice, you may loose all of your data.

---

### Post by tony-richmond-ii on 2015-07-05
Because I didn't make any such config backup. I do still have the ide disk on which the FreeNAS os was installed, but it won't boot on any of my machines via the USB adapter. I don't have any ide mobos laying around anymore. I did consider buying another box like I ran it on in the first place (Dimension 4600) since they are around $40 these days, but the wife is skeptical about dropping ANY more money unless there is a very high chance of success.

---

### Post by tgalati4 on 2015-07-06
You can try to *dd* (copy) the image to a USB drive and boot from that or simply create a new *freenas* USB and configure it with your zfs pool (as best as you can remember).  With luck, you should be able to resurrect the freenas zfs pool, put it on the network and then recover the important files from it.

---

### Post by lukeiamyourfather on 2015-07-16
Use ZFS on Linux for the recovery which is the kernel port of ZFS, don't use the FUSE one which is no longer updated. They have an Ubuntu PPA for it.

[http://zfsonlinux.org/](http://zfsonlinux.org/)
[https://launchpad.net/~zfs-native/+archive/ubuntu/stable](https://launchpad.net/~zfs-native/+archive/ubuntu/stable)

I have a brief tutorial for installing ZFS on Linux in Ubuntu on my website.

[http://whenpicsfly.com/wp-content/uploads/2014/09/Intro-to-ZFS-on-Linux.pdf](http://whenpicsfly.com/wp-content/uploads/2014/09/Intro-to-ZFS-on-Linux.pdf)

Once installed you can use the following command to check for available pools.

```
sudo zpool import
```

If it shows your pool you can import it with the following command.

```
sudo zpool import -f mypool
```

The -f flag will force the import even if the pool was never properly exported from another machine. Like in your case this usually happens when the other host has died and simply can't export the pool. If you run into other issues or it throws errors please post back here.

---

