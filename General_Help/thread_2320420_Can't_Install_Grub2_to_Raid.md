---
title: "Can't Install Grub2 to Raid"
date: 2016-04-13
forum: General Help
---

### Post by theonlytalkinggoat on 2016-04-13
Background: 

I am trying to create a RAID5 array, with 3, 2tb hard drives. The array appears to create and I can go in, create my partitions and install. Disks tells me there is an issue with one of the drives, but it's probably because it's initilizing. 

[IMG]https://lh3.googleusercontent.com/ReusseupCMY816TqXLj-FGVySMAsuLMV664HGUNvsJrq3lABRkBSwa62X2Qp7whANdYZRmq_Idm7K_Fk8rlgw1XdBDHOF8wk77ReQ8A4NBtIqm5qRgZ3d9l5aSvMEJKAKjQhNNq6iu9aiV9Djd6Pz-bgAfX3IElA_OwSpkddD8k7fV5Wk6XOiXNHbPxQec5yNPOL965Yl3o8KV0GtSYiPjk2gtgBaCM0eAC_d7tOU0y7vFLiF3O2WaobbTKcySnfFOemU1M5QaR3GtPfGFla9Vex3m5D7l5EcF8icYVGT5if53vgOGzkhP3Ty6Ftt2cVhv7ZmJiGVTdEb4tDNHiCaFmX7eCRgwFjWtUeHL_j8ay2XFCT2wvsFpAkHmNr7jYg67REQxp_2BF7viG4iyi5A5WcGKq73S-dTyPd2LwMnKZvVCMPy2K_XlMe9_nu94bQZTKjQCkWgFIKHS0YZ0nlDCB_o3lD7qYP1WlBDCKLQsFIwCOidpdi0zo96g8XANZCwXXVp1gk0JNLtmkQULUiWriQGmhnrYX9J5NT0XUjSpk03Rd0KdiBx2hTffSKECM22mA=w801-h726-no[/IMG]
[IMG]https://lh3.googleusercontent.com/yelKL17zHCgHFs7m-omwMqwkZjXeaKduEzkrjEPENo_s0-IJ6yeYTodlOisXObbduuuN7graVPpg8AWUNuIarDFAbeRQOGH_bF8AlU8e57d879V9I5S83-s1p4HNTkOg_eCJuhLdfcTUw6lxd-2B9WWPqtRyTrza_HcJAbMM64X_gRjwmSWVJeJMf3QXos7gVCQ5U-RnCdsk9hhcm5xsXYNV4lrpzgR_xcNaJXguBh_Je42OQjusrihy8ubFcqKIibsP8aNC7syIVxeH1M8ScnLiPJi5tOxP8BTzUFZAYKPw0wEjZD_fHgsDJu7Zb6TP0qcS40dSAG2FEaA68wmNuhkMxh0L-24EyPWozgbRdzE8I6NHLExDpXweVW4rfCaVSPiIcYssv_BLiu-dfcm240uOnAUe12riWoP2eeFQPTec2v3WMwvfZGsqteU3dxr1WS_hbjuk833K2WscriCObehkRKFcnzDhQSxhbKRNLiMnkP0YQzQJojuqz1WmfXqYjlUjPqrDXs7eRtOJN2D-UIpTHbsJDaqSyPs7xXfcG7fkE6-_UZERMloov7vndXaF98M=w807-h732-no[/IMG]

Here is the problem... 

At the end of the install process, when the installer is trying to put grub on /dev/mdX, it completely ignores that I told it to go onto /dev/md127 and tries to install it to /dev/md127p3, which is the root mount point ( / ). 

[IMG]https://lh3.googleusercontent.com/WfWJI7cHUouWB6ECEGtdUKYzKNhK2ABtUs58OmEeWXEr_ph-Uw73_ZIr4YacvdveTo6DaeU6py3QYSYf4DFVOD_Nop95BG-_8OLnnIJ8cpO24NN8X7xM6BHSSW8uTdjAU3JPurdsG0fCyZqpNQ9djAzkFkJ7uK5YEeAmQwkoFt8X3FnwEUjBkyYFP7Vr-x_isuVV7LwnWdXhFCu-SkmpgaQux3aaxKGs7UQfJxzvvQcqiYTdr-cGfoCvtSkDX2lSiBnvdUgSc92CMEgjZPiK84EYPzcx5LIS-1FfSdG_LXuLEQAX3gvo4hVxAaTjA_D2opsqQYMG_qS9qXFtD8FrJ7kCB7uV2RzVWzi270FvLkhNNSGUAzfh2Q-niAmY4a4SM5j_5A-nhyxcHoN7M--zSGDia6x71z7i7ykRS-t2lAFBLGxFn4qiLjaKmGAu88PrxZcTBRsJD0E0aqruAoyrnvz8qtWcyDZNk1Sl6jjwFQYgiYUn5wVO391WRvleEhecqncVr4k5zXLRQBuatl2Zyi882yO3ClhlEp4aADxKmAbw5ZA_zv-BHiFbvm6yg2RObmp8UQ=w1215-h912-no[/IMG]

So, another menu comes up and asks, again, where to install Grub and, again, I tell it, /dev/md127 and it completes, with no apparent error. When I try to boot the system, however, I get nothing... Insert boot disk. 

I tried booting into the live cd and manually putting grub into /dev/md127, but I get the errors...

```
root@ubuntu:/# grub-install --boot-directory=/mnt/boot /dev/md127Installing for i386-pc platform.
grub-install: warning: Couldn't find physical volume `(null)'. Some modules may be missing from core image..
grub-install: warning: Couldn't find physical volume `(null)'. Some modules may be missing from core image..
grub-install: error: diskfilter writes are not supported.
```

I am *THINKING* it is doing this, because it's rebuilding and once it's finished, it'll be ok, but I don't know. I found a couple other people complaining about a bug, however, I've installed Ubuntu 14.04 on dozens of servers and I've never come across this error or this problem. Maybe it's because the drives are softwre raid and not on an actual raid card? I have been working on this for over 24 hours and I can't figure out what to do, from here. Does anyone have any advise?

---

### Post by theonlytalkinggoat on 2016-04-14
UPDATE: The problem with the missing modules went away, after the array finished syncing. The other issue, diskfilter writes are not supported, however, persists. I found a bug report, #1274320, however, it should not apply, because I'm using grub 2.02, which should have been fixed. Does anyone have any ideas?

---

### Post by oldfred on 2016-04-14
Do not know RAID, but have this in my notes on grub installs.
Usually p127 is from an error as most do not have 127 partitions.
But with fakeRAID you install to the mapper, similar to example below.

 Does not recommend "fakeRAID"
[http://aryklein.wordpress.com/2013/10/28/a-quick-guide-to-linux-software-raid/](http://aryklein.wordpress.com/2013/10/28/a-quick-guide-to-linux-software-raid/)
[https://raid.wiki.kernel.org/index.php/DDF_Fake_RAID](https://raid.wiki.kernel.org/index.php/DDF_Fake_RAID)
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)
"fakeRaid" with nVidia, note p1 is partition, without p1 is root of RAID volume
sudo mount /dev/mapper/isw_cdjacjeebj_VOLUME_0p1 /mnt
sudo grub-install --root-directory=/mnt /dev/mapper/isw_cdjacjeebj_VOLUME_0
Hardware RAID drivers
[https://wiki.debian.org/LinuxRaidForAdmins](https://wiki.debian.org/LinuxRaidForAdmins)

---

