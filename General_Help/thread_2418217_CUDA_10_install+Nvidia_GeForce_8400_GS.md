---
title: "CUDA 10 install+Nvidia GeForce 8400 GS"
date: 2019-05-03
forum: General Help
---

### Post by bcramer2 on 2019-05-03
Hi, I was trying to install CUDA v.10 as root in Ubuntu18.4-x64b.  It instaled in /usr/local, but it isn't working. Only for info: CUDA is required by a Molec.Dynamics software.

Installations sequence:

------------------
sudo apt-get install build-essential dkms
sudo apt-get install freeglut3 freeglut3-dev libxi-dev libxmu-dev
------------
  NVidia drive
  	 	 	 	   [INDENT]sudo apt update
sudo ubuntu-drivers autoinstall
sudo reboot           
[/INDENT]  CUDA
  	 	 	 	   sudo dpkg -i cuda-repo-ubuntu1804-10-1-local-10.1.105-418.39_1.0-1_amd64.deb  

 sudo apt-key add /var/cuda-repo-10-1-local-10.1.105-418.39/7fa2af80.pub

 sudo apt-get install cuda-libraries-10-1

After installation test:
  	 	 	 	   
**nvidia-smi**

  
**error massage**:NVIDIA-SMI has failed because it couldn't communicate with the NVIDIA driver. Make sure that the latest NVIDIA driver is installed and running.

I also tryed the following recommendation:

  	 	 	 	   
"However, if the nvidia driver it installs is 390 (if you use 18.04), you need to manually install a newer version of nvidia driver. Why? Because we are going to use cuda 10.x, and it need newer nvidia driver.

 [INDENT]sudo add-apt-repository ppa:graphics-drivers
sudo apt-get update
sudo apt-get install nvidia-driver-418"

Nothing worked and I tried to fix broken but now not only Cuda is not workin as Mozilla Firefox is hanging all the time.
[/INDENT] Errors were encountered while processing: sudo apt-get install -f

  /var/cuda-repo-10-1-local-10.1.105-418.39/./cuda-driver-dev-10-1_10.1.105-1_amd64.deb

  /var/cuda-repo-10-1-local-10.1.105-418.39/./cuda-nvml-dev-10-1_10.1.105-1_amd64.deb

 E: Sub-process /usr/bin/dpkg returned an error code (1)
Finaly I aplied th command bellow to clean-up the installations but I still have problems.

  	 	 	 	   
installed.LC_MESSAGES=C dpkg-divert --list '*nvidia-340*' | sed -nre 's/^diversion of (.*) to .*/\1/p' | xargs -rd'\n' -n1 --  
 sudo dpkg-divert --remove
  check: cat /proc/driver/nvidia/version
cat: /proc/driver/nvidia/version: No such file or directory
So, the driver nvidia-340 was uninstalled.

I probably will have to uninstall and reinstall Ubuntu18.4 but before I do that I need to learn how to install CUDA and make it work. 

Any help is wellcome.
Thank you
Bruno

PS. Maybe my NVidia Hardware/Driver is incompatible with CUDA?If yes,  is there an older version of CUDA that could work with my NVidia Graphic Card?

---

### Post by Frogs Hair on 2019-05-03
> [COLOR=#000000]PS. Maybe my NVidia Hardware/Driver is incompatible with CUDA?If yes, is there an older version of CUDA that could work with my NVidia Graphic Card?[/COLOR]

That is likely because an 8400 GS which I had used was/is an entry level card. Supported technologies only include SLI. I would think it would use the 340 or 390 proprietary driver. The card does include 8 to 16 cuda cores depending on build were as the newer cards have 128 +.

[https://www.geforce.com/hardware/desktop-gpus/geforce-8400-gs/specifications](https://www.geforce.com/hardware/desktop-gpus/geforce-8400-gs/specifications)

---

### Post by bcramer2 on 2019-05-03
I will look for a new NVidia Graphic Card that may solve this issue.
Thank you.

---

### Post by Frogs Hair on 2019-05-03
It doesn't have to be new just supported. It can be new old-stock or even used.

 [https://en.wikipedia.org/wiki/CUDA#GPUs_supported](https://en.wikipedia.org/wiki/CUDA#GPUs_supported)

---

