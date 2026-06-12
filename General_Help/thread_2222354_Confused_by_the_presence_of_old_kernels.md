---
title: "Confused by the presence of old kernels"
date: 2014-05-06
forum: General Help
---

### Post by EnglishElectricAndy on 2014-05-06
A kernel update dropped into my Software Updater today. Whilst watching the installation process I spotted quite a few old kernel versions being detected.
```
ls /boot | grep vmlinuz | cut -d'-' -f2,3
```
produces this
```
3.11.0-12
3.11.0-15
3.11.0-17
3.11.0-18
3.11.0-19
3.11.0-20
3.8.0-22
3.8.0-23
3.8.0-25
3.8.0-26
3.8.0-27
3.8.0-29
3.8.0-30
3.8.0-31
3.8.0-32
3.8.0-33
3.8.0-34
3.8.0-35
```
The 3.8.0 versions appear to be hanging around from 13.04.

Running 'sudo apt-get autoremove' outputs this
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED
  linux-headers-3.11.0-12 linux-headers-3.11.0-12-generic linux-image-3.11.0-12-generic linux-image-extra-3.11.0-12-generic
0 upgraded, 0 newly installed, 4 to remove and 0 not upgraded.
After this operation, 258 MB disk space will be freed.
Do you want to continue [Y/n]?
```
This command
```
sudo apt-get remove linux-headers-3.8.0-22 linux-headers-3.8.0-22-generic linux-image-3.8.0-22-generic linux-restricted-modules-3.8.0-22-generic
```
outputs this
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package linux-headers-3.8.0-22
E: Couldn't find any package by regex 'linux-headers-3.8.0-22'
E: Unable to locate package linux-headers-3.8.0-22-generic
E: Couldn't find any package by regex 'linux-headers-3.8.0-22-generic'
E: Unable to locate package linux-image-3.8.0-22-generic
E: Couldn't find any package by regex 'linux-image-3.8.0-22-generic'
E: Unable to locate package linux-restricted-modules-3.8.0-22-generic
E: Couldn't find any package by regex 'linux-restricted-modules-3.8.0-22-generic'

```
I have looked at this thread

