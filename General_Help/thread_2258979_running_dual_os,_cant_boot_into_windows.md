---
title: "running dual os, cant boot into windows"
date: 2015-01-01
forum: General Help
---

### Post by elliott4 on 2015-01-01
So I built a new computer and since I am a gamer I went with windows and have been running that for a few weeks. I now want to use windows for gaming and Ubuntu for programming. I followed an online guide found here 

[http://linux.about.com/od/LinuxNewbieDesktopGuide/ss/The-Ultimate-Windows-7-And-Ubuntu-Linux-Dual-Boot-Guide_18.htm#step-heading](http://linux.about.com/od/LinuxNewbieDesktopGuide/ss/The-Ultimate-Windows-7-And-Ubuntu-Linux-Dual-Boot-Guide_18.htm#step-heading)

And followed all the instructions. After I installed the os I tried restarting my computer. It froze so I turned it off. I then turned the computer back on and it went right to Ubuntu. Then I tried booting into windows, I restarted the computer and it booted back into Ubuntu. I shut it off again and I was given no opportunity to boot into windows. When bios showed up as I was turning the computer on,(MSI board), it gave me the option to press f11 to boot. A menu that said, "select boot device", showed up. I tried using all of the options for select boot device and they all brought me to ubuntu. I know windows is there, how can I boot into it? Its really a shame I need to use windows at all.

---

### Post by carl4926 on 2015-01-01
New computer? Is the MB UEFI?
Windows version?

---

### Post by elliott4 on 2015-01-01
Yes I'm pretty sure the mobo is uefi. I built the computer recently.

[http://www.newegg.com/Product/Product.aspx?Item=N82E16813130782](http://www.newegg.com/Product/Product.aspx?Item=N82E16813130782)

Windows 7

---

### Post by carl4926 on 2015-01-01
We would need to know if you are running in EFI mode or Legacy?

Post the output of

```
sudo parted -l
```

Also run

```
sudo update-grub
```and post the feedback here

If you hold down SHIFT as you boot the machine, does the grub menu display?

---

### Post by elliott4 on 2015-01-01
I tried holding down shift. A gnu grub menu appeared. The options were, Ubuntu, advanced options from Ubuntu, and system setup. That didn't help, I will now try the code you gave me.

---

### Post by elliott4 on 2015-01-01
Also when I press f11 to go into boot menu one device shows up as, UEFI: built in EFI shell.

---

### Post by elliott4 on 2015-01-01
Also in my bios it says my boot mode is selected as, LEGACY+UEFI

---

### Post by Dennis N on 2015-01-01
> **elliott4 said:**
> Also when I press f11 to go into boot menu one device shows up as, UEFI: built in EFI shell.

The EFI shell allows you to interact with the UEFI firmware. Most users probably won't be using this capability (or need to).

[https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface#UEFI_Shell](https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface#UEFI_Shell)

---

### Post by elliott4 on 2015-01-01
I cannot run these sudo commands because it asks me for a password and does not give me anywhere to type it in. I assume you meant type the sudo code into terminal?

---

### Post by elliott4 on 2015-01-01
Alright I got sudo update grub to work in terminal and a bunch of stuff showed up mostly saying Linux but one saying windows 7 loader.

---

### Post by Dennis N on 2015-01-01
> **elliott4 said:**
> Also in my bios it says my boot mode is selected as, LEGACY+UEFI

Mine offers this too. The boot menu will show two entries for your USB installer. One will include a reference to UEFI and one will not. If you choose the UEFI, that's the way the OS will get installed. The other option will install in Legacy mode.

---

### Post by elliott4 on 2015-01-01
Alright so I will install uefi?

---

### Post by carl4926 on 2015-01-01
Post the info I asked for earlier

---

### Post by elliott4 on 2015-01-02
Big update man. Thanks for helping but I got everything running properly by pressing f8 at booting. Now I just need to figure out how to download java..  Ubuntu is a journey.

---

### Post by Dennis N on 2015-01-03
Nice board. I also used an H97 board for my newest computer build. It was an Asus board, however. Enjoy your new computer.

---

