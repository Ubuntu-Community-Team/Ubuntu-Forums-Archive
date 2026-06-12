---
title: "Boot volume has only 886.8 kb disk space"
date: 2018-01-23
forum: General Help
---

### Post by RogerDavis on 2018-01-23
I'm having massive confusion here :

Right after booting I get an error message that says "only 886.8 kb in boot.  I manually deleted about 6 old kernels and associated files (abi, config, initrd, System, Vmlinuz) - see list below.  This gained very little space, if any.  I emptied trash, no help.

If I click the "examine" button on the error message, it shows 111.4 mb in boot, but also says "could not scan some of the folders contained in boot.

All the files I deleted seem to be in a file boot/.trash-0/files, which might explain the lack of space.

Should I just delete these?

If so, and that gets me enough room, how do I fix the dependency errors I'm seeing, and catch up on failed updates of apps and maybe kernels, etc?

If not, then what?

Thanks!

/boot/.Trash-0/files/abi-4.4.0-79-generic
/boot/.Trash-0/files/abi-4.4.0-96-generic
/boot/.Trash-0/files/abi-4.4.0-97-generic
/boot/.Trash-0/files/abi-4.4.0-98-generic
/boot/.Trash-0/files/abi-4.4.0-101-generic
/boot/.Trash-0/files/abi-4.4.0-103-generic
/boot/.Trash-0/files/abi-4.4.0-104-generic
/boot/.Trash-0/files/config-4.4.0-79-generic
/boot/.Trash-0/files/config-4.4.0-96-generic
/boot/.Trash-0/files/config-4.4.0-97-generic
/boot/.Trash-0/files/config-4.4.0-98-generic
/boot/.Trash-0/files/config-4.4.0-101-generic
/boot/.Trash-0/files/config-4.4.0-103-generic
/boot/.Trash-0/files/config-4.4.0-104-generic
/boot/.Trash-0/files/initrd.img-4.4.0-79-generic
/boot/.Trash-0/files/initrd.img-4.4.0-81-generic
/boot/.Trash-0/files/initrd.img-4.4.0-96-generic
/boot/.Trash-0/files/initrd.img-4.4.0-97-generic
/boot/.Trash-0/files/initrd.img-4.4.0-98-generic
/boot/.Trash-0/files/initrd.img-4.4.0-101-generic
/boot/.Trash-0/files/initrd.img-4.4.0-103-generic
/boot/.Trash-0/files/initrd.img-4.4.0-104-generic
/boot/.Trash-0/files/memtest86+.bin
/boot/.Trash-0/files/memtest86+.elf
/boot/.Trash-0/files/memtest86+_multiboot.bin
/boot/.Trash-0/files/System.map-4.4.0-79-generic
/boot/.Trash-0/files/System.map-4.4.0-96-generic
/boot/.Trash-0/files/System.map-4.4.0-97-generic
/boot/.Trash-0/files/System.map-4.4.0-98-generic
/boot/.Trash-0/files/System.map-4.4.0-101-generic
/boot/.Trash-0/files/System.map-4.4.0-103-generic
/boot/.Trash-0/files/System.map-4.4.0-104-generic
/boot/.Trash-0/files/vmlinuz-4.4.0-79-generic
/boot/.Trash-0/files/vmlinuz-4.4.0-96-generic
/boot/.Trash-0/files/vmlinuz-4.4.0-97-generic
/boot/.Trash-0/files/vmlinuz-4.4.0-98-generic
/boot/.Trash-0/files/vmlinuz-4.4.0-101-generic
/boot/.Trash-0/files/vmlinuz-4.4.0-103-generic
/boot/.Trash-0/files/vmlinuz-4.4.0-104-generic

---

### Post by coffeecat on 2018-01-23
You made two fundamental mistakes:

1 - You tried to manually delete kernel files in /boot. **Never** do this. Use the package manager to delete unwanted kernels.

2 - You didn't actually delete the files, but soft deleted them - hence the .Trash-0 folder. And hence the failure to free up space. The .Trash-0/ folder is owned by root, which tells me you used a root-owned file manager to do the deleting. Piece of friendly advice: **never** use a root-owned file manager for anything. If you need to manipulate root-owned files, you need to use the terminal. If you can't, then don't manipulate root-owned files. I mean this kindly.

(Side comment - yes, I know there are plenty of howtos floating around on the internet telling you to open a root-owned file manager. They are 99% garbage, written by kids or people without good competence. Ignore them.) 

So what do you do? I haven't got time to go into detail at the moment so, hopefully, someone else will come along, but it will be a two-step process, thus:

1 - Restore the soft-deleted files.

2 - Use the package manager to remove unwanted kernels.

At the moment, I'm not quite sure how you would elegantly restore the soft-deleted files, apart from using bash, but I'll think about it. You might be able to with a root-owned file manager, but I think you need to wean yourself off that habit.

And, if there's a better way of doing this I haven't thought of, hopefully someone will be along shortly.

---

### Post by coffeecat on 2018-01-23
I've thought of what I hope is an elegant solution to getting all those files back where they belong in /boot. Try this:

Open a terminal and...

```
sudo -i
```

Type in your password to get a root terminal. You may need that to get past the .Trash-0/ directory, so rather than fiddling around with that in a non-privilege-elevated terminal, let's do it that way. Now:

```
cd /boot/.Trash-0/files
```

That will get you into the directory where the kernel files are. Now:

```
mv * ../../
```

That should move all the files back to where they should be. Now:

```
cd ../../
```

Check from the terminal prompt that you are now in the /boot directory, and check that all the files are where they should be with:

```
ls
```

Now:

```
rmdir .Trash-0/files
rmdir .Trash-0
```

That gets rid of the spurious root-owned trash directories.

Since you don't really need it any more and since it's only polite to say farewell to the root terminal:

```
exit
```

That should all get you back to where you were at the beginning. Before you attempt to delete the unwanted kernels the proper way, let's see something of your setup. From the ordinary non-root terminal:

```
df -h
```

Post the output between BBCode [noparse]```
 and 
```[/noparse] tags. There is a link in my sig if you don't know how.

Also, you said this:

[quote= RogerDavis]how do I fix the dependency errors I'm seeing, and catch up on failed updates of apps and maybe kernels, etc?[/quote]

The dependency errors may be because you bypassed the package manager to try to delete the kernels (possibly not) or perhaps this is a totally unrelated problem which may prevent you from deleting the old kernels until you fix it. To get some preliminary information so that forum members can help you with this, post the terminal output of these two commands:

```
sudo apt-get update
sudo apt-get -s dist-upgrade
```

Again, please post the output between code tags.

---

### Post by Impavidus on 2018-01-23
Good advice above, but
> **coffeecat said:**
> 
Now:

```
rmdir .Trash-0/files
rmdir .Trash-0
```

That gets rid of the spurious root-owned trash directories.

may not work: .Trash-0 contains some metadata on the deleted files, so the second rmdir command will probably fail. Now is running rm -r as root one of the most dangerous things you can do in Linux, but probably the best thing to do here. **So don't copy-paste the command below if you don't know what you're doing.**```
rm -r .Trash-0
```
> 
The dependency errors may be because you bypassed the package manager to try to delete the kernels (possibly not) or perhaps this is a totally unrelated problem which may prevent you from deleting the old kernels until you fix it. To get some preliminary information so that forum members can help you with this, post the terminal output of these two commands:

```
sudo apt-get update
sudo apt-get -s dist-upgrade
```

Again, please post the output between code tags.It's generally possible to uninstall old kernels before fixing the dependency errors by using a lower level tool (dpkg). To see what's currently there, show the output of```
uname -r
dpkg -l | egrep 'linux-image|linux-signed-image'
```

---

### Post by RogerDavis on 2018-01-25
```

