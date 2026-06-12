---
title: "GRUB Timout No Longer Supported!?"
date: 2017-10-16
forum: General Help
---

### Post by Rick St. George on 2017-10-16
Have UbuntuStudio v16.04 LTS, and Ran AutoRemove prior to update, rec'd this message;

```

Found Ubuntu 16.04.3 LTS (16.04) on /dev/sdc5
done
Removing linux-image-4.4.0-83-lowlatency (4.4.0-83.106) ...
Examining /etc/kernel/prerm.d.
run-parts: executing /etc/kernel/prerm.d/dkms 4.4.0-83-lowlatency /boot/vmlinuz-4.4.0-83-lowlatency
dkms: removing: bbswitch 0.8 (4.4.0-83-lowlatency) (x86_64)

-------- Uninstall Beginning --------
Module:  bbswitch
Version: 0.8
Kernel:  4.4.0-83-lowlatency (x86_64)
-------------------------------------

Status: Before uninstall, this module version was ACTIVE on this kernel.

bbswitch.ko:
 - Uninstallation
   - Deleting from: /lib/modules/4.4.0-83-lowlatency/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.

depmod.........

DKMS: uninstall completed.
dkms: removing: nvidia-375 375.66 (4.4.0-83-lowlatency) (x86_64)

-------- Uninstall Beginning --------
Module:  nvidia-375
Version: 375.66
Kernel:  4.4.0-83-lowlatency (x86_64)
-------------------------------------

Status: Before uninstall, this module version was ACTIVE on this kernel.

nvidia_375.ko:
 - Uninstallation
   - Deleting from: /lib/modules/4.4.0-83-lowlatency/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


nvidia_375_modeset.ko:
 - Uninstallation
   - Deleting from: /lib/modules/4.4.0-83-lowlatency/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


nvidia_375_drm.ko:
 - Uninstallation
   - Deleting from: /lib/modules/4.4.0-83-lowlatency/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


nvidia_375_uvm.ko:
 - Uninstallation
   - Deleting from: /lib/modules/4.4.0-83-lowlatency/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.

depmod....

DKMS: uninstall completed.
dkms: removing: vboxhost 5.0.26 (4.4.0-83-lowlatency) (x86_64)

-------- Uninstall Beginning --------
Module:  vboxhost
Version: 5.0.26
Kernel:  4.4.0-83-lowlatency (x86_64)
-------------------------------------

Status: Before uninstall, this module version was ACTIVE on this kernel.

vboxdrv.ko:
 - Uninstallation
   - Deleting from: /lib/modules/4.4.0-83-lowlatency/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


vboxnetflt.ko:
 - Uninstallation
   - Deleting from: /lib/modules/4.4.0-83-lowlatency/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


vboxnetadp.ko:
 - Uninstallation
   - Deleting from: /lib/modules/4.4.0-83-lowlatency/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


vboxpci.ko:
 - Uninstallation
   - Deleting from: /lib/modules/4.4.0-83-lowlatency/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.

depmod....

DKMS: uninstall completed.
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-83-lowlatency /boot/vmlinuz-4.4.0-83-lowlatency
update-initramfs: Deleting /boot/initrd.img-4.4.0-83-lowlatency
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-83-lowlatency /boot/vmlinuz-4.4.0-83-lowlatency
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.


```

Why is it REMOVING items that are "ACTIVE". I may not be able to reboot my machine or start VirtualBox. 
Is this something to be concerned about?

---

### Post by ajgreeny on 2017-10-16
Is this a Host for VBox or a Guest OS running in VBox?

---

### Post by Rick St. George on 2017-10-17
Host for VBox.

---

### Post by ajgreeny on 2017-10-17
That's what I thought but just wanted confirmation.

The removal of the modules is probably only from kernels that are no longer needed and are about to be removed by the autoremove command.
What kernel are you booting to now? Command **uname -a** will tell you but it should be 4.4.0-97 if you have been updating as usual, though if using terminal you will need to run either ```
sudo apt-get dist-upgrade
``` or ```
sudo apt full-upgrade
``` to get the updated kernel versions.

---

### Post by Rick St. George on 2017-10-17
Here is output;

```

uname -a
Linux stephen-evo-5723 4.4.0-89-lowlatency #112-Ubuntu SMP PREEMPT Mon Jul 31 20:56:03 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux

```

Output of dist-upgrade

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be REMOVED:
  audacious greybird-gtk-theme gtk2-engines-pixbuf openshot
  ubuntustudio-desktop ubuntustudio-desktop-core
The following NEW packages will be installed:
  linux-headers-4.4.0-97 linux-headers-4.4.0-97-lowlatency
  linux-image-4.4.0-97-lowlatency
The following packages will be upgraded:
  libgail-common libgail18 libgtk2.0-0 libgtk2.0-bin linux-headers-lowlatency
  linux-image-lowlatency linux-lowlatency
7 upgraded, 3 newly installed, 6 to remove and 0 not upgraded.
Need to get 70.9 MB of archives.
After this operation, 238 MB of additional disk space will be used.
Do you want to continue? [Y/n] 


