---
title: "nvidia-331 upgrade error: you have held broken packages??"
date: 2014-01-14
forum: General Help
---

### Post by einstein**-7 on 2014-01-14
I'm trying to install nvida-331 from xorg-edgers with nvidia-304 on the system and i get...


```
crush@crush7:~$ sudo apt-get install nvidia-331
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 nvidia-331 : Depends: x but it is not installable
              Recommends: nvidia-settings (>= 331.20) but 304.88-0ubuntu0.0.3 is to be installed
E: Unable to correct problems, you have held broken packages.

```

next if try to install the nvidia-settings-304.88

```
crush@crush7:~$ sudo apt-get install nvidia-settings
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 nvidia-settings : Depends: screen-resolution-extra (>= 0.14ubuntu2.1) but 0.14ubuntu2 is to be installed
E: Unable to correct problems, you have held broken packages.




```

try install the screen-resolution-extra

```
crush@crush7:~$ sudo apt-get install screen-resolution-extra
Reading package lists... Done
Building dependency tree       
Reading state information... Done
screen-resolution-extra is already the newest version.
screen-resolution-extra set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.
crush@crush7:~$ 
```

Any help would be appreciated!

---

### Post by Crypdos on 2014-01-14
Exact same problem here, had nvidia 331 installed and upgrading isn't possible. Will probably get fixed with the next repo update?

nvidia-331 : Depends: x which is a virtual package.
 nvidia-settings : Depends: screen-resolution-extra (>= 0.14ubuntu2.1) but it is not going to be installed.

---

### Post by jacopocarosi on 2014-01-14
Same problem here; I found the screen-resolution-extra 0,14ubuntu2.1 in Launchpad, but the "x"... uff, plz someone help  >______<

---

### Post by einstein**-7 on 2014-01-14
Yea wack, probably a repo problem like Crypdos said but i found a workaround.
I downloaded the driver from Nvidia's site placed on the root of the drive for easy access.
Logout and.....
contr-alt-F1 to tty then login and,

```
sudo stop lightdm
sudo chmod +x  ""yournvidiadriver""
sudo apt-get purge 'nvidia*'   #### removes anything with nvidia in the package name!!! solves problems when manually installing driver##
sudo ./"your nvidia driver file"  # yes to 32bit libs
sudo reboot
```

---

### Post by jadedcyborg on 2014-01-15
I have the exact same problem.

---

### Post by oldos2er on 2014-01-15
Moved to General Help.

---

### Post by jwcalla on 2014-01-17
Yeah there's a typo in the Depends line of the package:

[FONT=Courier New]Depends: x11-common (>= 1:7.0.0), make, sed (>> 3.0), dkms, linux-libc-dev, libc6-dev, patch, acpid, lib32gcc1, libc6-i386, libc6 (>= 2.2.5), libgl1, libx11-6, libxext6, zlib1g (>= 1:1.1.4), xorg-video-abi-11 | xorg-video-abi-12 | xorg-video-abi-13 | xorg-video-abi-14 | [COLOR="#0000FF"]xorg-video-abi-15, x, xserver-xorg-core[/COLOR] | xserver-xorg-core-lts-quantal | xserver-xorg-core-lts-raring | xserver-xorg-core-lts-saucy
[/FONT]

You want to get rid of that stray "x," in there.

If you're really motivated you can download the .deb, extract it, change the control file and remove that "x,", then repackage the .deb file and install it using the Software Center.

But it's probably less effort to just download the .run installer from NVIDIA.

Does anyone know how to notify the xorg-edgers peeps so they can repackage it?

John

---

### Post by jeanjd63 on 2014-01-18
Hello 
Can you do a :
**dpkg  -l  |   grep -i  nvidia**

---

### Post by modrobert on 2014-01-18
> **jwcalla said:**
> Yeah there's a typo in the Depends line of the package:

[FONT=Courier New]Depends: x11-common (>= 1:7.0.0), make, sed (>> 3.0), dkms, linux-libc-dev, libc6-dev, patch, acpid, lib32gcc1, libc6-i386, libc6 (>= 2.2.5), libgl1, libx11-6, libxext6, zlib1g (>= 1:1.1.4), xorg-video-abi-11 | xorg-video-abi-12 | xorg-video-abi-13 | xorg-video-abi-14 | [COLOR=#0000FF]xorg-video-abi-15, x, xserver-xorg-core[/COLOR] | xserver-xorg-core-lts-quantal | xserver-xorg-core-lts-raring | xserver-xorg-core-lts-saucy
[/FONT]

You want to get rid of that stray "x," in there.

If you're really motivated you can download the .deb, extract it, change the control file and remove that "x,", then repackage the .deb file and install it using the Software Center.

But it's probably less effort to just download the .run installer from NVIDIA.

Does anyone know how to notify the xorg-edgers peeps so they can repackage it?

John

Thanks for clearing that up.

---