roger@roger-System-Product-Name:~$ sudo -i
[sudo] password for roger: 
root@roger-System-Product-Name:~# cd /boot/.Trash-0/files
root@roger-System-Product-Name:/boot/.Trash-0/files# mv * ../../
root@roger-System-Product-Name:/boot/.Trash-0/files# cd ../../
root@roger-System-Product-Name:/boot# ls
abi-4.4.0-101-generic     config-4.4.0-98-generic       System.map-4.4.0-103-generic
abi-4.4.0-103-generic     grub                          System.map-4.4.0-104-generic
abi-4.4.0-104-generic     initrd.img-4.4.0-101-generic  System.map-4.4.0-109-generic
abi-4.4.0-109-generic     initrd.img-4.4.0-103-generic  System.map-4.4.0-112-generic
abi-4.4.0-112-generic     initrd.img-4.4.0-104-generic  System.map-4.4.0-79-generic
abi-4.4.0-79-generic      initrd.img-4.4.0-109-generic  System.map-4.4.0-96-generic
abi-4.4.0-96-generic      initrd.img-4.4.0-112-generic  System.map-4.4.0-97-generic
abi-4.4.0-97-generic      initrd.img-4.4.0-79-generic   System.map-4.4.0-98-generic
abi-4.4.0-98-generic      initrd.img-4.4.0-81-generic   vmlinuz-4.4.0-101-generic
config-4.4.0-101-generic  initrd.img-4.4.0-96-generic   vmlinuz-4.4.0-103-generic
config-4.4.0-103-generic  initrd.img-4.4.0-97-generic   vmlinuz-4.4.0-104-generic
config-4.4.0-104-generic  initrd.img-4.4.0-98-generic   vmlinuz-4.4.0-109-generic
config-4.4.0-109-generic  lost+found                    vmlinuz-4.4.0-112-generic
config-4.4.0-112-generic  memtest86+.bin                vmlinuz-4.4.0-79-generic
config-4.4.0-79-generic   memtest86+.elf                vmlinuz-4.4.0-96-generic
config-4.4.0-96-generic   memtest86+_multiboot.bin      vmlinuz-4.4.0-97-generic
config-4.4.0-97-generic   System.map-4.4.0-101-generic  vmlinuz-4.4.0-98-generic
root@roger-System-Product-Name:/boot# rmdir .Trash-0/files
root@roger-System-Product-Name:/boot# rmdir .Trash-0
rmdir: failed to remove '.Trash-0': Directory not empty
root@roger-System-Product-Name:/boot# ls
abi-4.4.0-101-generic     config-4.4.0-98-generic       System.map-4.4.0-103-generic
abi-4.4.0-103-generic     grub                          System.map-4.4.0-104-generic
abi-4.4.0-104-generic     initrd.img-4.4.0-101-generic  System.map-4.4.0-109-generic
abi-4.4.0-109-generic     initrd.img-4.4.0-103-generic  System.map-4.4.0-112-generic
abi-4.4.0-112-generic     initrd.img-4.4.0-104-generic  System.map-4.4.0-79-generic
abi-4.4.0-79-generic      initrd.img-4.4.0-109-generic  System.map-4.4.0-96-generic
abi-4.4.0-96-generic      initrd.img-4.4.0-112-generic  System.map-4.4.0-97-generic
abi-4.4.0-97-generic      initrd.img-4.4.0-79-generic   System.map-4.4.0-98-generic
abi-4.4.0-98-generic      initrd.img-4.4.0-81-generic   vmlinuz-4.4.0-101-generic
config-4.4.0-101-generic  initrd.img-4.4.0-96-generic   vmlinuz-4.4.0-103-generic
config-4.4.0-103-generic  initrd.img-4.4.0-97-generic   vmlinuz-4.4.0-104-generic
config-4.4.0-104-generic  initrd.img-4.4.0-98-generic   vmlinuz-4.4.0-109-generic
config-4.4.0-109-generic  lost+found                    vmlinuz-4.4.0-112-generic
config-4.4.0-112-generic  memtest86+.bin                vmlinuz-4.4.0-79-generic
config-4.4.0-79-generic   memtest86+.elf                vmlinuz-4.4.0-96-generic
config-4.4.0-96-generic   memtest86+_multiboot.bin      vmlinuz-4.4.0-97-generic
config-4.4.0-97-generic   System.map-4.4.0-101-generic  vmlinuz-4.4.0-98-generic
root@roger-System-Product-Name:/boot# exit
logout
roger@roger-System-Product-Name:~$ df -h
Filesystem                   Size  Used Avail Use% Mounted on
udev                         7.8G     0  7.8G   0% /dev
tmpfs                        1.6G  9.7M  1.6G   1% /run
/dev/mapper/ubuntu--vg-root  424G   22G  382G   6% /
tmpfs                        7.8G  245M  7.6G   4% /dev/shm
tmpfs                        5.0M  4.0K  5.0M   1% /run/lock
tmpfs                        7.8G     0  7.8G   0% /sys/fs/cgroup
/dev/loop0                    84M   84M     0 100% /snap/core/3604
/dev/loop1                   111M  111M     0 100% /snap/namebench-snap/4
/dev/loop2                    84M   84M     0 100% /snap/core/3748
/dev/loop3                    84M   84M     0 100% /snap/core/3440
/dev/sda1                    472M  447M  869K 100% /boot
tmpfs                        1.6G   60K  1.6G   1% /run/user/1000
roger@roger-System-Product-Name:~$ 

```

There is one remaining folder in .Trash-0 , called "info" that would not delete with the command given.  I suppose I could delete that also, but it only contains file "stubs"? about 70~80 bytes long.

Now, as you requested

```

roger@roger-System-Product-Name:~$ sudo apt-get update
[sudo] password for roger: 
Ign:1 http://linux.dropbox.com/ubuntu wily InRelease
Get:2 http://linux.dropbox.com/ubuntu wily Release [6,596 B]             
Hit:3 http://mirrors.namecheap.com/ubuntu xenial InRelease                                                   
Hit:4 http://mirrors.namecheap.com/ubuntu xenial-updates InRelease                                           
Hit:5 http://mirrors.namecheap.com/ubuntu xenial-backports InRelease                                         
Hit:7 http://mirrors.namecheap.com/ubuntu xenial-security InRelease                                          
Ign:8 http://dl.google.com/linux/earth/deb stable InRelease                                                  
Hit:9 http://dl.google.com/linux/earth/deb stable Release                                          
Get:10 http://dl.google.com/linux/earth/deb stable Release.gpg [819 B]  
Hit:11 http://ppa.launchpad.net/iconnor/zoneminder/ubuntu xenial InRelease          
Ign:10 http://dl.google.com/linux/earth/deb stable Release.gpg
Fetched 7,415 B in 0s (16.4 kB/s)
Reading package lists... Done
W: GPG error: http://dl.google.com/linux/earth/deb stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 1397BC53640DB551
W: The repository 'http://dl.google.com/linux/earth/deb stable Release' is not signed.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
N: Skipping acquire of configured file 'main/binary-i386/Packages' as repository 'http://dl.google.com/linux/earth/deb stable InRelease' doesn't support architecture 'i386'
roger@roger-System-Product-Name:~$ sudo apt-get -s dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be upgraded:
  linux-firmware
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
4 not fully installed or removed.
Inst linux-firmware [1.157.14] (1.157.15 Ubuntu:16.04/xenial-updates [all])
Conf initramfs-tools (0.122ubuntu8.10 Ubuntu:16.04/xenial-updates [all])
Conf linux-image-extra-4.4.0-112-generic (4.4.0-112.135 Ubuntu:16.04/xenial-updates, Ubuntu:16.04/xenial-security [amd64])
Conf linux-firmware (1.157.15 Ubuntu:16.04/xenial-updates [all])
Conf linux-image-generic (4.4.0.112.118 Ubuntu:16.04/xenial-updates, Ubuntu:16.04/xenial-security [amd64])
Conf linux-generic (4.4.0.112.118 Ubuntu:16.04/xenial-updates, Ubuntu:16.04/xenial-security [amd64])
roger@roger-System-Product-Name:~$ 

```

Shall I now remove the packages using Synaptic, or wait for further analysis and instructions?

I guess I could remove folder "info" from .Trash-0 using Nautilus as sudo, that's how I could see the name?

---

### Post by RogerDavis on 2018-01-25
```

