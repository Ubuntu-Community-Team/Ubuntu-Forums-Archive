---
title: "boot device full - freed up space and messed up kernel dependencies"
date: 2013-08-12
forum: General Help
---

### Post by lchalupa on 2013-08-12
Hello:

Initial problem:  apt-get upgrade would not.  no room left in /boot directory.

I tried this procedure to correct this problem:
[http://askubuntu.com/questions/171209/my-boot-partition-hit-100-and-now-i-cant-upgrade-cant-remove-old-kernels-to](http://askubuntu.com/questions/171209/my-boot-partition-hit-100-and-now-i-cant-upgrade-cant-remove-old-kernels-to)


I ended up removing files from the /boot directory.  That fixed the /boot directory full problem.  But now my dependencies appear to be screwed up.

here is the output I get when I try to do an apt-get upgrade:

lchalupa@purple:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run 'apt-get -finstall' to correct these.
The following packages have unmetdependencies:
 linux-generic-pae : Depends:linux-headers-generic-pae (= 3.2.0.38.46) but 3.2.0.51.61 isinstalled
 linux-image-generic-pae : Depends:linux-image-3.2.0-38-generic-pae but it is not installed
E: Unmet dependencies. Try using -f.

Here is what is in my /boot directory:


E: Unmet dependencies. Try using-f.lchalupa@purple:~$ cd /boot
lchalupa@purple:/boot$ ls
abi-3.2.0-23-generic-pae config-3.2.0-23-generic-pae      System.map-3.2.0-23-generic-pae vmlinuz-3.2.0-23-generic-pae
abi-3.2.0-25-generic-pae config-3.2.0-37-generic-pae      System.map-3.2.0-25-generic-pae vmlinuz-3.2.0-25-generic-pae
abi-3.2.0-26-generic-pae config-3.2.0-51-generic-pae      System.map-3.2.0-26-generic-pae vmlinuz-3.2.0-26-generic-pae
abi-3.2.0-27-generic-pae  grub                            System.map-3.2.0-27-generic-pae vmlinuz-3.2.0-27-generic-pae
abi-3.2.0-29-generic-pae initrd.img-3.2.0-35-generic-pae  System.map-3.2.0-29-generic-pae vmlinuz-3.2.0-29-generic-pae
abi-3.2.0-31-generic-pae initrd.img-3.2.0-36-generic-pae  System.map-3.2.0-31-generic-pae vmlinuz-3.2.0-31-generic-pae
abi-3.2.0-32-generic-pae initrd.img-3.2.0-37-generic-pae  System.map-3.2.0-32-generic-pae vmlinuz-3.2.0-32-generic-pae
abi-3.2.0-35-generic-pae initrd.img-3.2.0-51-generic-pae  System.map-3.2.0-35-generic-pae vmlinuz-3.2.0-35-generic-pae
abi-3.2.0-36-generic-pae  lost+found                      System.map-3.2.0-36-generic-pae vmlinuz-3.2.0-36-generic-pae
abi-3.2.0-37-generic-pae memtest86+.bin                   System.map-3.2.0-37-generic-pae vmlinuz-3.2.0-37-generic-pae
abi-3.2.0-51-generic-pae memtest86+_multiboot.bin         System.map-3.2.0-51-generic-pae vmlinuz-3.2.0-51-generic-pae
lchalupa@purple:/boot$


I'm stuck.  What do I need to do to fix this?

Thank you for your help.

Lee

---

### Post by oldfred on 2013-08-12
Have you run:
```

 sudo apt-get -f install


```

Do you have gui? If so I find synaptic works the best. I normally keep current & one old kernel as backup and houseclean out older ones.

I think this is essentially the same as the askUbuntu. Example below is just -generic, of course you have to use your version which is -generic-pae

 Determine your current kernel:
uname -a
uname -r
In synaptic search for linux-image to choose to delete old ones
Also command line in post #8
[http://ubuntuforums.org/showthread.php?t=1283521](http://ubuntuforums.org/showthread.php?t=1283521)
cd /boot
ls vmlinuz*
sudo apt-get purge  linux-image-[version]-generic linux-image-[version]-generic
Multiples, just be sure not to delete your current kerne.:
sudo apt-get purge linux-image-3.5.0-{XX,XX,XX,XX,XX,XX}-generic
Example:
sudo apt-get purge linux-image-3.5.0-{17,18,19,21,22,23,24}-generic
#current install:
lsb_release -a
Go to Synaptic Package Manager and search for linux-image.
More info in post #8
[http://ubuntuforums.org/showthread.php?t=1283521](http://ubuntuforums.org/showthread.php?t=1283521)

---

