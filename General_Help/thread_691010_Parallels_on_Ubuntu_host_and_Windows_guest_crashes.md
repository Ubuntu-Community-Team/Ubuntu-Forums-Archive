---
title: "Parallels on Ubuntu host and Windows guest crashes PC"
date: 2008-02-08
forum: General Help
---

### Post by psypher on 2008-02-08
I just tried the new Parallels for Linux from the partner repo's. Unfortunately all it does is completely crash my PC and the only way to unfreeze it is a hard reboot.  I did notitce that the VM only crashed the machine once the windows install booting process says: now booting windows .Since this is quite new to linux I am not sure where to start. Does parallels have it's own log file? Has anyone successfully gotten it to work AND install windows? Where should I start looking for error logs. Unfortunately I cannot simulate it right now as I need to work and cannot afford another crash but I would really love to get this working and if it works I will be definitely buying the product. Also if I have compiz-fusion switched on and I click start on the VM the OS window has this weird transparency thing going. If i move the window around my desktop everything behind the window is seen in a purple negative effect. 

I'm running Ubuntu Gutsy on a Dell M6300 and this crashes with compiz on and off.

Thanks

---

### Post by JGJones on 2008-02-08
I've not had the problems you had with Parallels - I had a installed windows working successfully for me in Parallels.

I know this doesn't help your problem but I have no idea of any logs or whatever else it does, but I don't think it does - so try running it from terminal, it might pop up an error if it crash.

However I have since uninstalled Parallels and am now using VirtualBox (also available in repos) - why? Because when Compiz is enabled (I never turn it off) - for some reason, Parallels never render black. All black colour is 100% transparent. It's a solid black if Compiz is off, but as soon as Compiz is turned back on, it's transparent. It's a nightmare to use Windows etc in Compiz with Parallels.

I've submitted a bug report to Parallels for that one and am now using VirtualBox (its key feature over Parallels is the ability to use snapshots, Parallels don't offer this)

I would just suggest that you do give VirtualBox a try if Parallels isn't working for you and you've not already created any virtual machines with it.

Cheers

---

### Post by psypher on 2008-02-08
OK so that explain the transparency thing. :confused: Lets hope they fix that soon. The reason for parallels is the seamless integration and the possible option of playing 3d games without having to reboot into windows. from what i understand i can run a windows app like IE in linux as if it is running in Windows. And no I don't like the way seamlessrdp with virtualbox/vmware does it, it doesn't work well, is extremely buggy and cut and paste is a best effort thing. I need stability for 9 hours a day while at work. i use a deeply embedded activex webapp that just won't work with wine or crossover, so my next best option is parallels. and like i said being able to play Unreal tournament 3 or BFME 2 without having to reboot will be AWE.........wait for it..... SOME!!!! :)

thanks for the help though. I will have a another try with parallels later and try and output the command line to text file, hopefully it will catch whats going wrong before it crashes completely

---

### Post by JGJones on 2008-02-08
I know that Parallels have gotten *some* 3D games to work in Windows on OSX. However as far as I know there's no plans to do the same for Linux however I'm happy to be proven wrong on this.

Regarding your Parallel problem - as I don't get your problem, so here's what I would do to try and narrow down the problem: What's your system? Have you gotten Intel VT-X or AMD-V enabled and does your CPU support it? If yes make sure that it's enabled in BIOS as well (some CPU can support it, but disable it in BIOS by default etc) If not then disable it in preferences and make sure it's the same for your virtual machine setting as well. Go as simple as possible and notch it up from there.

BTW to fix transparency thing (which is present even in full screen) - just disable Compiz - I use a button on toolbar to flick it on/off while running Parallel until they have it fixed.

---

### Post by Siobhany on 2008-05-07
I had this same exact problem on my work laptop, an HP Compaq nc6320, running Gutsy Gibbon.  I ended up installing Feisty Fawn and got Parallels to not freeze my computer every 5 minutes.  It does, however, often log me off when I turn on my guest XP machine.  I just make sure I don't have anything important running before I start Parallels.  Once you log in to Windows, it's stable, though.

---

### Post by JGJones on 2008-05-07
VirtualBox - if anyone's interested, it appears that they are now working on 3D support (DirectX to OpenGL thingy) for VirtualBox :) 

Competition's a grand thing...

---

### Post by Siobhany on 2008-05-29
I downloaded VirtualBox a few weeks ago and it's great!!  It's so much faster and stabler than Parallels.  It hasn't crashed my computer once! :D

---

