---
title: "how to install downloaded packages using synaptic"
date: 2008-05-06
forum: General Help
---

### Post by tr3s on 2008-05-06
hi!

i installed several packages (apache, mysql, php) through synaptic online and get the files cached in /var/cache/apt/archives. i pasted it to the /var/cache/apt/archives of a computer that is not connected to the internet hoping that i can also install it using synaptic on that computer. 

how can i make the packages be detected by synaptic on the offline computer? synaptic cannot see the packages even its already in the /var/cache/apt/archives folder. i already did apt-get update. im using edubuntu 7.10

tnx in advance

---

### Post by spd106 on 2008-05-06
Synaptic is clever enough to look in the archive before it tries to download the package as long as you have the version it expects.

Unfortunately, Synaptic relies on their being a link to the archives in order to know which packages are the most recent. This means if you download a newer version it won't pick it up automatically and instead it will look for the older version.

You can get around this by using gdebi instead of Synaptic. Just double-click the .deb file to install. You have to ensure that you have already installed the dependencies or just select a bunch of .deb files and it should install them in the correct order.

[https://launchpad.net/gdebi](https://launchpad.net/gdebi)

---

### Post by tr3s on 2008-05-06
ok thanks for that. that is actually how i accomplished it. but it is a lot of work since im setting up a lab room.

btw, what is the file updated or where are the packages indexed when you do apt-get update? maybe copying that file to the offline computer will make all the packages in the cache archive available in synaptic

---

### Post by spd106 on 2008-05-07
I believe the current snapshot is stored in /var/lib/apt/lists

I have no idea whether you can copy this over and it work as I haven't tried it.

---

