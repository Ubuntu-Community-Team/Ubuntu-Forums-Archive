---
title: "Unable to mount USB drives at boot"
date: 2016-05-12
forum: General Help
---

### Post by accessd on 2016-05-12
I'm hoping someone can help me. I'm running lubuntu 16.04 (upgraded from kodibuntu 14) running on a MintBox 2. The problem is that I cannot get USB drives to mount at boot. I have been trying to get an external USB 3.0 hard drive with an ntfs filesystem to mount when the computer starts up. When the machine is running and I plug the drive in, it automounts without issue. The drive also works flawlessly on my other computer running Ubuntu 12.04. However, when I create an fstab entry and restart, the computer boots into Emergency Mode, unless I set the "nofail" option. My current fstab entry is:

```
UUID=A2607CF0607CCD13 /home/jesse/TV\040Shows ntfs-3g rw,nosuid,nodev,relatime,user_id=0,group_id=0,default_permissions,allow_other,uhelper=udisks2,nofail 0 0
```

I have tried many different fstab options, but nothing seems to work. At first I thought it was because the drive was formatted as ntfs, but I formatted another usb drive as ext4 and got the same result. The relevant log entries that I have been able to find are as follows:

journalctl -b -p 3

```
May 08 22:31:19 mint-media-centre systemd[1]: Timed out waiting for device dev-disk-by\x2duuid-A2607CF0607CCD13.device.
```

/var/log/syslog

```
May  8 17:51:36 mint-media-centre systemd[1]: dev-disk-by\x2duuid-A2607CF0607CCD13.device: Job dev-disk-by\x2duuid-A2607CF0607CCD13.device/start timed out.
May  8 17:51:36 mint-media-centre systemd[1]: Timed out waiting for device dev-disk-by\x2duuid-A2607CF0607CCD13.device.
May  8 17:51:36 mint-media-centre systemd[1]: Dependency failed for /home/jesse/TV Shows.
May  8 17:51:36 mint-media-centre systemd[1]: home-jesse-TV\x20Shows.mount: Job home-jesse-TV\x20Shows.mount/start failed with result 'dependency'.
May  8 17:51:36 mint-media-centre systemd[1]: Startup finished in 6.575s (kernel) + 1min 33.883s (userspace) = 1min 40.459s.
May  8 17:51:36 mint-media-centre systemd[1]: dev-disk-by\x2duuid-A2607CF0607CCD13.device: Job dev-disk-by\x2duuid-A2607CF0607CCD13.device/start failed with result 'timeout'.
```

I have been searching Google and have not been able to find anything that seems to be relevant. If anyone can offer any guidance or suggestions, it would be very much appreciated.

---

### Post by accessd on 2016-05-16
Update: The drive now appears to be mounting at boot and I'm not sure what has changed. I will cross my fingers that it continues to work.

---

