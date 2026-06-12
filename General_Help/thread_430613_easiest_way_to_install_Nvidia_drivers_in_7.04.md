---
title: "easiest way to install Nvidia drivers in 7.04?"
date: 2007-05-02
forum: General Help
---

### Post by Martinbr on 2007-05-02
What is the easiest way to install Nvidia drivers in ubuntu 7.04?

I tried to install them along with beryl but that messed up ubuntu big time. 

I have also followed this guide :
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Graphics_Driver_.28NVIDIA.29](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Graphics_Driver_.28NVIDIA.29)

But I dont think its working. I dont see the nvidia logo, and the screen seem's kinda 'blurry'. 

Anything else i could try?

---

### Post by moon_dog on 2007-05-02
the easiest way would probably be to use tseliot's [ENVY]("http://www.albertomilone.com/nvidia_scripts1.html") script.  it installs the drivers and sets up your xorg.conf according to your system.

---

### Post by Martinbr on 2007-05-02
Thanks alot im gonna try that right away.

---

### Post by smartbei on 2007-05-02
I think an easier way by far is to go System -> Administration -> Restricted Drivers Manager and enable the nvidia driver.

---

### Post by GoBieN on 2007-05-02
> **smartbei said:**
> I think an easier way by far is to go System -> Administration -> Restricted Drivers Manager and enable the nvidia driver.

Unless it says "You do not need restricted drivers for your hardware" while i have a nvidia 7200 go in my laptop !

The nvidia-glx packet didnt work either, so i ran the script from the nvidia site. works fine, but i have to rerun the script every time i get an kernel upgrade.

Was thinking about trying envy, but i can't install the .deb, can't install dependecy xserver-xorg-dev. And indeed its not in the repo's ...

---

### Post by NeoChaosX on 2007-05-02
If you need the latest nVidia driver, install nvidia-glx-new.

---

### Post by syxbit on 2007-05-02
sudo apt-get install nvidia-glx-new
works best for 7th generation cards

---

### Post by Martinbr on 2007-05-02
Well the envy script really messed up everything. Had to reinstall Ubuntu. Ill try the 
sudo apt-get install nvidia-glx-new

---

### Post by Martinbr on 2007-05-02
Now i tried the 
sudo t
apt-get install nvidia-glx-new
and im not sure if it worked, I dont know if it worked. I dont get the nvidia logo when booting. Am i supposed to get that?

---

### Post by syxbit on 2007-05-02
after that run "sudo nvidia-xconfig"
i think that's what you type
it will basically tell xorg to use the nvidia driver
just type nvidia and tab complete and you should see an option that looks like -xconfig

then reboot.
to test that it's working load up the settings by typing nvidia-settings
if you see a bunch of options, then it worked.

if that doesn't work, you can basically do it manually, and do "sudo gedit /etc/X11/xorg.conf" and change the line 
driver "nv" 
to 
driver "nvidia"

---

