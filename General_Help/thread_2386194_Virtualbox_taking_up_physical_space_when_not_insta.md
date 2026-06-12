---
title: "Virtualbox taking up physical space when not installed!?"
date: 2018-03-02
forum: General Help
---

### Post by MibunoOokami on 2018-03-02
[Long story]("https://ubuntuforums.org/showthread.php?t=2384570") short, sudo ncdu reveals a 75GB Virtualbox in my / directory which I thought I had removed/purged. ```
--- /root ----------------------------------------------------------------------
                          /..
    75.0 GiB [##########] /VirtualBox VMs                                         
     2.1 MiB [          ] /.cache
    68.0 KiB [          ] /.config
    32.0 KiB [          ] /.gnupg
    20.0 KiB [          ] /module-signing
    16.0 KiB [          ] /.local
    16.0 KiB [          ] /.synaptic
    12.0 KiB [          ] /.dbus
 e   4.0 KiB [          ] /Desktop
 e   4.0 KiB [          ] /.nano
     4.0 KiB [          ]  .bashrc
     4.0 KiB [          ]  .rnd
     4.0 KiB [          ]  .bash_history
     4.0 KiB [          ]  .profile
 
```
 
 
 I ran ```
 sudo apt-get remove virtualbox* --purge
``` per the instructions I found in a different thread to try and solve this problem, however…
 
 ```
$ sudo apt-get remove virtualbox* --purge
 [sudo] password for username:  
 Reading package lists... Done
 Building dependency tree        
 Reading state information... Done
 Note, selecting 'virtualbox-source' for glob 'virtualbox*'
 Note, selecting 'virtualbox-guest-utils' for glob 'virtualbox*'
 Note, selecting 'virtualbox-ose' for glob 'virtualbox*'
 Note, selecting 'virtualbox-guest-modules' for glob 'virtualbox*'
 Note, selecting 'virtualbox-guest-additions-iso' for glob 'virtualbox*'
 Note, selecting 'virtualbox-guest-dkms' for glob 'virtualbox*'
 Note, selecting 'virtualbox-dkms' for glob 'virtualbox*'
 Note, selecting 'virtualbox-guest-dkms-hwe' for glob 'virtualbox*'
 Note, selecting 'virtualbox-ext-pack' for glob 'virtualbox*'
 Note, selecting 'virtualbox' for glob 'virtualbox*'
 Note, selecting 'virtualbox-guest-modules-hwe' for glob 'virtualbox*'
 Note, selecting 'virtualbox-guest-x11-hwe' for glob 'virtualbox*'
 Note, selecting 'virtualbox-guest-source' for glob 'virtualbox*'
 Note, selecting 'virtualbox-ose-fuse' for glob 'virtualbox*'
 Note, selecting 'virtualbox-qt' for glob 'virtualbox*'
 Note, selecting 'virtualbox-guest-source-hwe' for glob 'virtualbox*'
 Note, selecting 'virtualbox-2.0' for glob 'virtualbox*'
 Note, selecting 'virtualbox-2.1' for glob 'virtualbox*'
 Note, selecting 'virtualbox-2.2' for glob 'virtualbox*'
 Note, selecting 'virtualbox-modules' for glob 'virtualbox*'
 Note, selecting 'virtualbox-3.0' for glob 'virtualbox*'
 Note, selecting 'virtualbox-3.1' for glob 'virtualbox*'
 Note, selecting 'virtualbox-3.2' for glob 'virtualbox*'
 Note, selecting 'virtualbox-4.0' for glob 'virtualbox*'
 Note, selecting 'virtualbox-4.1' for glob 'virtualbox*'
 Note, selecting 'virtualbox-4.2' for glob 'virtualbox*'
 Note, selecting 'virtualbox-4.3' for glob 'virtualbox*'
 Note, selecting 'virtualbox-5.0' for glob 'virtualbox*'
 Note, selecting 'virtualbox-5.1' for glob 'virtualbox*'
 Note, selecting 'virtualbox-5.2' for glob 'virtualbox*'
 Note, selecting 'virtualbox-guest-utils-hwe' for glob 'virtualbox*'
 Note, selecting 'virtualbox-dbg' for glob 'virtualbox*'
 Note, selecting 'virtualbox-guest-x11' for glob 'virtualbox*'
 Note, selecting 'virtualbox-guest-additions' for glob 'virtualbox*'
 Package 'virtualbox-ose' is not installed, so not removed
 Package 'virtualbox-ose-fuse' is not installed, so not removed
 Note, selecting 'virtualbox-dkms' instead of 'virtualbox-modules'
 Package 'virtualbox-2.0' is not installed, so not removed
 Package 'virtualbox-2.1' is not installed, so not removed
 Package 'virtualbox-2.2' is not installed, so not removed
 Package 'virtualbox-3.0' is not installed, so not removed
 Package 'virtualbox-3.1' is not installed, so not removed
 Package 'virtualbox-3.2' is not installed, so not removed
 Package 'virtualbox-4.0' is not installed, so not removed
 Package 'virtualbox-4.1' is not installed, so not removed
 Package 'virtualbox-4.2' is not installed, so not removed
 Package 'virtualbox-4.3' is not installed, so not removed
 Package 'virtualbox-guest-additions' is not installed, so not removed
 Package 'virtualbox-guest-modules-hwe' is not installed, so not removed
 Package 'virtualbox' is not installed, so not removed
 Package 'virtualbox-dbg' is not installed, so not removed
 Package 'virtualbox-dkms' is not installed, so not removed
 Package 'virtualbox-ext-pack' is not installed, so not removed
 Package 'virtualbox-guest-additions-iso' is not installed, so not removed
 Package 'virtualbox-guest-dkms' is not installed, so not removed
 Package 'virtualbox-guest-dkms-hwe' is not installed, so not removed
 Package 'virtualbox-guest-source' is not installed, so not removed
 Package 'virtualbox-guest-source-hwe' is not installed, so not removed
 Package 'virtualbox-guest-utils' is not installed, so not removed
 Package 'virtualbox-guest-utils-hwe' is not installed, so not removed
 Package 'virtualbox-guest-x11' is not installed, so not removed
 Package 'virtualbox-guest-x11-hwe' is not installed, so not removed
 Package 'virtualbox-qt' is not installed, so not removed
 Package 'virtualbox-source' is not installed, so not removed
 Package 'virtualbox-5.0' is not installed, so not removed
 Package 'virtualbox-5.1' is not installed, so not removed
 Package 'virtualbox-5.2' is not installed, so not removed
 0 upgraded, 0 newly installed, 0 to remove and 13 not upgraded.
```
 
 
 I don’t know what to make of this, do you?

