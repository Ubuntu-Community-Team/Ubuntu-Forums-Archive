---
title: "Clean up /boot"
date: 2019-02-22
forum: General Help
---

### Post by pog22 on 2019-02-22
As you can see I need to delete some images but it's not letting me do this

```
root@Ubuntu-1604-xenial-64-minimal ~ # dpkg -l | grep -G "linux.*image.*"ii  linux-base                            4.5ubuntu1~16.04.1                    all          Linux image base package
ii  linux-image-4.13.0-32-generic         4.13.0-32.35~16.04.1                  amd64        Linux kernel image for version 4.13.0 on 64 bit x86 SMP
pi  linux-image-4.15.0-34-generic         4.15.0-34.37~16.04.1                  amd64        Signed kernel image generic
pi  linux-image-4.15.0-36-generic         4.15.0-36.39~16.04.1                  amd64        Signed kernel image generic
pi  linux-image-4.15.0-39-generic         4.15.0-39.42~16.04.1                  amd64        Signed kernel image generic
ii  linux-image-4.15.0-42-generic         4.15.0-42.45~16.04.1                  amd64        Signed kernel image generic
iU  linux-image-4.15.0-43-generic         4.15.0-43.46~16.04.1                  amd64        Signed kernel image generic
pi  linux-image-4.4.0-112-generic         4.4.0-112.135                         amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-135-generic         4.4.0-135.161                         amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-137-generic         4.4.0-137.163                         amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-138-generic         4.4.0-138.164                         amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-139-generic         4.4.0-139.165                         amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.8.0-58-generic          4.8.0-58.63~16.04.1                   amd64        Linux kernel image for version 4.8.0 on 64 bit x86 SMP
ii  linux-image-extra-4.13.0-32-generic   4.13.0-32.35~16.04.1                  amd64        Linux kernel extra modules for version 4.13.0 on 64 bit x86 SMP
pi  linux-image-extra-4.4.0-112-generic   4.4.0-112.135                         amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-135-generic   4.4.0-135.161                         amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-137-generic   4.4.0-137.163                         amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-138-generic   4.4.0-138.164                         amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-139-generic   4.4.0-139.165                         amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
iU  linux-image-extra-4.4.0-141-generic   4.4.0-141.167                         amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.8.0-58-generic    4.8.0-58.63~16.04.1                   amd64        Linux kernel extra modules for version 4.8.0 on 64 bit x86 SMP
iU  linux-image-extra-virtual             4.4.0.141.147                         amd64        Transitional package.
iU  linux-image-generic                   4.4.0.141.147                         amd64        Generic Linux kernel image
iU  linux-image-generic-hwe-16.04         4.15.0.43.64                          amd64        Generic Linux kernel image
root@Ubuntu-1604-xenial-64-minimal ~ # sudo apt-get purge linux-image-4.15.0-36-generic 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 linux-image-extra-4.4.0-141-generic : Depends: linux-image-4.4.0-141-generic but it is not going to be installed
 linux-image-generic : Depends: linux-image-4.4.0-141-generic but it is not going to be installed
 linux-modules-extra-4.15.0-36-generic : Depends: linux-image-4.15.0-36-generic but it is not going to be installed or
                                                  linux-image-unsigned-4.15.0-36-generic but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).



```

---

### Post by oldfred on 2019-02-22
Is this an upgraded system?
You show old kernels as well as some newer.
Generally you need to houseclean old kernels before upgrading. New versions of Ubuntu now only keep 2 kernels by default.

Did you run the suggested:
sudo apt-get -f install

You should always houseclean kernels with dpkg not rm. But if an upgrade, they may not even be in your list of installed kernels, then rm is only choice, but parts of kernel may be in other folders.
       [URL="https://help.ubuntu.com/community/RemoveOldKernels"]https://help.ubuntu.com/community/RemoveOldKernels

      [/URL]
 Check current kernel I also keep one older just in case:
#Current kernel:
uname -a
# kernels, shows older also?
dpkg --list | grep linux-image
-s is simulate so you can see what it will do, then run without -s
sudo apt-get -s autoremove 
    
Other locations of left over kernels. These get housecleaned with dpkg, but not an rm.
       Use dpkg -S to see which .dkms files were not placed by the package manager
dpkg -S /full/path/to/file
Only use rm on files not in dpkg
dpkg -S /lib/modules | sed s/:.\*//
uname --kernel-release
 Did you also check /var/cache/apt/archives? You may have the old .deb's taking up space.
 /var/cache/apt/archives
