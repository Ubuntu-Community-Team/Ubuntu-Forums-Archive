---
title: "iPhone, 16.04.1"
date: 2016-12-17
forum: General Help
---

### Post by adagio on 2016-12-17
Connecting an iPhone and retrieving photos with Shotwell has worked in the past (as recently as 16.04), the following error at the moment though with 16.04.1:

```
file failed to import due to a camera error
```

Attempting to mount with ifuse:

```
GnuTLS error: Error in the pull function.
Failed to connect to lockdownd service on the device.
Try again. If it still fails try rebooting your device.
```

`ideviceinfo` output:

```
GnuTLS error: Error in the pull function.
ERROR: Could not connect to lockdownd, error code -5
```

[EDIT]

Possibly related to this [https://github.com/libimobiledevice/libimobiledevice/issues/380](https://github.com/libimobiledevice/libimobiledevice/issues/380), linked to from this post [http://askubuntu.com/questions/830803/cant-mount-iphone-5s-with-ios10](http://askubuntu.com/questions/830803/cant-mount-iphone-5s-with-ios10) - libimobiledevice is currently at 1.2.0 in Xenial.

Running the shell script linked to in this post [http://askubuntu.com/questions/812006/how-can-i-mount-my-iphone-6s-on-ubuntu-16-04](http://askubuntu.com/questions/812006/how-can-i-mount-my-iphone-6s-on-ubuntu-16-04) the error from Shotwell is now:

```
Unable to lock camera: Could not claim the USB device (-53)
```

[EDIT]

Have been able to import a folder of images from the 'phone into Shotwell.

---

