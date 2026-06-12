---
title: "Do we think this will mostly work with ubuntu"
date: 2013-04-27
forum: General Help
---

### Post by abduljones on 2013-04-27
[http://www.novatech.co.uk/laptop/range/novatechnspiren1536.html](http://www.novatech.co.uk/laptop/range/novatechnspiren1536.html)

Does anyone know if the above should work okay with Ubuntu 12.04 ? I've scoured the Novatech forums to no avail. However, one buyer had confirmed Kbuntu worked on it. a friend of mine has been threatened with a laptop for her anniversary present. As she's only recently gone on line, I suggested Novatech to her as they're only just up the road and very helpful. She is using my laptop at the moment and it has ubuntu on it, so she would like ubuntu as her operating system as she is used to it. She only wants it for book keeping, writing and printing and surfing the internet. She will not, for example, be bothered if I can't get the web cam to work, though it would be nice if I could.

---

### Post by Impavidus on 2013-04-27
Sounds OK. Intel hardware rarely gives problems with Ubuntu. It's just when the build-in graphics is very recent (this one from January this year I read somewhere) there might be bugs in the graphics driver, which may only be noticable under high loads and should be solved by automatic updates within months. But if Kubuntu 12.10 works, then Ubuntu or other flavours 12.04.2 or 13.04 will work too.

---

### Post by Jedwinjim on 2013-04-28
I have a Novatech nFinity Ultrabook (although the exact model no longer seems to be available on the website). I bought it last year & installed 12.04LTS. It runs like a dream (with 2 issues; 1. delayed reaction when using the hot keys to alter brightness (no big deal). 2. Bluetooth doesn't work (altlough I didn't really look into this cos I don't need it). There were 2 issues out of the box as well. 1. Trackpad didn't work. 2. Wifi didn't work. The following instructions should solve both of those issues (probably more info than you need but it'll be here if anyone uses the search function!!)

Ubuntu on Novatech Ultrabook

2 Major things don't work on a fresh install. 

1. Wireless doesn't work. 2. The trackpad & mouse don't work.

Number 1 must be done EVERY TIME you update software via the Software Update function.

To solve No 1:

[http://rricketts.com/installing-ralink-rt3290-wireless-drivers-in-ubuntu-12-04/](http://rricketts.com/installing-ralink-rt3290-wireless-drivers-in-ubuntu-12-04/)

For anybody looking to install drivers for Ralink Device 3290, I&#8217;ve finally managed to get it working so I thought I&#8217;d share.
1. Check your wireless controller hardware
lspci | grep Network
You should get the following output
Network controller: Ralink corp. Device 3290
If so, you will need to install Ralink driver 3562.
2. Download the driver source from the Ralink website, my local mirror (download here)
[http://www.ralinktech.com/en/04_support/support.php](http://www.ralinktech.com/en/04_support/support.php)
3. Extract the folder (DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217) to your home directory.
4. Open DPO_RT&#8230;/os/linux/config.mk
5. Change line 12 to read HAS_WPA_SUPPLICANT=y
Change line 15 to read HAS_NATIVE_WPA_SUPPLICANT=y
6. Open a terminal
cd >>extracted folder name here!!!<<
7.*sudo make
8. Install the driver.
sudo make install
9. Next you need to blacklist the conflicting wireless drivers
sudo gedit /etc/modprobe.d/blacklist.conf
Add the following lines:
#Wireless drivers conflicting with rt3562sta
blacklist rt2800pci
blacklist rt2x00pci
10. Tell linux to load the correct module on boot
sudo gedit /etc/modules
Append the following line:
rt3290sta
11. Update the changes
sudo update-initramfs -u
12. Restart your system. You should see a list of available networks in the network manager next time it boots.





2. fix trackpad & mouse.

Follow this link (or instructions below) to open the grub in text editor.

[http://ubuntuforums.org/showthread.php?t=1603515](http://ubuntuforums.org/showthread.php?t=1603515)

Open a terminal (Applications -> Accessories -> Terminal) and run:
Code:
gksu gedit /etc/default/grub
You will be prompted for your password. Introduce it. The text editor will open the file. Edit it, save the changes(Ctrl+s), close it (Alt+F4),then run:
Code:
sudo update-grub
to generate a new grub2 config file.

Then edit the following....:

[http://forum.novatech.co.uk/showthread.php?25330-nfinity-i5-laptop-how-can-I-get-the-touchpad-and-wireless-working-with-Ubuntu](http://forum.novatech.co.uk/showthread.php?25330-nfinity-i5-laptop-how-can-I-get-the-touchpad-and-wireless-working-with-Ubuntu)

edit*/etc/default/grub
change line*GRUB_CMDLINE_LINUX=""
to
GRUB_CMDLINE_LINUX="i8042.noloop"
run*sudo update-grub*
reboot

---

### Post by heidricha on 2013-04-29
Hi!

after downloading the driver, make fails on 13.04:

DPO_RT3290_LinuxSTA_V2600_20120508# make
..
...
....
  CC [M]  /home/heidricha/Letöltések/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../os/linux/pci_main_dev.o
/home/heidricha/Letöltések/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../os/linux/pci_main_dev.c:43:23: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;rt2860_remove_one&#8217;
/home/heidricha/Letöltések/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../os/linux/pci_main_dev.c:44:22: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;rt2860_probe&#8217;
/home/heidricha/Letöltések/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../os/linux/pci_main_dev.c:63:46: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;__devinitdata&#8217;
/home/heidricha/Letöltések/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../os/linux/pci_main_dev.c:85:17: error: &#8216;rt2860_pci_tbl&#8217; undeclared here (not in a function)
/home/heidricha/Letöltések/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../os/linux/pci_main_dev.c:86:17: error: &#8216;rt2860_probe&#8217; undeclared here (not in a function)
/home/heidricha/Letöltések/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../os/linux/pci_main_dev.c:88:5: error: implicit declaration of function &#8216;__devexit_p&#8217; [-Werror=implicit-function-declaration]
/home/heidricha/Letöltések/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../os/linux/pci_main_dev.c:88:29: error: &#8216;rt2860_remove_one&#8217; undeclared here (not in a function)
/home/heidricha/Letöltések/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../os/linux/pci_main_dev.c:292:24: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;rt2860_probe&#8217;
/home/heidricha/Letöltések/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../os/linux/pci_main_dev.c:463:23: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;rt2860_remove_one&#8217;
/home/heidricha/Letöltések/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../os/linux/pci_main_dev.c:71:1: error: &#8216;__mod_pci_device_table&#8217; aliased to undefined symbol &#8216;rt2860_pci_tbl&#8217;
cc1: some warnings being treated as errors
make[2]: *** [/home/heidricha/Letöltések/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../os/linux/pci_main_dev.o] Error 1
make[1]: *** [_module_/home/heidricha/Letöltések/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.8.0-19-generic'
make: *** [LINUX] Error 2

---

