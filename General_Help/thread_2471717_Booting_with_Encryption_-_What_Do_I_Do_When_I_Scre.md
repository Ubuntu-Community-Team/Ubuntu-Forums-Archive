---
title: "Booting with Encryption - What Do I Do When I Screw Up My Password?"
date: 2022-02-07
forum: General Help
---

### Post by arius88 on 2022-02-07
My drive is encrypted. I have a very long password and a very unreliable keyboard, and there's no option to see what I'm typing; as a result, sometimes I screw up my password on boot-up. Previously, with Ubuntu, when I screwed up my password it would give me an error message and allow me to retry. However, with this version of Lubuntu (20.04),  I get a weird message, something about "Grub Recovery." I have no idea what to do once that happens. I can input text, but none of the commands I am familiar with ("reboot," and so forth) work. Basically I have no recourse at this point except to hard reboot the machine, which is obviously not optimal. Is there another approach? (And why is it like this?)

---

### Post by TheFu on 2022-02-09
I'd setup a key-based authentication method that uses (better) a HW token or (less good) a USB flash drive to unlock the encrypted storage.  I have a Yubikey HW token setup in challenge/response mode to unlock LUKS on laptops here.  

I don't currently encrypt desktops, though I have thought about it.

As for grub, have you tried the Advanced boot menu and either the "recovery" boot or last kernel?

The way to fix boot issues is with an Ubuntu Installer flash drive in the Try Ubuntu mode. From there, we can troubleshoot and correct pretty much anything. It is a basic tool for this stuff.  

I know the Boot-Repair guys are working on an update. Kinda surprised nobody has said anything about it. I know they've been adding support for things like ZFS and drastically improving the data gathering.  I wouldn't use it for attempted fixes yet, but the data gathering is helpful for people willing to look online at the results (not me since they added a mandated login to see it).

---

### Post by guiverc on 2022-02-09
If you enter your key incorrectly into the key prompt when booting; your drive is **not** unencrypted; so grub stage 0 cannot read (it's in `/boot`which is still encrypted) the following stages which is why you get the grub rescue prompt.  The easiest fix for that is just to reboot (eg. Ctrl+Alt+Del) and enter the key again.

Because of *full disk encryption* (*no access to /boot at boot time; [though Tj calls it "almost full disk encryption" as a system wouldn't boot if it was fully encrypted]("https://help.ubuntu.com/community/Full_Disk_Encryption_Howto_2019")*[)]("https://help.ubuntu.com/community/Full_Disk_Encryption_Howto_2019")  there is less code that is run-able that early in the process, so no error checking is possible (ie. *no chance to re-enter an incorrect password*). Yes Lubuntu differs slightly here to most other Ubuntu *flavors* as they are using more modern encryption that is installed by the `ubiquity` installed used by Ubuntu and most *flavors*.

I'm no expert at this sorry (*I use desktops too, having only encrypted home partition on this box*) and much of the encryption explanations I've been given *sailed over my head* (*thus apologies for any mistakes I've made*) so I only look at what exists after a full disk QA-test install (ie. *no `/boot` is readable on invalid entry of key; I'm involved in QA*) and after invalid key attempts to unlock a box; I just reboot using the most appropriate method for the box (eg. Ctrl+Alt+Del as suggested).

---

### Post by MAFoElffen on 2022-02-11
> [SIZE=3]*"It will be okay. I saw this work in a cartoon somewhere..."*[/SIZE]
As TheFu said, the script "boot-info" will show most of the pertinent information that we need to look at for this. We are currently updating this script and working to improve it... But it should help out with showing us what is going on... And this might just be a good test-case to help us improve those scripts...

I suggest using the latest version (now currently nppa190) script from: [https://launchpad.net/~yannubuntu/+archive/ubuntu/boot-repair-dev](https://launchpad.net/~yannubuntu/+archive/ubuntu/boot-repair-dev)

Use a 20.04.3 LiveCD to boot. Use "try". Open a terminal from it...
```

sudo add-apt-repository ppa:yannubuntu/boot-repair-dev 
sudo apt-get update
sudo apt install -y boot-info
boot-info

```
I currently have some 20.04.3 and 22.04 machines up trying to work out some things with the scripts to work for both default installer partially encrypted    installed luks (root as luks2) and custom-mostly encrypted installed luks (boot as luks1 and root as luks2) machines to try to help get the scripts updated, working and ready for 22.04 (where Grub 2.06 will be released on Ubuntu 22.04 and can then read and boot natively from luks2).

Yes, as guiverc said... It varies on just how much is encrypted, based on how it was installed and configured... But the current 'boot-info' scripts will show those, and help ID that. That will help in a plan in how to mount it and repair Grub2 on it.

Be aware the the current version of the script sees that "it is encrypted" and has a problem in that it loops a few times saying it needs to install encryted-utils... just keep pressing "okay" and it will get past that. (another part we are working on...)

---

