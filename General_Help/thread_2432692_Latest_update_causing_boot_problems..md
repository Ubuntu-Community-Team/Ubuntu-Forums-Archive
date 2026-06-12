---
title: "Latest update causing boot problems."
date: 2019-12-06
forum: General Help
---

### Post by mauser9069 on 2019-12-06
Xubuntu 18.04LTS. I received an update this morning that I installed but when I shut off my computer this afternoon and later when I went to boot it up after the Xubuntu splash screen the screen went blank and the key board and mouse went dead. I hit the power button and tried to boot again and the same happened. Then tried booting selecting advanced options with the same result. Then I tired booting with kernel 5.0.0-36-generic and while typing my password in it froze. Hit the power button again booting regular from kernel 5.0.0-37-generic which worked. I am afraid to reboot because of this. My computer was working fine until today's update. Is there any way to remove this latest update and if so how?

---

### Post by mauser9069 on 2019-12-06
I would like to add that at random times, Firefox has been freezing which is followed by the whole computer locking up since the last update this morning. On a positive note Xubuntu has started booting fine. Does anyone know how I can remove this last update that is causing all this trouble?

---

### Post by odee2 on 2019-12-07
I had same problem with ubuntu in last update, i think there is a intel driver who causes a problems, I just reinstalled whole ubuntu to kubuntu.

---

### Post by Impavidus on 2019-12-07
It may help if you tell us what packages were involved in your last upgrade. The log files may help:```
grep " upgrade " /var/log/dpkg.log
```
When you upgrade the kernel, the old kernel is not automatically removed. You can still boot it from the grub menu.

Sometimes you can choose among different versions of a package, like one from the original release and one from the -updates or -proposed repository (unless you want to test or urgently need a bugfix, keep -proposed disabled). Most of the time, this is not a good idea. Or you can restore from a backup or downgrade the package if the old version is still in your cache. But in general, there's no way to reverse an upgrade. And I've never needed it in 13 years of using Ubuntu.

---

### Post by Artim on 2019-12-07
The latest update included GRUB 2.  I wonder if that's what's wrong.  It hasn't caused me any issues, but on some hardware it seems to.

---

### Post by mauser9069 on 2019-12-07
> **odee2 said:**
> I had same problem with ubuntu in last update, i think there is a intel driver who causes a problems, I just reinstalled whole ubuntu to kubuntu.

Thanks. I don't have anything from Intel on my computer as it's AMD.

---

### Post by mauser9069 on 2019-12-07
> **Impavidus said:**
> It may help if you tell us what packages were involved in your last upgrade. The log files may help:```
grep " upgrade " /var/log/dpkg.log
```
When you upgrade the kernel, the old kernel is not automatically removed. You can still boot it from the grub menu.

Sometimes you can choose among different versions of a package, like one from the original release and one from the -updates or -proposed repository (unless you want to test or urgently need a bugfix, keep -proposed disabled). Most of the time, this is not a good idea. Or you can restore from a backup or downgrade the package if the old version is still in your cache. But in general, there's no way to reverse an upgrade. And I've never needed it in 13 years of using Ubuntu.

Thanks. This is the offending update. 2019-12-06 12:19:30 upgrade grub-pc:amd64 2.02-2ubuntu8.13 2.02-2ubuntu8.14
2019-12-06 12:19:31 upgrade grub2-common:amd64 2.02-2ubuntu8.13 2.02-2ubuntu8.14
2019-12-06 12:19:33 upgrade grub-pc-bin:amd64 2.02-2ubuntu8.13 2.02-2ubuntu8.14
2019-12-06 12:19:38 upgrade grub-efi-amd64-signed:amd64 1.93.14+2.02-2ubuntu8.13 1.93.15+2.02-2ubuntu8.14
2019-12-06 12:19:41 upgrade grub-efi-amd64-bin:amd64 2.02-2ubuntu8.13 2.02-2ubuntu8.14
2019-12-06 12:19:45 upgrade grub-common:amd64 2.02-2ubuntu8.13 2.02-2ubuntu8.14
The previous boot up locked up during typing my login password. I had to push the power button because my computer had locked up so hard. The following boot up worked. I don't believe it's the kernel version because trying a different kernel didn't fix the problem. If I need to do a re-install and restore from my back up I will go with an other distro. I will wait to see if any knows a way of removing this update or if a new update corrects the instability when ever a new update comes out.

