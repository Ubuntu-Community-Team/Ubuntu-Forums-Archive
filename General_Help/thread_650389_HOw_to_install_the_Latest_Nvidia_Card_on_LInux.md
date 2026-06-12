---
title: "HOw to install the Latest Nvidia Card on LInux"
date: 2007-12-26
forum: General Help
---

### Post by bigbrovar on 2007-12-26
Yeah i know that the restricted manager in Ubuntu would offer to install the Latest Nvidia Driver for u .. all in a click of a botton .. the problem is that Nvidia just released a new driver for the 8 series which correct most of the problem associated with the old drivers especially concerning compiz ..but i dont know the best way to install the driver NVIDIA-Linux-x86-169.07-pkg1.run* since its not a deb file and i dont want to mess up my xorg 

my hard ware 
Sony Vaio FZ21e 
Nvidia Geforce 8400 GT
2GB RAM
Core 2 duo 2.0 ghz


is envy any good should i use it

---

### Post by taurus on 2007-12-26
You can backup your /etc/X11/xorg.conf before you install the new nVidia driver.

Press <Ctrl><Alt>F2 and log in with your username and password.  Then run

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
sudo /etc/init.d/gdm stop
sudo sh NVIDIA-Linux-x86-169.07-pkg1.run
(Assuming you are in the same directory where NVIDIA-Linux-x86-169.07-pkg1.run is.)
sudo /etc/init.d/gdm start
```

---

### Post by bigbrovar on 2007-12-26
Thanks for ur reply i guess i have to use a second computer inorder to be able to see what u have typed.. beside hope i wont have any dependency issues .. or should i use envy.. am just scared cus i dont want to have to reinstall my system because of X failure 

Edit .. also do i have to install the former driver the one in the repo before installing this one or should i just proceed to install -- my system is a fresh install

---

### Post by taurus on 2007-12-26
Does envy come with the latest driver?  You can reconfigure X server again with one line if there is something wrong with it while trying to install the latest version of nvidia driver.

---

### Post by bigbrovar on 2007-12-26
yeah it does .. but is envy really good for installing drivers ? besides are there any dependency i need to have or any repo i need to enable be i start to compile
i.e do i need to enable the backport repo

---

### Post by astoltz on 2007-12-26
You should change back to the built-in drivers first and uninstall the restricted modules (assuming you're not using them for wireless).  Edit xorg.conf and change the "nvidia" line back to "nv" (or maybe you can do it by disabling the proprietary drivers in the restricted drivers manager - don't know it that works for sure).  Then re-boot and remove the restricted modules: ```
sudo apt-get remove --purge linux-restricted-modules
``` Then you should be good to go with the commands that taurus outlined above.  There won't be any dependency problems.

---

### Post by bigbrovar on 2007-12-26
thanks man but if i dis able the restricted modules would i still be able to enable them back cus i need it for my wifi driver to work.. also when i tried the command that taurus gave me i got something like this "sh cant open NVIDIA-Linux-x86-169.07-pkg1.run"

what should i do

---

### Post by articpenguin on 2007-12-26
try envy
[http://albertomilone.com/nvidia_scripts1.html]("http://albertomilone.com/nvidia_scripts1.html")

---

### Post by astoltz on 2007-12-26
Yeah, if you need the WiFi drivers, you've got to keep the restricted modules package.  In that case, just change to the "nv" driver, re-boot and then run the NVIDIA installer.  I just like to un-install the restricted modules to be on the safe side but the NVIDIA installer should be OK without.  I can't comment on envy as I've never tried that method.> when i tried the command that taurus gave me i got something like this "sh cant open NVIDIA-Linux-x86-169.07-pkg1.run"  You've got to be in the same directory as the NVIDIA file or give it the path to the file:  sh /path/to/file/NVIDIA-Linux-x86-169.07-pkg1.run

---

### Post by bigbrovar on 2007-12-26
bro i dont want to appear naggy but my first experience with envy left me with a broken system.. i just reinstalled that system and am kind of wary of  it.. u can give me a guide on how to use it on gutsy i would be glad ... i would also be glad if anybody can give me a guide- or a link to one - on how i can install the new Nvidia card on gutsy..please i just want a perfect system on ubuntu .. thats all :)

---

### Post by PmDematagoda on 2007-12-26
I have used Envy and it was really reliable, it did break my system once as well but it was easily fixable so if the same happens to you, myself or someone else will help you out in solving that issue.

---

### Post by bigbrovar on 2007-12-26
thanks man i think i would try and use envy again.. but one more thing.. what steps should i take if i want to use it

---

### Post by bigbrovar on 2007-12-26
please how do i use envy .. i dont want to make any mistake by doing soumething stupid

---

### Post by bigbrovar on 2007-12-26
I tried using Envy as advised but when i tired to use it to install the nvidia drive i got this error report...        

[PHPpython pulse.py nvidia 
root@bigbrovar-laptop:/usr/share/envy# python pulse.py nvidia
Envy - Version 0.9.9
Ubuntu Gutsy 32bit
Your graphic card has been detected as a GeForce 8400M GT
Your graphic card is supported by the latest driver
OK: All the packages are installed
Checking the Dependencies for the New Method
ENVY: The following packages are not installed:
libqt3-mt-dev
kernel-wedge
rpm
sharutils
libgtk2.0-dev
libxxf86misc-dev
libxtst-dev
libxxf86vm-dev
libxinerama-dev

ENVY: attempting to install the packages
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libqt3-mt-dev: Depends: libcupsys2-dev but it is not going to be installed
                 Depends: libqt3-mt (= 3:3.3.8really3.3.7-0ubuntu11) but 3:3.3.8really3.3.7-0ubuntu11.1 is to be installed
E: Broken packages
ENVY ERROR: The following packages cannot be installed:
libqt3-mt-dev
kernel-wedge
rpm
sharutils
libgtk2.0-dev
libxxf86misc-dev
libxtst-dev
libxxf86vm-dev
libxinerama-dev][/PHP]

THIS was exactly why i asked for a guide on how to use envy.. and i know now from experience that once i restart xserver would fail.. and i would be back to square one and since i dont have a internet connection at home (am writing from an internet cafe) i would have no option than to reinstall my system..
really am startign to lose faith in this Ubuntu thing..  this would be the 5th time am reinstall my system in a week due to one instability or the other... its very sad .. i have searched the web for a solution ..nothing .... damn 
 all i want is to install a damn display driver and am getting to spend hours online reinstalling me system and waiting without end for a reply... and there say windows is unstable ..

---

### Post by bigbrovar on 2007-12-26
oh well i guess i have to reinstall my system again an wait till the new driver in the the repos

---

### Post by bodhi.zazen on 2007-12-26
Well, first I do no t think you need to re-install.

Second you need to remove the nvidia-glx package. Open synaptic and search for it -> remove

Next you need to make the nvidia script executable :

```
sudo chmod a+x NVIDIA-Linux-x86-169.07-pkg1.run
```

Then install the depencencies :

```
sudo apt-get install build-essential linux-headers-`uname -r`
```
 *Note ; those are bac-tics ( `) , by the number 1 and not single ' in `uname -r`

Then drop out of X, see taurus's post :) (thanks taurus)

Install with ```
sudo sh NVIDIA
```

Re-start X

```
sudo /etc/init.d/gdm start
```

---

### Post by bigbrovar on 2007-12-27
Thanks mate.. i have been able to install the driver .. finally following ur guide and some intructions at the Nvidia forums .. however am having problem activating compiz  if i try to run it from system/preference/appearance/virtual effect . it would offer to download another driver from my restricted driver module which i have installed so that it wont confilct with the new nvidia driver... also my wireless has stopped working after i installed the nvidia driver...is there anything i can do ...

---