roger@roger-System-Product-Name:~$ uname -r
4.4.0-112-generic
roger@roger-System-Product-Name:~$ dpkg -l | egrep 'linux-image|linux-signed-image'
ii  linux-image-4.4.0-109-generic                 4.4.0-109.132                                            amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-112-generic                 4.4.0-112.135                                            amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-31-generic                  4.4.0-31.50                                              amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-38-generic                  4.4.0-38.57                                              amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-42-generic                  4.4.0-42.62                                              amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-43-generic                  4.4.0-43.63                                              amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-45-generic                  4.4.0-45.66                                              amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-47-generic                  4.4.0-47.68                                              amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-53-generic                  4.4.0-53.74                                              amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-57-generic                  4.4.0-57.78                                              amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-59-generic                  4.4.0-59.80                                              amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-62-generic                  4.4.0-62.83                                              amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-64-generic                  4.4.0-64.85                                              amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-66-generic                  4.4.0-66.87                                              amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-70-generic                  4.4.0-70.91                                              amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-71-generic                  4.4.0-71.92                                              amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-72-generic                  4.4.0-72.93                                              amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-75-generic                  4.4.0-75.96                                              amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-78-generic                  4.4.0-78.99                                              amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-91-generic                  4.4.0-91.114                                             amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-92-generic                  4.4.0-92.115                                             amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-93-generic                  4.4.0-93.116                                             amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-109-generic           4.4.0-109.132                                            amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
iF  linux-image-extra-4.4.0-112-generic           4.4.0-112.135                                            amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-31-generic            4.4.0-31.50                                              amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-38-generic            4.4.0-38.57                                              amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-42-generic            4.4.0-42.62                                              amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-43-generic            4.4.0-43.63                                              amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-45-generic            4.4.0-45.66                                              amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-47-generic            4.4.0-47.68                                              amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-53-generic            4.4.0-53.74                                              amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-57-generic            4.4.0-57.78                                              amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-59-generic            4.4.0-59.80                                              amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-62-generic            4.4.0-62.83                                              amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-64-generic            4.4.0-64.85                                              amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-66-generic            4.4.0-66.87                                              amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-70-generic            4.4.0-70.91                                              amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-71-generic            4.4.0-71.92                                              amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-72-generic            4.4.0-72.93                                              amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-75-generic            4.4.0-75.96                                              amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-78-generic            4.4.0-78.99                                              amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-79-generic            4.4.0-79.100                                             amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-81-generic            4.4.0-81.104                                             amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-91-generic            4.4.0-91.114                                             amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-92-generic            4.4.0-92.115                                             amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-93-generic            4.4.0-93.116                                             amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
iU  linux-image-generic                           4.4.0.112.118                                            amd64        Generic Linux kernel image
roger@roger-System-Product-Name:~$ 

```

Please see my reply to coffeecat for any info that might be helpful there.

Any further help would be appreciated.

---

### Post by coffeecat on 2018-01-25
A couple of points before addressing your specific questions.

You have an entry in your sources.list for the wily (15.10) linux.dropbox.com repository. What's that for? Wily is well past end-of-life and that entry may need to be updated or removed.

I don't see any dependency issues that you mention in your OP, but apt is complaining about the lack of a google public key. I don't believe that's stopping you from using the package manager, but fixing that will stop the alarmist "potentially dangerous" message. Here's a link that tells you how to install the google signing key:

[https://www.google.com/linuxrepositories/](https://www.google.com/linuxrepositories/)

> **RogerDavis said:**
> 
There is one remaining folder in .Trash-0 , called "info" that would not delete with the command given.  I suppose I could delete that also, but it only contains file "stubs"? about 70~80 bytes long.


Sounds like a plan. .Trash-0/ , .Trash-0/info , and .Trash-0/info/stubs are not taking up significant room but it would be tidy to get rid of them. 

> **RogerDavis said:**
> Shall I now remove the packages using Synaptic, or wait for further analysis and instructions?

You could use Synaptic. You'd have to search for all packages containing the string 4.4.0-31, mark them for complete removal, do the same for 4.4.0-38, and then rinse and repeat until you've marked all except the newest two, and then uninstall all marked packages. That's more fiddly and time-consuming than I would want to do. Here's a link that gives more streamlined methods:

[https://help.ubuntu.com/community/RemoveOldKernels](https://help.ubuntu.com/community/RemoveOldKernels)

I'd suggest trying *sudo apt-get autoremove --purge* first. If you do, I'd also suggest having a cup of coffee or two, or whatever your favourite beverage is, while the system is doing that. Unless, that is, you like watching the terminal output while it laboriously and futilely rebuilds the grub menu after each and every occasion that an old kernel is removed. 

Good luck!

**Edit:** One last point - The newest kernel - 4.4.0.112 - is not fully installed. It might be safer before running autoremove to use Synaptic to uninstall the very oldest kernel in order to free up some space so that you can re-install 4.4.0.112 . And only then run apt-get autoremove to uninstall all the unwanted kernels. I'm not sure how much safety margin is built into autoremove, and whether or not it might falter with an improperly installed kernel, but it *should* leave you with the two newest kernels. Whether it gets confused with one of them being incompletely installed, I don't know.

---

### Post by Impavidus on 2018-01-25
> **coffeecat said:**
> 
Sounds like a plan. .Trash-0/ , .Trash-0/info , and .Trash-0/info/stubs are not taking up significant room but it would be tidy to get rid of them. 

But make sure you actually delete them, not send them to trash. Sending the trash directory to trash is a bit pointless... Or be very careful and use the rm command in post #4.

It seems you have the files for kernel 4.4.0-79, -96, -97, -98, -101, -103 and -104 present in the /boot directory, but according to your package manager these are already uninstalled. Maybe putting them in the trash directory hid them from the uninstall script. Now we could gamble and assume the packages were properly removed except for those files still present in /boot, in which case simply deleting those files may work. The clean way to get rid of those files is to reinstall the old kernels and uninstall them again, but you're a bit tight on disk space. The best way may be to delete those files, then reinstall the old kernels and immediately remove them again.

---

### Post by RogerDavis on 2018-01-25
Another problem - Synaptic doesn't show all the older kernels as installed by searching linux-image, but they are shown as not installed (not green). 109 and 112 show green.  Might the info in the "info" directory be part of this mystery?

Contents of boot/.trash-0/info
```

/boot/.Trash-0/info/abi-4.4.0-79-generic.trashinfo
/boot/.Trash-0/info/abi-4.4.0-96-generic.trashinfo
/boot/.Trash-0/info/abi-4.4.0-97-generic.trashinfo
/boot/.Trash-0/info/abi-4.4.0-98-generic.trashinfo
/boot/.Trash-0/info/abi-4.4.0-101-generic.trashinfo
/boot/.Trash-0/info/abi-4.4.0-103-generic.trashinfo
/boot/.Trash-0/info/abi-4.4.0-104-generic.trashinfo
/boot/.Trash-0/info/config-4.4.0-79-generic.trashinfo
/boot/.Trash-0/info/config-4.4.0-96-generic.trashinfo
/boot/.Trash-0/info/config-4.4.0-97-generic.trashinfo
/boot/.Trash-0/info/config-4.4.0-98-generic.trashinfo
/boot/.Trash-0/info/config-4.4.0-101-generic.trashinfo
/boot/.Trash-0/info/config-4.4.0-103-generic.trashinfo
/boot/.Trash-0/info/config-4.4.0-104-generic.trashinfo
/boot/.Trash-0/info/initrd.img-4.4.0-79-generic.trashinfo
/boot/.Trash-0/info/initrd.img-4.4.0-81-generic.trashinfo
/boot/.Trash-0/info/initrd.img-4.4.0-96-generic.trashinfo
/boot/.Trash-0/info/initrd.img-4.4.0-97-generic.trashinfo
/boot/.Trash-0/info/initrd.img-4.4.0-98-generic.trashinfo
/boot/.Trash-0/info/initrd.img-4.4.0-101-generic.trashinfo
/boot/.Trash-0/info/initrd.img-4.4.0-103-generic.trashinfo
/boot/.Trash-0/info/initrd.img-4.4.0-104-generic.trashinfo
/boot/.Trash-0/info/memtest86+.bin.trashinfo
/boot/.Trash-0/info/memtest86+.elf.trashinfo
/boot/.Trash-0/info/memtest86+_multiboot.bin.trashinfo
/boot/.Trash-0/info/System.map-4.4.0-79-generic.trashinfo
/boot/.Trash-0/info/System.map-4.4.0-96-generic.trashinfo
/boot/.Trash-0/info/System.map-4.4.0-97-generic.trashinfo
/boot/.Trash-0/info/System.map-4.4.0-98-generic.trashinfo
/boot/.Trash-0/info/System.map-4.4.0-101-generic.trashinfo
/boot/.Trash-0/info/System.map-4.4.0-103-generic.trashinfo
/boot/.Trash-0/info/System.map-4.4.0-104-generic.trashinfo
/boot/.Trash-0/info/vmlinuz-4.4.0-79-generic.trashinfo
/boot/.Trash-0/info/vmlinuz-4.4.0-96-generic.trashinfo
/boot/.Trash-0/info/vmlinuz-4.4.0-97-generic.trashinfo
/boot/.Trash-0/info/vmlinuz-4.4.0-98-generic.trashinfo
/boot/.Trash-0/info/vmlinuz-4.4.0-101-generic.trashinfo
/boot/.Trash-0/info/vmlinuz-4.4.0-103-generic.trashinfo
/boot/.Trash-0/info/vmlinuz-4.4.0-104-generic.trashinfo

