---
title: "No sound, tried to fix, now its worse"
date: 2018-05-24
forum: General Help
---

### Post by danieljumbehr on 2018-05-24
I just installed ubuntu, but the sound only worked for about a minute before it dissapeared again.
So i googled how to fix it, was told to remove then reinstall also. so I put this into the terminal...
sudo apt-get install alsa-base pulseaudio
Then it remove both alsa and pulseaudio. Now when I try to reinstall alsa, the terminal keeps telling me that it cant be found.

So now I have no sound and no software to produce sound. Help, please?

---

### Post by danieljumbehr on 2018-05-24
When I used "sudo apt-get install alsa-base pulseaudio" this is the response I get...

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package alsa-base is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

Package pulseaudio is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'alsa-base' has no installation candidate
E: Package 'pulseaudio' has no installation candidate

---

### Post by monkeybrain20122 on 2018-05-24
Which Ubuntu version is that??

---

### Post by danieljumbehr on 2018-05-25
Ubuntu 18.04 LTS

---

