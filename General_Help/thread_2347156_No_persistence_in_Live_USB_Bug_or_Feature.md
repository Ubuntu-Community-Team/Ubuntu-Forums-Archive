---
title: "No persistence in Live USB? Bug or Feature?"
date: 2016-12-22
forum: General Help
---

### Post by CaptainMark on 2016-12-22
So I found out the hard way recently that Ubuntu doesn't support persistent Live USB's anymore with 16.04, apparently there is a workaround but it's complex and I couldn't get it to work.

I think that's a bad thing as the persistent USB's are incredibly useful IMO, does anyone know if this was a bug with 16.04 that was too complex to patch or are Canonical intentionally and permanently removing USB persistence altogether?


Regards
Mark

---

### Post by vasa1 on 2016-12-22
Have you tried with mkusb?

---

### Post by PaulW2U on 2016-12-22
> **CaptainMark said:**
> does anyone know if this was a bug with 16.04 that was too complex to patch or are Canonical intentionally and permanently removing USB persistence altogether?
The following threads on these forums are just two that might give you further information about the lack of persistence:

[https://ubuntuforums.org/showthread.php?t=2289225](https://ubuntuforums.org/showthread.php?t=2289225)
[https://ubuntuforums.org/showthread.php?t=1958073](https://ubuntuforums.org/showthread.php?t=1958073)

But yes, there was a decision made by Canonical to remove that function from **usb-disk-creator** otherwise known as **Startup Disk Creator**.

---

### Post by C.S.Cameron on 2016-12-22
Startup Disk Creator does not offer persistence with 16.04, UNetbootin does offer persistent casper-rw files, mkusb/dus offers persistent casper-rw partitions. 
Generally syslinux type installs - no persistent partitions, grub2 installs - persistent partitions allowed.

---

### Post by sudodus on 2016-12-22
> **CaptainMark said:**
> So I found out the hard way recently that Ubuntu doesn't support persistent Live USB's anymore with 16.04, apparently there is a workaround but it's complex and I couldn't get it to work.

I think that's a bad thing as the persistent USB's are incredibly useful IMO, does anyone know if this was a bug with 16.04 that was too complex to patch or are Canonical intentionally and permanently removing USB persistence altogether?


Regards
Mark

If you use a tool, that creates the persistence for you, I think it is not too difficult (even if it is complex under the hood). The fastest way to start making and repairing USB boot drives is to install the mkusb PPA, install and update the mkusb package like all the other program packages.

If you run standard Ubuntu, you need an extra instruction to get the repository Universe. (Kubuntu, Lubuntu ... Xubuntu have the repository Universe activated automatically.)

```
sudo add-apt-repository universe  # only for standard Ubuntu

sudo add-apt-repository ppa:mkusb/ppa  # and press Enter
sudo apt-get update
sudo apt-get install mkusb mkusb-nox usb-pack-efi
```

See this link about persistent live drives: [help.ubuntu.com/community/mkusb/persistent](https://help.ubuntu.com/community/mkusb/persistent)

Maybe you want to test the future version of mkusb, now called 'dus' with the GUI front end 'guidus'. Then I would recommend the unstable directory of mkusb,

```
sudo add-apt-repository universe  # only for standard Ubuntu

sudo add-apt-repository ppa:mkusb/unstable  # and press Enter
sudo apt-get update
sudo apt-get install guidus mkusb-common usb-pack-efi
```

The intention is that guidus should be easier to use compared to the current version of mkusb.

---

