---
title: "No boot menu."
date: 2015-05-10
forum: General Help
---

### Post by AzrinArius on 2015-05-10
I've been using Linux/Windows in tandem since the 90s. Though I'm still very much a newbie with Linux. I've never plunged that deep in to it. Usually I have it dual-booting with Windows and it just works. This time, however, it doesn't. There's no boot menu. I formatted the disk and did a clean install of Windows 7, leaving enough space for Ubuntu. Then I boot in to Ubuntu(live) using a USB stick I made with unetbootin -- I used EFI to boot it. When I got to disk management in the installation it didn't find my partitions. So I googled and ended up using FixDisk. This solved the problem, the installer found my partitions and I continued as I normally would. But, now, when I boot I have no grub. There's no option for Ubuntu or Windows. It just boots in to Ubuntu.

I've read some things saying this is an EFI or GPartition(?) thing. But I haven't really kept up and don't know what those problems are. All I want is Windows and Linux working side by side as they used too. 

Is there a simple solution to this or am I screwed?

Thanks.

---

### Post by grahammechanical on 2015-05-10
Booting straight into Ubuntu without showing a boot menu is what happens when Ubuntu is the only OS on the machine. When in Ubuntu run this command

```
sudo update-grub
```

Watch the printout. Do you see Windows 7 boot loader in the list? If you do then when you reboot you should see a boot menu with both Ubuntu and Windows options. But if you do not see Windows 7 boot loader listed in the printout then it may be because Windows 7 does not exist or Ubuntu is installed in EFI mode but Windows 7 is installed in legacy (CSM) mode. Or, Windows 7 is installed in EFI mode and Ubuntu is installed in legacy (CSM) mode.

When we have a UEFI boot system motherboard then both Ubuntu and Windows must be installed in the same mode be it EFI or Legacy.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Similar thread. There are several like this

[http://ubuntuforums.org/showthread.php?t=2277604&p=13282694#post13282694](http://ubuntuforums.org/showthread.php?t=2277604&p=13282694#post13282694)

Regards.

---

### Post by AzrinArius on 2015-05-10
> **grahammechanical said:**
> Booting straight into Ubuntu without showing a boot menu is what happens when Ubuntu is the only OS on the machine. When in Ubuntu run this command

```
sudo update-grub
```

Watch the printout. Do you see Windows 7 boot loader in the list? If you do then when you reboot you should see a boot menu with both Ubuntu and Windows options. But if you do not see Windows 7 boot loader listed in the printout then it may be because Windows 7 does not exist or Ubuntu is installed in EFI mode but Windows 7 is installed in legacy (CSM) mode. Or, Windows 7 is installed in EFI mode and Ubuntu is installed in legacy (CSM) mode.

When we have a UEFI boot system motherboard then both Ubuntu and Windows must be installed in the same mode be it EFI or Legacy.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Similar thread. There are several like this

[http://ubuntuforums.org/showthread.php?t=2277604&p=13282694#post13282694](http://ubuntuforums.org/showthread.php?t=2277604&p=13282694#post13282694)

Regards.

It finds Windows.

> 
xuri@xuri-nix:~$ sudo update-grub
[sudo] password for xuri: 
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-3.16.0-37-generic
Found initrd image: /boot/initrd.img-3.16.0-37-generic
Found linux image: /boot/vmlinuz-3.16.0-30-generic
Found initrd image: /boot/initrd.img-3.16.0-30-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
done


This is obviously a conflict between legacy and EFI but is there a simple way to resolve it. I upgraded my computer, which is why I had to reinstall everything, but I need Windows. My daughter and I play Borderlands every weekday in co-op. This hasn't been a problem before but now I really need Windows to work in dual boot.

If I have to choose between OS and my daughter then, well, lol. It's a pretty easy choice. :D

---

### Post by WinEunuchs2Unix on 2015-05-10
> **AzrinArius said:**
> It finds Windows.

If I have to choose between OS and my daughter then, well, lol. It's a pretty easy choice. :D

I'm confused by "border-lands" do you need Windows or Linux for good relations with your daughter?

---

### Post by WinEunuchs2Unix on 2015-05-10
> **WinEunuchs2Unix said:**
> I'm confused by "border-lands" do you need Windows or Linux for good relations with your daughter?

nvm I reread twice and borderlands is obviously a Windows app.

On the topic of grub however you can easily spend a couple of weeks of spare time sorting it all out. A statement like "upgrading my computer" doesn't shed very much light on what was changed to help us gleam necessary changes for grub.

FWIW.

---

