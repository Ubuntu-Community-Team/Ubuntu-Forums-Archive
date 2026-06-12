---
title: "Can't Open Synaptic(Seriously Screwed)"
date: 2007-07-22
forum: General Help
---

### Post by PresidentJFJ on 2007-07-22
First of all, I've been using Ubuntu for about 3 weeks now and I'm starting to get the hang of it. It is extremely hard compared to windows and anybody that says it isn't is lying. I do like it though, and it's worth the work. I've gotten pretty much everything to where i want it but have hit a huge problem. I wanted to install looking glass. So I downloaded all of the required .deb packages. The problem was, the method they give for installing them on their website did absolutely nothing for me. After somewhat getting through the installation of one file, I couldn't get any further so i quit. Now when I try to open synaptic I get this error.......................

OMFG. This is the wierdest thing thats ever happened to me. As I was writing this message and checked synaptic for the error, IT WORKED! I removed the package completely and I think I'm good. WTF. O well.

While I'm here, can somebody tell me how i can install project looking glass? I have the three .deb files I need
lg3d-core_1.0.0_i686.deb
lg3d_java3d_1.5.0_i686.deb
lg3d_jdk1.6.0_i686.deb
When I follow the online instructions, I get absolutely nowhere. I am a Linux noob but still, i have tons of stuff installed that works fine so....... i don't know. Please help. Sorry for the first part of the post, I don't know wtf happened. Thanks Alot, I'm happy to be part of the forums.

---

### Post by Seisen on 2007-07-22
You install .deb files two ways

```
sudo dpkg -i lg3d-core_1.0.0_i686.deb

```
you do that with each file or use gdebi by just clicking on the file.

---

### Post by PresidentJFJ on 2007-07-22
I've tried that and i see the liscense in a blue text screen. I go all the way to the bottom and it says <OK>.

How do I select OK? I've pressed enter, O, and I'm pretty lost. Can I install them 1 by 1? On their website it looks like they are telling you to install them all together. Thanks Alot BTW. Very quick and helpful. I don't really want to try anything else until I'm sure I don't screw up my package manager again. That was awful.

---

### Post by mikewhatever on 2007-07-22
Install the way advises on the project's site, not one file or one by one. I really do not think it is very hard to follow
[https://lg3d.dev.java.net/lg3d-getting-started.html](https://lg3d.dev.java.net/lg3d-getting-started.html)
> 2.2 Installing Debian .deb packages

The debian packages have been built and tested on Ubuntu Dapper systems, however they should work on other Debian based distros.
You can download and install the debian packages in one of two ways :

   1. Download the three .deb files from the the binary build page and then install using the following command:

      % sudo dpkg -i lg3d_jdk*.deb lg3d_java3d*.deb lg3d-core*.deb

      Note: the installation of the lg3d-core*.deb package automatically adds LG3D as a session type in the gdm desktop session chooser. There is no need to manually run a postinstall script.

      OR
   2. Install using apt or the Synaptic Package Manager (on Ubuntu) by doing the following (you will need root permissions to do this, so sudo bash first) :
          * There are 3 LG3D repositories. The stable repository has the latest stable releases (0.8.1, 1.0 etc.). The testing repository has the pre-release builds (alpha, beta etc.) for the latest version and the unstable repsoitory has the nightly builds. To access these repositories, add the following lines to /etc/apt/sources.list and then comment/uncomment the appropriate line(s).

              	## LG3D repsoitories
              	deb [http://javadesktop.org/lg3d/debian](http://javadesktop.org/lg3d/debian) stable contrib
              	# deb [http://javadesktop.org/lg3d/debian](http://javadesktop.org/lg3d/debian) testing contrib
              	# deb [http://javadesktop.org/lg3d/debian](http://javadesktop.org/lg3d/debian) unstable contrib
                    

          * Then you can

                      % apt-get update
              	  % apt-get install lg3d-core
                    

            OR, on Ubuntu systems,
                o run the Synaptic Package Manager from the System/Administration menu,
                o click on the Reload button and then
                o Search for lg3d and mark the lg3d-core package for installation.
                o click on the Apply button to download and install

      Choosing lg3d-core for installation should automatically choose/mark lg3d-jdk and lg3d-java3d for installation. You will need to accept the 3 licenses for lg3d, jdk and java3d to complete the installation.

> After somewhat getting through the installation of one file, I couldn't get any further so i quit. Now when I try to open synaptic I get this error.......................
What error did you get in synaptic, a bunch of dots? Do you want help or not?

---

### Post by PresidentJFJ on 2007-07-22
Ok now when I managed to get to installation in terminal it asks me if I want to continue. I say yes, and it procedes with installation. However, it stops and gives me this error message

E: /var/cache/apt/archives/lg3d-jdk_1.6.0+b104_i386.deb: subprocess pre-installation script returned error exit status 1
E: /var/cache/apt/archives/lg3d-java3d_1.5.0_i386.deb: subprocess pre-installation script returned error exit status 1
E: /var/cache/apt/archives/lg3d-core_1.0.0_i386.deb: subprocess pre-installation script returned error exit status 1

I have all the files they tell me that I need. It gives me the same error both in terminal and synaptic.

---

### Post by PresidentJFJ on 2007-07-23
bump

---

