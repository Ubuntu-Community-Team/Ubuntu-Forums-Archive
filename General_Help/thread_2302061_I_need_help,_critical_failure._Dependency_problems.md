---
title: "I need help, critical failure. Dependency problems."
date: 2015-11-07
forum: General Help
---

### Post by thewonderland on 2015-11-07
Hi! I am a IT Intrested guy from sweden, i am studying networking because that is what i see as my strong side. So now let's get to the problem, i have had this problem for MONTHS now, i don't remember how it actually started. but it was somewhere when i tried to install something and it failed. So this is what happened when i tried to fix it until i gave up, and i did try to fix it many times. It says something like "The following packages were automatically installed and are no longer necessary", and when i click Y, it starts to worsen up the computer, like also uninstalling programs i need, inactivating important services in my computer, and simply dumps me over, i have to go to ttyn do some research and activate some services, and then every time it happens my computers become worsened, as it uninstalls important things. And i haven't been able to use software-center for months, because guess what "software-center
The program "software-center" is not currently installed. You can install it by entering:
sudo apt-get install software-center"


Here is the results:

```
no@alpha1:~$sudo apt-get install software-center
[sudo] password for no:
Reading package lists ... Done
Building dependency tree
Reading state information ... Done
The following packages were automatically installed and are no longer necessary:
**fonts-Horai umefont fonts-texgyre libasn1-8-heimdal: i386
**libboost-filesystem1.54.0 libcapi20-3 libcapi20-3: i386 libenet2a
**libexif12: i386 libgd3: i386 libgif4: i386 libglade2.0-cil libgloox11
**libglu1-mesa: i386 libgphoto2-6: i386 libgphoto2-port10: i386
**libgssapi3-heimdal: i386 libgstreamer-plugins-base0.10-0: i386
**libgstreamer0.10-0: i386-libhcrypto4 Heimdal: i386-libheimbase1 Heimdal: i386
**libheimntlm0-Heimdal: i386-libhx509-5 Heimdal: i386 libieee1284-3: i386
**libkrb5-26-Heimdal: i386-libldap 2.4-2: i386 libltdl7: i386 libmozjs185-1.0
**libmpg123-0: i386 libnvtt2 libopenal1: i386 libosmesa6 libosmesa6: i386
**libp11 kit gnome-keyring: i386 libreoffice-gnome libroken18-heimdal: i386
**libsane: i386 libsasl2-2: i386 libsasl2-modules: i386 libsasl2-modules-db: i386
**libssl0.9.8 libusb-1.0-0: i386 libv4l-0: i386 libv4lconvert0: i386 libvpx1: i386
**libwind0-Heimdal: i386 libwxbase3.0-0 libwxgtk3.0-0 libxcomposite1: i386
**libxpm4: i386 linux-image-extra-3.13.0-45-generic nginx nginx-common
**nginx-core OCL-ICD libopencl1: i386 p11-kit modules: i386 p7zip tex-common
**transmission-gtk wine-gecko2.21 wine-gecko2.21: i386 wine-mono0.0.8 wine1.6
**wine1.6-amd64 wine1.6-i386: i386 winetricks wkhtmltopdf
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
**software-center
0 To upgrade, 1 newly installed, 0 to remove and 12 not upgraded.
3 not fully installed or removed.
Need to get 325 kB archives.
After this operation, additional 3,015 KB of space used on the drive.
Read: 1 [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) trusty-updates / main software-center all 13.10-0ubuntu4.1 [325 KB]
Downloaded 325 kB of 0s (2 399 kB / s)
Choose not previously chosen package software-center.
(Reading database ... 397509 files and directories currently installed.)
Preparing to decompress ... / software-center_13.10-0ubuntu4.1_all.deb ...
Unpack the software-center (13.10-0ubuntu4.1) ...
Handles trigger for mime-support (3.54ubuntu1.1) ...
Manages triggers for gnome-menus (3.10.1-0ubuntu2) ...
Manages triggers for desktop-file-utils (0.22-1ubuntu1) ...
Handles trigger for bamfdaemon (0.5.1 + 14.04.20140409-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index ...
Handles trigger for hicolor-icon-theme (0.13-1) ...
Manages triggers for man-db (2.6.7.1-1ubuntu1) ...
Sets linux-image-extra-3.13.0-66-generic (3.13.0-66.108) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.13.0-66-generic /boot/vmlinuz-3.13.0-66-generic
run-parts: executing /etc/kernel/postinst.d/dkms 3.13.0-66-generic /boot/vmlinuz-3.13.0-66-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.13.0-66-generic /boot/vmlinuz-3.13.0-66-generic
update-initramfs: Generating /boot/initrd.img-3.13.0-66-generic


gzip: stdout: No space left on device
E: mkinitramfs failure cpio 141 gzip 1
update-initramfs: failed for /boot/initrd.img-3.13.0-66-generic with first
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
dpkg: error processing linux-image-extra-3.13.0-66-generic (--configure):
*during the process installed post-installation script returned error 1
dpkg: dependency problems prevent configuration of linux-image-generic:
*linux-image-generic depends on linux-image-extra-3.13.0-66-generic, but:
**Linux-image-extra-3.13.0-66-generic is not configured yet.


dpkg: error processing linux-image-generic (--configure):
*dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
*linux-generic depends on linux-image-generic (= 3.13.0.66.72), but:
**Linux-image-generic is not configured yet.


dpkg: error processing linux-generic (--configure):
*dependency problems - leaving unconfigured
Sets the software-center (13.10-0ubuntu4.1) ...
Updating Software Catalog ... this May take a moment.
INFO: softwarecenter.db.pkginfo_impl.aptcache: aptcache.open ()
Software Catalog update was successful.
Error encountered while processing:
*linux-image-extra-3.13.0-66-generic
*linux-image-generic
*linux-generic
E: Sub-process / usr / bin / dpkg Returned an error code (1)
no@alpha1:~$[COLOR=#000000]
```[/COLOR]