kernel house clean
/usr/src/*
[http://askubuntu.com/questions/301466/files-are-piling-up-in-usr-src-how-can-i-stop-this](http://askubuntu.com/questions/301466/files-are-piling-up-in-usr-src-how-can-i-stop-this)
in /boot by version: abi, config, initrd.img, vmlinuz 
    [URL="https://help.ubuntu.com/community/RemoveOldKernels"]
[/URL]

---

### Post by pog22 on 2019-02-22
I'm unsure what do do here, this is my output. The server is a Hetzner dedi, it was not upgraded

```
root@Ubuntu-1604-xenial-64-minimal ~ # sudo apt-get -f installReading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  linux-headers-4.10.0-32 linux-headers-4.10.0-33 linux-headers-4.10.0-35 linux-headers-4.10.0-37 linux-headers-4.10.0-38
  linux-headers-4.10.0-40 linux-headers-4.10.0-42 linux-headers-4.13.0-26 linux-headers-4.13.0-26-generic linux-headers-4.13.0-31
  linux-headers-4.13.0-31-generic linux-headers-4.13.0-32 linux-headers-4.13.0-32-generic linux-headers-4.15.0-34
  linux-headers-4.15.0-34-generic linux-image-4.13.0-32-generic linux-image-4.15.0-34-generic linux-image-4.4.0-112-generic
  linux-image-4.4.0-139-generic linux-image-extra-4.13.0-32-generic linux-image-extra-4.4.0-112-generic linux-image-extra-4.4.0-139-generic
  linux-modules-4.15.0-34-generic linux-modules-extra-4.15.0-34-generic
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  linux-image-4.4.0-141-generic
Suggested packages:
  fdutils linux-doc-4.4.0 | linux-source-4.4.0 linux-tools linux-headers-4.4.0-141-generic
The following NEW packages will be installed:
  linux-image-4.4.0-141-generic
0 upgraded, 1 newly installed, 0 to remove and 39 not upgraded.
12 not fully installed or removed.
Need to get 0 B/22.2 MB of archives.
After this operation, 68.2 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
(Reading database ... 449824 files and directories currently installed.)
Preparing to unpack .../linux-image-4.4.0-141-generic_4.4.0-141.167_amd64.deb ...
Examining /etc/kernel/preinst.d/
run-parts: executing /etc/kernel/preinst.d/intel-microcode 4.4.0-141-generic /boot/vmlinuz-4.4.0-141-generic
Done.
Unpacking linux-image-4.4.0-141-generic (4.4.0-141.167) ...
dpkg: error processing archive /var/cache/apt/archives/linux-image-4.4.0-141-generic_4.4.0-141.167_amd64.deb (--unpack):
 cannot copy extracted data for './boot/vmlinuz-4.4.0-141-generic' to '/boot/vmlinuz-4.4.0-141-generic.dpkg-new': failed to write (No space left on device)
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-141-generic /boot/vmlinuz-4.4.0-141-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-141-generic /boot/vmlinuz-4.4.0-141-generic
Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-4.4.0-141-generic_4.4.0-141.167_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@Ubuntu-1604-xenial-64-minimal ~ # uname -a
Linux Ubuntu-1604-xenial-64-minimal 4.15.0-42-generic #45~16.04.1-Ubuntu SMP Mon Nov 19 13:02:27 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux
root@Ubuntu-1604-xenial-64-minimal ~ # dpkg --list | grep linux-image
ii  linux-image-4.13.0-32-generic         4.13.0-32.35~16.04.1                  amd64        Linux kernel image for version 4.13.0 on 64 bit x86 SMP
pi  linux-image-4.15.0-34-generic         4.15.0-34.37~16.04.1                  amd64        Signed kernel image generic
pi  linux-image-4.15.0-36-generic         4.15.0-36.39~16.04.1                  amd64        Signed kernel image generic
pi  linux-image-4.15.0-39-generic         4.15.0-39.42~16.04.1                  amd64        Signed kernel image generic
ii  linux-image-4.15.0-42-generic         4.15.0-42.45~16.04.1                  amd64        Signed kernel image generic
iU  linux-image-4.15.0-43-generic         4.15.0-43.46~16.04.1                  amd64        Signed kernel image generic
pi  linux-image-4.4.0-112-generic         4.4.0-112.135                         amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-135-generic         4.4.0-135.161                         amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-137-generic         4.4.0-137.163                         amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-138-generic         4.4.0-138.164                         amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-139-generic         4.4.0-139.165                         amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.8.0-58-generic          4.8.0-58.63~16.04.1                   amd64        Linux kernel image for version 4.8.0 on 64 bit x86 SMP
ii  linux-image-extra-4.13.0-32-generic   4.13.0-32.35~16.04.1                  amd64        Linux kernel extra modules for version 4.13.0 on 64 bit x86 SMP
pi  linux-image-extra-4.4.0-112-generic   4.4.0-112.135                         amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-135-generic   4.4.0-135.161                         amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-137-generic   4.4.0-137.163                         amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-138-generic   4.4.0-138.164                         amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-139-generic   4.4.0-139.165                         amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
iU  linux-image-extra-4.4.0-141-generic   4.4.0-141.167                         amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.8.0-58-generic    4.8.0-58.63~16.04.1                   amd64        Linux kernel extra modules for version 4.8.0 on 64 bit x86 SMP
iU  linux-image-extra-virtual             4.4.0.141.147                         amd64        Transitional package.
iU  linux-image-generic                   4.4.0.141.147                         amd64        Generic Linux kernel image
iU  linux-image-generic-hwe-16.04         4.15.0.43.64                          amd64        Generic Linux kernel image
root@Ubuntu-1604-xenial-64-minimal ~ # sudo apt-get -s autoremove 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 linux-image-extra-4.4.0-141-generic : Depends: linux-image-4.4.0-141-generic but it is not installed
 linux-image-generic : Depends: linux-image-4.4.0-141-generic but it is not installed
E: Unmet dependencies. Try using -f.



```

---

### Post by deadflowr on 2019-02-22
Post back the output for
```
df -h
```

---

### Post by pog22 on 2019-02-22
```
root@Ubuntu-1604-xenial-64-minimal ~ # df -hFilesystem      Size  Used Avail Use% Mounted on
udev             12G     0   12G   0% /dev
tmpfs           2.4G   18M  2.4G   1% /run
/dev/md2        1.8T  291G  1.5T  17% /
tmpfs            12G  1.3M   12G   1% /dev/shm
tmpfs           5.0M     0  5.0M   0% /run/lock
tmpfs            12G     0   12G   0% /sys/fs/cgroup
/dev/md1        488M  483M     0 100% /boot
gdrive:         1.0P     0  1.0P   0% /mnt/rclone-d
none            1.8T  291G  1.5T  17% /var/lib/docker/aufs/mnt/667f1acd49a859442c377ef30d714df6ff19bcb9e07e847ffd9a205e9a801eef
/dev/sdc1       235G  9.8G  213G   5% /mnt/emby
none            1.8T  291G  1.5T  17% /var/lib/docker/aufs/mnt/5c1c2927febc1f7a1b9417e223d3f47fb303e58764d33d290a26a0a3c99b5a1f
shm              64M     0   64M   0% /var/lib/docker/containers/21511508b9f3260a99c578f0ad4537099e14b223edf66f0c71f9f40807e38e0e/shm
shm              64M     0   64M   0% /var/lib/docker/containers/cfe3333e7ddc9d7196ecbd57fc5f1079f0c848ff1aa57169e48893da3424d65f/shm
none            1.8T  291G  1.5T  17% /var/lib/docker/aufs/mnt/d1ff336a7aaf9f4eb90fcf0600b1c34ffbd3f43b482855dcb02c035f560292fe
shm              64M     0   64M   0% /var/lib/docker/containers/a407922477362d1d48836d4c65269060a826a411a28d894f6f2dad48b0d8ae0d/shm
none            1.8T  291G  1.5T  17% /var/lib/docker/aufs/mnt/40f03d20de9f5e05670f9eae7389f371fb898a7823cf4b75eed2344e952363e9
shm              64M     0   64M   0% /var/lib/docker/containers/2485f534a8ab744b04f2ac4854573347c8d282f94f6368184bc2bf417531f726/shm
tmpfs           2.4G     0  2.4G   0% /run/user/0
none            1.8T  291G  1.5T  17% /var/lib/docker/aufs/mnt/144d9c50dd995bd8fe216d49f16121554908c3faee7471ada70514ebdbae4d12
none            1.8T  291G  1.5T  17% /var/lib/docker/aufs/mnt/07c752634969932526f505a0d23cf85b7e3aaab8cadb2ecbdedbf819bb2b6424
none            1.8T  291G  1.5T  17% /var/lib/docker/aufs/mnt/da1e3a40a7314ac96aa27111609382c7513f508da106d2367c6be2667c1a41c0
none            1.8T  291G  1.5T  17% /var/lib/docker/aufs/mnt/9ed2e98b0aa2fd672827a9953b0a3fceb934a9e216f4fe5dbaa8bb485727213b
none            1.8T  291G  1.5T  17% /var/lib/docker/aufs/mnt/8d129da31ec7a1c032c534f9b3f9a0dedbd7d0ae902dcc6a374f916d4a585cfe
none            1.8T  291G  1.5T  17% /var/lib/docker/aufs/mnt/4e77ee2c815f0a257a220578e19b5e83afdbe21f603702e2f6182bfedf81dd95
shm              64M     0   64M   0% /var/lib/docker/containers/cfc55ecc9894b9685630fb6ff17e6443d2f7ee87c7994c80bc97e2e35deb6e01/shm
shm              64M     0   64M   0% /var/lib/docker/containers/5d59cd88f6c0ad31f4a9c4308f1d53067db3758f16d2f373f25681531e867a4c/shm
shm              64M  4.0K   64M   1% /var/lib/docker/containers/a8ce4d04cd27933152b12b58b127021300730a9e9390550b4d3d2e55d18c8e30/shm
shm              64M     0   64M   0% /var/lib/docker/containers/0cdb04027d3e62378e5d3e1fd69e0453639091d93645bf5af0b9b2424cb2191c/shm
shm              64M     0   64M   0% /var/lib/docker/containers/a61ed2475f62935cc0f8bf312245bd3dbc11c456e47feb667eadadd911093a77/shm
shm              64M     0   64M   0% /var/lib/docker/containers/8fc618e9b1f7596d46aec8344e48a47a8efb7d3ce8078a5020932dc6b613a87a/shm
none            1.8T  291G  1.5T  17% /var/lib/docker/aufs/mnt/0402126d8554ab2c24bbff000636312f1f3920f06a5a7ef6972899cf4af10fc2
none            1.8T  291G  1.5T  17% /var/lib/docker/aufs/mnt/047b20e25af6dd410d77a069fd83bd943adae06412e7aa2658b7aa35931a86a0
none            1.8T  291G  1.5T  17% /var/lib/docker/aufs/mnt/8c5f12f259b6884abd0062021115ef1e26d133ed5bea6d407bd66322f2f859ca
none            1.8T  291G  1.5T  17% /var/lib/docker/aufs/mnt/b16819047c8dbe7b6b0606b4f8baeeb09be980380916d2f8daa8056408281862
shm              64M     0   64M   0% /var/lib/docker/containers/ef50a0b5a4363170899a50bbda92435c2f68a8a41cdb1c5d2dadba33c9e41b04/shm
shm              64M  4.0K   64M   1% /var/lib/docker/containers/e97028fb3e4d590e68a5d1c46a9b7d247bf7cd7f1d24f045301efd11fcb5771f/shm
shm              64M  4.0K   64M   1% /var/lib/docker/containers/812bc34d0b0d610f10758b7e166ea45d76af48225a511d0469bc60a36640814f/shm
shm              64M     0   64M   0% /var/lib/docker/containers/47ba16c10402e26f143a21a8f9c37a7c537a211bb3680a602b8c38efdf39dc4d/shm
```

---

### Post by Impavidus on 2019-02-22
Try a lower-level tool to get rid of the old kernels:```
dpkg --purge linux-image-4.13.0-32-generic linux-image-extra-4.13.0-32-generic
dpkg --purge linux-image-4.4.0-112-generic linux-image-extra-4.4.0-112-generic
dpkg --purge linux-image-4.4.0-139-generic linux-image-extra-4.4.0-139-generic
```
That may give you some headroom for other package management tools. Then fix the package manager and autoremove old packages:```
apt install -f
apt autoremove --purge
```
All these command have to run as root, but as you already use a root shell, there's no need for sudo.

---

### Post by pog22 on 2019-02-23
That cleaned up loads but some did not remove and gave an error that they were not empty

```

root@Ubuntu-1604-xenial-64-minimal ~ # dpkg --list | grep linux-image
ii  linux-image-4.15.0-42-generic         4.15.0-42.45~16.04.1                  amd64        Signed kernel image generic
ii  linux-image-4.15.0-43-generic         4.15.0-43.46~16.04.1                  amd64        Signed kernel image generic
rc  linux-image-4.4.0-135-generic         4.4.0-135.161                         amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-137-generic         4.4.0-137.163                         amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-138-generic         4.4.0-138.164                         amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-141-generic         4.4.0-141.167                         amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.8.0-58-generic          4.8.0-58.63~16.04.1                   amd64        Linux kernel image for version 4.8.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-135-generic   4.4.0-135.161                         amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-137-generic   4.4.0-137.163                         amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-138-generic   4.4.0-138.164                         amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-141-generic   4.4.0-141.167                         amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.8.0-58-generic    4.8.0-58.63~16.04.1                   amd64        Linux kernel extra modules for version 4.8.0 on 64 bit x86 SMP
ii  linux-image-extra-virtual             4.4.0.141.147                         amd64        Transitional package.
ii  linux-image-generic                   4.4.0.141.147                         amd64        Generic Linux kernel image
ii  linux-image-generic-hwe-16.04         4.15.0.43.64                          amd64        Generic Linux kernel image
root@Ubuntu-1604-xenial-64-minimal ~ #
```

---

### Post by pog22 on 2019-02-23
Ok. I have it nearly sorted but one will not remove

```

root@Ubuntu-1604-xenial-64-minimal ~ # dpkg --list | grep linux-image              ii  linux-image-4.15.0-42-generic         4.15.0-42.45~16.04.1                  amd64        Signed kernel image generic
ii  linux-image-4.15.0-43-generic         4.15.0-43.46~16.04.1                  amd64        Signed kernel image generic
pi  linux-image-4.4.0-141-generic         4.4.0-141.167                         amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
pi  linux-image-extra-4.4.0-141-generic   4.4.0-141.167                         amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-virtual             4.4.0.141.147                         amd64        Transitional package.
ii  linux-image-generic                   4.4.0.141.147                         amd64        Generic Linux kernel image
ii  linux-image-generic-hwe-16.04         4.15.0.43.64                          amd64        Generic Linux kernel image
root@Ubuntu-1604-xenial-64-minimal ~ # dpkg --purge linux-image-4.4.0-141-generic linux-image-extra-4.4.0-141-generic
dpkg: dependency problems prevent removal of linux-image-4.4.0-141-generic:
 linux-image-generic depends on linux-image-4.4.0-141-generic.

dpkg: error processing package linux-image-4.4.0-141-generic (--purge):
 dependency problems - not removing
dpkg: dependency problems prevent removal of linux-image-extra-4.4.0-141-generic:
 linux-image-generic depends on linux-image-extra-4.4.0-141-generic.

dpkg: error processing package linux-image-extra-4.4.0-141-generic (--purge):
 dependency problems - not removing
Errors were encountered while processing:
 linux-image-4.4.0-141-generic
 linux-image-extra-4.4.0-141-generic
root@Ubuntu-1604-xenial-64-minimal ~ #
```

---

### Post by Impavidus on 2019-02-23
Kernel 4.4.0-141 is the latest kernel for 16.04 without [hwe stack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack). It's pulled in by the **linux-image-generic** metapackage. As you installed the hwe stack for 16.04 (the package **linux-image-generic-hwe-16.04**), you also got the 4.15 kernel you want to use, so you can remove the 4.4 kernel.```
apt remove linux-image-generic
```Then you'll be able to remove the 4.4.0-141 kernel.

---

### Post by pog22 on 2019-02-23
I forgot I updated the kernel to enable the use of BBR on a Google Suite mount [https://www-techrepublic-com.cdn.ampproject.org/v/s/www.techrepublic.com/google-amp/article/how-to-enable-tcp-bbr-to-improve-network-speed-on-linux/?usqp=mq331AQECAFYAQ%3D%3D&amp_js_v=0.1#referrer=https%3A%2F%2Fwww.google.com&amp_tf=From%20%251%24s&ampshare=https%3A%2F%2Fwww.techrepublic.com%2Farticle%2Fhow-to-enable-tcp-bbr-to-improve-network-speed-on-linux%2F](https://www-techrepublic-com.cdn.ampproject.org/v/s/www.techrepublic.com/google-amp/article/how-to-enable-tcp-bbr-to-improve-network-speed-on-linux/?usqp=mq331AQECAFYAQ%3D%3D&amp_js_v=0.1#referrer=https%3A%2F%2Fwww.google.com&amp_tf=From%20%251%24s&ampshare=https%3A%2F%2Fwww.techrepublic.com%2Farticle%2Fhow-to-enable-tcp-bbr-to-improve-network-speed-on-linux%2F)

All is good now, thank you all for your time

---

