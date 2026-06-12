---
title: "bluetooth - not able to receive files"
date: 2008-05-01
forum: General Help
---

### Post by cosminb on 2008-05-01
Hi all,

I have an ASUS s55sv laptop with integrated bluetooth, and a Nokia N6600. I can send files from the computer to the phone, but not the other way around. I really don't know what's the problem.

I have tried several suggestions, like modifying the class of the laptop bt (from 0x000100 to 0x100100, meaning it does File Transfer), or using rfcomm0 like suggested in [http://ubuntuforums.org/showthread.php?t=34740&highlight=bluetooth](http://ubuntuforums.org/showthread.php?t=34740&highlight=bluetooth).

Neither approach works. I am attaching the output of hcidump, maybe someone more knowledgeable can figure out what happens under the hood.

Thanks in advance,
Cosmin

P.S. The version I use is ubuntu 8.04, updated.

---

### Post by cosminb on 2008-05-01
Searching other threads, I found the problem was a faulty bluez-utils package. I replaced the current version (3.26) with an older one (3.24) I found on:

[http://www.alliedquotes.com/mirrors/Ubuntu/pool/main/b/bluez-utils/](http://www.alliedquotes.com/mirrors/Ubuntu/pool/main/b/bluez-utils/)

The commands I used are:

```
cosmin@cosmin-laptop:~$ sudo dpkg -r bluez-audio bluez-cups bluetooth bluez-utils gnome-phone-manager
dpkg - warning: ignoring request to remove bluez-cups which isn't installed.
(Reading database ... 106521 files and directories currently installed.)
Removing gnome-phone-manager ...
Removing bluetooth ...
Removing bluez-utils ...
 * Stopping bluetooth                                                    [ OK ] 
Removing bluez-audio ...
cosmin@cosmin-laptop:~$ cd Desktop/Downloads/test\ bluez\ 3.19
cosmin@cosmin-laptop:~/Desktop/Downloads/test bluez 3.19$ ls
bluetooth_3.24-0ubuntu2_all.deb    bluez-utils_3.24-0ubuntu2_i386.deb
bluez-cups_3.24-0ubuntu2_i386.deb
cosmin@cosmin-laptop:~/Desktop/Downloads/test bluez 3.19$ sudo dpkg -i *
Selecting previously deselected package bluetooth.
(Reading database ... 106398 files and directories currently installed.)
Unpacking bluetooth (from bluetooth_3.24-0ubuntu2_all.deb) ...
Selecting previously deselected package bluez-cups.
Unpacking bluez-cups (from bluez-cups_3.24-0ubuntu2_i386.deb) ...
Selecting previously deselected package bluez-utils.
Unpacking bluez-utils (from bluez-utils_3.24-0ubuntu2_i386.deb) ...
Setting up bluez-cups (3.24-0ubuntu2) ...
Setting up bluez-utils (3.24-0ubuntu2) ...
Installing new version of config file /etc/bluetooth/audio.conf ...
Creating device nodes ...
udev active, devices will be created in /dev/.static/dev/
 * Starting bluetooth                                                    [ OK ] 

Setting up bluetooth (3.24-0ubuntu2) ...
cosmin@cosmin-laptop:~/Desktop/Downloads/test bluez 3.19$
```

If anyone got it working by using this, please let the rest of us know. :)

Thanks,
Cosmin

---

### Post by tanas on 2008-05-09
It worked!
(What happened was that AFTER the upgrade to Hardy, I could no longer send files from the phone to the computer.. but the other way around was ok)-

I downgraded the bluez-utils in synaptic to the gutsy version (3.19, just add 
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main
to the repositories list) and now my computer is again able to receive files from the mobile phone.

---

### Post by sayakb on 2008-05-27
Doesn't seem to work for me. I first removed the mentioned packages and installed version 3.24
Still didn't receive. So I install 3.19, but still no use. I also installed obexpushd for gutsy which used to work in gutsy. But still no use. What should I do?

---

### Post by Troll_the_Great on 2008-05-27
Can you be a bit more specific about how did you do it?I am new to linux, so I didn't understand....Sorry:(:(

---

### Post by fov9999 on 2008-06-06
it sucks that this isnt fixed yet..

---

### Post by c0ldfusi0n on 2008-07-12
Using cosminb's method, here's what I get:

```

[06:50:45 root@nviwks ~]# dpkg -r bluez-audio bluez-cups bluetooth bluez-utils gnome-phone-manager
(Reading database ... 194560 files and directories currently installed.)
Removing bluez-cups ...
Removing gnome-phone-manager ...
Removing bluetooth ...
Removing bluez-utils ...
 * Stopping bluetooth                                                    [ OK ] 
Removing bluez-audio ...
[06:55:03 root@nviwks ~/Desktop]# ls | grep deb
bluetooth_3.24-0ubuntu2_all.deb
bluez-cups_2.24-0ubuntu6_amd64.deb
bluez-utils_2.24-0ubuntu6_amd64.deb
[06:55:07 root@nviwks ~/Desktop]# dpkg -i *.deb
(Reading database ... 194489 files and directories currently installed.)
Preparing to replace bluetooth 3.24-0ubuntu2 (using bluetooth_3.24-0ubuntu2_all.deb) ...
Unpacking replacement bluetooth ...
Preparing to replace bluez-cups 2.24-0ubuntu6 (using bluez-cups_2.24-0ubuntu6_amd64.deb) ...
Unpacking replacement bluez-cups ...
Preparing to replace bluez-utils 2.24-0ubuntu6 (using bluez-utils_2.24-0ubuntu6_amd64.deb) ...
Unpacking replacement bluez-utils ...
dpkg: dependency problems prevent configuration of bluez-cups:
 bluez-cups depends on libbluetooth1 (>= 2.15); however:
  Package libbluetooth1 is not installed.
dpkg: error processing bluez-cups (--install):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of bluez-utils:
 bluez-utils depends on libbluetooth1 (>= 2.15); however:
  Package libbluetooth1 is not installed.
 bluez-utils depends on libdbus-1-2 (>= 0.60); however:
  Package libdbus-1-2 is not installed.
 bluez-utils depends on sysvinit (>= 2.80-1); however:
  Package sysvinit is not installed.
dpkg: error processing bluez-utils (--install):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of bluetooth:
 bluetooth depends on bluez-utils; however:
  Package bluez-utils is not configured yet.
dpkg: error processing bluetooth (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 bluez-cups
 bluez-utils
 bluetooth

```

Basically it tells me that there are unresolved dependencies with these packages: libbluetooth1, libdbus-1-2 and sysvinit and obviously they're not installable via apt.

---

### Post by cosminb on 2008-07-14
Maybe you should give it another try using i386...

---

### Post by Giano89 on 2008-08-04
> **cosminb said:**
> Searching other threads, I found the problem was a faulty bluez-utils package. I replaced the current version (3.26) with an older one (3.24) I found on:

[http://www.alliedquotes.com/mirrors/Ubuntu/pool/main/b/bluez-utils/](http://www.alliedquotes.com/mirrors/Ubuntu/pool/main/b/bluez-utils/)

The commands I used are:

```
cosmin@cosmin-laptop:~$ sudo dpkg -r bluez-audio bluez-cups bluetooth bluez-utils gnome-phone-manager
...
Setting up bluetooth (3.24-0ubuntu2) ...
cosmin@cosmin-laptop:~/Desktop/Downloads/test bluez 3.19$
```

If anyone got it working by using this, please let the rest of us know. :)

Thanks,
Cosmin
IT WORKS !! I had the same problem on LinuxMint but now it works! Why a mad package is in the repository while the working one is buried in the net?
Thank you guys!!

---

### Post by fragos on 2008-08-04
I run 8.04. I can send files to my palm E2 but not recieve them. I purchased a Nokia N810 and bluetooth works in both directions. It would appear that the device implementation of bluetooth makes a difference. The N810 is a Linux device.

---

### Post by ivan-frankfurt on 2008-08-11
This might help:
run bluetooth-applet from the command line (not sure if it's mapped anywhere in the menus)
select Browse Device...
This should give you access to the filesystem on the phone (on Nokia phones internal memory it's C:, memory cards are D:)
Right click on the file(s) you need, select Copy, then open another window on your computer's filesystem and select Paste.

This works at least for Kubuntu with kde 4.1 and Nokia phones.
Hope it helps
Ivan

---

### Post by mihai.ile on 2008-08-31
I couldn't receive files also, my phone does not detect file or object transfer capabilities on my laptop even if I selected "Receive files from remote devices"

I fixed it by doing steps described here:

[https://bugs.launchpad.net/ubuntu/+source/bluez-gnome/+bug/213885](https://bugs.launchpad.net/ubuntu/+source/bluez-gnome/+bug/213885)

If this fixes your problem also make a reply to confirm the bug.

---

### Post by nicola76b on 2008-10-09
thanks mihai007
restart bluetooth-applet resolved my problem too.

  -nicola

---

