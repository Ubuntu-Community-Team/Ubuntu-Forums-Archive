---
title: "Ubuntu 22.04.0 64-bit LTS: Ubuntu Jammy Flathub Flatpak update error"
date: 2022-04-23
forum: General Help
---

### Post by Welly Wu on 2022-04-23
I did a bare metal clean installation of Ubuntu 22.04.0 64-bit LTS GNU/Linux on my late 2019 Computer Upgrade King Hewlett Packard Omen 15t gaming notebook PC on the primary ADATA SX8100NP M.2 PCI-e 3.0 NVMe 2.0 TB solid-state disk alongside Microsoft Windows 11 64-bit Pro edition version 21H2 on my secondary SanDisk Ultra SATA-III 6 GB/s 960.0 GB solid-state disk. The two different desktop operating systems are installed on two different internal solid-state disks and the GRUB 2 boot loader is working fine. UEFI, TPM 2.0, and Microsoft Secure Boot are enabled and the Nvidia 510-series graphics driver is working.

When I try to update Ubuntu by opening a terminal, I get this specific error with regard to the default Ubuntu 22.04.0 64-bit LTS Flathub flatpak repository:

```
wellywu@2019HPOmen15t-Ubuntu:~$ uname -r
5.15.0-25-generic
wellywu@2019HPOmen15t-Ubuntu:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 22.04 LTS
Release:    22.04
Codename:    jammy
wellywu@2019HPOmen15t-Ubuntu:~$ sudo apt update
[sudo] password for wellywu: 
Hit:1 [https://ocean.surfshark.com/debian](https://ocean.surfshark.com/debian) stretch InRelease
Hit:2 [https://dl.google.com/linux/chrome/deb](https://dl.google.com/linux/chrome/deb) stable InRelease                  
Hit:3 [https://apt.enpass.io](https://apt.enpass.io) stable InRelease                                   
Hit:4 [https://repo.protonvpn.com/debian](https://repo.protonvpn.com/debian) stable InRelease                       
Hit:5 [http://repository.spotify.com](http://repository.spotify.com) stable InRelease                           
Ign:6 [https://ppa.launchpadcontent.net/flatpak/stable/ubuntu](https://ppa.launchpadcontent.net/flatpak/stable/ubuntu) jammy InRelease
Hit:7 [https://ppa.launchpadcontent.net/gerardpuig/ppa/ubuntu](https://ppa.launchpadcontent.net/gerardpuig/ppa/ubuntu) jammy InRelease   
Get:8 [http://mirror.math.princeton.edu/pub/ubuntu](http://mirror.math.princeton.edu/pub/ubuntu) jammy InRelease [270 kB]     
Hit:9 [https://ppa.launchpadcontent.net/graphics-drivers/ppa/ubuntu](https://ppa.launchpadcontent.net/graphics-drivers/ppa/ubuntu) jammy InRelease
Hit:10 [http://mirror.math.princeton.edu/pub/ubuntu](http://mirror.math.princeton.edu/pub/ubuntu) jammy-updates InRelease
Hit:11 [http://mirror.math.princeton.edu/pub/ubuntu](http://mirror.math.princeton.edu/pub/ubuntu) jammy-backports InRelease
Hit:12 [http://mirror.math.princeton.edu/pub/ubuntu](http://mirror.math.princeton.edu/pub/ubuntu) jammy-security InRelease    
Hit:13 [https://ppa.launchpadcontent.net/heyarje/makemkv-beta/ubuntu](https://ppa.launchpadcontent.net/heyarje/makemkv-beta/ubuntu) jammy InRelease
Err:14 [https://ppa.launchpadcontent.net/flatpak/stable/ubuntu](https://ppa.launchpadcontent.net/flatpak/stable/ubuntu) jammy Release
  404  Not Found [IP: 91.189.95.85 443]
Reading package lists... Done                             
E: The repository 'https://ppa.launchpadcontent.net/flatpak/stable/ubuntu jammy Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
wellywu@2019HPOmen15t-Ubuntu:~$
```

It looks like this Flathub flatpak from Canonical, Ltd. for Ubuntu 22.04.0 64-bit LTS Jammy Jellyfish can not be found and it is missing a release file. Can someone explain to me what is going wrong here and how to fix it? Thank you.

Update: I do not remember how to share code on Ubuntu Forums as I have been inactive for a long period of time. I apologize for my error and I hope someone can teach me so I can correct it in the future.

---

### Post by Frogs Hair on 2022-04-23
The maintainers haven't updated the PPA yet. It's only been two days since release day.   

[https://launchpad.net/~flatpak/+archive/ubuntu/stable](https://launchpad.net/~flatpak/+archive/ubuntu/stable)
> This PPA is provided as a convenience for Ubuntu users, with no  guarantee of support.

---

### Post by TheFu on 2022-04-23
> **Welly Wu said:**
>  
Update: I do not remember how to share code on Ubuntu Forums as I have been inactive for a long period of time. I apologize for my error and I hope someone can teach me so I can correct it in the future.

The **adv reply** button has a (#) which is used just like any other quote, bold, underline, italics button.  Or you can use any of those other tags, then just replace whatever is between the start/end brackets with 'code' instead.

But with repos, there isn't really any columns, so it isn't hard to read.  That's were code tags REALLY  help - when output columns are involved.

---

### Post by Frogs Hair on 2022-04-23
To add code tags you can highlight the terminal output after pasted with the cursor and select the # symbol on the reply window Menu. 

```
terminal text 
```

---

### Post by Welly Wu on 2022-04-23
Thank you very much for the important information and the help. I learned my lessons fellow kind Ubuntu users. I do not mean to go off on a tangent, but Ubuntu 22.04.0 64-bit LTS is nice to use. Previously, I used Red Hat Fedora 36 Beta Workstation GNU/Linux and getting the proprietary Nvidia graphics drivers to install and work with the 510-series and Linux kernel version 5.17 AMD64 was a pain in the butt. Ubuntu is more user-friendly especially with UEFI, TPM 2.0, Intel SGX, and Microsoft Secure Boot.

---

