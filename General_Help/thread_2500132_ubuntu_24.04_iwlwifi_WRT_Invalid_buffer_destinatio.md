---
title: "ubuntu 24.04 iwlwifi WRT: Invalid buffer destination on intel i915 Arc laptop"
date: 2024-08-24
forum: General Help
---

### Post by gebbione on 2024-08-24
I have installed ubuntu 24.04 along windows and it was initially booting fine. Then suddenly it failed with blackscreen output of 


```

[    2.439459] ucsi_acpi USBC000:00: UCSI_GET_PDOS failed (-70)
[    3.056541] iwlwifi 0000:00:14.3: WRT: Invalid buffer destination
[    3.216239] iwlwifi 0000:00:14.3: Not valid error log pointer 0x0027B0C0 for RT uCode
[    4.077251] iwlwifi 0000:00:14.3: WRT: Invalid buffer destination
[    4.186667] Bluetooth: hci0: Failed to send firmware data (-38)
[    4.235218] iwlwifi 0000:00:14.3: Not valid error log pointer 0x0027B0C0 for RT uCode
[    4.338477] Bluetooth: hci0: sending frame failed (-19)
[    4.338632] Bluetooth: hci0: Reading supported features failed (-19)
[    4.338850] Bluetooth: hci0: sending frame failed (-19)
[    4.338929] Bluetooth: hci0: Failed to read MSFT supported features (-19)
[    6.307134] Bluetooth: hci0: Malformed MSFT vendor event: 0x02

```