That was just an example, and you can also see what it "wants" me to unisntall every time i want to install something or do something. My background picture wont even show in my login screen and it also says "Kali GNU/Linux Desktop". It is almost everytime some diffrent error when i want to install something, as for example 0ad


Results:

[COLOR=#000000]```
[/COLOR]no@alpha1:~$sudo apt-get install 0AD
Reading package lists ... Done
Building dependency tree
Reading state information ... Done
Some packages could not be installed. It may mean that you have requested
an impossible situation or if you are using the unstable distribution
that some required packages have not yet been created or been moved
from "Incoming".
The following information may help to resolve the situation:


The following packages have dependencies that can not be satisfied:
  0AD: Depends: libboost-filesystem1.46.1 (> = 1.46.1-1) but it can not be installed
        Depends: libicu48 (> = 4.8-1) but it can not be installed
E: Unable to correct problems, you have held broken packages.[COLOR=#000000]
```[/COLOR]



I really need help, i have tried for months and this is my first attempt to seek ACTUAL help using forums. Btw, i have used translate.google.com to translate the resluts to an english version, so pardon the spelling. Thanks :)

---

### Post by Lars Noodén on 2015-11-07
Are you running out of space?

You can try removing the unneeded packages as the message suggests.

```

sudo apt-get autoremove

```

Then you can try removing retrieved package files that have been cached and are no longer needed.

```

sudo apt-get clean

```

Then if things are broken, you can try to have APT fix them.

```

sudo apt-get --fix-broken install

```

Then you can see how much space is left.

```

df -h

```

---

### Post by howefield on 2015-11-07
Thread moved to the "*Ubuntu/Debian BASED*" forum.

---

### Post by thewonderland on 2015-11-07
It want's me to remove
```
no@alpha01:~$ sudo apt-get install libboost-filesystem1.46.1Reading package lists ... Done
Building dependency tree
Reading state information ... Done
Package libboost-filesystem1.46.1 is not available, but a different package refers to it.
This may mean that the package is missing, has been obsoleted, or
only available from other sources
E: The package "libboost-filesystem1.46.1" has no installation candidate
adam @ Exploit3d: ~ $ sudo apt-get autoremove
[sudo] password for adam:
Reading package lists ... Done
Building dependency tree
Reading state information ... Done
The following packages will be REMOVED: fonts-Horai umefont fonts-texgyre libasn1-8-heimdal: i386 libboost-filesystem1.54.0 libcapi20-3 libcapi20-3: i386 libenet2a libexif12: i386 libgd3: i386 libgif4: i386 libglade2.0-cil libgloox11 libglu1-mesa: i386 libgphoto2-6: i386 libgphoto2-port10: i386 libgssapi3-heimdal: i386 libgstreamer-plugins-base0.10-0: i386 libgstreamer0.10-0: i386 libhcrypto4-heimdal: i386 libheimbase1-heimdal: i386 libheimntlm 0 heimdal: i386 libhx509-5-heimdal: i386 libieee1284-3: i386 libkrb5-26-heimdal: i386 libldap-2.4-2: i386 libltdl7: i386 libmozjs185-1.0 libmpg123-0: i386 libnvtt2 libopenal1: i386 libosmesa6 libosmesa6: i386 libp11 kit gnome-keyring: i386 libreoffice-gnome libroken18-heimdal: i386 libsane: i386 libsasl2-2: i386 libsasl2-modules: i386 libsasl2-modules-db: i386 libssl0.9.8 libusb-1.0-0: i386 libv4l-0 : i386 libv4lconvert0: i386 libvpx1: i386 libwind0-heimdal: i386 libwxbase3.0-0 libwxgtk3.0-0 libxcomposite1: i386 libxpm4: i386 linux-image-extra-3.13.0-45-generic nginx nginx nginx-common-core OCL -icd-libopencl1: i386 p11-kit modules: i386 p7zip tex-common transmission-gtk wine-gecko2.21 wine-gecko2.21: i386 wine-mono0.0.8 wine1.6 wine1.6-amd64 wine1.6-i386 : i386 winetricks wkhtmltopdf
0 upgrade, 0 newly installed, 66 to remove and 12 not upgraded.
3 not fully installed or removed.
After this operation, 654 MB of additional disk space.
Do you want to continue? [Y / n]
```
And by the way, i have 1 TB hdd space. df -h results
```
no@alpha01:~$ df -h
Filsystem                   Storlek Använt Ledigt Anv% Monterat på
/dev/mapper/ubuntu--vg-root    901G   357G   499G  42% /
none                           4,0K      0   4,0K   0% /sys/fs/cgroup
udev                           7,8G   4,0K   7,8G   1% /dev
tmpfs                          1,6G   4,5M   1,6G   1% /run
none                           5,0M      0   5,0M   0% /run/lock
none                           7,9G   100M   7,8G   2% /run/shm
none                           100M    64K   100M   1% /run/user
/dev/sda1                      236M   209M    15M  94% /boot
```

---

### Post by ajgreeny on 2015-11-07
It looks like the problem is a separate /boot partition, yet again.  When you installed, and assuming the installer is identical to Ubuntu's, you choose to use either encryption or LVM partitioning by the looks of your df -h output.  If neither of those is used, a separate /boot partition is not needed.

If you have not previously removed old kernels as new versions appeared in upgrades, the /boot partition 
**/dev/sda1                      236M   209M    15M  94% /boot**
which is only 236MB in size will fill up and block the package management system.

What does ```
ls /boot | grep vmlinuz
``` show as output?

That will give us information which lets us tell you how to remove unneeded kernels.
```
sudo apt-get autoremove
``` should do that for you, but if there is no room in /boot it will probably not work, and it sounds as if autoremoval is not currently how you wish to proceed as it has already removed packages you wanted to keep.

---

### Post by thewonderland on 2015-11-07
I did earlier today try to update my ubuntu version, so i did research the problem and i did uninstall some old kernels versions. But here is the output:

```
no@alpha01:~$ ls /boot | grep vmlinuzvmlinuz-3.13.0-32-generic
vmlinuz-3.13.0-43-generic
vmlinuz-3.13.0-44-generic
vmlinuz-3.13.0-45-generic
vmlinuz-3.13.0-53-generic
vmlinuz-3.13.0-66-generic
no@alpha01:~$
```

And the "vmlinuz" was red in all the lines. It wasn't before i uninstalled them. I uninstalled those who din't  have -generic, and if i remember i did go to /boot and remove all the old versions. Also the "generic"'s.

---

### Post by thewonderland on 2015-11-07
And yes, i have encrypted my HDD with the encryption Ubuntu offers at first installation. And i am also studying cryptology or cryptography.

---

### Post by coffeecat on 2015-11-08
> **thewonderland said:**
> And yes, i have encrypted my HDD with the encryption Ubuntu offers at first installation.

I think you need to clarify which operating system you are using. In an earlier post you said:

> **thewonderland said:**
> My background picture wont even show in my login screen and it also says "Kali GNU/Linux Desktop".

Kali - which is why your thread was moved to this sub-forum. Kali is not Ubuntu, indeed is not even based on Ubuntu. I don't know of a situation where Ubuntu would declare itself to be Kali at the login screen. So which is it, Ubuntu or Kali? If you are not sure, what is the name of the ISO file you used to prepare your installation medium when you first installed your OS?

---

### Post by thewonderland on 2015-11-11
I am using Ubuntu, but i added kali's source and installed tools that kali has. And now it says that while i am running Ubuntu.

---

### Post by coffeecat on 2015-11-11
> **thewonderland said:**
> I am using Ubuntu, but i added kali's source and installed tools that kali has. And now it says that while i am running Ubuntu.

OK. Since you are running Ubuntu, albeit a possibly damaged system through being a hybrid of Ubuntu and Kali, I've moved this to the General Help forum. I've also amended your thread title to reflect the main problem.

You've added repositories that were not designed for Ubuntu, nor have they been tested against Ubuntu. My view - an admittedly negative one - is to start over with a fresh installation of Ubuntu, and then install the sort of apps you find in Kali, but from proper Ubuntu sources, rather than simply adding the Kali sources. I think you will spend many hours trying to resolve those dependency problems, and not get very far.

But perhaps someone has a more optimistic view and can help you resolve this.

---

