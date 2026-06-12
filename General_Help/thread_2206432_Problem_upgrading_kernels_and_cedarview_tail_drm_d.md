---
title: "Problem upgrading kernels and cedarview tail drm driver"
date: 2014-02-19
forum: General Help
---

### Post by Psil0cybin on 2014-02-19
System Information:
**Kernel Causing Problems: **Linux  3.2.0-59-generic-pae Ubuntu 12.04 LTS
**Latest Working Kernel: **3.2.0-58-generic-pae 


Hey guys I turned on my computer and it suggested I needed to upgrade kernels.

After upgrading i got a crash report for cedarview tail, my graphic driver (great) not a great sign.

Restarting my laptop I noticed graphic issues right away, function keys do not work, etc, font is off (not displaying like it used to) 
Additional drivers suggested that I can install Cedarview Tail again, but when I click install it states

> Sorry, installation of this driver failed.


Please have a look at the log file for details: /var/log/jockey.log



**my jockey log.**
```
2014-02-19 02:47:02,781 DEBUG: Comparing 3.2.0-55 with 2014-02-19 02:47:02,819 DEBUG: Comparing 3.2.0-56 with 3.2.0-55
2014-02-19 02:47:02,829 DEBUG: Comparing 3.2.0-57 with 3.2.0-56
2014-02-19 02:47:02,842 DEBUG: Comparing 3.2.0-58 with 3.2.0-57
2014-02-19 02:47:02,862 DEBUG: Comparing 3.2.0-59 with 3.2.0-58
2014-02-19 02:47:04,859 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x95a3d2c>
2014-02-19 02:47:11,625 DEBUG: reading modalias file /lib/modules/3.2.0-59-generic-pae/modules.alias
2014-02-19 02:47:12,143 DEBUG: reading modalias file /usr/share/jockey/modaliases/b43
2014-02-19 02:47:12,157 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2014-02-19 02:47:12,400 DEBUG: loading custom handler /usr/share/jockey/handlers/pvr-omap4.py
2014-02-19 02:47:12,440 WARNING: modinfo for module omapdrm_pvr failed: ERROR: modinfo: could not find module omapdrm_pvr


2014-02-19 02:47:14,182 DEBUG: linux-lts-raring installed: False
linux-lts-saucy installed: False
linux minor version: 2
xserver ABI: 11
xserver-lts-quantal: False
2014-02-19 02:47:14,195 DEBUG: Instantiated Handler subclass __builtin__.PVROmap4Driver from name PVROmap4Driver
2014-02-19 02:47:15,566 DEBUG: PowerVR SGX proprietary graphics driver for OMAP 4 not available
2014-02-19 02:47:15,567 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2014-02-19 02:47:15,585 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci


2014-02-19 02:47:15,587 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2014-02-19 02:47:15,587 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2014-02-19 02:47:15,587 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2014-02-19 02:47:15,737 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2014-02-19 02:47:15,739 DEBUG: Firmware for DVB cards not available
2014-02-19 02:47:15,740 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2014-02-19 02:47:15,799 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2014-02-19 02:47:15,832 DEBUG: Software modem not available
2014-02-19 02:47:15,833 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2014-02-19 02:47:15,896 WARNING: modinfo for module fglrx_experimental_12 failed: ERROR: modinfo: could not find module fglrx_experimental_12


2014-02-19 02:47:16,001 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriverExperimental12 from name FglrxDriverExperimental12
2014-02-19 02:47:16,001 DEBUG: fglrx.available: falling back to default
2014-02-19 02:47:16,067 DEBUG: ATI/AMD proprietary FGLRX graphics driver (**experimental** beta) not available
2014-02-19 02:47:16,075 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates


2014-02-19 02:47:16,092 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriverUpdate from name FglrxDriverUpdate
2014-02-19 02:47:16,093 DEBUG: fglrx.available: falling back to default
2014-02-19 02:47:27,441 DEBUG: ATI/AMD proprietary FGLRX graphics driver (post-release updates) availability undetermined, adding to pool
2014-02-19 02:47:27,448 WARNING: modinfo for module fglrx_experimental_9 failed: ERROR: modinfo: could not find module fglrx_experimental_9


2014-02-19 02:47:27,501 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriverExperimental9 from name FglrxDriverExperimental9
2014-02-19 02:47:27,503 DEBUG: fglrx.available: falling back to default
2014-02-19 02:47:27,556 DEBUG: ATI/AMD proprietary FGLRX graphics driver (**experimental** beta) not available
2014-02-19 02:47:27,571 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx


2014-02-19 02:47:27,580 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriverHybrid from name FglrxDriverHybrid
2014-02-19 02:47:27,581 DEBUG: fglrx.available: falling back to default
2014-02-19 02:47:37,735 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2014-02-19 02:47:37,749 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx


2014-02-19 02:47:37,767 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2014-02-19 02:47:37,768 DEBUG: fglrx.available: falling back to default
2014-02-19 02:47:47,816 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2014-02-19 02:47:47,826 WARNING: modinfo for module fglrx_experimental_13 failed: ERROR: modinfo: could not find module fglrx_experimental_13


2014-02-19 02:47:47,913 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriverExperimental13 from name FglrxDriverExperimental13
2014-02-19 02:47:47,914 DEBUG: fglrx.available: falling back to default
2014-02-19 02:47:54,329 DEBUG: ATI/AMD proprietary FGLRX graphics driver (**experimental** beta) availability undetermined, adding to pool
2014-02-19 02:47:54,330 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2014-02-19 02:47:54,353 WARNING: modinfo for module nvidia_304 failed: ERROR: modinfo: could not find module nvidia_304


2014-02-19 02:47:54,362 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver304 from name NvidiaDriver304
2014-02-19 02:47:54,363 DEBUG: nvidia.available: falling back to default
2014-02-19 02:48:09,058 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2014-02-19 02:48:09,075 WARNING: modinfo for module nvidia_304_updates failed: ERROR: modinfo: could not find module nvidia_304_updates


2014-02-19 02:48:09,095 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver304Updates from name NvidiaDriver304Updates
2014-02-19 02:48:09,096 DEBUG: nvidia.available: falling back to default
2014-02-19 02:48:23,789 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2014-02-19 02:48:23,800 WARNING: modinfo for module nvidia_experimental_304 failed: ERROR: modinfo: could not find module nvidia_experimental_304


2014-02-19 02:48:23,890 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverExperimental304 from name NvidiaDriverExperimental304
2014-02-19 02:48:23,891 DEBUG: nvidia.available: falling back to default
2014-02-19 02:48:23,987 DEBUG: NVIDIA accelerated graphics driver (**experimental** beta) not available
2014-02-19 02:48:23,998 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current


2014-02-19 02:48:24,009 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2014-02-19 02:48:24,009 DEBUG: nvidia.available: falling back to default
2014-02-19 02:48:24,096 DEBUG: NVIDIA accelerated graphics driver not available
2014-02-19 02:48:24,103 WARNING: modinfo for module nvidia_current_updates failed: ERROR: modinfo: could not find module nvidia_current_updates


2014-02-19 02:48:24,121 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrentUpdates from name NvidiaDriverCurrentUpdates
2014-02-19 02:48:24,121 DEBUG: nvidia.available: falling back to default
2014-02-19 02:48:24,217 DEBUG: NVIDIA accelerated graphics driver (post-release updates) not available
2014-02-19 02:48:24,232 WARNING: modinfo for module nvidia_319 failed: ERROR: modinfo: could not find module nvidia_319


2014-02-19 02:48:24,252 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver319 from name NvidiaDriver319
2014-02-19 02:48:24,253 DEBUG: nvidia.available: falling back to default
2014-02-19 02:48:24,319 DEBUG: NVIDIA accelerated graphics driver not available
2014-02-19 02:48:24,328 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173


2014-02-19 02:48:24,347 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2014-02-19 02:48:24,348 DEBUG: nvidia.available: falling back to default
2014-02-19 02:48:49,800 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2014-02-19 02:48:49,812 WARNING: modinfo for module nvidia_173_updates failed: ERROR: modinfo: could not find module nvidia_173_updates


2014-02-19 02:48:49,825 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173Updates from name NvidiaDriver173Updates
2014-02-19 02:48:49,826 DEBUG: nvidia.available: falling back to default
2014-02-19 02:48:49,905 DEBUG: NVIDIA accelerated graphics driver (post-release updates) not available
2014-02-19 02:48:49,921 WARNING: modinfo for module nvidia_331 failed: ERROR: modinfo: could not find module nvidia_331


2014-02-19 02:48:49,940 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver331 from name NvidiaDriver331
2014-02-19 02:48:49,942 DEBUG: nvidia.available: falling back to default
2014-02-19 02:49:01,078 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2014-02-19 02:49:01,095 WARNING: modinfo for module nvidia_experimental_310 failed: ERROR: modinfo: could not find module nvidia_experimental_310


2014-02-19 02:49:01,203 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverExperimental310 from name NvidiaDriverExperimental310
2014-02-19 02:49:01,204 DEBUG: nvidia.available: falling back to default
2014-02-19 02:49:01,297 DEBUG: NVIDIA accelerated graphics driver (**experimental** beta) not available
2014-02-19 02:49:01,306 WARNING: modinfo for module nvidia_319_updates failed: ERROR: modinfo: could not find module nvidia_319_updates


2014-02-19 02:49:01,316 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver319Updates from name NvidiaDriver319Updates
2014-02-19 02:49:01,317 DEBUG: nvidia.available: falling back to default
2014-02-19 02:49:01,374 DEBUG: NVIDIA accelerated graphics driver (post-release updates) not available
2014-02-19 02:49:01,381 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96


2014-02-19 02:49:01,390 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2014-02-19 02:49:01,391 DEBUG: nvidia.available: falling back to default
2014-02-19 02:49:10,069 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2014-02-19 02:49:10,080 WARNING: modinfo for module nvidia_96_updates failed: ERROR: modinfo: could not find module nvidia_96_updates


2014-02-19 02:49:10,095 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96Updates from name NvidiaDriver96Updates
2014-02-19 02:49:10,097 DEBUG: nvidia.available: falling back to default
2014-02-19 02:49:14,389 DEBUG: XorgDriverHandler(nvidia_96_updates, nvidia-96-updates, None): Disabling as package video ABI(s) xorg-video-abi-10 not compatible with X.org video ABI xorg-video-abi-11
2014-02-19 02:49:14,391 DEBUG: NVIDIA accelerated graphics driver (post-release updates) not available
2014-02-19 02:49:14,406 WARNING: modinfo for module nvidia_331_updates failed: ERROR: modinfo: could not find module nvidia_331_updates


2014-02-19 02:49:14,425 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver331Updates from name NvidiaDriver331Updates
2014-02-19 02:49:14,427 DEBUG: nvidia.available: falling back to default
2014-02-19 02:49:25,452 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2014-02-19 02:49:25,453 DEBUG: loading custom handler /usr/share/jockey/handlers/vmware-client.py
2014-02-19 02:49:25,534 WARNING: modinfo for module vmxnet failed: ERROR: modinfo: could not find module vmxnet


2014-02-19 02:49:25,534 DEBUG: Instantiated Handler subclass __builtin__.VmwareClientHandler from name VmwareClientHandler
2014-02-19 02:49:25,619 DEBUG: VMWare Client Tools availability undetermined, adding to pool
2014-02-19 02:49:25,620 DEBUG: loading custom handler /usr/share/jockey/handlers/cdv.py
2014-02-19 02:49:25,661 WARNING: modinfo for module cedarview_gfx failed: ERROR: modinfo: could not find module cedarview_gfx


2014-02-19 02:49:25,664 DEBUG: Instantiated Handler subclass __builtin__.CdvDriver from name CdvDriver
2014-02-19 02:49:25,664 DEBUG: cdv.available: falling back to default
2014-02-19 02:49:27,158 DEBUG: Intel Cedarview graphics driver availability undetermined, adding to pool
2014-02-19 02:49:27,159 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2014-02-19 02:49:27,192 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl


2014-02-19 02:49:27,253 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2014-02-19 02:49:27,254 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2014-02-19 02:49:27,255 DEBUG: all custom handlers loaded
2014-02-19 02:49:27,256 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x95a3d2c> about HardwareID('modalias', 'pci:v00008086d000027D8sv00001025sd0000061Fbc04sc03i00')
2014-02-19 02:49:28,323 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2014-02-19 02:49:28,622 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2014-02-19 02:49:28,622 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2014-02-19 02:49:28,623 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2014-02-19 02:49:28,623 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x95a3d2c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2014-02-19 02:49:28,641 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2014-02-19 02:49:28,642 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2014-02-19 02:49:28,642 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x95a3d2c> about HardwareID('modalias', 'pci:v00008086d000027DAsv00001025sd0000061Fbc0Csc05i00')
2014-02-19 02:49:28,657 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801'}
2014-02-19 02:49:28,657 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801', 'jockey_handler': 'KernelModuleHandler'}
2014-02-19 02:49:28,658 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x95a3d2c> about HardwareID('modalias', 'pci:v00008086d000027C1sv00001025sd0000061Fbc01sc06i01')
2014-02-19 02:49:28,671 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x95a3d2c> about HardwareID('modalias', 'acpi:PNP0103:PNP0C01:')
2014-02-19 02:49:28,672 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x95a3d2c> about HardwareID('modalias', 'acpi:PNP0303:')
2014-02-19 02:49:28,672 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x95a3d2c> about HardwareID('modalias', 'pci:v000010ECd00008136sv00001025sd0000061Fbc02sc00i00')
2014-02-19 02:49:28,704 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'r8169'}
2014-02-19 02:49:28,704 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'r8169', 'jockey_handler': 'KernelModuleHandler'}
2014-02-19 02:49:28,705 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x95a3d2c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2014-02-19 02:49:28,705 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2014-02-19 02:49:28,706 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2014-02-19 02:49:28,706 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x95a3d2c> about HardwareID('modalias', 'platform:regulatory')
2014-02-19 02:49:28,708 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x95a3d2c> about HardwareID('modalias', 'usb:v1D6Bp0001d0302dc09dsc00dp00ic09isc00ip00')
2014-02-19 02:49:28,757 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x95a3d2c> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,8A,8C,8D,8E,8F,94,95,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,C0,C1,D9,E0,E1,E2,E3,EC,ED,EE,1A9,1B2,1B3,1D0,ram4,l0,1,2,sfw')
2014-02-19 02:49:28,758 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2014-02-19 02:49:28,758 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2014-02-19 02:49:28,758 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2014-02-19 02:49:28,759 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2014-02-19 02:49:28,759 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x95a3d2c> about HardwareID('modalias', 'acpi:INT0800:')
2014-02-19 02:49:28,760 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x95a3d2c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2014-02-19 02:49:28,761 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x95a3d2c> about HardwareID('modalias', 'pci:v00008086d000027CAsv00001025sd0000061Fbc0Csc03i00')
2014-02-19 02:49:28,775 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x95a3d2c> about HardwareID('modalias', 'platform:acer-wmi')
2014-02-19 02:49:28,777 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x95a3d2c> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2014-02-19 02:49:28,777 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x95a3d2c> about HardwareID('modalias', 'pci:v00008086d00000BF1sv00001025sd0000061Fbc06sc00i00')
2014-02-19 02:49:28,791 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x95a3d2c> about HardwareID('modalias', 'wmi:FE1DBBDA-3014-4856-870C-5B3A744BF341')
2014-02-19 02:49:28,791 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x95a3d2c> about HardwareID('modalias', 'acpi:LNXVIDEO:')
2014-02-19 02:49:28,792 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x95a3d2c> about HardwareID('modalias', 'acpi:LNXSYBUS:')
2014-02-19 02:49:28,792 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x95a3d2c> about HardwareID('modalias', 'pci:v00008086d00000BE1sv00001025sd0000061Fbc03sc00i00')
2014-02-19 02:49:28,805 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'cedarview_gfx', 'package': 'cedarview-drm'}
2014-02-19 02:49:28,813 WARNING: modinfo for module cedarview_gfx failed: ERROR: modinfo: could not find module cedarview_gfx


2014-02-19 02:49:28,882 WARNING: modinfo for module cedarview_gfx failed: ERROR: modinfo: could not find module cedarview_gfx


2014-02-19 02:49:28,884 DEBUG: got handler kmod:cedarview_gfx([KernelModuleHandler, nonfree, disabled] Cedar Trail drm driver in DKMS format.)
2014-02-19 02:49:28,885 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x95a3d2c> about HardwareID('modalias', 'acpi:PNP0200:')
2014-02-19 02:49:28,886 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x95a3d2c> about HardwareID('modalias', 'pci:v0000168Cd00000032sv0000105Bsd0000E047bc02sc80i00')
2014-02-19 02:49:28,931 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'ath9k'}
2014-02-19 02:49:28,931 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ath9k', 'jockey_handler': 'KernelModuleHandler'}
2014-02-19 02:49:28,932 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x95a3d2c> about HardwareID('modalias', 'acpi:PNP0000:')
2014-02-19 02:49:28,932 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x95a3d2c> about HardwareID('modalias', 'acpi:PNP0B00:')
2014-02-19 02:49:28,932 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x95a3d2c> about HardwareID('modalias', 'pci:v00008086d000027C8sv00001025sd0000061Fbc0Csc03i00')
2014-02-19 02:49:28,947 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x95a3d2c> about HardwareID('modalias', 'pci:v00008086d000027BCsv00001025sd0000061Fbc06sc01i00')
2014-02-19 02:49:28,960 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt'}
2014-02-19 02:49:28,961 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt', 'jockey_handler': 'KernelModuleHandler'}
2014-02-19 02:49:28,961 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x95a3d2c> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2014-02-19 02:49:28,962 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2014-02-19 02:49:28,962 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2014-02-19 02:49:28,963 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2014-02-19 02:49:28,963 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2014-02-19 02:49:28,963 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x95a3d2c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,8,')
2014-02-19 02:49:28,964 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2014-02-19 02:49:28,965 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2014-02-19 02:49:28,966 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x95a3d2c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2014-02-19 02:49:28,967 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2014-02-19 02:49:28,967 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2014-02-19 02:49:28,968 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2014-02-19 02:49:28,968 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2014-02-19 02:49:28,969 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x95a3d2c> about HardwareID('modalias', 'pci:v000010ECd00005209sv00001025sd0000061FbcFFsc00i00')
2014-02-19 02:49:28,970 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'rts_pstor'}
2014-02-19 02:49:28,970 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'rts_pstor', 'jockey_handler': 'KernelModuleHandler'}
2014-02-19 02:49:28,971 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x95a3d2c> about HardwareID('modalias', 'dmi:bvnInsydeCorp.:bvrV1.10:bd07/23/2013:svnAcer:pnAOD270:pvrV1.10:rvnAcer:rnJE01_CT:rvrBaseBoardVersion:cvnChassisManufacturer:ct10:cvrChassisVersion:')
2014-02-19 02:49:29,031 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x95a3d2c> about HardwareID('modalias', 'wmi:61EF69EA-865C-4BC3-A502-A0DEBA0CB531')
2014-02-19 02:49:29,032 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x95a3d2c> about HardwareID('modalias', 'acpi:PNP0C04:')
2014-02-19 02:49:29,032 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x95a3d2c> about HardwareID('modalias', 'wmi:79772EC5-04B1-4BFD-843C-61E7F77B6CC9')
2014-02-19 02:49:29,033 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x95a3d2c> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2014-02-19 02:49:29,033 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2014-02-19 02:49:29,034 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2014-02-19 02:49:29,034 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x95a3d2c> about HardwareID('modalias', 'usb:v1D6Bp0002d0302dc09dsc00dp00ic09isc00ip00')
2014-02-19 02:49:29,035 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x95a3d2c> about HardwareID('modalias', 'usb:v0402p7675d0004dcEFdsc02dp01ic0Eisc01ip00')
2014-02-19 02:49:29,039 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo'}
2014-02-19 02:49:29,040 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo', 'jockey_handler': 'KernelModuleHandler'}
2014-02-19 02:49:29,040 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x95a3d2c> about HardwareID('modalias', 'acpi:PNP0100:')
2014-02-19 02:49:29,040 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x95a3d2c> about HardwareID('modalias', 'acpi:PNP0C02:')
2014-02-19 02:49:29,040 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x95a3d2c> about HardwareID('modalias', 'pci:v00008086d00002448sv00001025sd0000061Fbc06sc04i01')
2014-02-19 02:49:29,054 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x95a3d2c> about HardwareID('modalias', 'wmi:F75F5666-B8B3-4A5D-A91C-7488F62E5637')
2014-02-19 02:49:29,054 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x95a3d2c> about HardwareID('modalias', 'pci:v00008086d000027CCsv00001025sd0000061Fbc0Csc03i20')
2014-02-19 02:49:29,068 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x95a3d2c> about HardwareID('modalias', 'pci:v00008086d000027C9sv00001025sd0000061Fbc0Csc03i00')
2014-02-19 02:49:29,082 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x95a3d2c> about HardwareID('modalias', 'platform:pcspkr')
2014-02-19 02:49:29,084 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr'}
2014-02-19 02:49:29,085 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2014-02-19 02:49:29,085 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp'}
2014-02-19 02:49:29,086 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2014-02-19 02:49:29,086 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x95a3d2c> about HardwareID('modalias', 'input:b0011v0002p0007e01B1-e0,1,3,k110,111,145,14A,14D,14E,ra0,1,18,1C,2F,35,36,39,mlsfw')
2014-02-19 02:49:29,087 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2014-02-19 02:49:29,087 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2014-02-19 02:49:29,087 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2014-02-19 02:49:29,088 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2014-02-19 02:49:29,088 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2014-02-19 02:49:29,089 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2014-02-19 02:49:29,089 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2014-02-19 02:49:29,089 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2014-02-19 02:49:29,090 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2014-02-19 02:49:29,090 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2014-02-19 02:49:29,090 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x95a3d2c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2014-02-19 02:49:29,091 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x95a3d2c> about HardwareID('modalias', 'usb:v0402p7675d0004dcEFdsc02dp01ic0Eisc02ip00')
2014-02-19 02:49:29,092 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x95a3d2c> about HardwareID('modalias', 'wmi:676AA15E-6A47-4D9F-A2CC-1E6D18D14026')
2014-02-19 02:49:29,092 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'acer_wmi'}
2014-02-19 02:49:29,093 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'acer_wmi', 'jockey_handler': 'KernelModuleHandler'}
2014-02-19 02:49:29,093 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x95a3d2c> about HardwareID('modalias', 'platform:eisa')
2014-02-19 02:49:29,095 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x95a3d2c> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2014-02-19 02:49:29,123 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw'}
2014-02-19 02:49:29,123 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2014-02-19 02:49:29,124 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'psmouse'}
2014-02-19 02:49:29,124 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2014-02-19 02:49:29,124 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x95a3d2c> about HardwareID('modalias', 'pci:v00008086d000027CBsv00001025sd0000061Fbc0Csc03i00')
2014-02-19 02:49:29,138 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x95a3d2c> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,1,4,k94,95,BF,CA,CB,E3,ED,EE,F0,ram4,lsfw')
2014-02-19 02:49:29,139 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2014-02-19 02:49:29,139 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2014-02-19 02:49:29,139 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2014-02-19 02:49:29,140 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2014-02-19 02:49:29,140 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x95a3d2c> about HardwareID('modalias', 'input:b0003v0402p7675e0004-e0,1,kD4,ramlsfw')
2014-02-19 02:49:29,140 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2014-02-19 02:49:29,141 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2014-02-19 02:49:29,141 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2014-02-19 02:49:29,142 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2014-02-19 02:49:29,142 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x95a3d2c> about HardwareID('modalias', 'acpi:SYN1B20:SYN1B00:SYN0002:PNP0F13:')
2014-02-19 02:49:29,142 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x95a3bcc> about HardwareID('modalias', 'pci:v00008086d000027D8sv00001025sd0000061Fbc04sc03i00')
2014-02-19 02:49:29,143 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x95a3bcc> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2014-02-19 02:49:29,143 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x95a3bcc> about HardwareID('modalias', 'pci:v00008086d000027DAsv00001025sd0000061Fbc0Csc05i00')
2014-02-19 02:49:29,143 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x95a3bcc> about HardwareID('modalias', 'pci:v00008086d000027C1sv00001025sd0000061Fbc01sc06i01')
2014-02-19 02:49:29,144 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x95a3bcc> about HardwareID('modalias', 'acpi:PNP0103:PNP0C01:')
2014-02-19 02:49:29,144 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x95a3bcc> about HardwareID('modalias', 'acpi:PNP0303:')
2014-02-19 02:49:29,144 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x95a3bcc> about HardwareID('modalias', 'pci:v000010ECd00008136sv00001025sd0000061Fbc02sc00i00')
2014-02-19 02:49:29,144 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x95a3bcc> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2014-02-19 02:49:29,145 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x95a3bcc> about HardwareID('modalias', 'platform:regulatory')
2014-02-19 02:49:29,145 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x95a3bcc> about HardwareID('modalias', 'usb:v1D6Bp0001d0302dc09dsc00dp00ic09isc00ip00')
2014-02-19 02:49:29,145 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x95a3bcc> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,8A,8C,8D,8E,8F,94,95,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,C0,C1,D9,E0,E1,E2,E3,EC,ED,EE,1A9,1B2,1B3,1D0,ram4,l0,1,2,sfw')
2014-02-19 02:49:29,145 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x95a3bcc> about HardwareID('modalias', 'acpi:INT0800:')
2014-02-19 02:49:29,146 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x95a3bcc> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2014-02-19 02:49:29,146 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x95a3bcc> about HardwareID('modalias', 'pci:v00008086d000027CAsv00001025sd0000061Fbc0Csc03i00')
2014-02-19 02:49:29,146 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x95a3bcc> about HardwareID('modalias', 'platform:acer-wmi')
2014-02-19 02:49:29,147 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x95a3bcc> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2014-02-19 02:49:29,147 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x95a3bcc> about HardwareID('modalias', 'pci:v00008086d00000BF1sv00001025sd0000061Fbc06sc00i00')
2014-02-19 02:49:29,147 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x95a3bcc> about HardwareID('modalias', 'wmi:FE1DBBDA-3014-4856-870C-5B3A744BF341')
2014-02-19 02:49:29,147 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x95a3bcc> about HardwareID('modalias', 'acpi:LNXVIDEO:')
2014-02-19 02:49:29,148 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x95a3bcc> about HardwareID('modalias', 'acpi:LNXSYBUS:')
2014-02-19 02:49:29,148 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x95a3bcc> about HardwareID('modalias', 'pci:v00008086d00000BE1sv00001025sd0000061Fbc03sc00i00')
2014-02-19 02:49:29,148 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x95a3bcc> about HardwareID('modalias', 'acpi:PNP0200:')
2014-02-19 02:49:29,148 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x95a3bcc> about HardwareID('modalias', 'pci:v0000168Cd00000032sv0000105Bsd0000E047bc02sc80i00')
2014-02-19 02:49:29,149 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x95a3bcc> about HardwareID('modalias', 'acpi:PNP0000:')
2014-02-19 02:49:29,149 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x95a3bcc> about HardwareID('modalias', 'acpi:PNP0B00:')
2014-02-19 02:49:29,149 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x95a3bcc> about HardwareID('modalias', 'pci:v00008086d000027C8sv00001025sd0000061Fbc0Csc03i00')
2014-02-19 02:49:29,149 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x95a3bcc> about HardwareID('modalias', 'pci:v00008086d000027BCsv00001025sd0000061Fbc06sc01i00')
2014-02-19 02:49:29,150 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x95a3bcc> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2014-02-19 02:49:29,150 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x95a3bcc> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,8,')
2014-02-19 02:49:29,150 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x95a3bcc> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2014-02-19 02:49:29,151 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x95a3bcc> about HardwareID('modalias', 'pci:v000010ECd00005209sv00001025sd0000061FbcFFsc00i00')
2014-02-19 02:49:29,151 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x95a3bcc> about HardwareID('modalias', 'dmi:bvnInsydeCorp.:bvrV1.10:bd07/23/2013:svnAcer:pnAOD270:pvrV1.10:rvnAcer:rnJE01_CT:rvrBaseBoardVersion:cvnChassisManufacturer:ct10:cvrChassisVersion:')
2014-02-19 02:49:29,151 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x95a3bcc> about HardwareID('modalias', 'wmi:61EF69EA-865C-4BC3-A502-A0DEBA0CB531')
2014-02-19 02:49:29,151 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x95a3bcc> about HardwareID('modalias', 'acpi:PNP0C04:')
2014-02-19 02:49:29,152 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x95a3bcc> about HardwareID('modalias', 'wmi:79772EC5-04B1-4BFD-843C-61E7F77B6CC9')
2014-02-19 02:49:29,152 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x95a3bcc> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2014-02-19 02:49:29,152 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x95a3bcc> about HardwareID('modalias', 'usb:v1D6Bp0002d0302dc09dsc00dp00ic09isc00ip00')
2014-02-19 02:49:29,152 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x95a3bcc> about HardwareID('modalias', 'usb:v0402p7675d0004dcEFdsc02dp01ic0Eisc01ip00')
2014-02-19 02:49:29,153 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x95a3bcc> about HardwareID('modalias', 'acpi:PNP0100:')
2014-02-19 02:49:29,153 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x95a3bcc> about HardwareID('modalias', 'acpi:PNP0C02:')
2014-02-19 02:49:29,153 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x95a3bcc> about HardwareID('modalias', 'pci:v00008086d00002448sv00001025sd0000061Fbc06sc04i01')
2014-02-19 02:49:29,153 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x95a3bcc> about HardwareID('modalias', 'wmi:F75F5666-B8B3-4A5D-A91C-7488F62E5637')
2014-02-19 02:49:29,154 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x95a3bcc> about HardwareID('modalias', 'pci:v00008086d000027CCsv00001025sd0000061Fbc0Csc03i20')
2014-02-19 02:49:29,154 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x95a3bcc> about HardwareID('modalias', 'pci:v00008086d000027C9sv00001025sd0000061Fbc0Csc03i00')
2014-02-19 02:49:29,154 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x95a3bcc> about HardwareID('modalias', 'platform:pcspkr')
2014-02-19 02:49:29,154 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x95a3bcc> about HardwareID('modalias', 'input:b0011v0002p0007e01B1-e0,1,3,k110,111,145,14A,14D,14E,ra0,1,18,1C,2F,35,36,39,mlsfw')
2014-02-19 02:49:29,155 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x95a3bcc> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2014-02-19 02:49:29,155 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x95a3bcc> about HardwareID('modalias', 'usb:v0402p7675d0004dcEFdsc02dp01ic0Eisc02ip00')
2014-02-19 02:49:29,155 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x95a3bcc> about HardwareID('modalias', 'wmi:676AA15E-6A47-4D9F-A2CC-1E6D18D14026')
2014-02-19 02:49:29,155 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x95a3bcc> about HardwareID('modalias', 'platform:eisa')
2014-02-19 02:49:29,156 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x95a3bcc> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2014-02-19 02:49:29,156 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x95a3bcc> about HardwareID('modalias', 'pci:v00008086d000027CBsv00001025sd0000061Fbc0Csc03i00')
2014-02-19 02:49:29,156 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x95a3bcc> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,1,4,k94,95,BF,CA,CB,E3,ED,EE,F0,ram4,lsfw')
2014-02-19 02:49:29,156 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x95a3bcc> about HardwareID('modalias', 'input:b0003v0402p7675e0004-e0,1,kD4,ramlsfw')
2014-02-19 02:49:29,157 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x95a3bcc> about HardwareID('modalias', 'acpi:SYN1B20:SYN1B00:SYN0002:PNP0F13:')
2014-02-19 02:49:38,606 WARNING: modinfo for module cedarview_gfx failed: ERROR: modinfo: could not find module cedarview_gfx


2014-02-19 02:49:38,608 WARNING: /sys/module/cedarview_gfx/drivers does not exist, cannot rebind cedarview_gfx driver



```


Do I keep using old kernels? Is there something I can do to fix this? Do I have to keep rebuilding cedarview from scratch each kernel upgrade? What is the best management for a Linux system when kernel upgrades cause these issues? I am using an Acer Aspire One D270
Thanks in advance guys,

---

