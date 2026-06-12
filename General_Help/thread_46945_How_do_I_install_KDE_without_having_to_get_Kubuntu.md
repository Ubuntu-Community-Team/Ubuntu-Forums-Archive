---
title: "How do I install KDE without having to get Kubuntu?"
date: 2005-07-06
forum: General Help
---

### Post by braveerudite on 2005-07-06
This is what I did 

System>Administration>Synaptic Pakage Manager.  I click on KDE for install and after it finished downloading (right before the installation) It told me that it couldn't download some pakage and asked me if I wanted to continue.... I clicked no because I didnt want to install unless I had all my dependency. Are these pakages broken? Any other way to get KDE with Ubuntu without having to download Kubuntu? Anyone else having this problem?  I already added extra repositories from:  ](*,) 

[http://amd64.ubuntuguide.org/#extrarepositories](http://amd64.ubuntuguide.org/#extrarepositories)

But still can't download all I need....What gives?

---

### Post by varunus on 2005-07-06
Usually the "couldn't download some packages" means that one of the backports mirrors is down.  Try switching to a different mirror, and then trying to install KDE.

Good luck, and make sure you have universe enabled at least.  I've done this on Warty just by adding universe, that should be all you need.  Check the packages that don't download and see if they are essential.

---

### Post by braveerudite on 2005-07-06
Im still confuse with these repository names... Can someone explain? Universe,Multiverse,restricted?

---

### Post by crashtest on 2005-07-06
[QUOTE=braveerudite]This is what I did 

System>Administration>Synaptic Pakage Manager.  I click on KDE for install and after it finished downloading (right before the installation) It told me that it couldn't download some pakage and asked me if I wanted to continue.... I clicked no because I didnt want to install unless I had all my dependency. Are these pakages broken? Any other way to get KDE with Ubuntu without having to download Kubuntu? Anyone else having this problem?  I already added extra repositories from:  ](*,) 

[http://amd64.ubuntuguide.org/#extrarepositories](http://amd64.ubuntuguide.org/#extrarepositories)

But still can't download all I need....What gives?[/QUOTE]

I did: sudo apt-get install kubuntu-desktop

---

### Post by braveerudite on 2005-07-06
[QUOTE=crashtest]I did: sudo apt-get install kubuntu-desktop[/QUOTE]


Great ... I'll try that now and get back at you... Thx   \\:D/

---

### Post by braveerudite on 2005-07-06
[QUOTE=crashtest]I did: sudo apt-get install kubuntu-desktop[/QUOTE]


Still can't download all I need.  This is the messege Im getting from synaptic.

> W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdepim/libkleopatra0a_3.4.0-0ubuntu10_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdepim/libkleopatra0a_3.4.0-0ubuntu10_amd64.deb)
  MD5Sum mismatch




---

