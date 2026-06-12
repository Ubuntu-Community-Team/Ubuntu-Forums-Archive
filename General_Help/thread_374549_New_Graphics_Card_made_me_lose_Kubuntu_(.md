---
title: "New Graphics Card made me lose Kubuntu :("
date: 2007-03-02
forum: General Help
---

### Post by NZ-Wanderer on 2007-03-02
Could someone please help me, I put a new Graphics card on my system yesterday (Nvidia Geforce 8800) and promptly lost the Graphical part of Kubuntu.

I tried a couple of things mentioned about reinstalling the legacy drivers etc, but all that did was give me a black screen with the computer freezing up..

This morning, I reinstalled Kubuntu Edgy and am now at the stage where I get:

> Starting up ...
usplash: Setting mode 1152x864 failed
usplash: Using mode 1024x768

Ubuntu 6.10 Kubuntu tty1

Kubuntu login:

I do my user name and password, and end up at the command prompt...

Could one of you experts out there please tell me (in plain and easy to understand) how to get my graphical Kubuntu back again...

Any help would be very much appreciated...

PS: At the command prompt I did a wget to the nvidia site to download the 1.0-9746 drivers

PPS: Can someone also tell me how to get all available updates from the command prompt please, I would rather have all the updates before I try to get the graphics back (cause as sure as heck if I get it working and then update it will break it again) :) :)

---

### Post by NZ-Wanderer on 2007-03-02
Hokay, I managed to get it going again (not updated yet, so I guess I gonna have to do it all again)

But here is all I did....

I typed: ```
sudo wget http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9746/NVIDIA-Linux-x86-1.0-9746-pkg1.run
```
(to get the latest drivers)

Then I typed ```
sudo sh NVIDIA-Linux-x86-1.0-9746-pkg1.run
```
(And followed all the prompts)

Then just rebooted the computer and it WORKED :) :)

Now to go get all the updates and see if it breaks it again....

------------------------------------------------------------------------------

UPDATE: Yup, the new 2.6.17.11 kernel broke the graphics again, but as soon as I did the:

```
sudo sh NVIDIA-Linux-x86-1.0-9746-pkg1.run
```

again it restored my Graphics again :)

---

