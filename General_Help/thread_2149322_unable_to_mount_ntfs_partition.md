---
title: "unable to mount ntfs partition"
date: 2013-05-28
forum: General Help
---

### Post by ozanne on 2013-05-28
Can anyone help?
I have installed ubuntu 12.04LTS on a new hard drive on an old desktop.
The old drive (sdb) has Windows XP that is inaccessible.
When I try to mount sdb2, I get this:

jonathan@jonathan-Dimension-5100:~$ sudo mount -t ntfs /dev/sdb2/mnt/win_nfts[sudo] password for jonathan:Failed to load runlist for $MFT/$DATA.highest_vcn = 0x1213b, last_vcn - 1 = 0x16c1fFailed to load $MFT: Input/output errorFailed to mount '/dev/sdb2': Input/output errorNTFS is either inconsistent, or there is a hardware fault, or it's aSoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windowsthen reboot into Windows twice. The usage of the /f parameter is veryimportant! If the device is a SoftRAID/FakeRAID then first activateit and mount a different device under the [I]/dev/mapper/ directory, (e.g./dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentationfor more details.
[/I]
I have tried nfts-3g but am a newbie and am lost with that.My objective here is to be able to boot Windows XP to enable me to use some windows programs there and/or access old files residing there.Any help will be appreciated - I have scoured the forums without success.

---

### Post by sudodus on 2013-05-28
Start running ```
chkdsk /f
``` on Windows then reboot into Windows twice according to the advice and let us know the result.

---

### Post by sudodus on 2013-05-28
If Windows won't boot, you can make a Bart PE or Windows 7 PE pendrive, boot from it and run **[FONT=courier new]chkdsk /f[/FONT]**

---

### Post by Mark Phelps on 2013-05-28
IF you know someone with access to a Windows PC, have them download and burn the Minitool Partition Wizard Boot CD.

Boot from that on your PC and use the option to Check the windows disk.  That will run CHKDSK for you.

---

### Post by ajgreeny on 2013-05-28
```
sudo mount -t ntfs /dev/sdb2/mnt/win_nfts
``` Is that a typo, or did you miss a space between **/dev/sdb2** and **/mnt/win_ntfs**?  I don't think you would get that error simply from missing a space, but what do I know- - -?

Also, do you already have the **/mnt/win_ntfs** folder in existence?

---

