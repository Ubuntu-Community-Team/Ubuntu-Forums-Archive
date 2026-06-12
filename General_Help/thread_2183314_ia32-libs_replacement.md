---
title: "ia32-libs replacement?"
date: 2013-10-24
forum: General Help
---

### Post by simon5 on 2013-10-24
I have an application that is dependent on ia32-libs and lib32nss-mdns. Among other things, ia32-libs packs libSDL-1.2 which I need to run the application. 

It's my understand that the way to accomplish installing 32 bit SDL (now that the ia32-libs and lib32nss-mdns have been deprecated?), I need to:
```
sudo apt-get install libsdl1.2-dev:i386
```

However, apt-get wants to delete the following libraries:
```
The following packages will be REMOVED:  bbswitch-dkms build-essential bumblebee bumblebee-nvidia dkms g++ g++-4.8
  gcc gcc-4.8 gcc-4.8-multilib gcc-multilib libavahi-client-dev
  libavahi-common-dev libcaca-dev libdrm-dev libgl1-mesa-dev libglew-dev
  libglib2.0-dev libglu1-mesa-dev libpng12-dev libpulse-dev
  libsdl-image1.2-dev libsdl-mixer1.2-dev libsdl-ttf2.0-dev libsdl1.2-dev
  libslang2-dev libx11-xcb-dev mesa-common-dev nvidia-304 nvidia-current
  nvidia-settings-304 primus virtualbox-dkms
```

Why? I don't want to re-install Bumblebee, Nvidia's driver, and gcc a million times (Why would it want to delete gcc and Bumblebee anyway??).
Can I install ia32-libs on 13.10? It would make things less complex. Is there some other solution? :mad:

---

### Post by fantab on 2013-10-24
Is the application you are trying to install 64bit? If yes, install the 32bit version if available.

---

### Post by simon5 on 2013-10-24
The app is 32 bit exclusively. In the past I'd just install ia32-libs and lib32nss-mdns and be done with it.
But now I'll have to find out the apps dependencies and mess with :i386? ~__~"

---

### Post by philinux on 2013-10-24
> **simon5 said:**
> The app is 32 bit. In the past I'd just install ia32-libs and lib32nss-mdns and be done with it.
But now I'll have to find out the apps dependencies and mess with :i386? ~__~"

13.10 has full multiarch and ia32-libs is now deprecated. Auto remove worked fine here in cleaning out a lot of i386 cruft packages that are no longer needed.

---

### Post by simon5 on 2013-10-24
> **philinux said:**
> 13.10 has full multiarch and ia32-libs is now deprecated. Auto remove worked fine here in cleaning out a lot of i386 cruft packages that are no longer needed.

It's not cruft. It's a fresh installation of 13.10 on top of which I installed gcc, bumblebee, smplayer and that's it. If I try to install libsdl1.2-dev:i386, apt deletes a lot of libraries that aren't cruft.

Anyway, I tried to create a symlink to /usr/lib/x86_64-linux-gnu/libSDL.so. this obviously was never going to work (wrong ELF class: ELFCLASS64).

How do I get 32 bit SDL without autoremove freaking out on me? is compiling from source the only option (and sdl is not even the only thing I would have to compile)...?

---

### Post by philinux on 2013-10-24
Gotcha. Hopefully someone has solved this and reply. Good luck.

---

### Post by simon5 on 2013-10-24
> **philinux said:**
> Gotcha. Hopefully someone has solved this and reply. Good luck.

My fault. I wasn't clear enough in the OP. :)

---

### Post by simon5 on 2013-10-25
Any thoughts, guys? How do I install i386 SDL 1.2 without apt uninstalling a plethora of libraries I need...?
```
sudo apt-get install libsdl1.2-dev:i386
[...]
The following packages will be REMOVED:  bbswitch-dkms build-essential bumblebee bumblebee-nvidia dkms g++ g++-4.8
  gcc gcc-4.8 gcc-4.8-multilib gcc-multilib libavahi-client-dev
  libavahi-common-dev libcaca-dev libdrm-dev libgl1-mesa-dev libglew-dev
  libglib2.0-dev libglu1-mesa-dev libpng12-dev libpulse-dev
  libsdl-image1.2-dev libsdl-mixer1.2-dev libsdl-ttf2.0-dev libsdl1.2-dev
  libslang2-dev libx11-xcb-dev mesa-common-dev nvidia-304 nvidia-current
  nvidia-settings-304 primus virtualbox-dkms
[...]
```

Do I just install libsdl1.2-dev:i386 and then re-install all of the aforementioned things? That's kind of stupid, now isn't it...?

---

### Post by simon5 on 2013-10-26
Alright. I haven't been able to find a cleaner solution to my problem other than re-installing all the libraries uninstalled by libSDL1.2-dev:i386. 
I'm going to mark this topic as solved; but this solution is terrible (neither bbswitch-dkms nor build-essential should have anything to do with i386 SDL). Simply using ia32-libs was more convenient; without any hassle, either.

---

### Post by HungerGalaxy on 2013-11-12
I'm having the same problem, has anyone found a better solution? I can't just remove gcc

---

### Post by adec2 on 2013-11-13
Not sure if this will help but i had a couple of programs that needed the ia32 libs too that refused to work in 13.10 just did this and now they work fine

Install Synaptic from terminal window

 sudo apt-get install synaptic

 Launch synaptic and goto &#8220;settings > Repositories&#8221;

 click &#8220;other software > add&#8221;

 insert this line in the box "deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) raring main restricted universe multiverse"

 click ok and close synaptic

 in terminal &#8220;sudo apt-get update&#8221;

 in terminal &#8220;sudo apt-get install ia32-libs&#8221;

Hope it helps

---

### Post by dave2001 on 2014-02-18
I'd love to hear a real solution or link to a real solution for the correct way to implement this much vaunted, but so far just a pain-in-my-A$$ "multi-arch support" for ANYthing that used to rely on ia32libs or other now "deprecrecated cruft" that was working so easily in past versions of 'buntu.

@adec, I appreicate the post, but I do not consider using an an old verison of the package, which may or may not cause major instabilties in my system (according to some others that have tried it), a solution.

---

