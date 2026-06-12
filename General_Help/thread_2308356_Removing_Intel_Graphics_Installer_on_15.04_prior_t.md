---
title: "Removing Intel Graphics Installer on 15.04 prior to 15.10 upgrade?"
date: 2016-01-02
forum: General Help
---

### Post by neu5eeCh on 2016-01-02
The best information I could find was this:

#source [http://theclonker.de/?p=89](http://theclonker.de/?p=89)
sudo sh -c 'echo "\nPackage: *\nPin: release a=trusty*\nPin-Priority: 1001\n\nPackage: *\nPin: origin download.01.org\nPin-Priority: -100\n" > /etc/apt/preferences.d/intel-removal'
sudo apt-get dist-upgrade
sudo rm /etc/apt/preferences.d/intel-removal
sudo rm /etc/apt/sources.list.d/intellinuxgraphics.list*
sudo apt-get update
echo "\n\n\n\n\n\n Remember to remove the i915-3.6-3.5-dkms and intel-linux-graphics-installer packages with \n\n sudo apt-get purge i915-3.6-3.5-dkms intel-linux-graphics-installer "

From here:

[https://gist.github.com/phdelodder/b28e8df770a6bc020aab#file-remove-intel-driver-sh-L1](https://gist.github.com/phdelodder/b28e8df770a6bc020aab#file-remove-intel-driver-sh-L1)

Can anyone advise as to what I should change in the commands above as it pertains to 15.04? For instance, **[COLOR=#ff0000]release a=trusty[/COLOR]** to **[COLOR=#ff0000]release a=vivid[/COLOR]**, etc...

---

### Post by neu5eeCh on 2016-01-02
Okay, just to get the ball rolling, I'll see if I can get this right myself. Please correct if anyone sees anything wrong. I listed the dkms version I was running:

**dpkg --list *dkms**

||/ Name                        Version            Architecture       Description
+++-===========================-==================-==================-===========================================================
ii  dkms                        2.2.0.3-2ubuntu3.3 all                Dynamic Kernel Module Support Framework
ii  i915-4.0.4-3.19-dkms
[U][B]
Then changed the commands[/B][/U] (**[COLOR=#ff0000]in red[/COLOR]**):

sudo sh -c 'echo "\nPackage: *\nPin: release a=**[COLOR=#ff0000]vivid[/COLOR]***\nPin-Priority:  1001\n\nPackage: *\nPin: origin download.01.org\nPin-Priority: -100\n"  > /etc/apt/preferences.d/intel-removal'
sudo apt-get dist-upgrade
sudo rm /etc/apt/preferences.d/intel-removal
sudo rm /etc/apt/sources.list.d/intellinuxgraphics.list*
sudo apt-get update
echo "\n\n\n\n\n\n Remember to remove the **[COLOR=#ff0000]i915-4.0.4-3.19-dkms[/COLOR]** and  intel-linux-graphics-installer packages with \n\n sudo apt-get purge **[COLOR=#ff0000]i915-4.0.4-3.19-dkms[/COLOR]** intel-linux-graphics-installer "

So... what could possibly go wrong? Look good? Yes? No?

---

### Post by neu5eeCh on 2016-01-02
Okay, after some review, I think the better way to do this is (as posted by me [here]("http://askubuntu.com/questions/685209/uninstall-intel-graphics-for-linux-1-20-on-ubuntu-15-04/716129#716129")):

Find out what dkms package  you're using: 

  dpkg --list *dkms
  You should get something like this:

  [B]
ii  i915-4.0.4-3.19-dkms[/B]

  
So if, like me, you're using 15.04 (vivid), then you're probably using the same dkms package. And so:

  Open a new Terminal (CTRL+Alt+T) and execute
  
gksudo gedit /etc/apt/preferences.d/intel-removal
  
Paste this code in the File and save it (don't forget to change the Ubuntu version if you're not using **vivid**):
      
> Package: *
    Pin: release a=vivid*
    Pin-Priority: 1001

    Package: *
    Pin: origin download.01.org
    Pin-Priority: -100
  
And then (don't forget to change the **dkms package** below if it's not the same):
  
sudo apt-get dist-upgrade

sudo rm /etc/apt/preferences.d/intel-removal

sudo rm /etc/apt/sources.list.d/intellinuxgraphics.list*

sudo apt-get update

sudo apt-get purge i915-4.0.4-3.19-dkms intel-linux-graphics-installer

---