```

There are the 3 memtest files in boot that I don't know how to get rid of either, but they are only 551.9 kB total, so probably not enough to help.

I could try installing one of the old ones (eg 104) and then remove it, but I guess that wouldn't work for lack of space.  Or even if it failed, would it then be properly removable with all it's parts?

Since you tell me 112 is not fully installed, it seems to me to be risky to remove 112 or 109 to get temporary room.

Would autoremove do any good at this point?

Is it possible to increase the size of the boot folder to work around this situation?

Thanks!

wily (15.10) linux.dropbox.com repository might be for Dropbox?, which I do use.

If I put the files back into .Trash-0 using Nautilus (same way I moved them out), and then move them back with Nautilus, might that make the packages show as installed in Symantic?

Is there a way to remove all of the files manually for at least one of the kernel packages to get working room?

---

### Post by Impavidus on 2018-01-26
> **RogerDavis said:**
> Another problem - Synaptic doesn't show all the older kernels as installed by searching linux-image, but they are shown as not installed (not green). 109 and 112 show green.  Might the info in the "info" directory be part of this mystery?The output from dpkg -l showed that too. The info directory is there to tell the file manager where to put the files from the trash can back if you want to restore them. As you have already restored the files without using the file manager, that information is no more of use. Moving the files back to the trash directory and using the file manager to restore them has exactly the same effect as deleting the trash directory. I suggest you just delete it (**warning: be careful, this is a dangerous command**):```
cd /boot
sudo rm -r .Trash-0
```
> 
There are the 3 memtest files in boot that I don't know how to get rid of either, but they are only 551.9 kB total, so probably not enough to help.Leave them alone. They belong to the memtest86+ package. Deleting them manually will lead to an even bigger mess, uninstalling the package will be a bit messy as the package manager is already in an inconsistent state.

> I could try installing one of the old ones (eg 104) and then remove it, but I guess that wouldn't work for lack of space.  Or even if it failed, would it then be properly removable with all it's parts?It may work or it may not work, that's hard to tell. I first like to know whether initramfs-tools thinks the old kernels are still installed. Show this:```
ls -la /var/lib/initramfs-tools
```
If initramfs-tools doesn't think the old kernels are installed, it won't try to recreate all those files in /boot whenever any kernel is installed or uninstalled. In that case you can simply delete a bunch of files in /boot to make room, then reinstall and uninstall each of the old kernels to get things cleaned up. If initramfs-tools thinks they are still installed, things get a little harder (not much, I think).

> Since you tell me 112 is not fully installed, it seems to me to be risky to remove 112 or 109 to get temporary room.Indeed, don't remove 109 or 112 until the package manager is fixed (and you got the next kernel upgrade).

> Would autoremove do any good at this point?No, autoremove only works when the package manager is in a consistent state and will only remove packages of which it is aware they are installed.

> Is it possible to increase the size of the boot folder to work around this situation?That would be the hard way to solve this problem.

> wily (15.10) linux.dropbox.com repository might be for Dropbox?, which I do use.Is there no xenial version of that repository? The wily version could get dropped at any time or may break compatibility. But that is not related to your current problem.

> If I put the files back into .Trash-0 using Nautilus (same way I moved them out), and then move them back with Nautilus, might that make the packages show as installed in Symantic?
No, won't work. The package manager keeps its own list of which packages are installed and which are not. It doesn't actually check if the files are there. You can make it check, but as only some files are there (I assume), the result would be inconclusive.

Sorry for breaking you quote in 8 parts, making this a very tall post.

---

### Post by RogerDavis on 2018-01-26
Removal of .Trash-0 seems successful
```

roger@roger-System-Product-Name:~$ cd /boot
roger@roger-System-Product-Name:/boot$ sudo rm -r .Trash-0
[sudo] password for roger: 
roger@roger-System-Product-Name:/boot$ 

```

As you asked - it seems to me that it sees only 81 (shipping / backup version?) and 109 and 112 
```

roger@roger-System-Product-Name:~$ ls -la /var/lib/initramfs-tools
total 20
drwxr-xr-x  2 root root 4096 Jan 22 23:27 .
drwxr-xr-x 80 root root 4096 Apr 13  2017 ..
-rw-r--r--  1 root root   77 Jan 11 15:59 4.4.0-109-generic
-rw-r--r--  1 root root   77 Jan 22 18:08 4.4.0-112-generic
-rw-r--r--  1 root root   76 Dec  6 13:45 4.4.0-81-generic

```

> 
If initramfs-tools doesn't think the old kernels are installed, it won't try to recreate all those files in /boot whenever any kernel is installed or uninstalled. In that case you can simply delete a bunch of files in /boot to make room, then reinstall and uninstall each of the old kernels to get things cleaned up. If initramfs-tools thinks they are still installed, things get a little harder (not much, I think).

In this case, present conditions, if I delete the files again, the system won't place the files in another location in boot, as it did before to lead to my problem?  I guess that happened because there was linkage between the files I moved and the system, and the system tried to preserve something?

> 
No, won't work. The package manager keeps its own list of which packages are installed and which are not. It doesn't actually check if the files are there. You can make it check, but as only some files are there (I assume), the result would be inconclusive.

As far as I can think right now, everything that was taken out is now returned to boot, but some kind of linkage was broken, telling the system that they were gone, and was not reinstated when they were returned.  Am I correct?  If we did make Synaptic check, how would we know success or failure, reliable or not, and if that was inconclusive?  Showing green box?  This would be a real 

> 
 In that case you can simply delete a bunch of files in /boot to make room, then reinstall and uninstall each of the old kernels to get things cleaned up.

If I do delete files in /boot, which ones (e.g. /boot/abi-4.4.0-96-generic, /boot/config-4.4.0-96-generic, /boot/initrd.img-4.4.0-96-generic, /boot/System.map-4.4.0-96-generic, /boot/vmlinuz-4.4.0-96-generic, as a set), and why would they not be automatically mirrored elsewhere in /boot, as they were before?  It seems to me some logic for them not being mirrored is that whatever linkage there was is no longer in effect?  And I would use Symantic to install and then remove the kernels, one by one (8 of them, not including 109 and 112)

I also note that /boot/initrd.img-4.4.0-81-generic has no correlated files in the sequences as do all the others.

What should my next step be?

My replies may be at inconsistent times, as I'm not always at this location with this machine.  A couple of days with no response from me is normal.  Please don't take this as lack of interest !

Thanks for all your extremely knowledgeable help in this difficult problem, I would be at a loss without it !!!

---

### Post by Impavidus on 2018-01-27
> **RogerDavis said:**
> 
In this case, present conditions, if I delete the files again, the system won't place the files in another location in boot, as it did before to lead to my problem?  I guess that happened because there was linkage between the files I moved and the system, and the system tried to preserve something?Rule 1 of Linux system management: The system assumes you're smarter than a computer. It will always do what you command, even if that breaks the system. What I believe that happened is that you first moved those files to trash, next either you or the system (it can do that automatically, if configured like that) ran autoremove to remove the old kernel packages. As those files were hidden in the trash directory, they were not removed, leading to an unclean uninstall of the kernel packages. What I propose is that you now use the rm command to remove files. This will not put them in a trash directory, but will actually remove them.

> As far as I can think right now, everything that was taken out is now returned to boot, but some kind of linkage was broken, telling the system that they were gone, and was not reinstated when they were returned.  Am I correct?  If we did make Synaptic check, how would we know success or failure, reliable or not, and if that was inconclusive?  Showing green box?  This would be a real 
Removing a file doesn't tell the package manager it has been uninstalled. The packages have been uninstalled though. When the package manager and uninstall scripts couldn't find some of the files, they may have thrown a few warning messages (now deeply hidden in some log file, if not already deleted), shrugged its shoulders and proceeded, reporting that the packages have been uninstalled successfully. But they haven't. They have been mostly uninstalled, but some files in /boot are still there and initramfs-tools believes kernel -81 is still installed, although the package manager says it isn't.

> What should my next step be?
First make a bit of room:```
cd /boot
sudo rm initrd.img-4.4.0-{96,97,98,101}-generic
```I picked those files because (a) the initrd.img* files are the biggest files present, (b) the package manager doesn't know about them and (c) initramfs-tools doesn't expect -96, -97, -98 and -101 to be there.

Next fix the package manager.```
sudo apt-get install -f
```That should complete installation of -112 and allow apt-get back to work.

Next reinstall and uninstall the old kernels. This will re-create the initrd.img files one at a time, before deleting them again, but there should be enough room to do that.```