[http://ubuntuforums.org/showthread.php?t=2191894&page=4&p=12866887&viewfull=1#post12866887](http://ubuntuforums.org/showthread.php?t=2191894&page=4&p=12866887&viewfull=1#post12866887)

but I'm not sure if the commands therein are applicable as I don't seem to able to actually locate the presence of the 3.8 kernel versions.

Where have I gone wrong above and what further steps should take?
TIA

---

### Post by kc1di on 2014-05-06
One easy way to get rid of old kernels is to down load and install ubuntu-tweak - the janitor will find old kernels and allow you to remove them. 
you can find it [here ]("http://ubuntu-tweak.com/")
you will have to manually add it to the menu as the install doesn't seem to do that. but it works well.

---

### Post by philinux on 2014-05-06
As above but you can also try the link in my signature. Try the dry run one liner command first.

---

### Post by EnglishElectricAndy on 2014-05-06
Thanks for the replies. Sadly neither the Janitor nor dpkg -l linux-* seem able to find the 3.8.0 kernel versions reported as being in vmlinuz.

For info, when I moved from 13.04 to 13.10 I used the upgrade option in a USB live session. I'm confused now as to whether this method leaves behind some phantom artifacts of the superseded kernels or whether they do actually exist on my HD.

---

### Post by sudodus on 2014-05-06
Did you install and run ***Ubuntu-Tweak***? They are talking about the Janitor in Ubuntu-Tweak. I have used it for several years and it can find and (if you wish) remove the old kernel files.

---

### Post by ibjsb4 on 2014-05-06
Did you follow through with the autoremove command?

---

### Post by EnglishElectricAndy on 2014-05-06
@sudodus, I have installed and run Ubuntu Tweak. Using the Janitor option found obselete versions of kernel 3.11. I cleaned these out after double-checking to make sure the current version wasn't listed. It did not report finding any 3.8 kernels.

@ibjsb4, I had already run the autoremove command. Trying it again generates the following
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

---

### Post by sudodus on 2014-05-06
Try these commands too (run one command each time and watch the output)

```
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get autoremove
sudo apt-get autoclean
sudo apt-get clean
```

You can see what they do in ```
man apt-get
```

---

### Post by deadflowr on 2014-05-06
Perhaps doing this
[http://askubuntu.com/questions/104126/can-i-purge-configuration-files-after-ive-removed-the-package](http://askubuntu.com/questions/104126/can-i-purge-configuration-files-after-ive-removed-the-package)

---

### Post by slickymaster on 2014-05-06
Another thread you could look into is this one: [http://ubuntuforums.org/showthread.php?t=1961409](http://ubuntuforums.org/showthread.php?t=1961409)

---

### Post by kc1di on 2014-05-06
you can also run the following command it will delete all kernels except the one that's currently in use.  copy and paste it into a terminal. 

```
sudo apt-get remove --purge $(dpkg -l 'linux-*' | sed '/^ii/!d;/'"$(uname -r | sed "s/\(.*\)-\([^0-9]\+\)/\1/")"'/d;s/^[^ ]* [^ ]* \([^ ]*\).*/\1/;/[0-9]/!d')
```

If that does not return any kernels removed then they are not on your system and you can safely remove any reference to them in the grub menu. 
Good Luck

---

### Post by EnglishElectricAndy on 2014-05-06
Many thanks for all the replies. I appear to have found a fix which I'm not sure why it works and am certainly not sure if it is recommended.

The various 'apt-get commands' didn't seem to touch the v3.8.0 kernels, reporting 0 packages installed/upgraded/removed. In the terminal 'cd /boot' followed by 'ls -a' gave this
```
 initrd.img-3.8.0-29-generic
..                            initrd.img-3.8.0-30-generic
abi-3.11.0-20-generic         initrd.img-3.8.0-31-generic
abi-3.8.0-23-generic          initrd.img-3.8.0-32-generic
abi-3.8.0-25-generic          initrd.img-3.8.0-33-generic
abi-3.8.0-26-generic          initrd.img-3.8.0-34-generic
abi-3.8.0-27-generic          initrd.img-3.8.0-35-generic
abi-3.8.0-29-generic          memtest86+.bin
abi-3.8.0-30-generic          memtest86+_multiboot.bin
abi-3.8.0-31-generic          System.map-3.11.0-20-generic
abi-3.8.0-32-generic          System.map-3.8.0-23-generic
abi-3.8.0-33-generic          System.map-3.8.0-25-generic
abi-3.8.0-34-generic          System.map-3.8.0-26-generic
abi-3.8.0-35-generic          System.map-3.8.0-27-generic
config-3.11.0-20-generic      System.map-3.8.0-29-generic
config-3.8.0-22-generic       System.map-3.8.0-30-generic
config-3.8.0-23-generic       System.map-3.8.0-31-generic
config-3.8.0-25-generic       System.map-3.8.0-32-generic
config-3.8.0-26-generic       System.map-3.8.0-33-generic
config-3.8.0-27-generic       System.map-3.8.0-34-generic
config-3.8.0-29-generic       System.map-3.8.0-35-generic
config-3.8.0-30-generic       vmlinuz-3.11.0-20-generic
config-3.8.0-31-generic       vmlinuz-3.8.0-23-generic
config-3.8.0-32-generic       vmlinuz-3.8.0-25-generic
config-3.8.0-33-generic       vmlinuz-3.8.0-26-generic
config-3.8.0-34-generic       vmlinuz-3.8.0-27-generic
config-3.8.0-35-generic       vmlinuz-3.8.0-29-generic
extlinux                      vmlinuz-3.8.0-30-generic
grub                          vmlinuz-3.8.0-31-generic
initrd.img-3.11.0-20-generic  vmlinuz-3.8.0-32-generic
initrd.img-3.8.0-23-generic   vmlinuz-3.8.0-33-generic
initrd.img-3.8.0-25-generic   vmlinuz-3.8.0-34-generic
initrd.img-3.8.0-26-generic   vmlinuz-3.8.0-35-generic
initrd.img-3.8.0-27-generic
```
I poked about in the file manager GUI, in File Systems> /boot ...and that little lot took up the best part of 500MB. I experimented to see if I could delete these using the right-click menu. No go, the option was greyed out. While I was there I clicked Properties> Permissions showing all these files ownership as root.

I ventured back to the terminal and, with heart in mouth and treading on eggshells, tried this
```
sudo chown <myuserID> /boot
```
Returning to the GUI I found that I could now delete items, though I was very VERY careful to check and double-check the version #s before 'pulling the trigger'.

I then relinquished ownership of /boot
```
sudo chown root /boot
```
and just for good measure
```
sudo update-grub
```

It did seem an unconventional way of going about things, mixing terminal commands with the GUI, and have no idea what command 'Delete' in the GUI actually runs at terminal level but it seems to work.

Many thanks once again for everyones interest.

---

