---
title: "Force seveas packages in gutsy"
date: 2007-11-12
forum: General Help
---

### Post by martijntje on 2007-11-12
I am trying to get FreeNX working on gutsy using the workaround described at [https://answers.launchpad.net/ubuntu/+question/15524](https://answers.launchpad.net/ubuntu/+question/15524) .

I added the seveas freenx repository for feisty, like this:
```
deb http://free.linux.hp.com/~brett/seveas/freenx feisty-seveas freenx
deb-src http://free.linux.hp.com/~brett/seveas/freenx feisty-seveas freenx
```

After running apt-get update i can see a few freenx dev packages. The packages i need are NOT there.

Can anyone please tell me what i am doing wrong?

---

### Post by daflame on 2007-11-18
If anyone is interested, I have Ubuntu packages for a working version of FreeNX  0.7.1.  Everything is quite good with only a config file change you can have unlimited sessions on your machine and RDP proxy using rdesktop.  The free version of !M server only allows 2 sessions max.  I have found this to be limiting at times.  Especially if you are trying to setup a server.  Plus it runs with the latest NX 3.0 backend and client.  I have working versions compiled for gutsy on x86_64 and i386.  If anyone needs other dist packages, please let me know and I'll start a VM to build one.

---

### Post by Marc Higgins on 2007-11-18
where can we get these packages?

---

### Post by daflame on 2007-11-22
I opened a forum with the packages linked in...  I'm still not going to have AMD64 packages until tomorrow though.

Click [here]("http://ubuntuforums.org/showthread.php?t=620057&highlight=freenx") to see the post.  Please contribute to the refinement of the installation.

---

