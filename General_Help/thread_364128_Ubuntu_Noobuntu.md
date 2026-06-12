---
title: "Ubuntu Noobuntu"
date: 2007-02-17
forum: General Help
---

### Post by ericunicast on 2007-02-17
Ok everyone, im new to the ubuntu scene and linux as my primary OS so help me out here.
two things i need to do

1. I need to download appropriate codecs to play DVDs 

2. I need to install VMWare workstation, which i can get an RPM or a Tarball. 
Im not sure what to do with either once I have them downloaded. what to use, etc.

Thnx

---

### Post by Arisna on 2007-02-17
For item one,

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats) .

For item two, I don't know, I'm afraid.

---

### Post by Fitzy_oz on 2007-02-17
> **ericunicast said:**
> Ok everyone, im new to the ubuntu scene and linux as my primary OS so help me out here.
two things i need to do

1. I need to download appropriate codecs to play DVDs 

2. I need to install VMWare workstation, which i can get an RPM or a Tarball. 
Im not sure what to do with either once I have them downloaded. what to use, etc.

Thnx

Goto synaptic package manager and enable all of the repositories -  under settings -> repositories.


Search for Mplayer and install everything related to it.  That should sort the DVD thing out for you.

A VMware Player is also available in the repos, just do a search for vmware.

---

### Post by amgeex on 2007-02-17
You might also want to install the VLC Media Player, it a nice video player that will let you play dvd's very easily. Install it like this:

sudo aptitude install vlc vlc-plugin-* mozilla-plugin-vlc avahi-daemon avahi-utils

---

### Post by ericunicast on 2007-02-17
I can still use Vmware player but i need workstation for the ISO creator. How do you use RPMs?

---

### Post by llamakc on 2007-02-17
You should search the forums for "VMWare howto". There are a bunch of threads. Perhaps one of them would fit your particular situation?

---

### Post by 3rdalbum on 2007-02-18
Unless you need VMWare for a particular reason (compatibility with existing virtual disk images, experience with an industry-standard product) I recommend using Virtualbox instead. ([www.virtualbox.org)](www.virtualbox.org)). It comes as a Debian package that will install onto your Ubuntu, is easy to use and set up, the performance is pretty good, and you can get 3D acceleration on Linux guests.

---

### Post by ericunicast on 2007-02-18
I try to install virtual box and it gives me an error message that says ' error, dependancy is not satisfiable: libc.dev.


???:guitar:

---

### Post by ericunicast on 2007-02-18
No ideas whatsoever?

---

### Post by Maestro23 on 2007-02-18
It needs "libc-dev".  Two ways to get it: Synaptic(GUI) or apt-get(command line).

In Synaptic, do a search for "libc-dev", should find what you are needing.  Install and try your program again.  If you don't find it, you may need to enable extra repositories: [http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

---