sudo apt-get install linux-image-4.4.0-79-generic linux-image-extra-4.4.0-79-generic
sudo apt-get purge linux-image-4.4.0-79-generic linux-image-extra-4.4.0-79-generic

sudo apt-get install linux-image-4.4.0-81-generic linux-image-extra-4.4.0-81-generic
sudo apt-get purge linux-image-4.4.0-81-generic linux-image-extra-4.4.0-81-generic

sudo apt-get install linux-image-4.4.0-96-generic linux-image-extra-4.4.0-96-generic
sudo apt-get purge linux-image-4.4.0-96-generic linux-image-extra-4.4.0-96-generic

sudo apt-get install linux-image-4.4.0-97-generic linux-image-extra-4.4.0-97-generic
sudo apt-get purge linux-image-4.4.0-97-generic linux-image-extra-4.4.0-97-generic

sudo apt-get install linux-image-4.4.0-98-generic linux-image-extra-4.4.0-98-generic
sudo apt-get purge linux-image-4.4.0-98-generic linux-image-extra-4.4.0-98-generic

sudo apt-get install linux-image-4.4.0-101-generic linux-image-extra-4.4.0-101-generic
sudo apt-get purge linux-image-4.4.0-101-generic linux-image-extra-4.4.0-101-generic

sudo apt-get install linux-image-4.4.0-103-generic linux-image-extra-4.4.0-103-generic
sudo apt-get purge linux-image-4.4.0-103-generic linux-image-extra-4.4.0-103-generic

sudo apt-get install linux-image-4.4.0-104-generic linux-image-extra-4.4.0-104-generic
sudo apt-get purge linux-image-4.4.0-104-generic linux-image-extra-4.4.0-104-generic
```
Now reboot to get the -112 kernel running. Keep -109 for a while as it's your only known working kernel.

---

### Post by RogerDavis on 2018-01-27
So far, maybe so good.  I saw some complaints (probably expected) in the Terminal output (attachment), but the intended results at each step seemed to be accomplished.

This is being written before reboot, just in case...  If it works, I'll edit soon to say so.  Worst case, I'll pick this up from another machine in a few hours to fill you in.

[ATTACH]278351[/ATTACH]

If there's anything that you see in there that I need to do, I'd appreciate being informed.  BUT it's a pretty big file of dry reading, and things at least SEEM to be working ok now...

/boot = 354.7 MB - Maybe I should increase boot dir size...

Back soon ...  

And back... all seems ok, cold reboot, waited 10 minutes, no error messages of any kind, ran updater, got one update of Linux firmware of some kind (this is confusing to me, I thought firmware was written to hardware?).    

I'm pretty sure I can place a README-BOOT DIRECTORY FULL text file in /boot just in case I forget this over the next year or so, so I can find it and be told "USE SYMANTIC !!!"  ?

> 
Rule 1 of Linux system management: The system assumes you're smarter than a computer. It will always do what you command, even if that breaks the system.

I believe anyone capable of performing any higher level functions, such as picking the nose, is smarter than a computer.  However, I place my confidence in whoever wrote the BIOS, or OS, and most Apps to know more about system operation than I do.  I simply wish I could read their mind more often...

If I see no further problems after a few days, and get no word from you about things that need doing, I'll mark this solved.


THANKS !!!   I'm not sure where you are, but if you're in the LA area, or ever get here, I owe you dinner for your magnificent assistance!!!

---

### Post by Impavidus on 2018-01-28
It seems fine to me. There were some complaints about missing kernel headers, which are suggested but not an actual dependency. That could be a problem when linking with drivers and things like that, but as you didn't intend to run the kernel, that shouldn't be a problem. It seems everything was properly uninstalled now.

As is the case with most problems, and especially full /boot partitions, preventing it is better than fixing it. Make sure you uninstall old kernels before the /boot partition gets full.

I'm in Europe (see coordinates in my profile), so I don't expect to be in LA any time soon.

---

### Post by RogerDavis on 2018-01-28
That's about what II guessed.  I'll watch things closely for a few day to make sure all is well.

If you have a couple more minutes, could you enlighten me on why this other machine at the other location, a very similar one, on 16.04 is only using 98 (-rw-r--r--  1 root root   76 Jan 24 14:37 4.4.0-98-generic) and not 112, and if I should bother to do anything about it?  All kernel updates on both have been through automatic updates.

Thanks!!!

---

### Post by Impavidus on 2018-01-28
-98? It should be using at least -109 by now. Make sure linux-image-generic and linux-headers-generic are installed:```
sudo apt-get install linux-headers-generic linux-image-generic
```Those are the meta-packages that should pull in the new versions. If that doesn't fix it, start a new thread.

---

### Post by JohnDillinger43 on 2018-01-28
Looks like you got your problem solved, but just wanted to mention that I've really liked Ubuntu Tweak for this purpose -- every week or two I check for any old kernels are have UT remove them.  I've had trouble cleanly doing this through the console, and I've definitely gotten into your situation before of trying to remove them manually and then messing up the package manager.  I typically leave a few older kernels as I have a 1GB boot partition, but anything more than a few versions old I get rid of.

---

### Post by RogerDavis on 2018-01-29
Looks like it went straight to 112 now.  Strange it didn't tell me to reboot, though I will do so very shortly.

Any idea on how this machine got "left behind"  Something I did/didn't do, or ?

Again, immense thanks !!!

```

