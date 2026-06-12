---
title: "Graphics Drivers PPA not updated to support 20.10 Groovy?"
date: 2021-03-22
forum: General Help
---

### Post by ULAMSS5 on 2021-03-22
It started off with trying to install CUDA... leading to some missing dependencies or outdated packages which couldn't get fixed with `--fix-broken`.

So ```
sudo apt purge nvidia*
``` and ```
sudo apt purge cuda*
```, and now I can't install drivers.

```

sudo apt install nvidia-driver-460
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
 nvidia-driver-460 : Depends: libnvidia-gl-460 (= 460.32.03-0ubuntu1) but 460.67-0ubuntu0~0.20.10.1 is to be installed
                     Depends: libnvidia-compute-460 (= 460.32.03-0ubuntu1) but 460.67-0ubuntu0~0.20.10.1 is to be installed
                     Depends: libnvidia-extra-460 (= 460.32.03-0ubuntu1) but 460.67-0ubuntu0~0.20.10.1 is to be installed
                     Depends: libnvidia-decode-460 (= 460.32.03-0ubuntu1) but 460.67-0ubuntu0~0.20.10.1 is to be installed
                     Depends: libnvidia-encode-460 (= 460.32.03-0ubuntu1) but 460.67-0ubuntu0~0.20.10.1 is to be installed
                     Depends: xserver-xorg-video-nvidia-460 (= 460.32.03-0ubuntu1) but 460.67-0ubuntu0~0.20.10.1 is to be installed
                     Depends: libnvidia-cfg1-460 (= 460.32.03-0ubuntu1) but 460.67-0ubuntu0~0.20.10.1 is to be installed
                     Depends: libnvidia-ifr1-460 (= 460.32.03-0ubuntu1) but 460.67-0ubuntu0~0.20.10.1 is to be installed
                     Depends: libnvidia-fbc1-460 (= 460.32.03-0ubuntu1) but 460.67-0ubuntu0~0.20.10.1 is to be installed
                     Recommends: nvidia-prime (>= 0.8) but it is not going to be installed
                     Recommends: libnvidia-compute-460:i386 (= 460.32.03-0ubuntu1)
                     Recommends: libnvidia-decode-460:i386 (= 460.32.03-0ubuntu1)
                     Recommends: libnvidia-encode-460:i386 (= 460.32.03-0ubuntu1)
                     Recommends: libnvidia-ifr1-460:i386 (= 460.32.03-0ubuntu1)
                     Recommends: libnvidia-fbc1-460:i386 (= 460.32.03-0ubuntu1)
                     Recommends: libnvidia-gl-460:i386 (= 460.32.03-0ubuntu1)
E: Unable to correct problems, you have held broken packages.

```

which led me to [https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa)

```

sudo add-apt-repository ppa:graphics-drivers/ppa
sudo apt-get update

```

```

Hit:1 [http://mirror.internode.on.net/pub/ubuntu/ubuntu](http://mirror.internode.on.net/pub/ubuntu/ubuntu) groovy InRelease
Hit:2 [http://mirror.internode.on.net/pub/ubuntu/ubuntu](http://mirror.internode.on.net/pub/ubuntu/ubuntu) groovy-updates InRelease
Hit:3 [http://mirror.internode.on.net/pub/ubuntu/ubuntu](http://mirror.internode.on.net/pub/ubuntu/ubuntu) groovy-backports InRelease
Hit:4 [http://mirror.internode.on.net/pub/ubuntu/ubuntu](http://mirror.internode.on.net/pub/ubuntu/ubuntu) groovy-security InRelease
Ign:5 [http://dl.google.com/linux/chrome-remote-desktop/deb](http://dl.google.com/linux/chrome-remote-desktop/deb) stable InRelease
Ign:6 [https://developer.download.nvidia.com/compute/cuda/repos/ubuntu2004/x86_64](https://developer.download.nvidia.com/compute/cuda/repos/ubuntu2004/x86_64)  InRelease
Hit:7 [https://developer.download.nvidia.com/compute/cuda/repos/ubuntu2004/x86_64](https://developer.download.nvidia.com/compute/cuda/repos/ubuntu2004/x86_64)  Release
Hit:9 [http://neurodeb.pirsquared.org](http://neurodeb.pirsquared.org) data InRelease                      
Ign:10 [http://ppa.launchpad.net/danielrichter2007/grub-customizer/ubuntu](http://ppa.launchpad.net/danielrichter2007/grub-customizer/ubuntu) groovy InRelease
Hit:11 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) groovy InRelease              
Hit:12 [http://neurodeb.pirsquared.org](http://neurodeb.pirsquared.org) xenial InRelease                   
Ign:13 [https://packagecloud.io/github/git-lfs/ubuntu](https://packagecloud.io/github/git-lfs/ubuntu) groovy InRelease    
Ign:14 [http://ppa.launchpad.net/deadsnakes/ppa/ubuntu](http://ppa.launchpad.net/deadsnakes/ppa/ubuntu) groovy InRelease   
Hit:15 [http://dl.google.com/linux/chrome-remote-desktop/deb](http://dl.google.com/linux/chrome-remote-desktop/deb) stable Release
Err:17 [https://packagecloud.io/shiftkey/desktop/any](https://packagecloud.io/shiftkey/desktop/any) any InRelease       
  429  Too Many Requests [IP: 54.176.179.107 443]
Ign:18 [http://ppa.launchpad.net/eugenesan/ppa/ubuntu](http://ppa.launchpad.net/eugenesan/ppa/ubuntu) groovy InRelease   
Err:19 [https://packagecloud.io/github/git-lfs/ubuntu](https://packagecloud.io/github/git-lfs/ubuntu) groovy Release
  404  Not Found [IP: 54.176.179.107 443]
Hit:20 [http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu](http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu) groovy InRelease
Err:21 [http://ppa.launchpad.net/danielrichter2007/grub-customizer/ubuntu](http://ppa.launchpad.net/danielrichter2007/grub-customizer/ubuntu) groovy Release
  404  Not Found [IP: 91.189.95.85 80]
Err:22 [http://ppa.launchpad.net/deadsnakes/ppa/ubuntu](http://ppa.launchpad.net/deadsnakes/ppa/ubuntu) groovy Release
  404  Not Found [IP: 91.189.95.85 80]
Err:23 [http://ppa.launchpad.net/eugenesan/ppa/ubuntu](http://ppa.launchpad.net/eugenesan/ppa/ubuntu) groovy Release
  404  Not Found [IP: 91.189.95.85 80]
Reading package lists... Done
E: The repository 'https://packagecloud.io/github/git-lfs/ubuntu groovy Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://ppa.launchpad.net/danielrichter2007/grub-customizer/ubuntu groovy Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://ppa.launchpad.net/deadsnakes/ppa/ubuntu groovy Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://ppa.launchpad.net/eugenesan/ppa/ubuntu groovy Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.

```

I saw some very old StackOverflow threads where one of the solutions was to simply open each file and rename "Groovy" to an older version, in this case "Focal", but all the comments below that "Solution" was warning against it.

Attempting Ubuntu's "Software & Updates" program, "Additional Drivers", spit out the same missing dependencies error.

Is this simply a problem of the PPA not being updated for 20.10? Or does my Ubuntu install have more serious problems?

---

### Post by CelticWarrior on 2021-03-22
All the listed errors are about other PPAs, not the graphics drivers one (that shouldn't be needed anyway). Fix that and fully update your system before anything else.

---

