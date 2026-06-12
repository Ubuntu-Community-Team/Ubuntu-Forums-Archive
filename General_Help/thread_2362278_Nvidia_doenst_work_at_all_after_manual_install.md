---
title: "Nvidia doenst work at all after manual install"
date: 2017-05-26
forum: General Help
---

### Post by docdoc2 on 2017-05-26
Hello,

i need the newest driver from nvidia, so i followed these steps to get it
> 

13.1- Terminal: sudo apt-get update && sudo apt-get upgrade && sudo apt-get install build-essential && sudo apt-get install linux-source && sudo apt-get install linux-headers-generic

13.2- Terminal: sudo gedit /etc/default/grub

13.3- In the opened archive look for the line:
"GRUB_CMDLINE_LINUX_DEFAULT..."

13.4- Change this line to:
GRUB_CMDLINE_LINUX_DEFAULT="nouveau.blacklist=1 quiet splash nomodeset"

*this forces low-level graphics to ensure putty does not give black screen.

13.5- Terminal: sudo update-grub2

13.6- Terminal: sudo apt-get remove nvidia* && sudo apt-get autoremove # ensures no former installation clashes with new install

13.7 Terminal: sudo reboot

14- After reboot download the NVidia Driver:
[http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)

15- After download the right version for your GPU, go to the download folder, click with the right button and go to properties. On the second tab (permissions) mark the checkbox "Allow Executing File as a Program" and close the properties window.

16- Terminal: sudo gedit /etc/modprobe.d/blacklist.conf 

17.1- In the archive opened add these lines at the end:
blacklist vga16fb
blacklist nouveau
blacklist rivafb
blacklist nvidiafb
blacklist rivatv
blacklist lbm-nouveua
options nouveau modeset=0
alias nouveau off
alias lbm-nouveau off

17.2- Save and close the archive

18- Open a putty-terminal with Ctrl + Alt + F1

18.1- Putty-Terminal: su root # and put your password

18.2- Putty-Terminal: sudo service lightdm stop # stops graphic session to enable nvidiainstallation

18.3- Navigate to the folder where the nvidia driver was downloaded and execute it

18.4- Putty-Terminal: sudo ./NVIDIADriverName.run

18.5- Putty-Terminal: sudo nano /etc/default/grub

18.6- In the opened file, go to the same line as before and change to it:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"

18.7- Hit F3 to save the file

18.8- Hit F2 to close the file

18.9- Putty-Terminal sudo update-grub2

19- Putty-Terminal: sudo reboot

The driver is installed!



After this, i could not log in. So, i purged everything i found of the new driver and installed the normal nvidia-current. I can login now, but the driver is somehow not active, everything is slow, i cant dim the display, etc.

Then, i tried to use the uninstall runtine of the manual driver package from nvidiato get rid of everything it changed, but it said no driver installed.

dkms status:
```

bbswitch, 0.8, 3.13.0-119-generic, x86_64: installedbcmwl, 6.30.223.248+bdcom, 3.13.0-119-generic, x86_64: installed
nvidia-304, 304.135, 3.13.0-119-generic, x86_64: installed
vboxhost, 4.3.26, 3.13.0-119-generic, x86_64: installed

```

lspci:
```
00:00.0 Host bridge: Intel Corporation 3rd Gen Core processor DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor PCI Express Root Port (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)
00:14.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 (rev c4)
00:1c.2 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 3 (rev c4)
00:1c.3 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 4 (rev c4)
00:1c.5 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 6 (rev c4)
00:1d.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation HM77 Express Chipset LPC Controller (rev 04)
00:1f.2 RAID bus controller: Intel Corporation 82801 Mobile SATA Controller [RAID mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller (rev 04)
01:00.0 VGA compatible controller: NVIDIA Corporation GF108M [GeForce GT 630M] (rev ff)
08:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5229 PCI Express Card Reader (rev 01)
0a:00.0 Network controller: Intel Corporation Centrino Wireless-N 2230 (rev c4)
0b:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 07)

```


Can anyone help me? I actually need the newest nvidia driver, but why can't i install it? Is it because i use Ubuntu 14.04 (Kernel 3.13.0-119-generic )? I have only bad experiences with distro upgrades, so i didnt upgrade yet.

---

### Post by ajgreeny on 2017-05-26
What driver is available if you use the **Additional Drivers** utility in the menu, or dash if using unity?

I think something more recent than 304, which is what you appear to have now, would be available.

In view of the **vboxhost, 4.3.26, 3.13.0-119-generic, x86_64: installed** that you show I wonder if this is a VM running in Virtualbox; probably not but let us know, as if it is a VM it will not need an nvidia driver.

---

### Post by docdoc2 on 2017-05-26
Thanks for the quick reply. It is not inside of a VM, but i have virtual box installed. I forgot to mention that after nvidia-current didnt work, i also purged all and installed nvidia-current-updates, but no difference. 

Additional driver shows multiple nvidia options and it says one is active, but it is obviously not. I changed to the new one, but after log out, again, i couldnt log in. As for the others, it says they work, but they just don't. Right now 340 is said to be active. I think the nvidia installation routine corrupted the xorg file or the dkms or something else, i don't know.

  [IMG]http://i.imgur.com/EUQKdCY.png[/IMG]

---

### Post by docdoc2 on 2017-06-05
So that means i can reinstall the wohle ubuntu now? I am out of Ideas. Also, i did ne manual install again in order to use the manual uninstall , no success. the driver just don't want to work, despite 'additional drivers' and dkms telling me it is active

---

### Post by Autodave on 2017-06-05
Is this a laptop? If so, are we dealing with 2 video cards? Please post some info on your machine.

---

