---
title: "[SOLVED] ATI Driver Problem"
date: 2008-03-19
forum: General Help
---

### Post by KraftSingle on 2008-03-19
I have been running into a wall here for a while trying to set up this ATI X300 SE driver. The auto-detect settings work ok, but they don't support 3D. Also, not sure if this is related, but when multi-tasking (3 programs or so) Ubuntu has been frequently freezing.

When I used Envy to install the 8.3 driver everything seemed to be working perfectly. Later I noticed that Envy had created a new kernal and totally wiped out all sound. Long story short, I just reinstalled Ubuntu and here I am back where I started.

---

### Post by danwood76 on 2008-03-19
Envy is nasty.

This guide is a lot better and is very easy:
[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Method_2:_Install_the_Catalyst_8.3_Driver_Manually](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Method_2:_Install_the_Catalyst_8.3_Driver_Manually)

How much RAM do you have on your PC?
The slowing when a few apps are open may mean you are running low and it is swapping a  lot of your RAM.

---

### Post by KraftSingle on 2008-03-19
Low ram... 512. I guess what I'm trying to say it is goes from fine to totally frozen really easily. While with Windows it seems to just gets progressively slower.

I'll try that, get back to you.

---

### Post by danwood76 on 2008-03-19
Thats probably due to it utilising swap.
Small memory is very cheap these days, 512mb of RAM is nothing and will speed you up no end.

---

### Post by KraftSingle on 2008-03-19
I have tried this exact guide before and it failed, but I will give it another shot when I have time I guess.

---

### Post by danwood76 on 2008-03-19
I will help you through it if you get any problems.

---

### Post by KraftSingle on 2008-03-19
Hit a snag already... I don't know what to do, the guide doesn't cover this.
```
mark@mark-desktop:~$ sudo sh /home/mark/Downloads/ati-driver-installer-8-3-x86.x86_64.run --buildpkg Ubuntu/gutsy
Created directory fglrx-install.id6261
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.471...
==================================================
 ATI Technologies Linux Driver Installer/Packager 
==================================================
Generating package: Ubuntu/gutsy
./packages/Ubuntu/ati-packager.sh: 311: sh -c '/usr/sbin/synaptic --set-selections --non-interactive --hide-main-window < /tmp/fileK3isXc': not found
Unable to install dpkg-dev and build-essential.  Please manually install and try again.
Removing temporary directory: fglrx-install.id6261
```

Thanks for all your help so far :)

---

### Post by danwood76 on 2008-03-19
run
```

sudo apt-get update
sudo apt-get install dpkg-dev build-essential fakeroot dh-make debhelper debconf libstdc++5 dkms

```

then try running that install line again.
If you get errors post the entire output from those first 2 right through.

---

### Post by KraftSingle on 2008-03-19
Scratch that post...

---

### Post by KraftSingle on 2008-03-19
I went through the installation successfully, everything seems to check out. I had been testing with the Chess 3D mode, but I think it is not working right. Downloading some games to test it out at the moment.

> sudo apt-get update
sudo apt-get install dpkg-dev build-essential fakeroot dh-make debhelper debconf libstdc++5 dkms did the trick. Should be put on the Wiki for sure. Thanks much friend.

---

