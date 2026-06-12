---
title: "GRUB kernel update problem on 22.04 ZFS"
date: 2023-05-18
forum: General Help
---

### Post by libertyspike138 on 2023-05-18
I have 22.04 installed on ZFS and everything is fine except every time I install a kernel update I need to manually fix it. What happens is I will reboot and land in initramfs where it asks me to manually mount the rpool, I do so and it still cannot find the linux image. I have to fix it by changing the linux path in my grub configuration, The reason this is happening is because "rpool" is missing from the beginning of the path. For example my grub configuration will read:
linux	/BOOT/ubuntu_d02ehm@/vmlinuz-5.19.0-41-generic root=ZFS=/ROOT/ubuntu_d02ehm ro  intremap=off pcie_aspm=off mds=full intel_iommu=on iommu=pt splash $vt_handoff
whereas it should instead be:
linux	/BOOT/ubuntu_d02ehm@/vmlinuz-5.19.0-41-generic root=ZFS=rpool/ROOT/ubuntu_d02ehm ro  intremap=off pcie_aspm=off mds=full intel_iommu=on iommu=pt splash $vt_handoff

How can I permanently fix this so that every time there is a kernel update I do not need to fix my grub configuration to boot into the new one?

---

### Post by libertyspike138 on 2023-05-18
I thought that this may have something to do with the scripts in /etc/grub.d because on a working system of the same the entries populate with the linux_zfs script but these entries that need to be corrected get populated with linux script so I tried replacing the scripts from a freshly installed working system and updating grub but get another error.
Generating grub configuration file ...
/etc/grub.d/10_linux_zfs: 404: .: cannot open /tmp/zfsmnt.dCD7rF/etc/os-release: No such file

---

### Post by libertyspike138 on 2023-05-18
Apparently others have experienced this error as well but I'm not understanding how to resolve it.
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1899372](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1899372)

---

### Post by libertyspike138 on 2023-06-19
This is a server and besides Ubuntu I also have TrueNAS installed to another disk as a backup to get to my files if for some reason I can't get in. What I have discovered is that anytime the disk containing TrueNAS is connected the GRUB scripts for ZFS take a dump and leave the "/etc/grub.d/10_linux_zfs: 404: .: cannot open /tmp/zfsmnt.dCD7rF/etc/os-release: No such file " error. I initially thought that maybe grub-customizer had botched it so I backed up my home and reinstalled the OS leaving out grub-customizer and manually editing my GRUB. I was having a black screen GRUB issue before enabling console mode and when I updated GRUB I noticed the script took a dump again so I thought to eject the disk with TrueNAS and try to update GRUB again so I'm not left in an unbootable state and it solved the issue. So now I have just disabled the port for my TrueNAS backup inside the BIOS and all seems well. The reason that rpool was missing in the grub.cfg is because it was adding the entries under linux instead of linux_zfs scripts. If anybody else has this issue pay attention to the scripts in /etc/grub.d/ to find out where your entries are being generated and disable or remove any other ZFS / Solaris type disks that may be conflicting. Other than that I'm not sure how else to leave the TrueNAS drive enabled and not have GRUB take a dump but in my case it is no big deal considering it is just a backup OS that I can leave disabled.

---

### Post by MAFoElffen on 2023-06-19
What a mess... Let me try to get this straight in my head. 

I'm sorry that I had overlooked and not seen this thread earlier...

The bug you posted the link to, that has nothing to do with anything you posted about, and what you described of what was going on.

This would be so much simpler if you ran both the 'boot-repair' and the UbuntuForums 'system-info' scripts and post the URL's of the reports. When you run the system-info script with the '--details' option to show the ZFS volume manager details. When you run the 'boot-info' report, do not do the suggest repair (yet).

I need to know how you installed this and how you have booth Ubuntu and TrueNAS installed and configured. You mentioed "Server". So I'm wondering, if like me, that you install ZFS-On-Root manually, as a minimal System to install 'ubuntu-server' onto, or you used the Ubuntu Desktop Editition ISO to install from it's ZFS install script, then install server services to run on that... A big difference in how that can vary between those two methods. Also, run the script from Yann's PPA. It is up-to-date and has the latest code there for ZFS. I know, becasue i contributed it.

So:
```

wget -N -t 5 -T 10 https://github.com/UbuntuForums/system-info/raw/main/system-info && \
chmod +x system-info && \
./system-info --details

sudo add-apt-repository ppa:yannubuntu/boot-repair
sudo apt update
sudo apt install boot-repair
boot-info

```

I myself have had that same specific problem with a few VM's in my test section, when I was doing testing on Lunar during the dev cycle for 23.04, where Grub was not adding the dataset name 'rpool' to the command line, to find the kernel. At the time, I just created a quick 40_custom file to boot it... I didn't pursue it earlier, because I thought that maybe it was just a fluke, and only affecting me. I didn't pursue it earlier, because I thought that maybe it was just a fluke, and only affecting me. When I'm doing my testing for the dev cycles, and for the scripts I work on, I come up with some fairly complex configurations to test against.

So, if this is the same kind of thing, I can share the work-around I did... Then, since I already have something here that has the same thing going on, ad have the problem replicated, I can sped the time to see what is wrong, and how to maybe correct it.

I am curious about it now...

---