---

### Post by deadflowr on 2018-03-02
apt only removes virtualbox the package.
it does not remove the VMs that you created.
You can delete those manually if you want.

---

### Post by MibunoOokami on 2018-03-02
> **deadflowr said:**
> apt only removes virtualbox the package.
it does not remove the VMs that you created.
You can delete those manually if you want.

How so?

---

### Post by vasa1 on 2018-03-02
Open your home folder in your file manager. Select the folder "VirtualBox VMs",  and delete it.

---

### Post by MibunoOokami on 2018-03-02
Thank you both for such a simple solution to what seemed like a complex problem.

Running as root to access the / directory, I was then able to run the following command to delete Virtualbox completely.

```
sudo rm -rv VirtualBox\ VMs/

```

---

### Post by vasa1 on 2018-03-02
> **MibunoOokami said:**
> Thank you both for such a simple solution to what seemed like a complex problem.

Running as root to access the / directory, I was then able to run the following command to delete Virtualbox completely.

```
sudo rm -rv VirtualBox\ VMs/

```
The *VirtualBox VMs* folder shouldn't have been in /, IMO.

Also re. *sudo ncdu*, *man sudo* has this:```


       If you want to scan a full filesystem, your root filesystem, for example, then you'll want to use "-x":

         ncdu -x /
```

---

### Post by vasa1 on 2018-03-02
> I can&#8217;t think of an occasion where I would have run a program as root, or even using sudo. Could I have done so without knowing?[from your other thread]("https://ubuntuforums.org/showthread.php?t=2384570&p=13742459#post13742459").

Well, you, or someone with access to your machine, certainly have managed to do so :(

Your "VirtualBox VMs" was in /. You have a "Desktop" folder in /. You have a ".config" folder in /.

---

