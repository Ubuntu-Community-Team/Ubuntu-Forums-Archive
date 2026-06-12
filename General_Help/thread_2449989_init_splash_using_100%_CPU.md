---
title: "init_splash using 100% CPU"
date: 2020-09-05
forum: General Help
---

### Post by Paddy Landau on 2020-09-05
My Ubuntu 18.04 had a rather large update earlier this morning. Since then, the CPU has been running between 99% and 100% all the time, even after restarting the machine.

Running [FONT=lucida console]htop[/FONT] shows that the problematic job is [FONT=lucida console]/sbin/init_splash[/FONT] with a process ID of 1 and belonging to root. So, that's not weird :confused:

I tried running [FONT=lucida console]sudo[/FONT] [FONT=lucida console]apt[/FONT] [FONT=lucida console]update[/FONT] and had a lot of errors. At this point, the machine was heating up, so I powered it down (I'm writing this post from a different machine).

Do you have suggestions as to what I can do to fix this, please?

---

### Post by CatKiller on 2020-09-05
That's the part of the boot process that draws the splash screen. You could try changing your boot parameters to remove the "splash" part to see if it helps. You can do that as a one-off test by editing the kernel line at the Grub menu.

---

### Post by Paddy Landau on 2020-09-05
CatKiller, thank you for your advice.

I set [FONT=lucida console]GRUB_CMDLINE_LINUX_DEFAULT=""[/FONT], ran [FONT=lucida console]sudo[/FONT] [FONT=lucida console]update-grub2[/FONT], and restarted (see comment below about REISUB).

Unfortunately, it made no difference. That job [FONT=lucida console]init_splash[/FONT] still took over 99% and sometimes 100% of CPU.

I think that something has gone horribly wrong. Here are the other symptoms:

[LIST]
[*]When I try to boot into recovery mode, as soon as the menu appears, I get streams of error messages that pass too fast for me to read. If I guess where the menu options are, I can get into recovery mode, but the messages continue. I have to use REISUB (or REISUO) to terminate.
[*]When powered on, and I try to reboot or shut down, the system freezes, and again I need REISUB.
[*]I've run the following three commands, and they return no error.
```
sudo apt --fix-broken install
sudo dpkg --configure --pending
sudo apt autoremove
```
However, [FONT=&amp]sudo[/FONT] [FONT=&amp]apt[/FONT] [FONT=&amp]update[/FONT] returned plenty of errors. I've included them below.
[/LIST]
I suspect that I'll have to reinstall from scratch, which is an opportunity to upgrade to 20.04.

Errors from [FONT=lucida console]sudo[/FONT] [FONT=lucida console]apt[/FONT] [FONT=lucida console]update[/FONT]:
```
Hit:1 http://archive.ubuntu.com/ubuntu groovy InReleaseHit:2 http://archive.canonical.com/ubuntu bionic InRelease                                                                                                               
Ign:3 http://oem.archive.canonical.com/updates bionic-oem InRelease                                                                                                      
Hit:4 http://gb.archive.ubuntu.com/ubuntu bionic InRelease                                                                                                  
Hit:5 http://ppa.launchpad.net/alexlarsson/flatpak/ubuntu bionic InRelease                                                            
Ign:6 http://dell.archive.canonical.com/updates bionic-dell-beaver-osp1-graveler InRelease                                            
Hit:7 http://oem.archive.canonical.com/updates bionic-oem Release                                                                     
Hit:8 http://deb.playonlinux.com bionic InRelease                                                               
Ign:9 http://dell.archive.canonical.com/updates bionic-dell-service InRelease                                   
Get:10 http://security.ubuntu.com/ubuntu bionic-security InRelease [88.7 kB]              
Hit:11 http://dell.archive.canonical.com/updates bionic-dell InRelease                                 
Get:12 http://gb.archive.ubuntu.com/ubuntu bionic-updates InRelease [88.7 kB]                          
Hit:13 http://dell.archive.canonical.com/updates bionic-dell-beaver-osp1-graveler Release                          
Hit:14 http://dell.archive.canonical.com/updates bionic-dell-service Release                                       
Err:2 http://archive.canonical.com/ubuntu bionic InRelease                                    
  The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3B4FE6ACC0B21F32
Get:15 http://gb.archive.ubuntu.com/ubuntu bionic-backports InRelease [74.6 kB]
Err:4 http://gb.archive.ubuntu.com/ubuntu bionic InRelease
  The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3B4FE6ACC0B21F32
Hit:16 http://dl.google.com/linux/chrome/deb stable InRelease
Err:17 http://oem.archive.canonical.com/updates bionic-oem Release.gpg
  Detached signature file '/var/lib/apt/lists/oem.archive.canonical.com_updates_dists_bionic-oem_Release.gpg' is in unsupported binary format
Err:18 http://dell.archive.canonical.com/updates bionic-dell-beaver-osp1-graveler Release.gpg
  Detached signature file '/var/lib/apt/lists/dell.archive.canonical.com_updates_dists_bionic-dell-beaver-osp1-graveler_Release.gpg' is in unsupported binary format
Err:19 http://dell.archive.canonical.com/updates bionic-dell-service Release.gpg
  Detached signature file '/var/lib/apt/lists/dell.archive.canonical.com_updates_dists_bionic-dell-service_Release.gpg' is in unsupported binary format
Err:10 http://security.ubuntu.com/ubuntu bionic-security InRelease
  The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3B4FE6ACC0B21F32
Err:12 http://gb.archive.ubuntu.com/ubuntu bionic-updates InRelease
  The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3B4FE6ACC0B21F32
Err:15 http://gb.archive.ubuntu.com/ubuntu bionic-backports InRelease
  The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3B4FE6ACC0B21F32
Fetched 252 kB in 1s (419 kB/s)
Reading package lists... Done
Building dependency tree       
Reading state information... Done
4 packages can be upgraded. Run 'apt list --upgradable' to see them.
W: An error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://archive.canonical.com/ubuntu bionic InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3B4FE6ACC0B21F32
W: An error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://gb.archive.ubuntu.com/ubuntu bionic InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3B4FE6ACC0B21F32
W: An error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://oem.archive.canonical.com/updates bionic-oem Release: Detached signature file '/var/lib/apt/lists/oem.archive.canonical.com_updates_dists_bionic-oem_Release.gpg' is in unsupported binary format
W: An error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://dell.archive.canonical.com/updates bionic-dell-beaver-osp1-graveler Release: Detached signature file '/var/lib/apt/lists/dell.archive.canonical.com_updates_dists_bionic-dell-beaver-osp1-graveler_Release.gpg' is in unsupported binary format
W: An error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://dell.archive.canonical.com/updates bionic-dell-service Release: Detached signature file '/var/lib/apt/lists/dell.archive.canonical.com_updates_dists_bionic-dell-service_Release.gpg' is in unsupported binary format
W: An error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://security.ubuntu.com/ubuntu bionic-security InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3B4FE6ACC0B21F32
W: An error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://gb.archive.ubuntu.com/ubuntu bionic-updates InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3B4FE6ACC0B21F32
W: An error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://gb.archive.ubuntu.com/ubuntu bionic-backports InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3B4FE6ACC0B21F32
N: Skipping acquisition of configured file 'main/binary-i386/Packages', as repository 'http://dl.google.com/linux/chrome/deb stable InRelease' doesn't support architecture 'i386'
W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/bionic/InRelease  The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3B4FE6ACC0B21F32
W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/bionic-updates/InRelease  The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3B4FE6ACC0B21F32
W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/bionic-backports/InRelease  The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3B4FE6ACC0B21F32
W: Failed to fetch http://archive.canonical.com/ubuntu/dists/bionic/InRelease  The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3B4FE6ACC0B21F32
W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/bionic-security/InRelease  The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3B4FE6ACC0B21F32
W: Failed to fetch http://oem.archive.canonical.com/updates/dists/bionic-oem/Release.gpg  Detached signature file '/var/lib/apt/lists/oem.archive.canonical.com_updates_dists_bionic-oem_Release.gpg' is in unsupported binary format
W: Failed to fetch http://dell.archive.canonical.com/updates/dists/bionic-dell-beaver-osp1-graveler/Release.gpg  Detached signature file '/var/lib/apt/lists/dell.archive.canonical.com_updates_dists_bionic-dell-beaver-osp1-graveler_Release.gpg' is in unsupported binary format
W: Failed to fetch http://dell.archive.canonical.com/updates/dists/bionic-dell-service/Release.gpg  Detached signature file '/var/lib/apt/lists/dell.archive.canonical.com_updates_dists_bionic-dell-service_Release.gpg' is in unsupported binary format
W: Some index files failed to download. They have been ignored, or old ones used instead.
```

---

### Post by tea for one on 2020-09-05
Did the update provide a new kernel?

If so, have you tried an earlier one?

---

### Post by Paddy Landau on 2020-09-05
> **tea for one said:**
> Did the update provide a new kernel?
No, not a new kernel.

But, I've decided to reinstall from scratch, using 20.04 instead of 18.04.

Thanks anyway!

---