---

### Post by lvm on 2019-12-08
Looks like I am in the same boat with you guys :( During the last update I've got 

Setting up grub-efi-amd64-signed (1.93.15+2.02-2ubuntu8.14) ... 
Installing for x86_64-efi platform. 
Could not delete variable: Invalid argument 
grub-install: error: efibootmgr failed to register the boot entry: Block device required. 
dpkg: error processing package grub-efi-amd64-signed (--configure): 
installed grub-efi-amd64-signed package post-installation script subprocess returned error exit status 1 
Errors were encountered while processing: 
grub-efi-amd64-signed 
E: Sub-process /usr/bin/dpkg returned an error code (1)

and now I am afraid to reboot. kubuntu 18.04

---

### Post by Impavidus on 2019-12-08
Maybe there was something wrong with the update-grub script that caused a wrong kernel boot option. Try to use [Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) to create a boot info summary and show us the link. And did you have to set any boot options to make your computer work, like nomodeset?

---

### Post by mauser9069 on 2019-12-08
> **Impavidus said:**
> Maybe there was something wrong with the update-grub script that caused a wrong kernel boot option. Try to use [Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair") to create a boot info summary and show us the link. And did you have to set any boot options to make your computer work, like nomodeset?
  I have no options set. I can eventually get it to boot but I get random hard freezes where nothing responds at all including X-Kill. As for Boot Repair, it's too confusing unlike Boot Repair in MX Linux which is user friendly. I am going to wait for an update to fix the update that broke Xubuntu. The Saturday update did improve stability but Xubutu is still unstable unlike before the offending update that broke it when it was solid as a rock. If the fix doesn't come by the time I finish updating my back ups I will install a different distro.

---

### Post by rinnnn2 on 2019-12-10
I have something similar, started this morning... 

> 
tail -n 30 /var/log/apt/history.log
Start-Date: 2019-12-06  09:11:38
Commandline: /usr/bin/unattended-upgrade
Upgrade: intel-microcode:amd64 (3.20191115.1ubuntu0.18.04.1, 3.20191115.1ubuntu0.18.04.2)
End-Date: 2019-12-06  09:11:52


Start-Date: 2019-12-10  09:36:29
Commandline: aptdaemon role='role-commit-packages' sender=':1.253'
Upgrade: grub-common:amd64 (2.02-2ubuntu8.13, 2.02-2ubuntu8.14), slack-desktop:amd64 (4.1.2, 4.2.0), grub2-common:amd64 (2.02-2ubuntu8.13, 2.02-2ubuntu8.14), grub-pc:amd64 (2.02-2ubuntu8.13, 2.02-2ubuntu8.14), grub-pc-bin:amd64 (2.02-2ubuntu8.13, 2.02-2ubuntu8.14), firefox-locale-de:amd64 (70.0.1+build1-0ubuntu0.18.04.1, 71.0+build5-0ubuntu0.18.04.1), firefox-locale-en:amd64 (70.0.1+build1-0ubuntu0.18.04.1, 71.0+build5-0ubuntu0.18.04.1), firefox-locale-nb:amd64 (70.0.1+build1-0ubuntu0.18.04.1, 71.0+build5-0ubuntu0.18.04.1), firefox-locale-ru:amd64 (70.0.1+build1-0ubuntu0.18.04.1, 71.0+build5-0ubuntu0.18.04.1), firefox-locale-uk:amd64 (70.0.1+build1-0ubuntu0.18.04.1, 71.0+build5-0ubuntu0.18.04.1), unattended-upgrades:amd64 (1.1ubuntu1.18.04.12, 1.1ubuntu1.18.04.13), libnss3:amd64 (2:3.35-2ubuntu2.5, 2:3.35-2ubuntu2.6), firefox:amd64 (70.0.1+build1-0ubuntu0.18.04.1, 71.0+build5-0ubuntu0.18.04.1), linux-firmware:amd64 (1.173.12, 1.173.13)
Error: Sub-process /usr/bin/dpkg exited unexpectedly
End-Date: 2019-12-10  16:40:22


Start-Date: 2019-12-10  16:45:59
Commandline: aptdaemon role='role-commit-packages' sender=':1.403'
Upgrade: python-samba:amd64 (2:4.7.6+dfsg~ubuntu-0ubuntu2.13, 2:4.7.6+dfsg~ubuntu-0ubuntu2.14), libwbclient0:amd64 (2:4.7.6+dfsg~ubuntu-0ubuntu2.13, 2:4.7.6+dfsg~ubuntu-0ubuntu2.14), skypeforlinux:amd64 (8.54.0.91, 8.55.0.123), samba-libs:amd64 (2:4.7.6+dfsg~ubuntu-0ubuntu2.13, 2:4.7.6+dfsg~ubuntu-0ubuntu2.14), samba-common:amd64 (2:4.7.6+dfsg~ubuntu-0ubuntu2.13, 2:4.7.6+dfsg~ubuntu-0ubuntu2.14), libsmbclient:amd64 (2:4.7.6+dfsg~ubuntu-0ubuntu2.13, 2:4.7.6+dfsg~ubuntu-0ubuntu2.14), smbclient:amd64 (2:4.7.6+dfsg~ubuntu-0ubuntu2.13, 2:4.7.6+dfsg~ubuntu-0ubuntu2.14), samba-common-bin:amd64 (2:4.7.6+dfsg~ubuntu-0ubuntu2.13, 2:4.7.6+dfsg~ubuntu-0ubuntu2.14)
Error: Sub-process /usr/bin/dpkg returned an error code (1)
End-Date: 2019-12-10  16:53:40


Start-Date: 2019-12-10  16:57:07
Commandline: synaptic
Requested-By: me (1000)
Remove: evolution-ews:amd64 (3.28.5-0ubuntu0.18.04.1), evolution-indicator:amd64 (0.2.20-0ubuntu33), evolution-common:amd64 (3.28.5-0ubuntu0.18.04.1), evolution-plugin-bogofilter:amd64 (3.28.5-0ubuntu0.18.04.1), evolution-plugin-pstimport:amd64 (3.28.5-0ubuntu0.18.04.1), evolution-plugins:amd64 (3.28.5-0ubuntu0.18.04.1), libevolution:amd64 (3.28.5-0ubuntu0.18.04.1), evolution:amd64 (3.28.5-0ubuntu0.18.04.1)
Error: Sub-process /usr/bin/dpkg returned an error code (1)
End-Date: 2019-12-10  16:58:15


Start-Date: 2019-12-10  17:05:45
Commandline: synaptic
Requested-By: me (1000)
Reinstall: grub-pc-bin:amd64 (2.02-2ubuntu8.14)
Error: Sub-process /usr/bin/dpkg exited unexpectedly
End-Date: 2019-12-10  17:07:20




It stuck on the grub-pc configuration. So I tried to revert to grub 2.02-2ubuntu8.13, and it stuck the same way.

It seems it calls internally "/var/lib/dpkg/info/grub-pc.postinst configure 2.02-2ubuntu8.13"  (or "/var/lib/dpkg/info/grub-pc.postinst configure 2.02-2ubuntu8.14") which in turn is stack at the "grub-mkdevicemap -m - " command.  Indeed, there are lots of them still stuck running, including the morning's one (I haven't rebooted yet, actually the stuck update prevents rebooting and it is easier to fix things beforehand):

> 
ps axwwwu | grep -i grub-mkdevicemap
root     18790  0.0  0.0  37236   152 ?        DN   09:37   0:00 grub-mkdevicemap -m -
root     18981  0.0  0.0  37236  1672 ?        DN   16:46   0:00 grub-mkdevicemap -m -
root     20660  0.0  0.0  37236  1548 ?        D    16:57   0:00 grub-mkdevicemap -m -
root     21615  0.0  0.0  37236  1588 ?        D    17:05   0:00 grub-mkdevicemap -m -
root     24443  0.0  0.0  37236  1668 pts/5    D    17:26   0:00 grub-mkdevicemap -m -
root     28210  0.0  0.0  37236  1592 pts/0    D+   17:59   0:00 grub-mkdevicemap -m -
root     29076  0.0  0.0  24716  2692 pts/5    S+   18:15   0:00 grep --color=auto -i grub-mkdevicemap


Seems to me like [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/426239](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/426239) , the process 18790 cannot be killed even by sudo kill -9 18790...

Does anyone have an advice?

---

### Post by rinnnn2 on 2019-12-11
Update: rebooted ok and everything went well then.

---