```

The problem is - I DO NOT want to remove Audacious, Greybird Theme, UbuntuStudio-Desktop, or OpenShot.

---

### Post by deadflowr on 2017-10-17
> Why is it REMOVING items that are "ACTIVE". 
Active only as it relates to that kernel. Not active as in "in use".
It's clearing the old 4.4.0-83 kernel so it needs to remove the built modules for it.
Simple as that.
Anyway vbox should be well beyond the version being removed by now.
(Currently it's 5.0.40-something)
What version is your vbox?
```
apt-cache policy virtualbox
```


As to the thread title GRUB_TIMEOUT does not work with a non-zero entry if GRUB_HIDDEN_TIMEOUT is enabled
meaning if you have GRUB_HIDDEN_TIMEOUT enabled and set in /etc/default/grub then anything other than 0 in GRUB_TIMEOUT will be ignored.
Disabling GRUB_HIDDEN_TIMEOUT should allow setting GRUB_TIMEOUT to a non-zero entry.
(One would think)

---

### Post by Rick St. George on 2017-10-17
> **deadflowr said:**
> Active only as it relates to that kernel. Not active as in "in use".
It's clearing the old 4.4.0-83 kernel so it needs to remove the built modules for it.
Simple as that.

OH ... duh!

> 
Anyway vbox should be well beyond the version being removed by now.
(Currently it's 5.0.40-something)
What version is your vbox?
```
apt-cache policy virtualbox
```



```
apt-cache policy virtualbox
```
Output:
virtualbox:
  Installed: (none)
  Candidate: (none)
  Version table:


I believe you meant;
```
vboxmanage --version
```

Answer:
5.0.26r108824

---

### Post by deadflowr on 2017-10-18
> I believe you meant;
No.
I wrote what I meant and I meant what I wrote.
Perhaps a better understanding would have been
```
dpkg -l | grep virtualbox
```

To see what virtualbox packages are installed.

(I'm guessing you installed virtualbox from Oracles deb package?
If so, it's miles out of date now. consider updating it; even the version available in Ubuntu is up to 5.0.40, currently, though it seems you do not have the multiverse repository enabled so that's moot, probably)

---

### Post by ajgreeny on 2017-10-18
I suggest you try VBox 5.1.30 by enabling the VBox repositories as explained at [https://www.virtualbox.org/wiki/Linux_Downloads](https://www.virtualbox.org/wiki/Linux_Downloads) by running commands
```
wget -q https://www.virtualbox.org/download/oracle_vbox_2016.asc -O- | sudo apt-key add -
wget -q https://www.virtualbox.org/download/oracle_vbox.asc -O- | sudo apt-key add -
``` then installing **virtualbox-5.1** in your usual manner.

It will remove VBox 5.0 and install the most recent 5.1 version and also keep it updated as you do your usual OS updates.

---

### Post by Rick St. George on 2017-10-18
> **deadflowr said:**
> No.
I wrote what I meant and I meant what I wrote.
Perhaps a better understanding would have been
```
dpkg -l | grep virtualbox
```

To see what virtualbox packages are installed.

(I'm guessing you installed virtualbox from Oracles deb package?
If so, it's miles out of date now. consider updating it; even the version available in Ubuntu is up to 5.0.40, currently, though it seems you do not have the multiverse repository enabled so that's moot, probably)

Yes, from DEB Pkg several years ago. Here is the output from your code above;

```

dpkg -l | grep virtualbox
rc  virtualbox-4.3                                       4.3.20-96996~Ubuntu~raring                        amd64        Oracle VM VirtualBox
ii  virtualbox-5.0                                       5.0.26-108824~Ubuntu~trusty                       amd64        Oracle VM VirtualBox

```

I will take AJGreeny's advice. I was wondering why Vbox was not in the update que!

---

### Post by Rick St. George on 2017-10-18
VirtualBox new version installed OK, Running OK, modified GRUB file, Reboot shows GRUB Boot Loader. All seems fine except that "autoremove" removed Audacious program. Posted in another Thread here;
[https://ubuntuforums.org/showthread.php?t=2374725](https://ubuntuforums.org/showthread.php?t=2374725)

Will mark this one SOLVED. Thanks to all responders for their time and input!
:popcorn:

---

### Post by ajgreeny on 2017-10-20
I see there is a newer VBox version 5.2 released two days ago.
To upgrade to it you will have to specifically install virtualbox-5.2 which I assume will remove the 5.1 version.

I have not yet tried it but will do so later today and report back.

---

### Post by ajgreeny on 2017-10-20
Now installed VBox 5.2 and all seems to be fine.  Some minor visual and GUI changes but otherwise it runs well as did 5.1.

---

### Post by ajgreeny on 2017-10-26
> **ajgreeny said:**
> Now installed VBox 5.2 and all seems to be fine.  Some minor visual and GUI changes but otherwise it runs well as did 5.1.
I take that back!
There is a known problem with the guest additions  of that version mentioned at the VBox download site at [https://www.virtualbox.org/wiki/Downloads](https://www.virtualbox.org/wiki/Downloads)
> Update: The Guest Additions image with the 5.2.0 release fails to work with recent Linux guest kernels. Please try [this image]("https://www.virtualbox.org/download/testcase/VBoxGuestAdditions_5.2.1-118447.iso") which we believe fixes the problem. For experimental Linux 4.14 support, please try [this image]("https://www.virtualbox.org/download/testcase/VBoxGuestAdditions_5.2.1-118452.iso"). Both should work on all older guest systems too: please let us know if they do not.

The links shown take you to an iso file for the newer versions 5.2.1 but neither of those worked with all my VMs, Debian-9 in particular not being able to go to full screen at my monitor's resolution, so for now at least I have gone back to VBox 5.1.30, including the guest additions, and all is working again as it should.

---

