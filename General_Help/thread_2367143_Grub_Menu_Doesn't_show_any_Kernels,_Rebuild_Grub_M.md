---
title: "Grub Menu Doesn't show any Kernels, Rebuild Grub Menu"
date: 2017-07-26
forum: General Help
---

### Post by rsteinmetz70112 on 2017-07-26
Ubuntu 16.04 LTS

I deleted a some very old kernels for one of my machines. 
Now the Grub menu doesn't show any kernels only MemTest. I know they are there. 
How can I rebuild the Grub menu.

I can either boot using options on Grub or from a Live DVD.

---

### Post by Frogs Hair on 2017-07-26
Have you updated grub ?

 ```
sudo update-grub

```

---

### Post by rsteinmetz70112 on 2017-07-26
Well, I did but in order to boot I had to start a live DVD mount the drive and chroot to the hard drive. update-grub didn't find any thing.

I have copied some stuff from another machine and it boots but it isn't exactly correct.

---

### Post by deadflowr on 2017-07-26
Sounds like you removed all the kernels.
You should be able to reinstall a kernel from within a chroot.

Might help to know what command to remove was actually run:
If the command isn't something you remember or is something long and confusing you can look at those commands in the live session mount of the hard drive in the user's home folder in the .bash_history file.
If that makes sense.

Myself, I would simply setup the chroot and try reinstalling linux-generic.
That should pull in the linux-image-generic and linux-headers-generic packages, which they themselves will pull in the latest kernel versions
(The linux-image-4.4.0-11-generic linux-headers-4.4.0-11-generic packages, for example, but not those specifically )
simply run
```
apt-get update
apt-get install --reinstall linux-generic
```
inside the chroot.
(Note you will need to set networking for the chroot:
What I find works for that is to simply copy the live sessions /etc/resolv.conf file in the chroot before you run chroot:
```
sudo cp /etc/resolv.conf /mountpoint-of-the-chroot/etc/resolv.conf
```)

See if that helps

---

### Post by rsteinmetz70112 on 2017-07-26
The kernels were removed using synaptic. Several were not removed. 

I am now able to boot using files copied from another machine. I do need to get networking running. It may be a little difficult since this machine uses wireless only.
That seems to be my task for this evening. 

If I can get access the Ubuntu archives and update the system I believe it will pull in a new kernel version and that should solve my problem.

---

### Post by rsteinmetz70112 on 2017-07-28
Got networking going, still no wifi, I can boot did a dist-upgrade and it works except I have another issue. 
I'm going to start a new thread with the new problem.

---

