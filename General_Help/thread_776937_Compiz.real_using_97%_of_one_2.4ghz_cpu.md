---
title: "Compiz.real using 97% of one 2.4ghz cpu"
date: 2008-05-01
forum: General Help
---

### Post by apokkalyps on 2008-05-01
Compiz.real is using 97% of one 2.4ghz cpu. Is this normal? its entirely eating up one of my two processors.

I used to run the gears and a fishtank and the snowglobe and it was all very smooth. Something has happened and now it runs like dogturds. All im running is the cube and a very toned down snowglobe. Just rotating the cube is pretty poor now (Judging from quake3 experience I would guess <15fps), even tho when i run the compiz benchmark plugin it reports ~25fps. Also, when I try to rotate the cube while the benchmark is going, it drops to about about one frame every 3 seconds.
This is on a dualcore 2.4ghz amd64 with 4 gig of memory.

I'm using the nvidia restricted drivers, and they seem to be active.

glxgears is getting ~900fps
glxinfo | grep direct says 3d is enabled

Can anyone help me?

---

### Post by Zorael on 2008-05-01
Is this in Hardy? Compiz build from the repositories or elsewhere?

---

### Post by apokkalyps on 2008-05-01
no im in gutsy, its im not sure what that means about the repositories, its what has always been on here since I installed the OS.

---

### Post by apokkalyps on 2008-05-03
*Bump*  Does no one have an idea of what could cause this?   Or is my post just getting lost behind others?

---

### Post by CarnivorouZ on 2008-05-03
Ubuntu is a very lite system, even with Compiz running to its full potential it should not be using that much.  What he means by the repositories is in /etc/apt/sources.list
which can be edited with the terminal using:
```
sudo gedit /etc/apt/sources.list
```
look inside there for strange sources, by that I mean any webpages that don't contain the words Universe or Multiuniverse as they might be the source for what has been causing so much overdrawing on your CPU.

---

### Post by Zorael on 2008-05-03
Repositories are listed in Software Sources, or in Synaptic (under File -> Repositories). If you have any such enabled, you might just be using a build which is bugging out on you.

[list][*]IF there are any such extra repositories in there, disable them (for now), then search for "compiz" in Synaptic and tag relevant packages for **complete removal**. Then reinstall. (You should only need to mark the compiz and compizconfig-settings-manager packages to get everything you want installed)

Terminal way would be something like this. Assumes repositories disabled.
```
$ sudo aptitude purge ~ncompiz ~nemerald ~nberyl ~nlibdeco
$ sudo aptitude update
$ sudo aptitude clean
$ sudo aptitude install compiz compizconfig-settings-manager emerald
```

Then restart Compiz and see if things improved.
```
$ compiz --replace &
```


[*]If there aren't any extra repositories, I'm not sure I can help. You may want to try to delete your profile in ccsm (compizconfig-settings-manager) and rebuild it from scratch. Keep a monitor of your CPU usage open and enable one plugin at a time - if at any point it skyrockets you'll know which plugin is the culprit.[/list]

---

### Post by apokkalyps on 2008-05-07
Unfortunately, no everything in that sources list looks like its normal.  However a few of my plugins i had to download from somewhere and manually add from make.  Like 3dwindows and atlantis and the snowglobe come to think of it.  

Could that be the problem?  I'd hate to blow away all my compiz and reinstall it because I think id have to reinstall all those manually and its kindof a huge pain.  Unless they are the problem.

I'm watching my processor in htop and adding my plugins in one at a time, its only the plugins that render stuff inside the cube that make the cpu usage jump up to  90+ percent.  Atlantis, snowglobe, photowheel, and even cube gears which wasn't a manual install, it came in compiz.   Without any of them, it goes down to between 10% and 30%.  Any of those individually will make it go up to 90%+. All of them together dont seem to be much worse than one of them.

---

### Post by apokkalyps on 2008-05-15
I'm getting really frustrated with this because NO ONE knows what is causing this problem.  I've put posts on the forums and I've been asking on IRC in both the #ubuntu and #compiz freenode channels and people have no idea.

I finally formatted my entire linux boot partition and reinstalled everything from scratch in hardy just for this compiz problem.  It was fine for a while.  <10% until I brought in the cube gears, and then its back up to 80%+.  I take out the cube gears, and im sitting here not doing anything with compiz not changing desktops or anything, just totally idle and its taking 40-70%.

> barrett@barrett-desktop:~$ lspci | grep -i vga
00:0d.0 VGA compatible controller: nVidia Corporation GeForce 6100 nForce 430 (rev a2)


People say this graphics card should be plenty good.  Can anyone please PLEASE tell me anything you know about whats going on here?  Is it maybe a hardware problem?  Is my GPU not working and my CPU is doing all the work for it (does that even make sense I dont know)?  Or maybe a better place to ask?  What always happens is people ask me a few questions and then lose interest because they have no idea.

System specs:
2x 2.4ghz 64bit
4gig of ram
nVidia Corporation GeForce 6100 nForce 430 (rev a2)
Ubuntu Hardy Heron 8.04
restricted Nvidia Drivers
Direct Rendering is enabled
Anti-aliasing is at 4x

---

### Post by apokkalyps on 2008-05-18
I went ahead and turned off anti aliasing which was the only thing i had modded in my Nvidia settings.  Didn't change the CPU problem at all.  

**BUT** I did notice theres a section for my GPU and under powermizer and it says that my performance level is zero.  Is that normal?

> Performance Mode
Maximum Performance

Performance level
0

NV Clock
425 MHz

Memory Clock
0 MHz

Could this be the cause of my problem?  How can I fix it?  Is it a defective video card or setting?

---

