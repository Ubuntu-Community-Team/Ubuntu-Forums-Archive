---
title: "Need to add Nvida repository"
date: 2019-03-21
forum: General Help
---

### Post by Autodave on 2019-03-21
I have an RTX 2070 that I need to install a driver for to get me off of this 640 x 480 screen!  I have tried adding the repository but I get an unknown error.  Can someone offer assistance?

---

### Post by Autodave on 2019-03-21
Just tried installing the driver from Nvidia's site and I get this:
ERROR: You appear to be running an X server; please exit X before            
         installing.  For further details, please see the section INSTALLING   
         THE NVIDIA DRIVER in the README available on the Linux driver         
         download page at [www.nvidia.com](www.nvidia.com).


How do I do that?

---

### Post by poorguy on 2019-03-21
Here's what I did and sometimes it loaded the ***Nvidia Driver*** and sometimes it didn't.

[COLOR=#000000]**sudo apt-get purge nvidia***

Press Enter and Enter password.

**sudo add-apt-repository ppa:graphics-drivers/ppa**

Press Enter

**sudo apt-get update**

Press Enter

**sudo apt-get install nvidia-driver-410**

Press Enter 

When this is finished then close terminal and restart computer.

If the Nvidia driver installed it will show an output by running this command.

**lsmod | grep nvidia**
[/COLOR]

---

### Post by #&amp;thj^% on 2019-03-21
poorguy has the correct method for a preferred install. :)
I'm just stumped seeing Autodave installing the driver from nvidia.com....:)
   How I do it, Save the file into your home directory. Example:

 ```
ls
    NVIDIA-Linux-x86_64-410.73.bin
```

    Install Prerequisites. The following prerequisites are required to compile and install Nvidia driver:
```

     sudo dpkg --add-architecture i386
     sudo apt update
     sudo apt install build-essential libc6:i386
```

    Next step is to disable the default nouveau Nvidia driver. Follow this guide on how to disable the default Nouveau Nvidia driver.
```
 sudo bash -c "echo blacklist nouveau > /etc/modprobe.d/blacklist-nvidia-nouveau.conf"
 sudo bash -c "echo options nouveau modeset=0 >> /etc/modprobe.d/blacklist-nvidia-nouveau.conf"
```
Confirm the content of the new modprobe config file:

```
 cat /etc/modprobe.d/blacklist-nvidia-nouveau.conf
blacklist nouveau
options nouveau modeset=0
```


    Make sure you reboot your system before you proceed to the next step.
    In order to install new Nvidia driver we need to stop the current display server. The easiest way to do this is to change into runlevel 3 using the telinit command.(I use key combo..<Ctrl+Alt=F2>) After executing the following linux command the display server will stop, therefore make sure you save all your current work ( if any ) before you proceed:
```

     sudo telinit 3
```

    Hit CTRL+ALT+F2 and login with your username and password to open a new TTY1 session.
    To start installation of Nvidia driver execute the following linux command and follow the wizard:

    ```
bash NVIDIA-Linux-x86_64-410.73.bin
```
Or the Version you d-loaded

    You now need to Accept License and follow the wizard to completed the installation. You may also be asked questions like:

    The distribution-provided pre-install script failed!
    Are you sure you want to continue? -> CONTINUE INSTALLATION
    Would you like to run the nvidia-xconfig utility? -> YES 

    The Nvidia driver is now installed.
    Reboot your system:

  
[list]
    [*]Configure NVIDIA X Server Settings. After reboot you should be able to start NVIDIA X Server Settings app from the Activities menu.

[*]Appendix
Error message:

[*]WARNING: Unable to find suitable destination to install 32-bit compatibility libraries

[*]Depending on your needs, this can be safely ignored. However, if you wish to install steam game platform this issue cannot be ignored. To resolve execute:[/list]
```

 sudo dpkg --add-architecture i386
 sudo apt update
 sudo apt install libc6:i386
```

**and re-run the nvidia driver installation.**

---

### Post by Autodave on 2019-03-21
That is telling me that it didn't install because it didn't find the public key.  I know what the key is, but I don't know how to install that.

---

### Post by Autodave on 2019-03-21
If there is a better way than d-ling it from Nvidia, please tell me!

I have tried adding the repository, but that keeps failing.

