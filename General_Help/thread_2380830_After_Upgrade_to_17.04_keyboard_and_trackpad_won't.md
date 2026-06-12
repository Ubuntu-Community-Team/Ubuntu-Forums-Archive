---
title: "After Upgrade to 17.04 keyboard and trackpad won't work"
date: 2017-12-22
forum: General Help
---

### Post by paulakreuzer on 2017-12-22
This morning I decided to upgrade my brand new Why Laptop and the process worked great, but after the reboot I was unable to unlock the computer as neither keyboard nor trackpad are working.

Naturally the first thing I tried was connect external keyboards and mouses via USB, but none of them worked either.

Then I found a post saying I should go to recovery and put in ```
sudo apt-get install xserver-xorg-input-all
```, but to do that I need an internet connection in recovery which doesn't work for some reason.
If I connect the Laptop via Lan to the Wifi-Router or directly to the telephone-box all ping-commands just return a Network error and the command above returns something like "unable to download some packages".

I found a post explaining how to conntect to wireless via recovery, but ```
ifconfig wlan0 up
``` returns: ifconfig not installed" and ```
sudo service network-manager start
``` returns "Network Manager couldn't start because of timeout".

Anybody got another idea? Is it for example possible to download xserver-xorg-input-all from another machine and access it in recovery from an USB stick?

PS: Which file would I even download from: [https://packages.ubuntu.com/zesty/xserver-xorg-input-all](https://packages.ubuntu.com/zesty/xserver-xorg-input-all). My architecture is x86_64 which isn't listed there.

---

### Post by DuckHook on 2017-12-22
I've looked through your other posts, and just want to give you a more general piece of advice. As a general user and one entirely new to Ubuntu, I highly recommend that you stick to LTS releases. These are the stable, solid, every-two-years releases that minimize your chances of getting into trouble. If you are attempting to upgrade to Zesty, you only have a month of life left in that version anyway and will shortly have to go to Artful. Staying with standard releases means that you will be stuck on the upgrade treadmill every six months so long as you keep using Ubuntu. They also mean less stability and robustness: witness [this]("https://ubuntuforums.org/showthread.php?t=2380837") thread.

In contrast, LTS releases are designed for general users and don't need to be upgraded for five years. The last LTS was Xenial (16.04) and will be good until 2021. That gives you a good long run of support during which you won't have to reinvent the wheel every six months. You can upgrade to the next LTS, Bionic, when it comes out in April of 2018, but only if you so choose—not forced to do so because of an end date on your current system that's always just few weeks away.

Is all of your data backed up? If so, then I suggest installing Xenial as a fresh install on your laptop. You don't seem to have made many customizations yet, so there isn't much to lose. It should not be hard to recreate the few settings and customizations that you've made so far.

---

### Post by paulakreuzer on 2017-12-23
> **DuckHook said:**
> If you are attempting to upgrade to Zesty, you only have a month of life left in that version anyway and will shortly have to go to Artful. 

Well my plan was to upgrade to Artful right after the upgrade to Zesty was done. I'd rather have to get used to a few changes every half-year than have to get used to a lot of changes at once every two years.


> **DuckHook said:**
> Is all of your data backed up? If so, then I suggest installing Xenial as a fresh install on your laptop. You don't seem to have made many customizations yet, so there isn't much to lose. It should not be hard to recreate the few settings and customizations that you've made so far.

No, unfortunately my data is not backed up. At least on the secondary internal drive I have my whole Movies and TV collection. I guess I could live with loosing what's on my primary internal drive.

The problem is: I don't think reinstalling Xenial will be any easier than installing xserver-xorg-input-all. I don't have a CD-drive and no internet connection in recovery.

---

### Post by paulakreuzer on 2017-12-23
Ok so after going through tens of posts and sites about x86-64 I found one that said it was the same as amd64, so I downloaded xserver-xorg-input-all and xserver-xorg-input-libinput for amd64 and put it on my USB drive.

Now I understand I have to mount the usb drive to the file-system with something like

```
sudo mount /dev/sdb1 /media/usb

```

to be able to access the files.

The problem is it keeps telling me /media is read-only.

Is there anywhere on the filesystem I could mount the USB drive to where it's not read only?

---

### Post by DuckHook on 2017-12-23
Was not able to return to this thread until now.

This may be a misleading message, possibly caused by you not having a /media/usb directory to mount to. Try mounting to /media instead. Or create /media/usb with:```
sudo mkdir -m 777 -p /media/usb
```
When mounting, do:```
sudo mount -w /dev/sdb1 /media
```…or, if you have created the /media/usb directory:```
sudo mount -w /dev/sdb1 /media/usb
```

---

### Post by HermanAB on 2017-12-24
Errr... "No, unfortunately my data is not backed up."

FIRST backup your data, THEN experiment further, since things can go further down hill very quickly.

You can boot with install media, mount the disk and a USB widget to copy your data to safety.

Staying on the rolling release is a good way to learn, but making backups is a crucial first step, else you may get very disappointed.

---

### Post by DuckHook on 2017-12-24
> **HermanAB said:**
> Errr... "No, unfortunately my data is not backed up."

FIRST backup your data, THEN experiment further, since things can go further down hill very quickly.

You can boot with install media, mount the disk and a USB widget to copy your data to safety.

Staying on the rolling release is a good way to learn, but making backups is a crucial first step, else you may get very disappointed.

&#8593;+++

See link in my sig: !!BACKUP FIRST!!

---

### Post by paulakreuzer on 2017-12-26
So I keep getting steps further, but never closer. Whenever I try a new way I run into a new error.

So I tried 

```
sudo mount -w /dev/sdb1 /media
```


in recovery - which worked - but then sudo dpkg -i xserver-xorg-input-all.deb prints out:

```
dpkg: error: unable to access dpkg status area: Read-only file system
```

Meanwhile a friend suggested to create a live USB, boot from there mount the root partition in /mnt, change root directory to there with chroot and from there try to install the package. It didn't work downloading and installing from there because of a network error and when I moved the deb files there and tried to install them with dpkg -i I get a conflicting package error.


PS: Oh wow, it's solved now! :) My friend told me to how to fix the network issues in chroot with:
```
wget https://pastebin.com/raw/r78sm3uG -O arch-chroot
``` then
```
chmod +x arch-chroot
``` and then
```
sudo ./arch-chroot /mnt
```
Then I could simply:
```
sudo apt-get install xserver-xorg-input-all
```

Now I'll just have to figure out how I keep this from happening again after the next update.

PPS: I just ran the upgrade via terminal and before rebooting made sure xserver-xorg-input-all was updated (which it was). :)
So this topic can be closed.

---

