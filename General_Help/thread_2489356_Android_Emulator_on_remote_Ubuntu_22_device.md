---
title: "Android Emulator on remote Ubuntu 22 device"
date: 2023-07-27
forum: General Help
---

### Post by blue-flamingo on 2023-07-27
Hello,
I'm trying to run the Android Studio Emulator on an Arm64 device.  The intention is to run it hardware headless but not software headless, in other words outputting to a monitor that will never be there and using the command line for control.


I'm not able to simply install the Android Studio as Arm64 systems are not supported by it, however the rest of the tools can be installed manually and do support Arm64.  I've installed the Command Line Tools manually.  I couldn't automatically install the Build Tools, and the Platform tools etc. until the Emulator was installed.  I had to manually install the Emulator and get the *sdkmanager* to recognise it but now all parts are installed.  I can run *sdkmanager --list_installed* and it shows that I've all these 'packages' installed:
```
Installed packages:
  Path                                           | Version    | Description
  -------                                        | -------    | -------
  build-tools;34.0.0-rc3                         | 34.0.0 rc3 | Android SDK Build-Tools 34-rc3 
  cmdline-tools;latest                           | 9.0        | Android SDK Command-line Tools (latest) 
  emulator                                       | 32.1.13    | Android Emulator
  patcher;v4                                     | 1          | SDK Patch Applier v4
  platform-tools                                 | 34.0.4     | Android SDK Platform-Tools
  system-images;android-31;google_apis;arm64-v8a | 10         | Google APIs ARM 64 v8a System Image

```I'm able to use the *avdmanager* to create a Android Virtual Device image:
```
$ ./avdmanager -v create avd -f -n MyAVD -k "system-images;android-31;google_apis;arm64-v8a"

```and I can list the disk image with
```
$ ./avdmanager list
Available Android Virtual Devices:
    Name: MyAVD
    Path: /home/user/testing/android_devices/MyAVD.avd
  Target: Google APIs (Google Inc.)
          Based on: Android 12.0 (S) Tag/ABI: google_apis/arm64-v8a

```
However when I try to load the image using the *emulator* command from the emulator folder and this happens:
```
$ emulator -avd @MyAVD
-bash: /home/user/android_sdk/emulator/emulator: Permission denied

```So I tried maxxing the authority of the request with *sudo*:
```
$ sudo emulator -avd @MyAVD
sudo: emulator: command not found

```And then tried with *./emulator* and got the same results.
I decided to get a bit heavy handed and recursively set all ownership to both *'user'* and then *'root'* but didn't get a different result.
```
$ sudo chown root $ANDROID_HOME -R
$ sudo chgrp root $ANDROID_HOME -R

```Given denying permission to something suggests the something exists I find that reassuring, however for it then to be 'not found' with sudo I find it quite interesting and it suggests an unknown OS reason to me (I'm not that Ubuntu / Linux savvy.)

---

### Post by TheFu on 2023-07-30
The userid and root (when run under sudo) have different PATHs. That's all.

---