roger@roger-desktop:~$ sudo apt-get install linux-headers-generic linux-image-generic
[sudo] password for roger: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-generic is already the newest version (4.4.0.112.118).
The following packages were automatically installed and are no longer required:
  libgles1-mesa libllvm3.8 libllvm3.8:i386 libllvm4.0 libllvm4.0:i386
  libmircommon5 libpaps0 linux-headers-4.4.0-101
  linux-headers-4.4.0-101-generic linux-headers-4.4.0-103
  linux-headers-4.4.0-103-generic linux-headers-4.4.0-104
  linux-headers-4.4.0-104-generic linux-headers-4.4.0-108
  linux-headers-4.4.0-108-generic linux-headers-4.4.0-109
  linux-headers-4.4.0-109-generic linux-headers-4.4.0-62
  linux-headers-4.4.0-62-generic linux-headers-4.4.0-63
  linux-headers-4.4.0-63-generic linux-headers-4.4.0-64
  linux-headers-4.4.0-64-generic linux-headers-4.4.0-66
  linux-headers-4.4.0-66-generic linux-headers-4.4.0-70
  linux-headers-4.4.0-70-generic linux-headers-4.4.0-71
  linux-headers-4.4.0-71-generic linux-headers-4.4.0-72
  linux-headers-4.4.0-72-generic linux-headers-4.4.0-75
  linux-headers-4.4.0-75-generic linux-headers-4.4.0-77
  linux-headers-4.4.0-77-generic linux-headers-4.4.0-78
  linux-headers-4.4.0-78-generic linux-headers-4.4.0-79
  linux-headers-4.4.0-79-generic linux-headers-4.4.0-83
  linux-headers-4.4.0-83-generic linux-headers-4.4.0-87
  linux-headers-4.4.0-87-generic linux-headers-4.4.0-96
  linux-headers-4.4.0-96-generic linux-image-4.4.0-83-generic
  linux-image-4.4.0-87-generic linux-image-4.4.0-96-generic
  linux-image-extra-4.4.0-83-generic linux-image-extra-4.4.0-87-generic
  linux-image-extra-4.4.0-96-generic paps snap-confine ubuntu-core-launcher
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  linux-image-4.4.0-112-generic linux-image-extra-4.4.0-112-generic
Suggested packages:
  fdutils linux-doc-4.4.0 | linux-source-4.4.0 linux-tools
The following NEW packages will be installed:
  linux-image-4.4.0-112-generic linux-image-extra-4.4.0-112-generic
  linux-image-generic
0 upgraded, 3 newly installed, 0 to remove and 3 not upgraded.
Need to get 0 B/58.0 MB of archives.
After this operation, 220 MB of additional disk space will be used.
Do you want to continue? [Y/n] Y
Selecting previously unselected package linux-image-4.4.0-112-generic.
(Reading database ... 903837 files and directories currently installed.)
Preparing to unpack .../linux-image-4.4.0-112-generic_4.4.0-112.135_amd64.deb ...
Done.
Unpacking linux-image-4.4.0-112-generic (4.4.0-112.135) ...
Selecting previously unselected package linux-image-extra-4.4.0-112-generic.
Preparing to unpack .../linux-image-extra-4.4.0-112-generic_4.4.0-112.135_amd64.deb ...
Unpacking linux-image-extra-4.4.0-112-generic (4.4.0-112.135) ...
Selecting previously unselected package linux-image-generic.
Preparing to unpack .../linux-image-generic_4.4.0.112.118_amd64.deb ...
Unpacking linux-image-generic (4.4.0.112.118) ...
Setting up linux-image-4.4.0-112-generic (4.4.0-112.135) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-112-generic /boot/vmlinuz-4.4.0-112-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.4.0-112-generic /boot/vmlinuz-4.4.0-112-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-112-generic /boot/vmlinuz-4.4.0-112-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-112-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-112-generic /boot/vmlinuz-4.4.0-112-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-112-generic /boot/vmlinuz-4.4.0-112-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-112-generic /boot/vmlinuz-4.4.0-112-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-112-generic /boot/vmlinuz-4.4.0-112-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-4.4.0-112-generic
Found initrd image: /boot/initrd.img-4.4.0-112-generic
Found linux image: /boot/vmlinuz-4.4.0-98-generic
Found initrd image: /boot/initrd.img-4.4.0-98-generic
Found linux image: /boot/vmlinuz-4.4.0-97-generic
Found initrd image: /boot/initrd.img-4.4.0-97-generic
Found linux image: /boot/vmlinuz-4.4.0-96-generic
Found initrd image: /boot/initrd.img-4.4.0-96-generic
Found linux image: /boot/vmlinuz-4.4.0-87-generic
Found initrd image: /boot/initrd.img-4.4.0-87-generic
Found linux image: /boot/vmlinuz-4.4.0-83-generic
Found initrd image: /boot/initrd.img-4.4.0-83-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
done
Setting up linux-image-extra-4.4.0-112-generic (4.4.0-112.135) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-112-generic /boot/vmlinuz-4.4.0-112-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.4.0-112-generic /boot/vmlinuz-4.4.0-112-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-112-generic /boot/vmlinuz-4.4.0-112-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-112-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-112-generic /boot/vmlinuz-4.4.0-112-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-112-generic /boot/vmlinuz-4.4.0-112-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-112-generic /boot/vmlinuz-4.4.0-112-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-112-generic /boot/vmlinuz-4.4.0-112-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-4.4.0-112-generic
Found initrd image: /boot/initrd.img-4.4.0-112-generic
Found linux image: /boot/vmlinuz-4.4.0-98-generic
Found initrd image: /boot/initrd.img-4.4.0-98-generic
Found linux image: /boot/vmlinuz-4.4.0-97-generic
Found initrd image: /boot/initrd.img-4.4.0-97-generic
Found linux image: /boot/vmlinuz-4.4.0-96-generic
Found initrd image: /boot/initrd.img-4.4.0-96-generic
Found linux image: /boot/vmlinuz-4.4.0-87-generic
Found initrd image: /boot/initrd.img-4.4.0-87-generic
Found linux image: /boot/vmlinuz-4.4.0-83-generic
Found initrd image: /boot/initrd.img-4.4.0-83-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
done
Setting up linux-image-generic (4.4.0.112.118) ...
roger@roger-desktop:~$ 

```

---

### Post by Impavidus on 2018-01-29
If you install or upgrade from the terminal, it doesn't tell you immediately to reboot.

There was an issue with kernel -108 and some people recommended uninstalling it immediately. Maybe you did so, and that would have forced removal of linux-image-generic, because that depended on that latest (broken) kernel. An update to linux-image-generic should have pulled in kernels -109 and the next update to -112, but as the package was uninstalled, that never happened.

And I suggest you run```
sudo apt autoremove --purge
```to free up some disk space and remove clutter. That can prevent a full /boot partition. You've got a lot of old kernel and header packages there, and a few transitional dummy packages too. If you want to keep any of the others, mark them as manually installed first. You can do so in synaptic.

---

### Post by RogerDavis on 2018-01-29
Did this, lots of stuff removed...
```

roger@roger-desktop:~$ sudo apt autoremove --purge
[sudo] password for roger: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  libgles1-mesa* libllvm3.8* libllvm3.8:i386* libllvm4.0* libllvm4.0:i386*
  libmircommon5* libpaps0* linux-headers-4.4.0-101*
  linux-headers-4.4.0-101-generic* linux-headers-4.4.0-103*
  linux-headers-4.4.0-103-generic* linux-headers-4.4.0-104*
  linux-headers-4.4.0-104-generic* linux-headers-4.4.0-108*
  linux-headers-4.4.0-108-generic* linux-headers-4.4.0-109*
  linux-headers-4.4.0-109-generic* linux-headers-4.4.0-62*
  linux-headers-4.4.0-62-generic* linux-headers-4.4.0-63*
  linux-headers-4.4.0-63-generic* linux-headers-4.4.0-64*
  linux-headers-4.4.0-64-generic* linux-headers-4.4.0-66*
  linux-headers-4.4.0-66-generic* linux-headers-4.4.0-70*
  linux-headers-4.4.0-70-generic* linux-headers-4.4.0-71*
  linux-headers-4.4.0-71-generic* linux-headers-4.4.0-72*
  linux-headers-4.4.0-72-generic* linux-headers-4.4.0-75*
  linux-headers-4.4.0-75-generic* linux-headers-4.4.0-77*
  linux-headers-4.4.0-77-generic* linux-headers-4.4.0-78*
  linux-headers-4.4.0-78-generic* linux-headers-4.4.0-79*
  linux-headers-4.4.0-79-generic* linux-headers-4.4.0-81*
  linux-headers-4.4.0-81-generic* linux-headers-4.4.0-83*
  linux-headers-4.4.0-83-generic* linux-headers-4.4.0-87*
  linux-headers-4.4.0-87-generic* linux-headers-4.4.0-96*
  linux-headers-4.4.0-96-generic* linux-headers-4.4.0-97*
  linux-headers-4.4.0-97-generic* linux-image-4.4.0-83-generic*
  linux-image-4.4.0-87-generic* linux-image-4.4.0-96-generic*
  linux-image-4.4.0-97-generic* linux-image-extra-4.4.0-83-generic*
  linux-image-extra-4.4.0-87-generic* linux-image-extra-4.4.0-96-generic*
  linux-image-extra-4.4.0-97-generic* paps* snap-confine*
  ubuntu-core-launcher*
