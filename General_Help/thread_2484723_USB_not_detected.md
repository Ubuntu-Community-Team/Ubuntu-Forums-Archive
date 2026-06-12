---
title: "USB not detected"
date: 2023-03-07
forum: General Help
---

### Post by sonicdiscovery on 2023-03-07
Ubuntu 22.04 LTS Hello, When I insert a usb drive into my desktop, it is not recognized in my folders and in my disks app. On my previous install, the usb's were recognized.  Any help is greatly appreciated. Thank you

---

### Post by papakanush2 on 2023-03-09
Deleted

---

### Post by sonicdiscovery on 2023-03-09
Thank you for taking time to reply to my question. I will save your solution for when it happens again.After a few re-installs and other issues with Ubuntu I installed MX Linux. I then re-installed Ubuntu with some do's/don't learned. It is running and I have backups going. Ubuntu used to be easier than Debian to install, now not so much.

---

### Post by MAFoElffen on 2023-03-10
[COLOR=#ff0000][B]*** IMPORTANT ***
[/B][/COLOR]> **papakanush2 said:**
> ```
sudo modprobe [COLOR=#ff0000]usb_storage[/COLOR]
sudo gpasswd -a $USER [COLOR=#ff0000]wheel[/COLOR]
sudo gpasswd -a $USER  [COLOR=#ff0000]storage[/COLOR]
sudo gpasswd -a $USER  [COLOR=#ff0000]disk[/COLOR]
sudo gpasswd -a $USER [COLOR=#ff0000]users[/COLOR]
sudo [COLOR=#ff0000]pacman[/COLOR] -S ntfs-3g
```
Then reboot.

[COLOR=#ff0000]Again, this was for an Arch install[/COLOR]. ntfs-3g should already be installed on your Ubuntu 22.04 (it is on mine)

Hope this offers a few clues........
No. Do not do this. This is for Arch and is intrusive. You are adding the current user to groups... which for Ubuntu, some of those (actually all) do not exist. And trying to add a kernel module that does not exist in Ubuntu...
```

mafoelffen@Mikes-ThinkPad-T520:~$ lsmod | grep usb
btusb                  61440  0
btrtl                  24576  1 btusb
btbcm                  24576  1 btusb
btintel                40960  1 btusb
btmtk                  16384  1 btusb
bluetooth             827392  28 btrtl,btmtk,btintel,btbcm,bnep,btusb,rfcomm

```
Notice, there is no module 'usb_storage'...
```

mafoelffen@Mikes-ThinkPad-T520:~$ apt list ntfs-3g --installed
Listing... Done
ntfs-3g/jammy-updates,jammy-security,now 1:2021.8.22-3ubuntu1.2 amd64 [installed,automatic]
N: There is 1 additional version. Please use the '-a' switch to see it

```
That is how you check for if that is installed, without trying to install it....

And checking for group membership is safer to check, without adding, via
```

mafoelffen@Mikes-ThinkPad-T520:~$ groups
mafoelffen adm cdrom sudo dip [COLOR=#ff0000]plugdev[/COLOR] kvm lpadmin whoopsie lxd sambashare libvirt

```
Note that group 'plugdev' is what a user needs to see USB devices in Ubuntu... And that membership should be set by default. If not, then a problem.

I use Debian, RHEL, SUSE, Arch, others...Watch what commands are recommended, and be clear on what they do, or might do to your system. Some commands are intrusive and will make changes to your system... While other's read information for you to make the changes you might need to make... While Linux, as a whole is "Linux", not all things are the same between Distributions.

Command that are useful for diagnosing USB problems are
```

lsusb -vvv
sudo dmesg | grep -i 'usb'

```
Plug and unplug the device in and look for the changes in running those two commands. Then go from there.

Also: The URL given ([https://help.ubuntu.com/community/DebuggingUSBStorage](https://help.ubuntu.com/community/DebuggingUSBStorage)) was for Ubuntu LTS 10.04, which things have changed a bit since then. (That doc was last edited 2010-05-28 15:25:27) LOL

---

### Post by papakanush2 on 2023-03-10
My apologies for the potentially dangerous advise. I'll be more careful.
I deleted my previous suggestions.

---

### Post by MAFoElffen on 2023-03-10
Please do not take wrong, or as a criticism... Not meant to be that. Just be careful. Users are wanting advise.

Me? I test what I advise, and try to explain to a user what commands will do...

Take a look at the [UbuntuForums 'system-info' scirpt]("https://github.com/UbuntuForums/system-info")... That script is based on diagnostics commands that are mostly universal for many distributions of Linux, for many kinds of hardware and returns a report to use as a tool for members here to help users with their problems.

We try to recommend things to help users. The key is to get the information we need to be able to make those recommendations.

I welcome your enthusiasm and desire to help others. That, in itself is commendable. I welcome all sound advise, from all experience and exposures.

---

### Post by sonicdiscovery on 2023-03-10
Thank you!

---