---

### Post by #&amp;thj^% on 2019-03-21
Show us the output for 
```
sudo apt update
```

---

### Post by Autodave on 2019-03-21
[code]Hit:1 http://us.archive.ubuntu.com/ubuntu bionic InRelease
Hit:2 http://us.archive.ubuntu.com/ubuntu bionic-updates InRelease             
Get:3 http://us.archive.ubuntu.com/ubuntu bionic-backports InRelease [74.6 kB] 
Get:4 http://security.ubuntu.com/ubuntu bionic-security InRelease [88.7 kB]    
Hit:6 http://linux.teamviewer.com/deb stable InRelease                         
Hit:8 http://ppa.launchpad.net/openrct2/nightly/ubuntu bionic InRelease        
Ign:7 https://launchpad.net/graphics-drivers/ubuntu bionic InRelease           
Get:5 http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu bionic InRelease [21.3 kB]
Err:9 https://launchpad.net/graphics-drivers/ubuntu bionic Release             
  Certificate verification failed: The certificate is NOT trusted. The certificate issuer is unknown.  Could not handshake: Error in the certificate verification. [IP: 2001:67c:1560:8003::8004 443]
Get:10 http://security.ubuntu.com/ubuntu bionic-security/main amd64 Packages [281 kB]
Err:5 http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu bionic InRelease
  The following signatures couldn't be verified because the public key is not available: NO_PUBKEY FCAE110B1118213C
Get:11 http://security.ubuntu.com/ubuntu bionic-security/main i386 Packages [208 kB]
Get:12 http://security.ubuntu.com/ubuntu bionic-security/universe amd64 Packages [128 kB]
Get:13 http://security.ubuntu.com/ubuntu bionic-security/universe i386 Packages [124 kB]
Get:14 http://security.ubuntu.com/ubuntu bionic-security/universe Translation-en [71.8 kB]
Reading package lists... Done                                     
W: http://launchpad.net/graphics-drivers/ubuntu/dists/bionic/InRelease: No system certificates available. Try installing ca-certificates.
W: http://launchpad.net/graphics-drivers/ubuntu/dists/bionic/Release: No system certificates available. Try installing ca-certificates.
E: The repository 'http://launchpad.net/graphics-drivers/ubuntu bionic Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: GPG error: http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu bionic InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY FCAE110B1118213C
E: The repository 'http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu bionic InRelease' is not signed.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.[code]

---

### Post by #&amp;thj^% on 2019-03-21
Cool Thanks!
Now
```
 sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys FCAE110B1118213C
```
post the return.

---

### Post by Autodave on 2019-03-21
$ sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys FCAE110B1118213C
[sudo] password for dave: 
Executing: /tmp/apt-key-gpghome.dufUgMUh0d/gpg.1.sh --keyserver keyserver.ubuntu.com --recv-keys FCAE110B1118213C
gpg: key FCAE110B1118213C: 12 signatures not checked due to missing keys
gpg: key FCAE110B1118213C: public key "Launchpad PPA for Graphics Drivers Team" imported
gpg: Total number processed: 1
gpg:               imported: 1

---

### Post by Autodave on 2019-03-21
That appears to have fixed the issue.  The 418 driver is installing now.  I HOPE that I will no longer have to look at a 640 x 480 screen.  The last time I had that size screen was about 30 years ago under Dos 5.0!

---

### Post by #&amp;thj^% on 2019-03-21
Great, now run:
```
sudo apt update

```
To see a list of Drivers run:
```
ubuntu-drivers devices
```
To auto-install:
```
sudo ubuntu-drivers autoinstall
```
To install a specific driver from the listed choices:
```
sudo apt install nvidia-graphics-drivers-410  ## Or -415
```

---

### Post by #&amp;thj^% on 2019-03-21
> **Autodave said:**
> I HOPE that I will no longer have to look at a 640 x 480 screen.  The last time I had that size screen was about 30 years ago under Dos 5.0!
I feel your pain, it's been about that long for me also.:lolflag:

---

### Post by Autodave on 2019-03-21
dave@dave-MS-7641:~$ sudo ubuntu-drivers autoinstall
[sudo] password for dave: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 nvidia-driver-418 : Depends: xserver-xorg-video-nvidia-418 (= 418.43-0ubuntu0~gpu18.04.1) but it is not going to be installed
                     Depends: libnvidia-cfg1-418 (= 418.43-0ubuntu0~gpu18.04.1) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
