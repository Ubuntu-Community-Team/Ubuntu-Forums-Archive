---
title: "Stuck in Login Loop in 14.04"
date: 2015-10-06
forum: General Help
---

### Post by nfmcclure on 2015-10-06
I just updated my Ubuntu 14.04 system with a Nvidia Geforce 960M video card.  After a reboot, I entered a repeated login screen (asks me to login, over and over...). The steps that got me here, were:

[LIST=1]
[*]I started with a clean, working Ubuntu 14.04 install.  I updated/upgraded everything.
[*]I have a CUDA capable card (geforce 960m) and went about installing CUDA via these commands:
[/LIST]

```

sudo apt-get --purge remove nvidia*
sudo su
echo nouveau >> /etc/modprobe.d/blacklist.conf
cd ~/Downloads
mkdir nvidia_installer
cd nvidia_installer
wget http://developer.download.nvidia.com/compute/cuda/7_0/Prod/local_installers/cuda_7.0.28_linux.run
chmod +x cuda_7.0.28_linux.run
./cuda_7.0.28_linux.run -extract=~/Downloads/nvidia_installer

```

Then I 'sudo gedit /etc/default/grub' and changed: GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"

```

sudo init 3
cd ~/Downloads/nvidia_installer
sudo ./NVIDIA-Linux-x86_64-346.46.run
sudo modprobe nvidia
sudo ./cuda-linux64-rel-7.0.28-19326674.run
sudo ./cuda-samples-linux-7.0.28-19326674.run
sudo init 5

```

Then, I installed my 960m driver, Nvidia-352 via:

```

sudo add-apt-repository ppa:xorg-edgers/ppa
sudo apt-get update
sudo apt-get install nvidia-352 nvidia-prime
sudo add-apt-repository -r ppa:xorg-edgers/ppa

```

    3.  Then I rebooted and checked some test files and it appeared that CUDA was working.
    4.  Today, there was an update pushed that required a reboot and now I'm stuck in a repeated login loop. [EDIT] I believe the updates had to do with updating the linux headers and chrome plugins, plus some more things.  I would also love to know how to 'roll-back' updates applied on a certain date so I can see exactly what updates were applied. [/EDIT]

I've tried looking at the permissions on .Xauthority, and they seem correct.  I've even deleted .Xauth* and rebooted and still can't login.

Any ideas on what happened? And what I can do?

Thanks.

---

### Post by nfmcclure on 2015-10-07
Update:

I've investigated the .Xauthority file and it appears to have the right permissions, via:

[http://askubuntu.com/questions/314259/login-loop-ubuntu-12-04](http://askubuntu.com/questions/314259/login-loop-ubuntu-12-04)

But in an answer there, they talk about a ~/.dmrc file.

```

$ ls -la ~/.dmrc
ls: cannot access /home/user/.dmrc: No such file or directory

```

Where did my .dmrc file go?  Is this the problem, and if so, how do I get it back?

---