0 upgraded, 0 newly installed, 60 to remove and 8 not upgraded.
After this operation, 2,706 MB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 909456 files and directories currently installed.)
Removing libgles1-mesa (17.2.4-0ubuntu1~16.04.4) ...
Removing libllvm3.8:i386 (1:3.8-2ubuntu4) ...
Removing libllvm3.8:amd64 (1:3.8-2ubuntu4) ...
Removing libllvm4.0:i386 (1:4.0-1ubuntu1~16.04.2) ...
Removing libllvm4.0:amd64 (1:4.0-1ubuntu1~16.04.2) ...
Removing libmircommon5:amd64 (0.21.0+16.04.20160330-0ubuntu1) ...
Removing paps (0.6.8-7ubuntu1) ...
Removing libpaps0 (0.6.8-7ubuntu1) ...
Purging configuration files for libpaps0 (0.6.8-7ubuntu1) ...
Removing linux-headers-4.4.0-101-generic (4.4.0-101.124) ...
Removing linux-headers-4.4.0-101 (4.4.0-101.124) ...
Removing linux-headers-4.4.0-103-generic (4.4.0-103.126) ...
Removing linux-headers-4.4.0-103 (4.4.0-103.126) ...
Removing linux-headers-4.4.0-104-generic (4.4.0-104.127) ...
Removing linux-headers-4.4.0-104 (4.4.0-104.127) ...
Removing linux-headers-4.4.0-108-generic (4.4.0-108.131) ...
Removing linux-headers-4.4.0-108 (4.4.0-108.131) ...
Removing linux-headers-4.4.0-109-generic (4.4.0-109.132) ...
Removing linux-headers-4.4.0-109 (4.4.0-109.132) ...
Removing linux-headers-4.4.0-62-generic (4.4.0-62.83) ...
Removing linux-headers-4.4.0-62 (4.4.0-62.83) ...
Removing linux-headers-4.4.0-63-generic (4.4.0-63.84) ...
Removing linux-headers-4.4.0-63 (4.4.0-63.84) ...
Removing linux-headers-4.4.0-64-generic (4.4.0-64.85) ...
Removing linux-headers-4.4.0-64 (4.4.0-64.85) ...
Removing linux-headers-4.4.0-66-generic (4.4.0-66.87) ...
Removing linux-headers-4.4.0-66 (4.4.0-66.87) ...
Removing linux-headers-4.4.0-70-generic (4.4.0-70.91) ...
Removing linux-headers-4.4.0-70 (4.4.0-70.91) ...
Removing linux-headers-4.4.0-71-generic (4.4.0-71.92) ...
Removing linux-headers-4.4.0-71 (4.4.0-71.92) ...
Removing linux-headers-4.4.0-72-generic (4.4.0-72.93) ...
Removing linux-headers-4.4.0-72 (4.4.0-72.93) ...
Removing linux-headers-4.4.0-75-generic (4.4.0-75.96) ...
Removing linux-headers-4.4.0-75 (4.4.0-75.96) ...
Removing linux-headers-4.4.0-77-generic (4.4.0-77.98) ...
Removing linux-headers-4.4.0-77 (4.4.0-77.98) ...
Removing linux-headers-4.4.0-78-generic (4.4.0-78.99) ...
Removing linux-headers-4.4.0-78 (4.4.0-78.99) ...
Removing linux-headers-4.4.0-79-generic (4.4.0-79.100) ...
Removing linux-headers-4.4.0-79 (4.4.0-79.100) ...
Removing linux-headers-4.4.0-81-generic (4.4.0-81.104) ...
Removing linux-headers-4.4.0-81 (4.4.0-81.104) ...
Removing linux-headers-4.4.0-83-generic (4.4.0-83.106) ...
Removing linux-headers-4.4.0-83 (4.4.0-83.106) ...
Removing linux-headers-4.4.0-87-generic (4.4.0-87.110) ...
Removing linux-headers-4.4.0-87 (4.4.0-87.110) ...
Removing linux-headers-4.4.0-96-generic (4.4.0-96.119) ...
Removing linux-headers-4.4.0-96 (4.4.0-96.119) ...
Removing linux-headers-4.4.0-97-generic (4.4.0-97.120) ...
Removing linux-headers-4.4.0-97 (4.4.0-97.120) ...
Removing linux-image-extra-4.4.0-83-generic (4.4.0-83.106) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-83-generic /boot/vmlinuz-4.4.0-83-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.4.0-83-generic /boot/vmlinuz-4.4.0-83-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-83-generic /boot/vmlinuz-4.4.0-83-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-83-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-83-generic /boot/vmlinuz-4.4.0-83-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-83-generic /boot/vmlinuz-4.4.0-83-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-83-generic /boot/vmlinuz-4.4.0-83-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-83-generic /boot/vmlinuz-4.4.0-83-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-4.4.0-112-generic
Found initrd image: /boot/initrd.img-4.4.0-112-generic
Found linux image: /boot/vmlinuz-4.4.0-98-generic
Found initrd image: /boot/initrd.img-4.4.0-98-generic
Found linux image: /boot/vmlinuz-4.4.0-97-generic
Found initrd image: /boot/initrd.img-4.4.0-97-generic
Found linux image: /boot/vmlinuz-4.4.0-96-generic
Found initrd image: /boot/initrd.img-4.4.0-96-generic
Found linux image: /boot/vmlinuz-4.4.0-87-generic
Found initrd image: /boot/initrd.img-4.4.0-87-generic
Found linux image: /boot/vmlinuz-4.4.0-83-generic
Found initrd image: /boot/initrd.img-4.4.0-83-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
done
Purging configuration files for linux-image-extra-4.4.0-83-generic (4.4.0-83.106) ...
Removing linux-image-4.4.0-83-generic (4.4.0-83.106) ...
Examining /etc/kernel/prerm.d.
run-parts: executing /etc/kernel/prerm.d/dkms 4.4.0-83-generic /boot/vmlinuz-4.4.0-83-generic
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-83-generic /boot/vmlinuz-4.4.0-83-generic
update-initramfs: Deleting /boot/initrd.img-4.4.0-83-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-83-generic /boot/vmlinuz-4.4.0-83-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-4.4.0-112-generic
Found initrd image: /boot/initrd.img-4.4.0-112-generic
Found linux image: /boot/vmlinuz-4.4.0-98-generic
Found initrd image: /boot/initrd.img-4.4.0-98-generic
Found linux image: /boot/vmlinuz-4.4.0-97-generic
Found initrd image: /boot/initrd.img-4.4.0-97-generic
Found linux image: /boot/vmlinuz-4.4.0-96-generic
Found initrd image: /boot/initrd.img-4.4.0-96-generic
Found linux image: /boot/vmlinuz-4.4.0-87-generic
Found initrd image: /boot/initrd.img-4.4.0-87-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
done
Purging configuration files for linux-image-4.4.0-83-generic (4.4.0-83.106) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-83-generic /boot/vmlinuz-4.4.0-83-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-83-generic /boot/vmlinuz-4.4.0-83-generic
Removing linux-image-extra-4.4.0-87-generic (4.4.0-87.110) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-87-generic /boot/vmlinuz-4.4.0-87-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.4.0-87-generic /boot/vmlinuz-4.4.0-87-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-87-generic /boot/vmlinuz-4.4.0-87-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-87-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-87-generic /boot/vmlinuz-4.4.0-87-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-87-generic /boot/vmlinuz-4.4.0-87-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-87-generic /boot/vmlinuz-4.4.0-87-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-87-generic /boot/vmlinuz-4.4.0-87-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-4.4.0-112-generic
Found initrd image: /boot/initrd.img-4.4.0-112-generic
Found linux image: /boot/vmlinuz-4.4.0-98-generic
Found initrd image: /boot/initrd.img-4.4.0-98-generic
Found linux image: /boot/vmlinuz-4.4.0-97-generic
Found initrd image: /boot/initrd.img-4.4.0-97-generic
Found linux image: /boot/vmlinuz-4.4.0-96-generic
Found initrd image: /boot/initrd.img-4.4.0-96-generic
Found linux image: /boot/vmlinuz-4.4.0-87-generic
Found initrd image: /boot/initrd.img-4.4.0-87-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
done
Purging configuration files for linux-image-extra-4.4.0-87-generic (4.4.0-87.110) ...
Removing linux-image-4.4.0-87-generic (4.4.0-87.110) ...
Examining /etc/kernel/prerm.d.
run-parts: executing /etc/kernel/prerm.d/dkms 4.4.0-87-generic /boot/vmlinuz-4.4.0-87-generic
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-87-generic /boot/vmlinuz-4.4.0-87-generic
update-initramfs: Deleting /boot/initrd.img-4.4.0-87-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-87-generic /boot/vmlinuz-4.4.0-87-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-4.4.0-112-generic
Found initrd image: /boot/initrd.img-4.4.0-112-generic
Found linux image: /boot/vmlinuz-4.4.0-98-generic
Found initrd image: /boot/initrd.img-4.4.0-98-generic
Found linux image: /boot/vmlinuz-4.4.0-97-generic
Found initrd image: /boot/initrd.img-4.4.0-97-generic
Found linux image: /boot/vmlinuz-4.4.0-96-generic
Found initrd image: /boot/initrd.img-4.4.0-96-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
done
Purging configuration files for linux-image-4.4.0-87-generic (4.4.0-87.110) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-87-generic /boot/vmlinuz-4.4.0-87-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-87-generic /boot/vmlinuz-4.4.0-87-generic
Removing linux-image-extra-4.4.0-96-generic (4.4.0-96.119) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-96-generic /boot/vmlinuz-4.4.0-96-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.4.0-96-generic /boot/vmlinuz-4.4.0-96-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-96-generic /boot/vmlinuz-4.4.0-96-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-96-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-96-generic /boot/vmlinuz-4.4.0-96-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-96-generic /boot/vmlinuz-4.4.0-96-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-96-generic /boot/vmlinuz-4.4.0-96-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-96-generic /boot/vmlinuz-4.4.0-96-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-4.4.0-112-generic
Found initrd image: /boot/initrd.img-4.4.0-112-generic
Found linux image: /boot/vmlinuz-4.4.0-98-generic
Found initrd image: /boot/initrd.img-4.4.0-98-generic
Found linux image: /boot/vmlinuz-4.4.0-97-generic
Found initrd image: /boot/initrd.img-4.4.0-97-generic
Found linux image: /boot/vmlinuz-4.4.0-96-generic
Found initrd image: /boot/initrd.img-4.4.0-96-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
done
Purging configuration files for linux-image-extra-4.4.0-96-generic (4.4.0-96.119) ...
Removing linux-image-4.4.0-96-generic (4.4.0-96.119) ...
Examining /etc/kernel/prerm.d.
run-parts: executing /etc/kernel/prerm.d/dkms 4.4.0-96-generic /boot/vmlinuz-4.4.0-96-generic
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-96-generic /boot/vmlinuz-4.4.0-96-generic
update-initramfs: Deleting /boot/initrd.img-4.4.0-96-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-96-generic /boot/vmlinuz-4.4.0-96-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-4.4.0-112-generic
Found initrd image: /boot/initrd.img-4.4.0-112-generic
Found linux image: /boot/vmlinuz-4.4.0-98-generic
Found initrd image: /boot/initrd.img-4.4.0-98-generic
Found linux image: /boot/vmlinuz-4.4.0-97-generic
Found initrd image: /boot/initrd.img-4.4.0-97-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
done
Purging configuration files for linux-image-4.4.0-96-generic (4.4.0-96.119) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-96-generic /boot/vmlinuz-4.4.0-96-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-96-generic /boot/vmlinuz-4.4.0-96-generic
Removing linux-image-extra-4.4.0-97-generic (4.4.0-97.120) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-97-generic /boot/vmlinuz-4.4.0-97-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.4.0-97-generic /boot/vmlinuz-4.4.0-97-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-97-generic /boot/vmlinuz-4.4.0-97-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-97-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-97-generic /boot/vmlinuz-4.4.0-97-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-97-generic /boot/vmlinuz-4.4.0-97-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-97-generic /boot/vmlinuz-4.4.0-97-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-97-generic /boot/vmlinuz-4.4.0-97-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-4.4.0-112-generic
Found initrd image: /boot/initrd.img-4.4.0-112-generic
Found linux image: /boot/vmlinuz-4.4.0-98-generic
Found initrd image: /boot/initrd.img-4.4.0-98-generic
Found linux image: /boot/vmlinuz-4.4.0-97-generic
Found initrd image: /boot/initrd.img-4.4.0-97-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
done
Purging configuration files for linux-image-extra-4.4.0-97-generic (4.4.0-97.120) ...
Removing linux-image-4.4.0-97-generic (4.4.0-97.120) ...
Examining /etc/kernel/prerm.d.
run-parts: executing /etc/kernel/prerm.d/dkms 4.4.0-97-generic /boot/vmlinuz-4.4.0-97-generic
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-97-generic /boot/vmlinuz-4.4.0-97-generic
update-initramfs: Deleting /boot/initrd.img-4.4.0-97-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-97-generic /boot/vmlinuz-4.4.0-97-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-4.4.0-112-generic
Found initrd image: /boot/initrd.img-4.4.0-112-generic
Found linux image: /boot/vmlinuz-4.4.0-98-generic
Found initrd image: /boot/initrd.img-4.4.0-98-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
done
Purging configuration files for linux-image-4.4.0-97-generic (4.4.0-97.120) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-97-generic /boot/vmlinuz-4.4.0-97-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-97-generic /boot/vmlinuz-4.4.0-97-generic
Removing snap-confine (2.29.4.2) ...
Purging configuration files for snap-confine (2.29.4.2) ...
Removing ubuntu-core-launcher (2.29.4.2) ...
Processing triggers for libc-bin (2.23-0ubuntu10) ...
Processing triggers for man-db (2.7.5-1) ...
roger@roger-desktop:~$ 