dave@dave-MS-7641:~$ sudo apt install nvidia-graphics-drivers-418
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package nvidia-graphics-drivers-418
dave@dave-MS-7641:~$ sudo apt install nvidia-graphics-drivers-415
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package nvidia-graphics-drivers-415
dave@dave-MS-7641:~$ sudo apt install nvidia-graphics-drivers-410
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package nvidia-graphics-drivers-410
dave@dave-MS-7641:~$

---

### Post by Autodave on 2019-03-21
None of my games are loading and the Nvidia control panel in Settings is not working either.

---

### Post by #&amp;thj^% on 2019-03-21
Houston we have a problem!
Did you update again after adding the key?
```
cat /etc/apt/sources.list.d/
```
and 
```
cat /etc/apt/sources.list
```
BTW I don't consider 418 ready for primetime yet.
Ah Ha
use:
```
sudo apt remove --purge nvidia*
```
Then use the correct syntax
```
sudo apt install nvidia-driver-418
```

---

### Post by Autodave on 2019-03-21
## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) bionic partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) bionic partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security main restricted
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security multiverse
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security multiverse
deb [http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu](http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu) bionic main #4096R/2388FF3BE10A76F638F80723FCAE110B1
# deb-src [http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu](http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu) bionic main
deb [http://launchpad.net/graphics-drivers/ubuntu](http://launchpad.net/graphics-drivers/ubuntu) bionic main
# deb-src [http://launchpad.net/graphics-drivers/ubuntu](http://launchpad.net/graphics-drivers/ubuntu) bionic main
da

After rebooting, I am back to 640 x 480.  Sigh.

---

### Post by Autodave on 2019-03-21
reverting back to the 415 driver now.  Nvidia control and games are inop.  I get a dydtem problem detected upon rebooting, but nothing there to identify the issue.

---

### Post by Autodave on 2019-03-21
Reverted back to 415.  Now, when running update I get this:
Ign:7 [https://launchpad.net/graphics-drivers/ubuntu](https://launchpad.net/graphics-drivers/ubuntu) bionic InRelease           
Hit:12 [http://ppa.launchpad.net/openrct2/nightly/ubuntu](http://ppa.launchpad.net/openrct2/nightly/ubuntu) bionic InRelease       
Err:11 [https://launchpad.net/graphics-drivers/ubuntu](https://launchpad.net/graphics-drivers/ubuntu) bionic Release            
  Certificate verification failed: The certificate is NOT trusted. The certificate issuer is unknown.  Could not handshake: Error in the certificate verification. [IP: 2001:67c:1560:8003::8003 443]
Reading package lists... Done                                                  
W: [http://launchpad.net/graphics-drivers/ubuntu/dists/bionic/InRelease:](http://launchpad.net/graphics-drivers/ubuntu/dists/bionic/InRelease:) No system certificates available. Try installing ca-certificates.
W: [http://launchpad.net/graphics-drivers/ubuntu/dists/bionic/Release:](http://launchpad.net/graphics-drivers/ubuntu/dists/bionic/Release:) No system certificates available. Try installing ca-certificates.
E: The repository 'http://launchpad.net/graphics-drivers/ubuntu bionic Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.

---

### Post by #&amp;thj^% on 2019-03-21
This darn bug has been around since September, I'm beginning to lose my trust with the Devs lately. ](*,)
I have to go to work now but I'll try to leave you with this as a work-around:
```
wget https://dl.cacerts.digicert.com/DigiCertSHA2SecureServerCA.crt
mv DigiCertSHA2SecureServerCA.crt DigiCertSHA2SecureServerCA.der
openssl x509 -inform DER -outform PEM -in DigiCertSHA2SecureServerCA.der -out DigicertSHA2SecureServerCA.pem.crt
sudo mkdir -p /usr/share/ca-certificates/extra
sudo cp DigicertSHA2SecureServerCA.pem.crt /usr/share/ca-certificates/extra/
sudo dpkg-reconfigure ca-certificates
```
I hope you have good back-ups.

---

### Post by Autodave on 2019-03-21
No joy.  

Ign:7 [https://launchpad.net/graphics-drivers/ubuntu](https://launchpad.net/graphics-drivers/ubuntu) bionic InRelease           
Err:9 [https://launchpad.net/graphics-drivers/ubuntu](https://launchpad.net/graphics-drivers/ubuntu) bionic Release
  404  Not Found [IP: 2001:67c:1560:8003::8003 443]
Reading package lists... Done
E: The repository 'http://launchpad.net/graphics-drivers/ubuntu bionic Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.

---

### Post by Autodave on 2019-03-21
My screen resolution is OK, but the Nvidia control panel won't open, Super Tux Karts and Torcs won't open either.

---

### Post by Autodave on 2019-03-22
bump

---

### Post by #&amp;thj^% on 2019-03-22
Autodave I have not been able to reproduce what you are seeing on your end, something in apt is corupt>
The only thing to try now is:

```
sudo -i

apt-get clean

cd /var/lib/apt

mv lists lists.old

mkdir -p lists/partial

apt clean

apt update
```

I know you already know this but for the sake of future visitors, this will rename your "list" folder to "list.old" for backup purposes and then rebuild.

Good Luck
```
lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	xubuntu
Release:	18.04
Codename:	bionic

```

---

### Post by Autodave on 2019-03-22
Still no good.  Screen resolution is fine, but no games or Nvidia control panel.  The Nvidia control panel icon is there, but does nothing when clicked on.

One thing that I did notice: when you ran lsb-release -a, your Description returned "xubuntu".  Mine returns Ubuntu.  Does that mean anything?  I have only run Xubuntu for the last 6 or 7 years and I have always done clean installs.  In fact, Ubuntu has never been on this SSD.

---

### Post by Autodave on 2019-03-22
Should I try re-installing Xubuntu?

---

### Post by Autodave on 2019-03-22
Tried to run from terminal and got this:

dave@dave-MS-7641:~$ nvidia-settings
screen 0 does not appear to be DRI2 capable
screen 0 does not appear to be DRI2 capable
amdgpu_device_initialize: amdgpu_get_auth (1) failed (-1)
Segmentation fault (core dumped)

---

### Post by CatKiller on 2019-03-22
> **Autodave said:**
> My screen resolution is OK, but the Nvidia control panel won't open, Super Tux Karts and Torcs won't open either.

That's not too surprising. From your earlier outputs it seems that you haven't got the driver installed, and for some reason - keys, certificates, IPv6 connectivity, or something else - you haven't been able to add the graphics-drivers PPA, which means that you haven't got access to the later versions of the drivers.

You really, really need to purge the proprietary drivers when moving between branches. Neither upgrading nor downgrading between branches works cleanly. The graphics-drivers team also don't seem to be as well-versed in package management as the teams that maintain the main Ubuntu repositories, so there are sometimes additional unnecessary pain points.

There are two issues with where you are at the moment. If you're to be able to use it, you need to get the graphics-drivers PPA added properly. I have no idea whether it's a problem their end or a problem your end that's caused it, but you haven't yet added the PPA. You also need to purge all the nvidia stuff before trying to install a (any) version of the proprietary driver. The driver installation doesn't clean up the kernel modules for previous versions, so you end up with version mismatches.

As an alternative, if you can't get the graphics-drivers PPA to work, you might have more luck with the Nvidia CUDA repository. You'll want the .deb file for the Network Install repository from Nvidia's website rather than downloading a local copy of the whole repository. You don't have to install CUDA: the cuda-drivers metapackage will bring in just the drivers.

---

### Post by Autodave on 2019-03-22
I got it finally!  Evidently, when I uninstalled the AMDGPU drivers before I installed the new card, something did not uninstall.  For the heck of it, I again uninstalled the AMDGPU driver and it fixed it!  Thank you all for your help, especially 1fallen!

---

### Post by #&amp;thj^% on 2019-03-23
Very Nice! Good work, there is always one hidden ingredient that spoils the whole recipe. :)
BTW I added the xubuntu just for clarity. (For lsb_release)

---

### Post by Autodave on 2019-03-23
OK.  I have NO idea why something still remained, but it did and sure screwed everything up for awhile.  Thanks again for your help.

---

