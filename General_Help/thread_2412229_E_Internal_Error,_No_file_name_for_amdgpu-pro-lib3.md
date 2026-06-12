---
title: "E: Internal Error, No file name for amdgpu-pro-lib32:amd64"
date: 2019-02-09
forum: General Help
---

### Post by Autodave on 2019-02-09
Started today: getting an error screen after booting.  Only one time did it say what was wrong and that was in the amdgpu files.  I installed the newest 18.50 update from the AMDGPU website, but still getting errors when booting.  However, everything seems to be working just fine.  What should I do?

---

### Post by Autodave on 2019-02-10
This is as far as I have been able to get:

dave@dave-MS-7641:~$ sudo apt-get upgrade
[sudo] password for dave: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt --fix-broken install' to correct these.
The following packages have unmet dependencies:
 amdgpu : Depends: amdgpu-lib (= 18.50-725072) but it is not installed
 amdgpu-lib32 : Depends: amdgpu-lib (= 18.50-725072) but it is not installed
                Depends: libllvm7.0-amdgpu:i386 (= 1:7.0-725072)
                Depends: libwayland-amdgpu-egl1:i386 (= 1.15.0-725072)
                Depends: libegl1-amdgpu-mesa:i386 (= 1:18.2.0-725072)
                Depends: libgl1-amdgpu-mesa-dri:i386 (= 1:18.2.0-725072)
                Depends: mesa-amdgpu-va-drivers:i386 (= 1:18.2.0-725072)
                Depends: mesa-amdgpu-vdpau-drivers:i386 (= 1:18.2.0-725072)
 libegl1-amdgpu-mesa-drivers : Depends: libegl1-amdgpu-mesa (= 1:18.2.0-725072) but 1:18.1.0-676022 is installed
                               Depends: libwayland-amdgpu-egl1 but it is not installed
 libegl1-amdgpu-mesa-drivers:i386 : Depends: libegl1-amdgpu-mesa:i386 (= 1:18.2.0-725072) but 1:18.1.0-676022 is installed
                                    Depends: libwayland-amdgpu-egl1:i386 but it is not installed
 libxatracker2-amdgpu : Depends: libllvm7.0-amdgpu but it is not installed
 libxatracker2-amdgpu:i386 : Depends: libllvm7.0-amdgpu:i386 but it is not installed
E: Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution).
dave@dave-MS-7641:~$ 


Any ideas?  Running apt fix-broken install doesn't do anything: I just keep getting the above.

---

### Post by Autodave on 2019-02-11
bump

---

### Post by Autodave on 2019-02-13
bump

---

### Post by him610 on 2019-02-13
@AutoDave:
You normally give sound, logical advice. Step back and figure out what advice you would give someone else who had the problem you describe.
When was the last time you booted without error?
What has changed since the last errorless boot?
Can you revert back to that errorless state?
Did you get your original amdgpu driver from Settings>Additional Drivers?

Good luck. You can figure this out.

---

### Post by Autodave on 2019-02-14
This problem started a couple weeks ago.  At that time, upon booting, a system problem box appeared stating that there were problems with  the amdgpu files.  I tried to reinstall driver 18.40.  Same issue after.  I downloaded driver 18.50 and tried to install.  System problem box still appeared on every boot.  I have tried everything that I can think of.  After supposedly reinstalling 18.50 for the 4th time, this is what I get:

dave@dave-MS-7641:~$ dpkg -l amdgpu-pro
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version      Architecture Description
+++-==============-============-============-=================================
iU  amdgpu-pro     18.50-725072 amd64        Meta package to install amdgpu Pr
dave@dave-MS-7641:~$ 

I am at a total loss.  I have been playing with this for an hour+ everyday and I have gotten nowhere.  Any help will be greatly appreciated.

---

### Post by Autodave on 2019-02-14
My driver appears to be working properly. But, going into Synaptic, it tells me that I have 11 broken packages: and all have to do with the amdgpu driver.

---

### Post by him610 on 2019-02-14
I do not have an AMD GFX, but synaptic only shows 7 packages when searching for 'amdgpu'. I suppose you downloaded and installed the amdgpu-pro packages from the AMD website - maybe, this was root cause of problems. Does amdgpu-pro package provide that much (how much?) of performance increase over amdgpu driver?
Is AutoDave going to clean up the broken packages, or is he going to live with them?

---

### Post by Autodave on 2019-02-15
I am trying to clean the broken packages: that is the problem: they will not clean.  In the 18.50 download, there are over 120 deb files: some for 64 bit, some for 32 bit, some for both.  I have actually found some of the files that the installer has trouble with and I have tried installing them individually, but still no good.  After installing the program, I start with 11 broken.  After playing, I can get it to 7, but no lower.  Every time I boot the machine, I get an error message, but no details are available. 

Yesterday, I removed the 18.50 driver and tried playing SuperTuxKarts.  45 - 50 FPS.  Reinstalled the driver, and even with the errors, 60-65 FPS.

Right now, with the AMD ppa disabled, synaptic does not show any broken packages, but I still get the system error message when rebooting.  If I enable the AMD ppa, then synaptic shows 11 broken packages.

---

