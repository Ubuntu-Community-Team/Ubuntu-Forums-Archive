---
title: "Update --&gt; error, need to remove old kernels?"
date: 2008-06-17
forum: General Help
---

### Post by _sAm_ on 2008-06-17
After running the Update Manager I got an error, the /boot partition is full(the total size of it is about 110mb). I got kernel panic when rebooting into the new kernel, but it works when I choose the kernel 26.24-18-server. I have confirmed an error message about it on launchpad. 

Looking at my grub list I have several kernels installed, and I want to remove some of them. I have these; 
kernel 26.24-19-generic
kernel 26.24-19-server
kernel 26.24-18-generic
kernel 26.24-18-server
kernel 26.24-17-generic
kernel 26.24-17-server
kernel 26.24-16-generic

But I am not sure how to do this, if I search for linux-image in Synaptic I get the main “names” - but how can I remove the other stuff that it used?

---

### Post by kpkeerthi on 2008-06-17
> **_sAm_ said:**
> 

But I am not sure how to do this, if I search for linux-image in Synaptic I get the main “names” - but how can I remove the other stuff that it used?

Right-click on the main name and mark for complete removal. It will remove appropriate packages.

---

### Post by iaculallad on 2008-06-17
Try to relate with this recently opened [thread]("http://ubuntuforums.org/showthread.php?t=831658"), you both have similar situation.

---

### Post by _sAm_ on 2008-06-17
I opend Synaptic and tried to remove; 
kernel 26.24-17-generic
kernel 26.24-17-server

I get this error; 
> (Reading database ... 199844 files and directories currently installed.)
Removing linux-ubuntu-modules-2.6.24-16-generic ...
update-initramfs: Generating /boot/initrd.img-2.6.24-16-generic

gzip: stdout: No space left on device
update-initramfs: failed for /boot/initrd.img-2.6.24-16-generic
dpkg: error processing linux-ubuntu-modules-2.6.24-16-generic (--remove):
 subprocess post-removal script returned error exit status 1

Removing linux-ubuntu-modules-2.6.24-17-generic ...
update-initramfs: Generating /boot/initrd.img-2.6.24-17-generic
gzip: stdout: No space left on device
update-initramfs: failed for /boot/initrd.img-2.6.24-17-generic
dpkg: error processing linux-ubuntu-modules-2.6.24-17-generic (--remove):
 subprocess post-removal script returned error exit status 1

Removing linux-ubuntu-modules-2.6.24-19-server ...
update-initramfs: Generating /boot/initrd.img-2.6.24-19-server

gzip: stdout: No space left on device
update-initramfs: failed for /boot/initrd.img-2.6.24-19-server
dpkg: error processing linux-ubuntu-modules-2.6.24-19-server (--remove):

 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 linux-ubuntu-modules-2.6.24-16-generic
 linux-ubuntu-modules-2.6.24-17-generic
 linux-ubuntu-modules-2.6.24-19-server

E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up linux-ubuntu-modules-2.6.24-19-generic (2.6.24-19.27) ...
update-initramfs: Generating /boot/initrd.img-2.6.24-19-generic

gzip: stdout: No space left on device
update-initramfs: failed for /boot/initrd.img-2.6.24-19-generic
dpkg: error processing linux-ubuntu-modules-2.6.24-19-generic (--configure):

 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-ubuntu-modules-2.6.24-19-generic; however:
  Package linux-ubuntu-modules-2.6.24-19-generic is not configured yet.

dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
Setting up linux-image-2.6.24-19-server (2.6.24-19.33) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.24-19-server

gzip: stdout: No space left on device
update-initramfs: failed for /boot/initrd.img-2.6.24-19-server
Failed to create initrd image.

dpkg: error processing linux-image-2.6.24-19-server (--configure):
 subprocess post-installation script returned error exit status 2

How can I clean up /boot when I cant even uninstall whats in it? I have tried;
sudo aptitude autoclean
sudo aptitude clean
sudo aptitude autoremove
sudo aptitude install -f

I have booted into failsafe modus and run the dpkg option to fix broken packages and so on.

Edit:
After running sudo aptitude update I get this error:
> E: I wasn't able to locate file for the linux-ubuntu-modules-2.6.24-17-generic package. This might mean you need to manually fix this package.
How can I make it?

---

### Post by danwood76 on 2008-06-17
What you can do is remove them from the /boot partition manually, and then remove them from dpkg manually.

In your /boot partition you will have at least 3 files for each kernel, only 2 of which take up a lot of space.
Remove the initrd.img-2.6.xx and the vmlinuz-2.6.xx files to remove the kernels.
The issue you have is that its trying to update the initramfs (the initrd file above) with each un-install.

This will leave you with broken packages in dpkg, but you can force remove packages with something like:
```

sudo dpkg --force-all -r PACKAGE_NAME

```

---

### Post by danwood76 on 2008-06-17
I just re-read the output you gave a second ago and you are actually trying to remove the modules NOT the kernels.

You want the packages called linux image not the modules package.

---

### Post by _sAm_ on 2008-06-17
I am back in business:)

I had to manually remove the 2.6.24-17-generic and server from /boot to get enough space. 

Then I had to run: 
sudo touch /boot/System.map-2.6.24-17-generic
sudo apt-get remove /boot/System.map-2.6.24-17-generic

After this apt worked as it should, with no more error message, and I could use the Update Manger(and no kernel panic this time).

Linux for Humans - lol 

Thanks for all your help

---

