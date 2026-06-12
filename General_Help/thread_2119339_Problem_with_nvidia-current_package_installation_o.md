---
title: "Problem with nvidia-current package installation on Ubuntu 12.04.2"
date: 2013-02-23
forum: General Help
---

### Post by Lead Expression on 2013-02-23
Hi all,
I have a laptop Asus 1015pn and I made a fresh Ubuntu 12.04.2 installation and I am trying to install the softwares needed for graphic card switching as per this thread.
[http://ubuntuforums.org/showthread.php?t=1677780](http://ubuntuforums.org/showthread.php?t=1677780)
However, I have a problem with nvidia-current package installation. This is the error I got since the first boot:
```
sudo apt-get install nvidia-current nvidia-settings
Reading package lists... Done
Building dependency tree        
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 nvidia-current : Depends: xorg-video-abi-11
                  Depends: xserver-xorg-core (>= 2:1.10.99.901)
E: Unable to correct problems, you have held broken packages.
```

I tried both to force nvidia-current package installation downloading the .deb from the Internet and installing xorg-video-abi-11 but both solutions had catastrophic results.
Does anyone know how to fix this problem? I found some bugs but I cannot find neither workaronds nor fixing actions to perform. It seems a problem in the nvidia-current package dependencies but... I cannot fix it.

Thank you very much

---

### Post by bogan on 2013-02-24
Hi!, **Lead Expression,**

I had a similar problem trying to install the nvidia driver with a clean install of 12.04.2, and got a warning from Synaptic that a lot of '.... -lts-quantal files and backports would be un-installed; so I backed off and installed the 304.xx driver from nvidia.com Downloads without any problems.

There are several more posts in other forums quoting the same problem with xorg-video-abi-11 and the lack of updates for it.

Chao!, **bogan.**

---

### Post by Lead Expression on 2013-02-24
> **bogan said:**
> Hi!, **Lead Expression,**

I had a similar problem trying to install the nvidia driver with a clean install of 12.04.2, and got a warning from Synaptic that a lot of '.... -lts-quantal files and backports would be un-installed; so I backed off and installed the 304.xx driver from nvidia.com Downloads without any problems.

There are several more posts in other forums quoting the same problem with xorg-video-abi-11 and the lack of updates for it.

Chao!, **bogan.**

Ok, it finally seems to work with the currently available 310.xx driver! The problem is that nvidia driver is not installed for dpkg so I cannot install any package depending on nvidia-current (namely: bumblebee). How can I fix this? Note: I don't have the warnings you are speaking about...

---

### Post by bogan on 2013-02-25
Hi!,** Lead Expressio**n,

 > How can I fix this?Sorry, I do not have an answer; as far as i know you have to use Bumblebee to install the nvidia driver.

Chao!, **bogan**.

---