full dmesg output (adding link to dropbox because file exceeds forum size limit)  [https://www.dropbox.com/scl/fi/3wepopvodf0nrg38dq53o/asus_dmesgOutput_202408241037.txt?rlkey=q1wk1qr2km04d95cmesy49vyk&dl=0](https://www.dropbox.com/scl/fi/3wepopvodf0nrg38dq53o/asus_dmesgOutput_202408241037.txt?rlkey=q1wk1qr2km04d95cmesy49vyk&dl=0)

full journalctl output -> [https://www.dropbox.com/scl/fi/0ygz3chbky0vfgxb17mb9/asus_journalctlOutput_202408241042.txt?rlkey=biq8twm9ttj9umhmzeqbisl3l&dl=0](https://www.dropbox.com/scl/fi/0ygz3chbky0vfgxb17mb9/asus_journalctlOutput_202408241042.txt?rlkey=biq8twm9ttj9umhmzeqbisl3l&dl=0)

**inxi -G** output 

> Graphics:
  Device-1: Intel Meteor Lake-P [Intel Arc Graphics] driver: N/A
  Device-2: Shinetech USB2.0 FHD UVC WebCam driver: uvcvideo type: USB
  Display: server: X.org v: 1.21.1.11 driver: X: loaded: modesetting,vesa unloaded: fbdev
    gpu: N/A tty: 205x64
  API: EGL v: 1.5 drivers: kms_swrast,swrast platforms: gbm,surfaceless,device
  API: OpenGL v: 4.5 note: console (EGL sourced) renderer: llvmpipe (LLVM 17.0.6 256 bits)

**lspci** output

> 0000:00:00.0 Host bridge: Intel Corporation Device 7d01 (rev 04)
0000:00:02.0 VGA compatible controller: Intel Corporation Meteor Lake-P [Intel Arc Graphics] (rev 08)
0000:00:04.0 Signal processing controller: Intel Corporation Device 7d03 (rev 04)
0000:00:07.0 PCI bridge: Intel Corporation Meteor Lake-P Thunderbolt 4 PCI Express Root Port #0 (rev 10)
0000:00:07.1 PCI bridge: Intel Corporation Meteor Lake-P Thunderbolt 4 PCI Express Root Port #1 (rev 10)
0000:00:08.0 System peripheral: Intel Corporation Device 7e4c (rev 20)
0000:00:0a.0 Signal processing controller: Intel Corporation Device 7d0d (rev 01)
0000:00:0b.0 Processing accelerators: Intel Corporation Meteor Lake NPU (rev 04)
0000:00:0d.0 USB controller: Intel Corporation Meteor Lake-P Thunderbolt 4 USB Controller (rev 10)
0000:00:0d.2 USB controller: Intel Corporation Meteor Lake-P Thunderbolt 4 NHI #0 (rev 10)
0000:00:0e.0 RAID bus controller: Intel Corporation Volume Management Device NVMe RAID Controller Intel Corporation
0000:00:12.0 Serial controller: Intel Corporation Device 7e45 (rev 20)
0000:00:14.0 USB controller: Intel Corporation Meteor Lake-P USB 3.2 Gen 2x1 xHCI Host Controller (rev 20)
0000:00:14.2 RAM memory: Intel Corporation Device 7e7f (rev 20)
0000:00:14.3 Network controller: Intel Corporation Meteor Lake PCH CNVi WiFi (rev 20)
0000:00:15.0 Serial bus controller: Intel Corporation Meteor Lake-P Serial IO I2C Controller #0 (rev 20)
0000:00:15.1 Serial bus controller: Intel Corporation Meteor Lake-P Serial IO I2C Controller #1 (rev 20)
0000:00:16.0 Communication controller: Intel Corporation Device 7e70 (rev 20)
0000:00:1e.0 Communication controller: Intel Corporation Meteor Lake-P Serial IO UART Controller #0 (rev 20)
0000:00:1e.3 Serial bus controller: Intel Corporation Meteor Lake-P Serial IO SPI Controller #1 (rev 20)
0000:00:1f.0 ISA bridge: Intel Corporation Device 7e02 (rev 20)
0000:00:1f.3 Multimedia audio controller: Intel Corporation Meteor Lake-P HD Audio Controller (rev 20)
0000:00:1f.4 SMBus: Intel Corporation Meteor Lake-P SMBus Controller (rev 20)
0000:00:1f.5 Serial bus controller: Intel Corporation Meteor Lake-P SPI Controller (rev 20)
10000:e0:06.0 System peripheral: Intel Corporation RST VMD Managed Controller
10000:e0:06.2 PCI bridge: Intel Corporation Device 7ecb (rev 10)
10000:e1:00.0 Non-Volatile memory controller: Micron Technology Inc 2400 NVMe SSD (DRAM-less) (rev 03)

It was pointed to me that the driver is not detected but this is not supposed to happen.

 Given the bluetooth error line i disabled bluetooth as suggested here [https://bbs.archlinux.org/viewtopic.php?pid=2047364#p2047364](https://bbs.archlinux.org/viewtopic.php?pid=2047364#p2047364) but this has not stopped the bluetooth error "Bluetooth: hci0: Malformed MSFT vendor event: 0x02" from being printed out.

Some of these issues usually underly in something else but I am unable to establish what the problem is. Definitely not a full disk

**So far I tried**:
- added the nomodeset option that sometimes causes kernel blackscreens, but this did not fix it
- disabled wifi and bluetooth from bios but still had a blackscreen, just not the errors about wifi and bluetooth
- I can CTRL + ALT + F2 and use a shell to login. Just  X/UI is not starting
- I added some options, xe.force_probe etc, to the booting command in GRUB as suggested in the journalctl so now the booting command looks like this "*BOOT_IMAGE=/boot/vmlinuz-6.8.0-41-generic root=UUID=17cfdb2a-c749-45b7-88df-c5c9fbfbd8cc ro quiet nomodeset snd_hda_intel.dmic_detect=0 xe.force_probe=7d55 i915.force_probe=!7d55*"
- I have added some extra drivers as suggested on IRC Libera [https://launchpad.net/~oibaf/+archive/ubuntu/graphics-drivers](https://launchpad.net/~oibaf/+archive/ubuntu/graphics-drivers)
After installing the drivers i can see this output from **inxi -G**

> Graphics:
  Device-1: Intel Meteor Lake-P [Intel Arc Graphics] driver: xe v: kernel
  Device-2: Shinetech USB2.0 FHD UVC WebCam driver: uvcvideo type: USB
  Display: server: X.org v: 1.21.1.11 driver: X: loaded: modesetting,vesa unloaded: fbdev
    gpu: xe tty: 180x56 resolution: 2880x1800
  API: EGL v: 1.5 drivers: iris,swrast platforms: gbm,surfaceless,device
  API: OpenGL v: 4.6 compat-v: 4.5 note: console (EGL sourced) renderer: Mesa Intel Arc
    Graphics (MTL), llvmpipe (LLVM 17.0.6 256 bits)

[B]So it looks like xe is the driver running it but i am still not seeing the UX
[/B]
Screen is still black and not starting the UI. What else can I try to fix this?

---

### Post by gebbione on 2024-08-29
Today i tried to run an update, ie 

> *sudo apt update && upgrade* 
... this did not fix the blackscreen. 
Out of ideas i looked at ways to re-install and i run

> *sudo apt-get install --reinstall ubuntu-desktop*

After reinstalling ubuntu-desktop i got a completely blackscreen and could not even get a shell. I restarted the lapton and then suddenly I saw the Gnome login prompt. The laptop is running but i still see flickering on the screen. 
I noticed the bios was not to the latest version so i also updated it. But it did not fix the problem. At least for now i have a running laptop, but I think there might be a drivers problem of sorts.

I would be happy to run any further diagnostic to ensure I9 ARC drivers are fully compatible for Ubuntu

---

### Post by Yellow Pasque on 2024-08-31
Are you still using xe kernel module or did you switch back to i915?

---

### Post by gebbione on 2024-08-31
I am still booting with "*xe.force_probe=7d55 i915.force_probe=!7d55*" . Screen still flickering and i tried to install cairo-dock that fails to run even if started in safe mode **cairo-dock -f** . 

Output 

> bizmate@bizmate-Zenbook14:~$ cairo-dock -f
warning :  (./src/implementations/cairo-dock-egl.c:gldi_register_egl_backend:232)  
  Cairo-Dock was not built with EGL support
MESA: warning: Support for this platform is experimental with Xe KMD, bug reports may be ignored.
warning :  (./src/implementations/cairo-dock-glx.c:_initialize_opengl_backend:129)  
  couldn't find an appropriate visual, trying to get one without Stencil buffer
(it may cause some little deterioration in the rendering) ...


 ============================================================================
	Cairo-Dock version : 3.4.1
	Compiled date      : Mar 31 2024 17:45:13
	Built with GTK     : 3.24
	Running with OpenGL: 1
 ============================================================================


warning :  (./src/gldit/cairo-dock-utils.c:cairo_dock_launch_command_sync_with_stderr:253)  
  Failed to execute child process &#8220;gconftool-2&#8221; (No such file or directory)
g_file_test: assertion 'filename != NULL' failed
g_file_test: assertion 'filename != NULL' failed

Laster journal output here [https://termbin.com/ouft](https://termbin.com/ouft)

---

