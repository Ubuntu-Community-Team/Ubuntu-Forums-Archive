---
title: "Installing Google Earth on Ubuntu 14.04.2 64bit"
date: 2015-03-21
forum: General Help
---

### Post by nicolaferrari on 2015-03-21
Hi everybody! Please be patient for my poor english, I'm italian...

I was trying to install Google Earth on Ubuntu 14.04.2 64bit. I'm experiencing problems with MESA libraries and their dependences.
Almost any tutorial I found on the net (ie.[http://www.webupd8.org/2014/04/install-google-earth-in-ubuntu-1404.html](http://www.webupd8.org/2014/04/install-google-earth-in-ubuntu-1404.html)), suggest install these packages:
```
sudo apt-get install libfontconfig1:i386 libx11-6:i386  libxrender1:i386 libxext6:i386 libgl1-mesa-glx:i386 libglu1-mesa:i386  libglib2.0-0:i386 libsm6:i386 
```

... but I get some dependences errors.. It seems that I'm not the only one having these problems with the .2 minor version:
[URL="http://answers.ros.org/question/203610/ubuntu-14042-unmet-dependencies/"]http://answers.ros.org/question/203610/ubuntu-14042-unmet-dependencies/
[/URL]
Any suggestion?
Did anyone manage in making google earth work on Ubuntu 14.04.2 64bit?

Thanks, best regards,
Nick

---

### Post by dino99 on 2015-03-21
the link you provided above explain the why & how, and the required 'extra' dependencies:

sudo apt-get install libfontconfig1:i386 libx11-6:i386 libxrender1:i386 libxext6:i386 libgl1-mesa-glx:i386 libglu1-mesa:i386 libglib2.0-0:i386 libsm6:i386
cd /tmp && wget [http://dl.google.com/dl/earth/client/current/google-earth-stable_current_i386.deb](http://dl.google.com/dl/earth/client/current/google-earth-stable_current_i386.deb)
sudo dpkg -i google-earth-stable_current_i386.deb
sudo apt-get install -f

do you have downloaded the 32 bits version of google earth ?
( sorry but i've never tried to install it)
[https://help.ubuntu.com/community/GoogleEarth](https://help.ubuntu.com/community/GoogleEarth)

---

### Post by nicolaferrari on 2015-03-21
I've already tried....

I got these errors:

```
sudo apt-get install libfontconfig1:i386 libx11-6:i386 libxrender1:i386 libxext6:i386 libgl1-mesa-glx:i386 libglu1-mesa:i386 libglib2.0-0:i386 libsm6:i386
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:
The following packages have unmet dependencies:
 libcheese-gtk23 : Depends: libclutter-gtk-1.0-0 (>= 0.91.8) but it is not going to be installed
                   Depends: libcogl15 (>= 1.15.8) but it is not going to be installed
 libcheese7 : Depends: libclutter-gst-2.0-0 (>= 0.10.0) but it is not going to be installed
              Depends: gstreamer1.0-clutter but it is not going to be installed
 libclutter-1.0-0 : Depends: libcogl-pango15 (>= 1.15.8) but it is not going to be installed
                    Depends: libcogl15 (>= 1.15.8) but it is not going to be installed
 libgl1-mesa-glx:i386 : Depends: libglapi-mesa:i386 (= 10.1.3-0ubuntu0.3)
                        Recommends: libgl1-mesa-dri:i386 (>= 7.2)
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.


```

Just for testing, I'm trying it also on a 14.04.2 vm fresh install...


Any suggestion?
Nick

---

### Post by fwrun2011 on 2015-03-23
I have tried everything as well. Tried the current stable i386 version (amd64 will never work), and an older version that I found -6.22 I think it is.
Both of these worked when I was running Ubuntu 14.04.1 which I had installed from a DVD, but later I downloaded the newer Ubuntu 14.04.2 onto a flash drive and have been working with this version since, and no luck with Google Earth.
I have two installs of Ubuntu, so I will try going back to 14.04.1 and go through the process of installing Google Earth that worked previously. I will post my results here by the end of the day Mon 3/23. I am on US Eastern Daylight-Saving time, so time adjustment may be needed.

FW

---

### Post by fwrun2011 on 2015-03-23
Here's what I did.
Re-installed a copy of Ubuntu 14.04.1 - not 14.04.2. I had this on a DVD, but I believe you can still get it on the regular download site.
To install Google Earth takes several steps. I used the terminal method rather than the software center. You get move information that way - if something doesn't go right.
Here is the link to the website where I found the instructions for installing the latest Google Earth stable version.
[http://www.webupd8.org/2014/04/install-google-earth-in-ubuntu-1404.html](http://www.webupd8.org/2014/04/install-google-earth-in-ubuntu-1404.html)
Make sure you follow the instructions under the title "[SIZE=2]**Install Google Earth in Ubuntu 14.04 64bit**"[/SIZE]
If you get an error after installing the required libraries, follow the suggestion presented. This happened to me when I was trying to install on Ubuntu 14.04.2, but did not come up when I installed on Ubuntu 14.04.1.

Note: There is a very long line of commands that is listed on two lines, but is really one continuous line. I copied and pasted this, but I did it on three separate commands, hitting the enter key after pasting in each line:

sudo apt-get install libfontconfig1:i386 libx11-6:i386 libxrender1:i386 libxext6:i386 libgl1-mesa-glx:i386 libglu1-mesa:i386 libglib2.0-0:i386 libsm6:i386
cd /tmp
wget [http://dl.google.com/dl/earth/client/current/google-earth-stable_current_i386.deb](http://dl.google.com/dl/earth/client/current/google-earth-stable_current_i386.deb)
sudo dpkg -i google-earth-stable_current_i386.deb
sudo apt-get install -f

note that I left out the && that were between the "cd /tmp" and "wget http://..." you don't need them if you do the commands separately
Also, note that you do not need sudo to download the package using the wget command.

You should find your Google Earth icon in Dash by searching for it.
It runs fine on my 14.04.1 install, but will not run on the 14.04.2 install - I will try again on 14.04.2, maybe it was just a problem getting some of the library dependents.

Also of interest:
When I tried to install wine 1.7 (or the stable release - 6.2 I think) I got all sorts of errors, and was unable to install Amazon Kindle PC no matter what I tried. 
But when I did the same thing on 14.04.1, I was able to get wine installed, and Kindle for PC running.

I really don't know what's going on here. If more of us are having the same issues, it should be reported as a bug. But I want to do more research before doing so.

FW

---

### Post by fwrun2011 on 2015-03-23
More info:
After having successfully installed Google Earth current stable version (32-bit) on Ubuntu 14.04.1 64-bit, I went back to my 14.04.2 64-bit install, and attempted to install the same version of Google Earth.
This is what happened when I tried to install the libraries, using the instructions in my last post:

fw2015@frank-ubuntu:~$ sudo apt-get install libfontconfig1:i386 libx11-6:i386 libxrender1:i386 libxext6:i386 libgl1-mesa-glx:i386 libglu1-mesa:i386 libglib2.0-0:i386 libsm6:i386
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libcheese-gtk23 : Depends: libclutter-gtk-1.0-0 (>= 0.91.8) but it is not going to be installed
                   Depends: libcogl15 (>= 1.15.8) but it is not going to be installed
 libcheese7 : Depends: libclutter-gst-2.0-0 (>= 0.10.0) but it is not going to be installed
              Depends: gstreamer1.0-clutter but it is not going to be installed
 libclutter-1.0-0 : Depends: libcogl-pango15 (>= 1.15.8) but it is not going to be installed
                    Depends: libcogl15 (>= 1.15.8) but it is not going to be installed
 libgl1-mesa-glx:i386 : Depends: libglapi-mesa:i386 (= 10.1.3-0ubuntu0.3)
                        Recommends: libgl1-mesa-dri:i386 (>= 7.2)
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
fw2015@frank-ubuntu:~$ 

I do not believe this is caused by server problems. It appears to be something about the 14.04.2 install.
Further inspection of the error code, I believe the library versions being installed here are incorrect for this version of Ubuntu. So what I need to do is find the updated library files.

FW

---

### Post by mc4man on 2015-03-23
For a 14.04.2 image (HWE stack) you need to change 1 package name, so - 
```
sudo apt-get install libfontconfig1:i386 libx11-6:i386  libxrender1:i386 \
libxext6:i386 libgl1-mesa-glx-lts-utopic:i386 libglu1-mesa:i386 \
libglib2.0-0:i386 libsm6:i386 lsb-core
```

---

### Post by fwrun2011 on 2015-03-23
Thanks mc4man;
That did it on Ubuntu 14.04.2. Where did you find these library files ?
I guess once I update the library files (there are only two that are different/new) I can update my other install to 14.04.2.

---

### Post by mc4man on 2015-03-23
Once you update your sources & run an apt-get upgrade then both your installs are 14.04.2
The one that started from the 14.04.1 image is using the release versions of the kernel & mesa, the one that started from the 14.04.2 image is a HWE (hardware enablement) install & is using the utopic (14.10) kernel & mesa source packages. Otherwise they are the same..
So that's why it needed libgl1-mesa-glx-lts-utopic vs. libgl1-mesa-glx

(- the same thing will happen with 14.04.3, the image will use vivid's kernel & mesa, ex. - libgl1-mesa-glx-lts-vivid, ect.

You can't upgrade the orig. 14.04.1 install to the utopic kernel & mesa though you can install the kernel packages & replace it's mesa packages with the -lts-utopic ones if desired but, -  newer isn't synonymous with better by any means.
 I'd use both & see what you think..

---

### Post by bradyq on 2015-03-26
I was able to get it installed by changing the packages as described above. However, when I open it the GUI appears, but not the "earth". I'm also met with a warning just before it opens that says, "Your graphics card does not meet the minimum spec required to run Google Earth, which is a 3D accelerated card with shader support....". I have a Quadro K2000M with a manually installed NVIDIA 340.76 driver (from NVIDIA's website since the ubuntu packages didn't let me use the CUDA toolkit after installing the 331 driver). The driver works just fine and CUDA works. Any ideas? Thanks.

---

### Post by bradyq on 2015-03-27
Nevermind, it works now (not sure why). I updated (it had been a few days), which necessitated reinstalling the NVIDIA driver (not sure if it was an xconfig thing or the drivers were bad) and now it works.

---

### Post by fwrun2011 on 2015-04-03
Now, this is very strange. A couple days ago I installed a new video card. Upgraded from NVidia GeForce 9800 GTX+ 512 to GeForce GTX 750 TI 2Gig.
After much frustration, I got Ubuntu 14.04.2 working with NVidia 340.76 driver.
I installed Ubuntu 14.04.2 twice in two separate partitions on my system.
I installed Google Earth (current version) on one of the partitions, but now, when I go to the other partition - same version of Ubuntu (14.04.2), I am getting the errors while trying to install the library files.
I am installing the same libraries that mc4man listed, but now I get the warnings about missing dependencies.

I had originally listed the entire output from terminal in this post, but after doing that, I found that I had not yet installed LibreOffice Base on this Ubuntu install. When I tried to install Base, I got pretty much the same warnings about unmet dependencies. So I figure something is broken with this Ubuntu install. Perhaps I'll just do another re-install.

FW

---