```
Looks like it leaves 2 images automatically.

Is there a list somewhere of what needs to be done for maintenance, like this, that must be done manually?  I presume I should do this on the other machine too, when I get back there tomorrow?

Thanks!

---

### Post by Impavidus on 2018-01-30
Installing updates and occasionally autoremoving old stuff, in particular old kernels and headers, is the only regular maintenance you have to do. You can even use unattended-upgrades (it's a package you can install and configure) to do so automatically, but many prefer to do it manually to keep track.

---

### Post by RogerDavis on 2018-01-31
I installed unattended-upgrades, but found major confusion in trying to work with it's intended purpose(s) and the setup files.

First, as long as Software Updater does it's job, I don't think I need anything but older kernel and related files removal.  Is that correct?

I found huge difficulty in getting an understanding, line by line, of the setup files and contents.  I got partway through, and found that I was unsure of what I had done.  In particular it seemed that some of the lines authorized upgrades (e.g. like 16.04 to 17.04).  I want to control those myself.  So I used Symantic to fully remove what I had and reinstall the basic package.  Afterward I ran dpkg-reconfigure --priority=low unattended-upgrades and nothing else.  It's unclear if this is sufficient to deal with old kernels and associated files, or if I need to add at least "Unattended-Upgrade::Remove-Unused-Dependencies "true";" and if so, where?

Also, have I missed anything?

Thanks!!!

---

### Post by Impavidus on 2018-01-31
I don't use unattended-upgrades myself, so if you have questions about that, better start a new thread (and mark this one as solved).

---

