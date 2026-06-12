---
title: "NVIDIA driver question?"
date: 2007-06-19
forum: General Help
---

### Post by Butthead on 2007-06-19
Hi,

Probably a goofy question, but I was just wondering what graphics driver (nvidia-glx OR nvidia-glx-new) should be installed if you have an EVGA GeForce 7950 GT KO graphics card installed in your computer?

Also, is there a good NVIDIA graphics card installation tutorial out there somewhere online if you are using an older version of Ubuntu (Kubuntu "Dapper Drake" 6.06) in my case?

Thanks for any help!

---

### Post by NeoLithium on 2007-06-19
Ubuntuguide has a dapper tutorial for NVIDIA Graphics Drivers. Here ya go :
[http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_install_Graphics_Driver_.28NVIDIA.29](http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_install_Graphics_Driver_.28NVIDIA.29)

---

### Post by kuja on 2007-06-19
nvidia-glx-new for sure.

Alternatively you could use envy for the installation, that might be easier in (k)ubuntu 6.06.

---

### Post by fragos on 2007-06-19
I recommend you stay with the nvidia-glx-new package as installed from the Ubuntu repositories.  If you don't, when Kernel updates occur you will have to reinstall the driver.  With nvidia-glx-new that is taken care of for you by the update manager.

---

### Post by Qu4k3R on 2007-06-20
I would read the [http://ubuntuguide.org](http://ubuntuguide.org) :D

---

### Post by Butthead on 2007-06-20
Hmm, thanks for all the help everybody! :guitar:

I can't seem to find nvidia-glx-new listed under Adept installer (only nvidia-glx).:(

Envy didn't seem to work for me the six times I tried it.:(

How come somebody has to always link you to a Feisty page (as far as I know, Dapper and Feisty are two different animals when it comes to installing stuff, right?). :confused:

---

### Post by DeathOnJuice on 2007-06-20
What's the difference between the nvidia-glx and the nvidia-glx-new packages? I'm using nvidia-glx with my 7800GT right now. Should I switch?

---

### Post by fragos on 2007-06-20
Nvidia-glx-new is only in Feisty 7.04.  In the past Ubuntu had nvidia-glx and nvidia-glx-legacy.  As new nvidia drivers came out they were moved into nvidia-glx.  This last time the new driver no longer supported everything that nvidia-glx had supported which caused no end of confusion.  what we have now is an nvidia-glx that has the same device coverage as it had and an nvidia-glx-new which has a more recent driver but doesn't cover all that nvidia-glx covered.  nvidia-glx-legacy remains as before.  I believe glx and glx-new will both support the 7800GT.  I don't know but doubt that you will notice any difference in performance or features with many nvidia cards if you use nvidia-glx-new.  You could try both drivers and use glx-gears to test the fps to see if there is a difference for your video card.

---

### Post by Butthead on 2007-06-21
Hmm, would it be possible for versions of K/Ubuntu older than Feisty to get the nvidia-glx-new driver with programs like Automatix and Synaptic, especially since we don't have this hot new "install restricted drivers" menu item that everyone with newer versions of K/Ubuntu seems to have now? :confused:

Oh, and BTW - I think I figured out why some people keep having problems with running the "Envy" graphics driver installer.  Could it be they all have x64 architecture like I do (I assume "Envy" is written for x32. :confused:

---

### Post by fragos on 2007-06-21
> **Butthead said:**
> Hmm, would it be possible for versions of K/Ubuntu older than Feisty to get the nvidia-glx-new driver with programs like Automatix and Synaptic, especially since we don't have this hot new "install restricted drivers" menu item that everyone with newer versions of K/Ubuntu seems to have now? :confused:

Oh, and BTW - I think I figured out why some people keep having problems with running the "Envy" graphics driver installer.  Could it be they all have x64 architecture like I do (I assume "Envy" is written for x32. :confused:

Conceivable the older Ubuntu versions can get newer Nvidia drivers.  What's key to realize is those drivers have to be compiled for the specific kernel version in play.  Personally I always update to new Ubuntu versions so I'm not familiar with the support provided by older versions although I believe all versions 6.06 onward are still under support.  As a rule support relates to security and bug fixes to the package versions that were part of the release.  Every six months there is a new distribution release that has all the latest package versions.  That's one of the reasons I keep current with the latest Ubuntu release.

---

### Post by kuja on 2007-06-22
> **Butthead said:**
> Hmm, would it be possible for versions of K/Ubuntu older than Feisty to get the nvidia-glx-new driver with programs like Automatix and Synaptic, especially since we don't have this hot new "install restricted drivers" menu item that everyone with newer versions of K/Ubuntu seems to have now? :confused:

Oh, and BTW - I think I figured out why some people keep having problems with running the "Envy" graphics driver installer.  Could it be they all have x64 architecture like I do (I assume "Envy" is written for x32. :confused:

no, envy works fine in x86_64. As per the version of the graphics driver - nvidia-glx-new has better support for much newer cards (geforce 8 series) and also should have better support for 3d-desktop like things.

---

### Post by hessiess on 2007-06-22
easy test for graphics proformance,

download blender

salect the cube

go onto edit buttons

tab

hit subdivide

rotate the viewport(mmb)

subdivide again, rotate again.

when the viewport starts to lag, check the vert count in the top righthand corner of the screen. ses ve....

you should be able to run 500,000 to 1,000,000 ish verts with that card(a ruf guss) if it starts laging at 4,000 or somthing you have a problem with the driver:)

---

### Post by Butthead on 2007-06-22
Yeah, it's probably the best idea to just get the newer versions of "K/Ubuntu" instead of trying to manually install stuff by hand. :(

I might just try Envy again (although I don't have much hope of it working :rolleyes:).  I should be happy with how nvidia-glx driver performs on my system now, but I just can't stand to see that it claims I only have 256 Megs of video RAM when in fact the card has 500.:mad:

---

### Post by Butthead on 2007-06-22
Well, running Envy f**ked up my system again. :mad:

I guess it doesn't work on all x85_64 systems now, doesn't it?:rolleyes:

How come someone can't write a simple Nvidia driver walkthrough that you don't need six years of C++ programming language training to understand? :confused:

---

### Post by Butthead on 2007-06-23
Well, I take it all back.  Envy *DOES* seem to work in x86_64 systems. :rolleyes:

Some tips I found for people who seem to be having trouble with Envy:

1.  *DO NOT* use the text based Envy installer menu. [-X

2. Be sure to restart (I actually rebooted my rig) first (after exactly following the installation instructions on the Envy webpage) before you use it.

3. When K/Uubuntu starts up again, there should be a Envy + NVIDIA GUI menu options added under the System menu. 

Now can anyone tell me how to get the new monitor resolution to stick after shutdown using the NVIDIA settings program?

---

