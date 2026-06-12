---
title: "Additional Drivers (jockey-gtk i think) problem when installing driver"
date: 2013-04-24
forum: General Help
---

### Post by bernardosgr on 2013-04-24
Hi guys, i was trying to install a driver through the software mentioned and i was unable to do so due to some unknown error, ps help me.

Find attached a screenshot (It basically says that something went wrong and that I should check what happened in the .log file):

And here's the log on it:

```

2013-04-24 16:32:46,523 DEBUG: Updating repository indexes...
2013-04-24 16:32:46,669 DEBUG: ... fail!
2013-04-24 16:32:46,781 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x8864a4c>
2013-04-24 16:32:46,836 DEBUG: reading modalias file /lib/modules/3.5.0-23-generic/modules.alias
2013-04-24 16:32:47,107 DEBUG: reading modalias file /usr/share/jockey/modaliases/b43
2013-04-24 16:32:47,120 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2013-04-24 16:32:47,167 WARNING: _detect_handlers(): No package repositories available, skipping check
2013-04-24 16:32:47,186 WARNING: new_used_available(): No package repositories available, skipping check
2013-04-24 16:04:15,926 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x9815b8c>
2013-04-24 16:04:17,193 DEBUG: reading modalias file /lib/modules/3.5.0-23-generic/modules.alias
2013-04-24 16:04:17,547 DEBUG: reading modalias file /usr/share/jockey/modaliases/b43
2013-04-24 16:04:17,629 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2013-04-24 16:04:17,699 DEBUG: loading custom handler /usr/share/jockey/handlers/cdv.py
2013-04-24 16:04:18,297 WARNING: modinfo for module cedarview_gfx failed: ERROR: modinfo: could not find module cedarview_gfx


2013-04-24 16:04:18,298 DEBUG: Instantiated Handler subclass __builtin__.CdvDriver from name CdvDriver
2013-04-24 16:04:18,298 DEBUG: cdv.available: falling back to default
2013-04-24 16:04:18,578 DEBUG: XorgDriverHandler(cedarview_gfx, cedarview-graphics-drivers, None): Disabling as package is not compatible with Q-LTS X.org
2013-04-24 16:04:18,578 DEBUG: Intel Cedarview graphics driver not available
2013-04-24 16:04:18,578 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2013-04-24 16:04:18,588 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl


2013-04-24 16:04:18,603 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2013-04-24 16:04:18,603 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2013-04-24 16:04:18,604 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2013-04-24 16:04:18,614 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates


2013-04-24 16:04:18,616 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriverUpdate from name FglrxDriverUpdate
2013-04-24 16:04:18,616 DEBUG: fglrx.available: falling back to default
2013-04-24 16:04:18,728 DEBUG: ATI/AMD proprietary FGLRX graphics driver (post-release updates) availability undetermined, adding to pool
2013-04-24 16:04:18,730 WARNING: modinfo for module fglrx_experimental_9 failed: ERROR: modinfo: could not find module fglrx_experimental_9


2013-04-24 16:04:18,747 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriverExperimental9 from name FglrxDriverExperimental9
2013-04-24 16:04:18,747 DEBUG: fglrx.available: falling back to default
2013-04-24 16:04:18,849 DEBUG: ATI/AMD proprietary FGLRX graphics driver (**experimental** beta) availability undetermined, adding to pool
2013-04-24 16:04:18,852 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx


2013-04-24 16:04:18,855 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2013-04-24 16:04:18,855 DEBUG: fglrx.available: falling back to default
2013-04-24 16:04:18,948 DEBUG: XorgDriverHandler(fglrx, fglrx, None): Disabling as package is not compatible with Q-LTS X.org
2013-04-24 16:04:18,948 DEBUG: ATI/AMD proprietary FGLRX graphics driver not available
2013-04-24 16:04:18,949 DEBUG: loading custom handler /usr/share/jockey/handlers/pvr-omap4.py
2013-04-24 16:04:18,968 WARNING: modinfo for module omapdrm_pvr failed: ERROR: modinfo: could not find module omapdrm_pvr


2013-04-24 16:04:18,973 DEBUG: Instantiated Handler subclass __builtin__.PVROmap4Driver from name PVROmap4Driver
2013-04-24 16:04:19,089 DEBUG: XorgDriverHandler(omapdrm_pvr, pvr-omap4, None): Disabling as package is not compatible with Q-LTS X.org
2013-04-24 16:04:19,090 DEBUG: PowerVR SGX proprietary graphics driver for OMAP 4 not available
2013-04-24 16:04:19,090 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2013-04-24 16:04:19,129 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96


2013-04-24 16:04:19,132 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2013-04-24 16:04:19,148 DEBUG: Disabling Nvidia driver on intel/hybrid system
2013-04-24 16:04:19,148 DEBUG: NVIDIA accelerated graphics driver not available
2013-04-24 16:04:19,150 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current


2013-04-24 16:04:19,152 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2013-04-24 16:04:19,153 DEBUG: Disabling Nvidia driver on intel/hybrid system
2013-04-24 16:04:19,153 DEBUG: NVIDIA accelerated graphics driver not available
2013-04-24 16:04:19,155 WARNING: modinfo for module nvidia_current_updates failed: ERROR: modinfo: could not find module nvidia_current_updates


2013-04-24 16:04:19,157 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrentUpdates from name NvidiaDriverCurrentUpdates
2013-04-24 16:04:19,157 DEBUG: Disabling Nvidia driver on intel/hybrid system
2013-04-24 16:04:19,157 DEBUG: NVIDIA accelerated graphics driver (post-release updates) not available
2013-04-24 16:04:19,159 WARNING: modinfo for module nvidia_96_updates failed: ERROR: modinfo: could not find module nvidia_96_updates


2013-04-24 16:04:19,162 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96Updates from name NvidiaDriver96Updates
2013-04-24 16:04:19,162 DEBUG: Disabling Nvidia driver on intel/hybrid system
2013-04-24 16:04:19,162 DEBUG: NVIDIA accelerated graphics driver (post-release updates) not available
2013-04-24 16:04:19,164 WARNING: modinfo for module nvidia_173_updates failed: ERROR: modinfo: could not find module nvidia_173_updates


2013-04-24 16:04:19,167 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173Updates from name NvidiaDriver173Updates
2013-04-24 16:04:19,168 DEBUG: Disabling Nvidia driver on intel/hybrid system
2013-04-24 16:04:19,168 DEBUG: NVIDIA accelerated graphics driver (post-release updates) not available
2013-04-24 16:04:19,169 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173


2013-04-24 16:04:19,172 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2013-04-24 16:04:19,172 DEBUG: Disabling Nvidia driver on intel/hybrid system
2013-04-24 16:04:19,172 DEBUG: NVIDIA accelerated graphics driver not available
2013-04-24 16:04:19,174 WARNING: modinfo for module nvidia_experimental_310 failed: ERROR: modinfo: could not find module nvidia_experimental_310


2013-04-24 16:04:19,194 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverExperimental310 from name NvidiaDriverExperimental310
2013-04-24 16:04:19,195 DEBUG: Disabling Nvidia driver on intel/hybrid system
2013-04-24 16:04:19,196 DEBUG: NVIDIA accelerated graphics driver (**experimental** beta) not available
2013-04-24 16:04:19,199 WARNING: modinfo for module nvidia_experimental_304 failed: ERROR: modinfo: could not find module nvidia_experimental_304


2013-04-24 16:04:19,216 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverExperimental304 from name NvidiaDriverExperimental304
2013-04-24 16:04:19,217 DEBUG: Disabling Nvidia driver on intel/hybrid system
2013-04-24 16:04:19,217 DEBUG: NVIDIA accelerated graphics driver (**experimental** beta) not available
2013-04-24 16:04:19,217 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2013-04-24 16:04:19,249 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2013-04-24 16:04:19,655 DEBUG: Software modem not available
2013-04-24 16:04:19,655 DEBUG: loading custom handler /usr/share/jockey/handlers/vmware-client.py
2013-04-24 16:04:19,668 WARNING: modinfo for module vmxnet failed: ERROR: modinfo: could not find module vmxnet


2013-04-24 16:04:19,668 DEBUG: Instantiated Handler subclass __builtin__.VmwareClientHandler from name VmwareClientHandler
2013-04-24 16:04:19,682 DEBUG: VMWare Client Tools availability undetermined, adding to pool
2013-04-24 16:04:19,683 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2013-04-24 16:04:19,773 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2013-04-24 16:04:19,774 DEBUG: Firmware for DVB cards not available
2013-04-24 16:04:19,774 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2013-04-24 16:04:20,004 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci


2013-04-24 16:04:20,005 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2013-04-24 16:04:20,005 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2013-04-24 16:04:20,005 DEBUG: all custom handlers loaded
2013-04-24 16:04:20,005 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9815b8c> about HardwareID('modalias', 'pci:v00008086d00001E2Dsv0000144Dsd0000C0D8bc0Csc03i20')
2013-04-24 16:04:20,191 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9815b8c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2013-04-24 16:04:20,194 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-04-24 16:04:20,297 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-04-24 16:04:20,297 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9815b8c> about HardwareID('modalias', 'acpi:PNP0B00:')
2013-04-24 16:04:20,297 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9815b8c> about HardwareID('modalias', 'pci:v00008086d00000166sv0000144Dsd0000C0D8bc03sc00i00')
2013-04-24 16:04:20,300 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'i915'}
2013-04-24 16:04:20,300 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i915', 'jockey_handler': 'KernelModuleHandler'}
2013-04-24 16:04:20,300 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9815b8c> about HardwareID('modalias', 'pci:v00001002d00006840sv0000144Dsd0000C0D8bc03sc00i00')
2013-04-24 16:04:20,507 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'radeon'}
2013-04-24 16:04:20,507 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'radeon', 'jockey_handler': 'KernelModuleHandler'}
2013-04-24 16:04:20,507 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx_experimental_12', 'package': 'fglrx-experimental-12'}
2013-04-24 16:04:20,511 WARNING: modinfo for module fglrx_experimental_12 failed: ERROR: modinfo: could not find module fglrx_experimental_12


2013-04-24 16:04:20,528 WARNING: modinfo for module fglrx_experimental_12 failed: ERROR: modinfo: could not find module fglrx_experimental_12


2013-04-24 16:04:20,528 DEBUG: got handler kmod:fglrx_experimental_12([KernelModuleHandler, nonfree, disabled] Experimental AMD binary Xorg driver and kernel module)
2013-04-24 16:04:20,528 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx_experimental_9', 'package': 'fglrx-experimental-9'}
2013-04-24 16:04:20,572 DEBUG: fglrx.enabled(fglrx_experimental_9): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2013-04-24 16:04:20,572 DEBUG: fglrx_experimental_9 is not the alternative in use
2013-04-24 16:04:20,529 DEBUG: found match in handler pool xorg:fglrx_experimental_9([FglrxDriverExperimental9, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (**experimental** beta))
2013-04-24 16:04:20,573 WARNING: modinfo for module fglrx_experimental_9 failed: ERROR: modinfo: could not find module fglrx_experimental_9


2013-04-24 16:04:20,575 DEBUG: fglrx.available: falling back to default
2013-04-24 16:04:20,668 DEBUG: fglrx.enabled(fglrx_experimental_9): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2013-04-24 16:04:20,668 DEBUG: fglrx_experimental_9 is not the alternative in use
2013-04-24 16:04:20,657 DEBUG: got handler xorg:fglrx_experimental_9([FglrxDriverExperimental9, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (**experimental** beta))
2013-04-24 16:04:20,668 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx_updates', 'package': 'fglrx-updates'}
2013-04-24 16:04:20,676 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2013-04-24 16:04:20,676 DEBUG: fglrx_updates is not the alternative in use
2013-04-24 16:04:20,668 DEBUG: found match in handler pool xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2013-04-24 16:04:20,678 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates


2013-04-24 16:04:20,680 DEBUG: fglrx.available: falling back to default
2013-04-24 16:04:20,776 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2013-04-24 16:04:20,776 DEBUG: fglrx_updates is not the alternative in use
2013-04-24 16:04:20,768 DEBUG: got handler xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2013-04-24 16:04:20,776 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx', 'package': 'fglrx'}
2013-04-24 16:04:20,787 DEBUG: fglrx.enabled(fglrx): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2013-04-24 16:04:20,787 DEBUG: fglrx is not the alternative in use
2013-04-24 16:04:20,776 DEBUG: found match in handler pool xorg:fglrx([FglrxDriver, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver)
2013-04-24 16:04:20,789 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx


2013-04-24 16:04:20,792 DEBUG: fglrx.available: falling back to default
2013-04-24 16:04:20,889 DEBUG: XorgDriverHandler(fglrx, fglrx, None): Disabling as package is not compatible with Q-LTS X.org
2013-04-24 16:04:20,900 DEBUG: fglrx.enabled(fglrx): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2013-04-24 16:04:20,900 DEBUG: fglrx is not the alternative in use
2013-04-24 16:04:20,889 DEBUG: ignoring unavailable handler xorg:fglrx([FglrxDriver, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver)
2013-04-24 16:04:20,900 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9815b8c> about HardwareID('modalias', 'platform:pcspkr')
2013-04-24 16:04:20,901 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr'}
2013-04-24 16:04:20,901 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2013-04-24 16:04:20,901 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp'}
2013-04-24 16:04:20,901 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2013-04-24 16:04:20,901 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9815b8c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2013-04-24 16:04:20,901 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-04-24 16:04:20,901 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-04-24 16:04:20,901 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9815b8c> about HardwareID('modalias', 'usb:v1D6Bp0002d0305dc09dsc00dp01ic09isc00ip00')
2013-04-24 16:04:20,909 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9815b8c> about HardwareID('modalias', 'usb:v0C45pC35Ad0300dcEFdsc02dp01ic0Eisc02ip00')
2013-04-24 16:04:20,927 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9815b8c> about HardwareID('modalias', 'input:b0003v045Ep0745e0111-e0,1,2,3,4,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,8B,8C,8E,8F,90,94,96,98,9B,9C,9E,9F,A1,A3,A4,A5,A6,A7,A8,A9,AB,AC,AD,AE,B0,B1,B2,B3,B4,B5,B6,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,CE,CF,D0,D1,D2,D4,D8,D9,DB,DF,E4,E7,E8,E9,EA,EB,F0,F1,100,13A,13B,161,162,164,166,16A,16E,172,174,176,178,179,17A,17B,17C,17D,17F,180,182,183,185,188,189,18C,18D,18E,18F,190,191,192,193,195,198,199,19A,1A0,1A1,1A2,1A3,1A4,1A5,1A6,1A7,1A8,1A9,1AA,1AB,1AC,1AD,1AE,1B0,1B1,1B6,1B7,1BA,r6,a0,1,2,3,4,5,6,7,8,10,11,12,20,28,29,2A,2B,2C,2D,2E,2F,30,31,32,33,34,35,36,37,38,39,3A,3B,3C,3D,3E,m4,lsfw')
2013-04-24 16:04:20,928 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-04-24 16:04:20,928 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-04-24 16:04:20,928 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2013-04-24 16:04:20,928 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2013-04-24 16:04:20,928 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2013-04-24 16:04:20,928 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2013-04-24 16:04:20,928 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2013-04-24 16:04:20,928 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2013-04-24 16:04:20,928 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-04-24 16:04:20,928 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-04-24 16:04:20,928 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9815b8c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2013-04-24 16:04:20,928 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9815b8c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2013-04-24 16:04:20,929 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9815b8c> about HardwareID('modalias', 'usb:v8087p0024d0000dc09dsc00dp01ic09isc00ip00')
2013-04-24 16:04:20,929 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9815b8c> about HardwareID('modalias', 'acpi:PNP0100:')
2013-04-24 16:04:20,929 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9815b8c> about HardwareID('modalias', 'input:b0011v0002p0007e01B1-e0,1,3,k110,111,145,14A,14D,14E,ra0,1,18,1C,2F,35,36,39,mlsfw')
2013-04-24 16:04:20,929 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-04-24 16:04:20,929 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-04-24 16:04:20,929 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2013-04-24 16:04:20,929 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2013-04-24 16:04:20,929 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2013-04-24 16:04:20,929 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2013-04-24 16:04:20,929 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2013-04-24 16:04:20,929 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2013-04-24 16:04:20,929 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-04-24 16:04:20,929 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-04-24 16:04:20,929 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9815b8c> about HardwareID('modalias', 'wmi:C16C47BA-50E3-444A-AF3A-B1C348380000')
2013-04-24 16:04:20,929 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9815b8c> about HardwareID('modalias', 'pci:v00008086d00001E3Asv0000144Dsd0000C0D8bc07sc80i00')
2013-04-24 16:04:20,932 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mei'}
2013-04-24 16:04:20,932 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mei', 'jockey_handler': 'KernelModuleHandler'}
2013-04-24 16:04:20,932 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9815b8c> about HardwareID('modalias', 'wmi:C16C47BA-50E3-444A-AF3A-B1C348380001')
2013-04-24 16:04:20,932 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9815b8c> about HardwareID('modalias', 'usb:v0CF3p3004d0002dcE0dsc01dp01icE0isc01ip01')
2013-04-24 16:04:20,936 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'ath3k'}
2013-04-24 16:04:20,936 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ath3k', 'jockey_handler': 'KernelModuleHandler'}
2013-04-24 16:04:20,936 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'btusb'}
2013-04-24 16:04:20,936 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'btusb', 'jockey_handler': 'KernelModuleHandler'}
2013-04-24 16:04:20,936 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9815b8c> about HardwareID('modalias', 'pci:v00008086d00001E03sv0000144Dsd0000C0D8bc01sc06i01')
2013-04-24 16:04:20,938 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9815b8c> about HardwareID('modalias', 'pci:v00008086d00001E22sv0000144Dsd0000C0D8bc0Csc05i00')
2013-04-24 16:04:20,940 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801'}
2013-04-24 16:04:20,940 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801', 'jockey_handler': 'KernelModuleHandler'}
2013-04-24 16:04:20,940 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9815b8c> about HardwareID('modalias', 'pci:v00008086d00001E31sv0000144Dsd0000C0D8bc0Csc03i30')
2013-04-24 16:04:20,942 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9815b8c> about HardwareID('modalias', 'acpi:PNP0303:PNP030B:')
2013-04-24 16:04:20,942 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9815b8c> about HardwareID('modalias', 'acpi:PNP0C04:')
2013-04-24 16:04:20,942 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9815b8c> about HardwareID('modalias', 'acpi:PNP0C02:')
2013-04-24 16:04:20,942 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9815b8c> about HardwareID('modalias', 'pci:v00008086d00001E26sv0000144Dsd0000C0D8bc0Csc03i20')
2013-04-24 16:04:20,944 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9815b8c> about HardwareID('modalias', 'usb:v1E3Dp2093d0100dc00dsc00dp00ic08isc06ip50')
2013-04-24 16:04:20,944 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'uas'}
2013-04-24 16:04:20,944 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uas', 'jockey_handler': 'KernelModuleHandler'}
2013-04-24 16:04:20,944 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9815b8c> about HardwareID('modalias', 'acpi:INT3F0D:PNP0C02:')
2013-04-24 16:04:20,944 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9815b8c> about HardwareID('modalias', 'platform:microcode')
2013-04-24 16:04:20,945 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9815b8c> about HardwareID('modalias', 'input:b0003v045Ep0745e0111-e0,1,2,3,4,k71,72,73,74,77,80,82,83,85,86,87,88,89,8A,8B,8C,8E,90,96,98,9B,9C,9E,9F,A1,A3,A4,A5,A6,A7,A8,A9,AB,AC,AD,AE,B0,B1,B2,B5,B6,CE,CF,D0,D1,D2,D4,D8,D9,DB,DF,E4,E7,E8,E9,EA,EB,F1,100,110,111,112,113,114,161,162,166,16A,16E,172,174,176,178,179,17A,17B,17C,17D,17F,180,182,183,185,188,189,18C,18D,18E,18F,190,191,192,193,195,198,199,19A,1A0,1A1,1A2,1A3,1A4,1A5,1A6,1A7,1A8,1A9,1AA,1AB,1AC,1AD,1AE,1B0,1B1,1B7,1BA,r0,1,6,7,8,9,a20,m4,lsfw')
2013-04-24 16:04:20,945 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-04-24 16:04:20,945 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-04-24 16:04:20,945 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2013-04-24 16:04:20,945 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2013-04-24 16:04:20,945 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-04-24 16:04:20,945 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-04-24 16:04:20,945 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9815b8c> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8E,8F,94,95,96,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,C0,C1,CA,D9,E0,E1,E2,E3,EC,EE,ram4,l0,1,2,sfw')
2013-04-24 16:04:20,945 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-04-24 16:04:20,945 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-04-24 16:04:20,945 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-04-24 16:04:20,945 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-04-24 16:04:20,945 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9815b8c> about HardwareID('modalias', 'usb:v1D6Bp0003d0305dc09dsc00dp03ic09isc00ip00')
2013-04-24 16:04:20,946 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9815b8c> about HardwareID('modalias', 'input:b0003v0C45pC35Ae0300-e0,1,kD4,ramlsfw')
2013-04-24 16:04:20,946 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-04-24 16:04:20,946 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-04-24 16:04:20,946 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-04-24 16:04:20,946 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-04-24 16:04:20,946 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9815b8c> about HardwareID('modalias', 'acpi:PNP0F03:PNP0F13:')
2013-04-24 16:04:20,946 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9815b8c> about HardwareID('modalias', 'dmi:bvnAmericanMegatrendsInc.:bvrP03ABE:bd09/20/2012:svnSAMSUNGELECTRONICSCO.,LTD.:pn350V5C/350V5X/350V4C/350V4X/351V5C/351V5X/351V4C/351V4X/3540VC/3540VX/3440VC/3440VX:pvrP03ABE.006.CP:rvnSAMSUNGELECTRONICSCO.,LTD.:rnNP350V5C-S04PT:rvrBOARDREVISION00:cvnSAMSUNGELECTRONICSCO.,LTD.:ct9:cvr0.1:')
2013-04-24 16:04:20,953 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9815b8c> about HardwareID('modalias', 'pci:v000010ECd00008168sv0000144Dsd0000C0D8bc02sc00i00')
2013-04-24 16:04:20,958 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'r8169'}
2013-04-24 16:04:20,958 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'r8169', 'jockey_handler': 'KernelModuleHandler'}
2013-04-24 16:04:20,958 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9815b8c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,8,')
2013-04-24 16:04:20,958 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-04-24 16:04:20,959 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-04-24 16:04:20,959 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9815b8c> about HardwareID('modalias', 'usb:v045Ep0745d0634dc00dsc00dp00ic03isc00ip00')
2013-04-24 16:04:20,990 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2013-04-24 16:04:20,990 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2013-04-24 16:04:20,990 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9815b8c> about HardwareID('modalias', 'usb:v045Ep0745d0634dc00dsc00dp00ic03isc01ip02')
2013-04-24 16:04:20,990 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2013-04-24 16:04:20,990 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2013-04-24 16:04:20,990 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse'}
2013-04-24 16:04:20,990 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse', 'jockey_handler': 'KernelModuleHandler'}
2013-04-24 16:04:20,990 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9815b8c> about HardwareID('modalias', 'pci:v00008086d00001E59sv0000144Dsd0000C0D8bc06sc01i00')
2013-04-24 16:04:20,992 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'lpc_ich'}
2013-04-24 16:04:20,992 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'lpc_ich', 'jockey_handler': 'KernelModuleHandler'}
2013-04-24 16:04:20,992 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9815b8c> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2013-04-24 16:04:20,993 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-04-24 16:04:20,993 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-04-24 16:04:20,993 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9815b8c> about HardwareID('modalias', 'pci:v0000168Cd00000032sv0000144Dsd00004105bc02sc80i00')
2013-04-24 16:04:20,999 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'ath9k'}
2013-04-24 16:04:20,999 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ath9k', 'jockey_handler': 'KernelModuleHandler'}
2013-04-24 16:04:20,999 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9815b8c> about HardwareID('modalias', 'acpi:PNP0C01:')
2013-04-24 16:04:20,999 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9815b8c> about HardwareID('modalias', 'usb:v1D6Bp0002d0305dc09dsc00dp00ic09isc00ip00')
2013-04-24 16:04:20,999 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9815b8c> about HardwareID('modalias', 'pci:v00008086d00001E20sv0000144Dsd0000C0D8bc04sc03i00')
2013-04-24 16:04:21,001 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2013-04-24 16:04:21,001 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2013-04-24 16:04:21,001 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2013-04-24 16:04:21,001 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2013-04-24 16:04:21,001 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9815b8c> about HardwareID('modalias', 'acpi:PNP0200:')
2013-04-24 16:04:21,001 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9815b8c> about HardwareID('modalias', 'acpi:INT0800:')
2013-04-24 16:04:21,001 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9815b8c> about HardwareID('modalias', 'platform:eisa')
2013-04-24 16:04:21,001 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9815b8c> about HardwareID('modalias', 'pci:v00008086d00000154sv0000144Dsd0000C0D8bc06sc00i00')
2013-04-24 16:04:21,003 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9815b8c> about HardwareID('modalias', 'hid:b0003g0001v0000045Ep00000745')
2013-04-24 16:04:21,030 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'hid_generic'}
2013-04-24 16:04:21,030 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'hid_generic', 'jockey_handler': 'KernelModuleHandler'}
2013-04-24 16:04:21,030 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9815b8c> about HardwareID('modalias', 'usb:v045Ep0745d0634dc00dsc00dp00ic03isc01ip01')
2013-04-24 16:04:21,031 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2013-04-24 16:04:21,031 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2013-04-24 16:04:21,031 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd'}
2013-04-24 16:04:21,031 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd', 'jockey_handler': 'KernelModuleHandler'}
2013-04-24 16:04:21,031 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9815b8c> about HardwareID('modalias', 'acpi:PNP0000:')
2013-04-24 16:04:21,031 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9815b8c> about HardwareID('modalias', 'platform:samsung')
2013-04-24 16:04:21,031 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9815b8c> about HardwareID('modalias', 'platform:regulatory')
2013-04-24 16:04:21,032 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9815b8c> about HardwareID('modalias', 'x86cpu:vendor:0000:family:0006:model:003A:feature:,0000,0001,0002,0003,0004,0005,0006,0007,0008,0009,000B,000C,000D,000E,000F,0010,0011,0013,0015,0016,0017,0018,0019,001A,001B,001C,001D,001F,0034,003B,003D,0066,0068,006B,006C,006D,0072,0076,0078,007C,0080,0081,0082,0083,0084,0085,0087,0088,0089,008D,008E,008F,0091,0093,0094,0095,0097,0098,0099,009A,009B,009C,009D,009E,00C0,00E0,00E1,00E3,00E4,00E5,00E6,00E7,0100,0101,0102,0103,0104,0120,0127,0129')
2013-04-24 16:04:21,035 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'aesni_intel'}
2013-04-24 16:04:21,035 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'aesni_intel', 'jockey_handler': 'KernelModuleHandler'}
2013-04-24 16:04:21,035 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'kvm_intel'}
2013-04-24 16:04:21,035 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'kvm_intel', 'jockey_handler': 'KernelModuleHandler'}
2013-04-24 16:04:21,035 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'microcode'}
2013-04-24 16:04:21,035 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'microcode', 'jockey_handler': 'KernelModuleHandler'}
2013-04-24 16:04:21,035 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'coretemp'}
2013-04-24 16:04:21,036 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'coretemp', 'jockey_handler': 'KernelModuleHandler'}
2013-04-24 16:04:21,036 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9815b8c> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2013-04-24 16:04:21,040 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw'}
2013-04-24 16:04:21,040 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2013-04-24 16:04:21,040 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'psmouse'}
2013-04-24 16:04:21,040 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2013-04-24 16:04:21,040 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9815b8c> about HardwareID('modalias', 'usb:v0C45pC35Ad0300dcEFdsc02dp01ic0Eisc01ip00')
2013-04-24 16:04:21,041 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo'}
2013-04-24 16:04:21,041 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo', 'jockey_handler': 'KernelModuleHandler'}
2013-04-24 16:04:21,041 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9815b8c> about HardwareID('modalias', 'platform:coretemp')
2013-04-24 16:04:21,041 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9815b8c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2013-04-24 16:04:21,041 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-04-24 16:04:21,041 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-04-24 16:04:21,041 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-04-24 16:04:21,041 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-04-24 16:04:21,041 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9815b8c> about HardwareID('modalias', 'acpi:PNP0103:')
2013-04-24 16:04:21,041 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9815b8c> about HardwareID('modalias', 'input:b0003v045Ep0745e0111-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,sfw')
2013-04-24 16:04:21,042 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-04-24 16:04:21,042 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-04-24 16:04:21,042 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-04-24 16:04:21,042 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-04-24 16:04:21,042 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9815b8c> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2013-04-24 16:04:21,042 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-04-24 16:04:21,042 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-04-24 16:04:21,042 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-04-24 16:04:21,042 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-04-24 16:04:21,042 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9815b8c> about HardwareID('modalias', 'acpi:INT340E:PNP0C02:')
2013-04-24 16:04:21,042 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x981deac> about HardwareID('modalias', 'pci:v00008086d00001E2Dsv0000144Dsd0000C0D8bc0Csc03i20')
2013-04-24 16:04:21,042 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x981deac> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2013-04-24 16:04:21,042 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x981deac> about HardwareID('modalias', 'acpi:PNP0B00:')
2013-04-24 16:04:21,042 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x981deac> about HardwareID('modalias', 'pci:v00008086d00000166sv0000144Dsd0000C0D8bc03sc00i00')
2013-04-24 16:04:21,042 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x981deac> about HardwareID('modalias', 'pci:v00001002d00006840sv0000144Dsd0000C0D8bc03sc00i00')
2013-04-24 16:04:21,042 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x981deac> about HardwareID('modalias', 'platform:pcspkr')
2013-04-24 16:04:21,042 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x981deac> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2013-04-24 16:04:21,042 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x981deac> about HardwareID('modalias', 'usb:v1D6Bp0002d0305dc09dsc00dp01ic09isc00ip00')
2013-04-24 16:04:21,042 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x981deac> about HardwareID('modalias', 'usb:v0C45pC35Ad0300dcEFdsc02dp01ic0Eisc02ip00')
2013-04-24 16:04:21,042 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x981deac> about HardwareID('modalias', 'input:b0003v045Ep0745e0111-e0,1,2,3,4,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,8B,8C,8E,8F,90,94,96,98,9B,9C,9E,9F,A1,A3,A4,A5,A6,A7,A8,A9,AB,AC,AD,AE,B0,B1,B2,B3,B4,B5,B6,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,CE,CF,D0,D1,D2,D4,D8,D9,DB,DF,E4,E7,E8,E9,EA,EB,F0,F1,100,13A,13B,161,162,164,166,16A,16E,172,174,176,178,179,17A,17B,17C,17D,17F,180,182,183,185,188,189,18C,18D,18E,18F,190,191,192,193,195,198,199,19A,1A0,1A1,1A2,1A3,1A4,1A5,1A6,1A7,1A8,1A9,1AA,1AB,1AC,1AD,1AE,1B0,1B1,1B6,1B7,1BA,r6,a0,1,2,3,4,5,6,7,8,10,11,12,20,28,29,2A,2B,2C,2D,2E,2F,30,31,32,33,34,35,36,37,38,39,3A,3B,3C,3D,3E,m4,lsfw')
2013-04-24 16:04:21,042 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x981deac> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2013-04-24 16:04:21,043 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x981deac> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2013-04-24 16:04:21,043 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x981deac> about HardwareID('modalias', 'usb:v8087p0024d0000dc09dsc00dp01ic09isc00ip00')
2013-04-24 16:04:21,043 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x981deac> about HardwareID('modalias', 'acpi:PNP0100:')
2013-04-24 16:04:21,043 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x981deac> about HardwareID('modalias', 'input:b0011v0002p0007e01B1-e0,1,3,k110,111,145,14A,14D,14E,ra0,1,18,1C,2F,35,36,39,mlsfw')
2013-04-24 16:04:21,043 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x981deac> about HardwareID('modalias', 'wmi:C16C47BA-50E3-444A-AF3A-B1C348380000')
2013-04-24 16:04:21,043 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x981deac> about HardwareID('modalias', 'pci:v00008086d00001E3Asv0000144Dsd0000C0D8bc07sc80i00')
2013-04-24 16:04:21,043 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x981deac> about HardwareID('modalias', 'wmi:C16C47BA-50E3-444A-AF3A-B1C348380001')
2013-04-24 16:04:21,043 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x981deac> about HardwareID('modalias', 'usb:v0CF3p3004d0002dcE0dsc01dp01icE0isc01ip01')
2013-04-24 16:04:21,043 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x981deac> about HardwareID('modalias', 'pci:v00008086d00001E03sv0000144Dsd0000C0D8bc01sc06i01')
2013-04-24 16:04:21,043 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x981deac> about HardwareID('modalias', 'pci:v00008086d00001E22sv0000144Dsd0000C0D8bc0Csc05i00')
2013-04-24 16:04:21,043 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x981deac> about HardwareID('modalias', 'pci:v00008086d00001E31sv0000144Dsd0000C0D8bc0Csc03i30')
2013-04-24 16:04:21,043 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x981deac> about HardwareID('modalias', 'acpi:PNP0303:PNP030B:')
2013-04-24 16:04:21,043 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x981deac> about HardwareID('modalias', 'acpi:PNP0C04:')
2013-04-24 16:04:21,043 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x981deac> about HardwareID('modalias', 'acpi:PNP0C02:')
2013-04-24 16:04:21,043 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x981deac> about HardwareID('modalias', 'pci:v00008086d00001E26sv0000144Dsd0000C0D8bc0Csc03i20')
2013-04-24 16:04:21,043 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x981deac> about HardwareID('modalias', 'usb:v1E3Dp2093d0100dc00dsc00dp00ic08isc06ip50')
2013-04-24 16:04:21,043 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x981deac> about HardwareID('modalias', 'acpi:INT3F0D:PNP0C02:')
2013-04-24 16:04:21,043 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x981deac> about HardwareID('modalias', 'platform:microcode')
2013-04-24 16:04:21,043 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x981deac> about HardwareID('modalias', 'input:b0003v045Ep0745e0111-e0,1,2,3,4,k71,72,73,74,77,80,82,83,85,86,87,88,89,8A,8B,8C,8E,90,96,98,9B,9C,9E,9F,A1,A3,A4,A5,A6,A7,A8,A9,AB,AC,AD,AE,B0,B1,B2,B5,B6,CE,CF,D0,D1,D2,D4,D8,D9,DB,DF,E4,E7,E8,E9,EA,EB,F1,100,110,111,112,113,114,161,162,166,16A,16E,172,174,176,178,179,17A,17B,17C,17D,17F,180,182,183,185,188,189,18C,18D,18E,18F,190,191,192,193,195,198,199,19A,1A0,1A1,1A2,1A3,1A4,1A5,1A6,1A7,1A8,1A9,1AA,1AB,1AC,1AD,1AE,1B0,1B1,1B7,1BA,r0,1,6,7,8,9,a20,m4,lsfw')
2013-04-24 16:04:21,043 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x981deac> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8E,8F,94,95,96,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,C0,C1,CA,D9,E0,E1,E2,E3,EC,EE,ram4,l0,1,2,sfw')
2013-04-24 16:04:21,043 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x981deac> about HardwareID('modalias', 'usb:v1D6Bp0003d0305dc09dsc00dp03ic09isc00ip00')
2013-04-24 16:04:21,043 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x981deac> about HardwareID('modalias', 'input:b0003v0C45pC35Ae0300-e0,1,kD4,ramlsfw')
2013-04-24 16:04:21,043 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x981deac> about HardwareID('modalias', 'acpi:PNP0F03:PNP0F13:')
2013-04-24 16:04:21,043 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x981deac> about HardwareID('modalias', 'dmi:bvnAmericanMegatrendsInc.:bvrP03ABE:bd09/20/2012:svnSAMSUNGELECTRONICSCO.,LTD.:pn350V5C/350V5X/350V4C/350V4X/351V5C/351V5X/351V4C/351V4X/3540VC/3540VX/3440VC/3440VX:pvrP03ABE.006.CP:rvnSAMSUNGELECTRONICSCO.,LTD.:rnNP350V5C-S04PT:rvrBOARDREVISION00:cvnSAMSUNGELECTRONICSCO.,LTD.:ct9:cvr0.1:')
2013-04-24 16:04:21,043 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x981deac> about HardwareID('modalias', 'pci:v000010ECd00008168sv0000144Dsd0000C0D8bc02sc00i00')
2013-04-24 16:04:21,043 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x981deac> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,8,')
2013-04-24 16:04:21,043 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x981deac> about HardwareID('modalias', 'usb:v045Ep0745d0634dc00dsc00dp00ic03isc00ip00')
2013-04-24 16:04:21,044 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x981deac> about HardwareID('modalias', 'usb:v045Ep0745d0634dc00dsc00dp00ic03isc01ip02')
2013-04-24 16:04:21,044 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x981deac> about HardwareID('modalias', 'pci:v00008086d00001E59sv0000144Dsd0000C0D8bc06sc01i00')
2013-04-24 16:04:21,044 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x981deac> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2013-04-24 16:04:21,044 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x981deac> about HardwareID('modalias', 'pci:v0000168Cd00000032sv0000144Dsd00004105bc02sc80i00')
2013-04-24 16:04:21,044 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x981deac> about HardwareID('modalias', 'acpi:PNP0C01:')
2013-04-24 16:04:21,044 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x981deac> about HardwareID('modalias', 'usb:v1D6Bp0002d0305dc09dsc00dp00ic09isc00ip00')
2013-04-24 16:04:21,044 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x981deac> about HardwareID('modalias', 'pci:v00008086d00001E20sv0000144Dsd0000C0D8bc04sc03i00')
2013-04-24 16:04:21,044 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x981deac> about HardwareID('modalias', 'acpi:PNP0200:')
2013-04-24 16:04:21,044 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x981deac> about HardwareID('modalias', 'acpi:INT0800:')
2013-04-24 16:04:21,044 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x981deac> about HardwareID('modalias', 'platform:eisa')
2013-04-24 16:04:21,044 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x981deac> about HardwareID('modalias', 'pci:v00008086d00000154sv0000144Dsd0000C0D8bc06sc00i00')
2013-04-24 16:04:21,044 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x981deac> about HardwareID('modalias', 'hid:b0003g0001v0000045Ep00000745')
2013-04-24 16:04:21,044 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x981deac> about HardwareID('modalias', 'usb:v045Ep0745d0634dc00dsc00dp00ic03isc01ip01')
2013-04-24 16:04:21,044 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x981deac> about HardwareID('modalias', 'acpi:PNP0000:')
2013-04-24 16:04:21,044 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x981deac> about HardwareID('modalias', 'platform:samsung')
2013-04-24 16:04:21,044 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x981deac> about HardwareID('modalias', 'platform:regulatory')
2013-04-24 16:04:21,044 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x981deac> about HardwareID('modalias', 'x86cpu:vendor:0000:family:0006:model:003A:feature:,0000,0001,0002,0003,0004,0005,0006,0007,0008,0009,000B,000C,000D,000E,000F,0010,0011,0013,0015,0016,0017,0018,0019,001A,001B,001C,001D,001F,0034,003B,003D,0066,0068,006B,006C,006D,0072,0076,0078,007C,0080,0081,0082,0083,0084,0085,0087,0088,0089,008D,008E,008F,0091,0093,0094,0095,0097,0098,0099,009A,009B,009C,009D,009E,00C0,00E0,00E1,00E3,00E4,00E5,00E6,00E7,0100,0101,0102,0103,0104,0120,0127,0129')
2013-04-24 16:04:21,044 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x981deac> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2013-04-24 16:04:21,044 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x981deac> about HardwareID('modalias', 'usb:v0C45pC35Ad0300dcEFdsc02dp01ic0Eisc01ip00')
2013-04-24 16:04:21,044 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x981deac> about HardwareID('modalias', 'platform:coretemp')
2013-04-24 16:04:21,044 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x981deac> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2013-04-24 16:04:21,044 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x981deac> about HardwareID('modalias', 'acpi:PNP0103:')
2013-04-24 16:04:21,044 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x981deac> about HardwareID('modalias', 'input:b0003v045Ep0745e0111-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,sfw')
2013-04-24 16:04:21,044 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x981deac> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2013-04-24 16:04:21,044 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x981deac> about HardwareID('modalias', 'acpi:INT340E:PNP0C02:')
2013-04-24 16:04:21,234 DEBUG: fglrx.enabled(fglrx_experimental_9): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2013-04-24 16:04:21,234 DEBUG: fglrx_experimental_9 is not the alternative in use
2013-04-24 16:04:21,255 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2013-04-24 16:04:21,256 DEBUG: fglrx_updates is not the alternative in use
2013-04-24 16:04:21,294 DEBUG: fglrx.enabled(fglrx_experimental_9): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2013-04-24 16:04:21,294 DEBUG: fglrx_experimental_9 is not the alternative in use
2013-04-24 16:04:21,307 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2013-04-24 16:04:21,307 DEBUG: fglrx_updates is not the alternative in use
2013-04-24 16:04:52,922 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2013-04-24 16:04:52,923 DEBUG: fglrx_updates is not the alternative in use
2013-04-24 16:04:57,792 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2013-04-24 16:04:57,792 DEBUG: fglrx_updates is not the alternative in use
2013-04-24 16:05:04,495 DEBUG: Installing package: linux-headers-generic
2013-04-24 16:05:06,245 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 0.000000
2013-04-24 16:05:06,245 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 0.000000
2013-04-24 16:05:06,607 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 0.000000
2013-04-24 16:05:07,108 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 0.000000
2013-04-24 16:05:07,609 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 0.000000
2013-04-24 16:05:08,110 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 0.000000
2013-04-24 16:05:08,611 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 0.000000
2013-04-24 16:05:09,112 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 0.000000
2013-04-24 16:05:09,613 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 0.000000
2013-04-24 16:05:10,115 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 0.000000
2013-04-24 16:05:10,616 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 0.000000
2013-04-24 16:05:11,117 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 0.000000
2013-04-24 16:05:11,618 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 0.000000
2013-04-24 16:05:12,119 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 0.000000
2013-04-24 16:05:12,620 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 0.000000
2013-04-24 16:05:13,121 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 0.000000
2013-04-24 16:05:13,622 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 0.000000
2013-04-24 16:05:14,123 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 0.000000
2013-04-24 16:05:14,624 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 0.000000
2013-04-24 16:05:15,126 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 0.000000
2013-04-24 16:05:15,627 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 0.000000
2013-04-24 16:05:16,128 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 0.000000
2013-04-24 16:05:16,629 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 0.000000
2013-04-24 16:05:17,130 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 0.000000
2013-04-24 16:05:17,631 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 0.000000
2013-04-24 16:05:18,132 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 0.000000
2013-04-24 16:05:18,633 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 0.000000
2013-04-24 16:05:19,134 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 0.000000
2013-04-24 16:05:19,635 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 0.000000
2013-04-24 16:05:20,137 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 0.000000
2013-04-24 16:05:20,638 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 0.000000
2013-04-24 16:05:21,139 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 0.000000
2013-04-24 16:05:21,640 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 0.000000
2013-04-24 16:05:21,660 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 0.000000
2013-04-24 16:05:22,162 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 0.000000
2013-04-24 16:05:22,663 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 0.000000
2013-04-24 16:05:23,163 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 0.000000
2013-04-24 16:05:23,665 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 0.000000
2013-04-24 16:05:24,166 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 0.000000
2013-04-24 16:05:24,666 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 0.000000
2013-04-24 16:05:25,167 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 0.000000
2013-04-24 16:05:25,668 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 0.000000
2013-04-24 16:05:26,169 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 0.000000
2013-04-24 16:05:26,670 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 0.000000
2013-04-24 16:05:27,171 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 0.000000
2013-04-24 16:05:27,672 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 0.000000
2013-04-24 16:05:28,173 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 0.000000
2013-04-24 16:05:28,674 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 0.000000
2013-04-24 16:05:29,175 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 0.000000
2013-04-24 16:05:29,675 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 0.000000
2013-04-24 16:05:30,176 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 0.000000
2013-04-24 16:05:30,677 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 0.000000
2013-04-24 16:05:31,178 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 0.000000
2013-04-24 16:05:31,679 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 0.000000
2013-04-24 16:05:32,180 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 0.000000
2013-04-24 16:05:32,681 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 0.000000
2013-04-24 16:05:33,182 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 0.000000
2013-04-24 16:05:33,682 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 0.000000
2013-04-24 16:05:34,183 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 0.000000
2013-04-24 16:05:34,684 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 0.000000
2013-04-24 16:05:35,185 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 0.000000
2013-04-24 16:05:35,686 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 0.000000
2013-04-24 16:05:36,187 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 0.000000
2013-04-24 16:05:36,688 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 0.000000
2013-04-24 16:05:37,189 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 0.000000
2013-04-24 16:05:37,690 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 0.000000
2013-04-24 16:05:38,191 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 0.000000
2013-04-24 16:05:38,692 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 0.000000
2013-04-24 16:05:39,193 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 0.000000
2013-04-24 16:05:39,694 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 0.000000
2013-04-24 16:05:40,194 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 0.000000
2013-04-24 16:05:40,695 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 0.000000
2013-04-24 16:05:41,196 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 0.000000
2013-04-24 16:05:41,697 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 0.000000
2013-04-24 16:05:42,198 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 0.000000
2013-04-24 16:05:42,699 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 0.000000
2013-04-24 16:05:43,200 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 0.000000
2013-04-24 16:05:43,700 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 0.000000
2013-04-24 16:05:44,201 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 0.000000
2013-04-24 16:05:44,702 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 0.000000
2013-04-24 16:05:45,203 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 0.000000
2013-04-24 16:05:45,704 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 0.000000
2013-04-24 16:05:46,205 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 0.000000
2013-04-24 16:05:46,706 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 0.000000
2013-04-24 16:05:47,207 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 0.000000
2013-04-24 16:05:47,708 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 0.000000
2013-04-24 16:05:48,209 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 0.000000
2013-04-24 16:05:48,710 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 0.000000
2013-04-24 16:05:49,211 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 0.000000
2013-04-24 16:05:49,712 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 0.000000
2013-04-24 16:05:50,213 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 0.000000
2013-04-24 16:05:50,714 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 0.000000
2013-04-24 16:05:51,215 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 0.000000
2013-04-24 16:05:51,716 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 0.000000
2013-04-24 16:05:52,216 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 0.000000
2013-04-24 16:05:52,717 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 0.000000
2013-04-24 16:05:53,218 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 0.000000
2013-04-24 16:05:53,719 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 0.000000
2013-04-24 16:05:54,221 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 0.000000
2013-04-24 16:05:54,722 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 0.000000
2013-04-24 16:05:55,223 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 0.000000
2013-04-24 16:05:55,724 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 0.000000
2013-04-24 16:05:56,225 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 0.000000
2013-04-24 16:05:56,726 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 0.000000
2013-04-24 16:05:57,227 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 0.000000
2013-04-24 16:05:57,728 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 0.000000
2013-04-24 16:05:58,229 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 0.000000
2013-04-24 16:05:58,730 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 0.000000
2013-04-24 16:05:59,231 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 0.000000
2013-04-24 16:05:59,732 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 0.000000
2013-04-24 16:06:00,233 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 0.000000
2013-04-24 16:06:00,734 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 0.000000
2013-04-24 16:06:01,235 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 0.000000
2013-04-24 16:06:01,736 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 0.000000
2013-04-24 16:06:02,237 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 0.000000
2013-04-24 16:06:02,738 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 0.000000
2013-04-24 16:06:03,601 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 0.000000
2013-04-24 16:06:04,102 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 0.000000
2013-04-24 16:06:04,603 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 0.000000
2013-04-24 16:06:05,104 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 0.000000
2013-04-24 16:06:05,605 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 0.000000
2013-04-24 16:06:06,106 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 0.000000
2013-04-24 16:06:06,607 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 0.000000
2013-04-24 16:06:07,109 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 0.000000
2013-04-24 16:06:07,610 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 0.000000
2013-04-24 16:06:08,111 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 0.000000
2013-04-24 16:06:08,612 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 0.000000
2013-04-24 16:06:09,113 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 0.000000
2013-04-24 16:06:09,614 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 0.000000
2013-04-24 16:06:10,115 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 0.000000
2013-04-24 16:06:10,615 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 0.000000
2013-04-24 16:06:11,116 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 0.000000
2013-04-24 16:06:11,617 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 0.000000
2013-04-24 16:06:12,118 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 0.000000
2013-04-24 16:06:12,620 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 0.000000
2013-04-24 16:06:13,121 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 0.000000
2013-04-24 16:06:13,622 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 0.000000
2013-04-24 16:06:14,123 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 0.000000
2013-04-24 16:06:14,624 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 0.000000
2013-04-24 16:06:15,125 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 0.000000
2013-04-24 16:06:15,626 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 0.000000
2013-04-24 16:06:16,127 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 0.000000
2013-04-24 16:06:16,628 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 0.000000
2013-04-24 16:06:17,129 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 0.000000
2013-04-24 16:06:17,630 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 0.000000
2013-04-24 16:06:18,132 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 0.000000
2013-04-24 16:06:18,632 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 0.000000
2013-04-24 16:06:18,945 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 0.008635
2013-04-24 16:06:19,446 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 0.237016
2013-04-24 16:06:19,948 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 0.465396
2013-04-24 16:06:20,449 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 0.944995
2013-04-24 16:06:20,950 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 1.161956
2013-04-24 16:06:21,451 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 1.413174
2013-04-24 16:06:21,952 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 1.413174
2013-04-24 16:06:22,453 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 1.413174
2013-04-24 16:06:22,954 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 1.413174
2013-04-24 16:06:23,455 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 1.413174
2013-04-24 16:06:23,956 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 1.413174
2013-04-24 16:06:24,457 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 1.515945
2013-04-24 16:06:24,959 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 1.744326
2013-04-24 16:06:25,460 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 1.835678
2013-04-24 16:06:25,961 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 2.143991
2013-04-24 16:06:26,462 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 2.292439
2013-04-24 16:06:26,963 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 2.806294
2013-04-24 16:06:27,464 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 3.617045
2013-04-24 16:06:27,965 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 4.530566
2013-04-24 16:06:28,466 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 5.512601
2013-04-24 16:06:28,966 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 6.551732
2013-04-24 16:06:29,467 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 7.179778
2013-04-24 16:06:29,968 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 8.184652
2013-04-24 16:06:30,469 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 9.406486
2013-04-24 16:06:30,970 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 10.262913
2013-04-24 16:06:31,471 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 11.416233
2013-04-24 16:06:31,973 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 12.112793
2013-04-24 16:06:32,474 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 12.718001
2013-04-24 16:06:32,975 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 13.722875
2013-04-24 16:06:33,476 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 14.567882
2013-04-24 16:06:33,977 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 15.115995
2013-04-24 16:06:34,478 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 15.504241
2013-04-24 16:06:34,979 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 15.698365
2013-04-24 16:06:35,480 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 16.531953
2013-04-24 16:06:35,982 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 17.194256
2013-04-24 16:06:36,483 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 17.479731
2013-04-24 16:06:36,984 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 18.027844
2013-04-24 16:06:37,485 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 18.313320
2013-04-24 16:06:37,986 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 18.484605
2013-04-24 16:06:38,486 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 18.701566
2013-04-24 16:06:38,987 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 19.158327
2013-04-24 16:06:39,488 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 19.615088
2013-04-24 16:06:39,989 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 20.094686
2013-04-24 16:06:40,490 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 20.094686
2013-04-24 16:06:40,991 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 21.887472
2013-04-24 16:06:41,491 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 22.652996
2013-04-24 16:06:41,993 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 23.429489
2013-04-24 16:06:42,494 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 23.429489
2013-04-24 16:06:42,995 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 25.153760
2013-04-24 16:06:43,496 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 25.975930
2013-04-24 16:06:43,997 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 26.741004
2013-04-24 16:06:44,498 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 27.551754
2013-04-24 16:06:45,000 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 27.894325
2013-04-24 16:06:45,501 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 28.522371
2013-04-24 16:06:46,002 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 29.435892
2013-04-24 16:06:46,503 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 30.337994
2013-04-24 16:06:47,004 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 31.262935
2013-04-24 16:06:47,505 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 32.302065
2013-04-24 16:06:48,006 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 33.501062
2013-04-24 16:06:48,507 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 34.779992
2013-04-24 16:06:49,009 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 35.773446
2013-04-24 16:06:49,510 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 36.926767
2013-04-24 16:06:50,011 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 37.806031
2013-04-24 16:06:50,512 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 38.913676
2013-04-24 16:06:51,013 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 40.009902
2013-04-24 16:06:51,514 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 41.026194
2013-04-24 16:06:52,014 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 42.168096
2013-04-24 16:06:52,515 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 43.355674
2013-04-24 16:06:53,016 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 44.623185
2013-04-24 16:06:53,517 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 45.879277
2013-04-24 16:06:54,019 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 47.009759
2013-04-24 16:06:54,520 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 48.334176
2013-04-24 16:06:55,021 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 49.366493
2013-04-24 16:06:55,522 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 50.412879
2013-04-24 16:06:56,023 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 51.257886
2013-04-24 16:06:56,524 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 52.011541
2013-04-24 16:06:57,025 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 52.011541
2013-04-24 16:06:57,526 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 52.011541
2013-04-24 16:06:58,026 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 54.376792
2013-04-24 16:06:58,528 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 55.316116
2013-04-24 16:06:59,029 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 56.149705
2013-04-24 16:06:59,530 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 56.332409
2013-04-24 16:07:00,031 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 57.245930
2013-04-24 16:07:00,532 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 58.342156
2013-04-24 16:07:01,033 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 59.449801
2013-04-24 16:07:01,534 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 60.271970
2013-04-24 16:07:02,035 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 60.500350
2013-04-24 16:07:02,536 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 61.368195
2013-04-24 16:07:03,037 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 62.453002
2013-04-24 16:07:03,538 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 63.298009
2013-04-24 16:07:04,039 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 64.005988
2013-04-24 16:07:04,540 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 64.656872
2013-04-24 16:07:05,041 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 64.839577
2013-04-24 16:07:05,542 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 65.775936
2013-04-24 16:07:06,043 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 66.506753
2013-04-24 16:07:06,544 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 67.328922
2013-04-24 16:07:07,045 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 67.956968
2013-04-24 16:07:07,546 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 68.813395
2013-04-24 16:07:08,047 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 69.898201
2013-04-24 16:07:08,548 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 70.594761
2013-04-24 16:07:09,050 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 71.382673
2013-04-24 16:07:09,551 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 72.187872
2013-04-24 16:07:10,052 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 73.088712
2013-04-24 16:07:10,553 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 74.254146
2013-04-24 16:07:11,054 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 75.156249
2013-04-24 16:07:11,555 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 76.069770
2013-04-24 16:07:12,056 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 76.928657
2013-04-24 16:07:12,557 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 77.568122
2013-04-24 16:07:13,058 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 78.424548
2013-04-24 16:07:13,559 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 78.424548
2013-04-24 16:07:14,060 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 80.263010
2013-04-24 16:07:14,561 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 81.255707
2013-04-24 16:07:15,062 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 82.400574
2013-04-24 16:07:15,564 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 83.679504
2013-04-24 16:07:16,065 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 84.707215
2013-04-24 16:07:16,566 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 85.301004
2013-04-24 16:07:17,067 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 86.203107
2013-04-24 16:07:17,568 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 87.086913
2013-04-24 16:07:18,069 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 88.148882
2013-04-24 16:07:18,570 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 89.233689
2013-04-24 16:07:19,071 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 90.181467
2013-04-24 16:07:19,572 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 91.311950
2013-04-24 16:07:20,073 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 92.225471
2013-04-24 16:07:20,081 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 92.269373
2013-04-24 16:07:20,096 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 92.278040
2013-04-24 16:07:20,597 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 93.202980
2013-04-24 16:07:21,098 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 94.527586
2013-04-24 16:07:21,599 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 95.772259
2013-04-24 16:07:22,100 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 96.708618
2013-04-24 16:07:22,601 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 97.850520
2013-04-24 16:07:23,101 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 98.535661
2013-04-24 16:07:23,602 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 99.449182
2013-04-24 16:07:24,103 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 99.711820
2013-04-24 16:07:24,604 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 99.894524
2013-04-24 16:07:24,741 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 99.979741
2013-04-24 16:07:24,742 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 99.983163
2013-04-24 16:07:24,752 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 100.000000
2013-04-24 16:07:27,656 DEBUG: install progress dpkg-exec 0.000000
2013-04-24 16:07:27,757 DEBUG: dpkg: error: dpkg status database is locked by another process
Error in function: 
SystemError: E:Sub-process /usr/bin/dpkg returned an error code (2)


2013-04-24 16:07:27,757 ERROR: Package failed to install:
dpkg: error: dpkg status database is locked by another process
Error in function: 
SystemError: E:Sub-process /usr/bin/dpkg returned an error code (2)


2013-04-24 16:07:27,841 DEBUG: Installing package: fglrx-updates
2013-04-24 16:07:28,069 ERROR: Package fetching failed: Failed to lock /var/cache/apt/archives/lock
2013-04-24 16:07:28,173 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates


2013-04-24 16:07:28,173 WARNING: /sys/module/fglrx_updates/drivers does not exist, cannot rebind fglrx_updates driver
2013-04-24 16:07:28,174 ERROR: XorgDriverHandler.enable(): package or module not installed, aborting
2013-04-24 16:07:28,177 ERROR: xorg:fglrx_updates: get_alternative_by_name(fglrx-updates) returned nothing
2013-04-24 16:07:28,350 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2013-04-24 16:07:28,350 DEBUG: fglrx_updates is not the alternative in use
2013-04-24 16:07:32,292 DEBUG: fglrx.enabled(fglrx_experimental_9): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2013-04-24 16:07:32,292 DEBUG: fglrx_experimental_9 is not the alternative in use
2013-04-24 16:07:32,307 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2013-04-24 16:07:32,307 DEBUG: fglrx_updates is not the alternative in use
2013-04-24 16:07:32,325 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2013-04-24 16:07:32,325 DEBUG: fglrx_updates is not the alternative in use
2013-04-24 16:07:32,352 DEBUG: fglrx.enabled(fglrx_experimental_9): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2013-04-24 16:07:32,352 DEBUG: fglrx_experimental_9 is not the alternative in use
2013-04-24 16:07:32,364 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2013-04-24 16:07:32,364 DEBUG: fglrx_updates is not the alternative in use
2013-04-24 16:10:28,277 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2013-04-24 16:10:28,277 DEBUG: fglrx_updates is not the alternative in use
2013-04-24 16:10:31,996 DEBUG: Installing package: linux-headers-generic
2013-04-24 16:10:32,258 ERROR: Package fetching failed: Failed to lock /var/cache/apt/archives/lock
2013-04-24 16:10:32,355 DEBUG: Installing package: fglrx-updates
2013-04-24 16:10:32,623 ERROR: Package fetching failed: Failed to lock /var/cache/apt/archives/lock
2013-04-24 16:10:32,739 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates


2013-04-24 16:10:32,740 WARNING: /sys/module/fglrx_updates/drivers does not exist, cannot rebind fglrx_updates driver
2013-04-24 16:10:32,740 ERROR: XorgDriverHandler.enable(): package or module not installed, aborting
2013-04-24 16:10:32,745 ERROR: xorg:fglrx_updates: get_alternative_by_name(fglrx-updates) returned nothing
2013-04-24 16:10:32,814 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2013-04-24 16:10:32,814 DEBUG: fglrx_updates is not the alternative in use
2013-04-24 16:10:36,522 DEBUG: fglrx.enabled(fglrx_experimental_9): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2013-04-24 16:10:36,522 DEBUG: fglrx_experimental_9 is not the alternative in use
2013-04-24 16:10:36,542 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2013-04-24 16:10:36,542 DEBUG: fglrx_updates is not the alternative in use
2013-04-24 16:10:36,567 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2013-04-24 16:10:36,568 DEBUG: fglrx_updates is not the alternative in use
2013-04-24 16:10:36,604 DEBUG: fglrx.enabled(fglrx_experimental_9): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2013-04-24 16:10:36,604 DEBUG: fglrx_experimental_9 is not the alternative in use
2013-04-24 16:10:36,622 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2013-04-24 16:10:36,622 DEBUG: fglrx_updates is not the alternative in use
2013-04-24 16:14:04,779 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2013-04-24 16:14:04,779 DEBUG: fglrx_updates is not the alternative in use
2013-04-24 16:14:04,851 DEBUG: Installing package: linux-headers-generic
2013-04-24 16:14:05,101 ERROR: Package fetching failed: Failed to lock /var/cache/apt/archives/lock
2013-04-24 16:14:05,190 DEBUG: Installing package: fglrx-updates
2013-04-24 16:14:05,443 ERROR: Package fetching failed: Failed to lock /var/cache/apt/archives/lock
2013-04-24 16:14:05,552 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates


2013-04-24 16:14:05,553 WARNING: /sys/module/fglrx_updates/drivers does not exist, cannot rebind fglrx_updates driver
2013-04-24 16:14:05,553 ERROR: XorgDriverHandler.enable(): package or module not installed, aborting
2013-04-24 16:14:05,559 ERROR: xorg:fglrx_updates: get_alternative_by_name(fglrx-updates) returned nothing
2013-04-24 16:14:05,646 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2013-04-24 16:14:05,646 DEBUG: fglrx_updates is not the alternative in use
2013-04-24 16:14:06,881 DEBUG: fglrx.enabled(fglrx_experimental_9): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2013-04-24 16:14:06,881 DEBUG: fglrx_experimental_9 is not the alternative in use
2013-04-24 16:14:06,923 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2013-04-24 16:14:06,923 DEBUG: fglrx_updates is not the alternative in use
2013-04-24 16:14:06,974 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2013-04-24 16:14:06,974 DEBUG: fglrx_updates is not the alternative in use
2013-04-24 16:14:07,050 DEBUG: fglrx.enabled(fglrx_experimental_9): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2013-04-24 16:14:07,051 DEBUG: fglrx_experimental_9 is not the alternative in use
2013-04-24 16:14:07,089 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2013-04-24 16:14:07,090 DEBUG: fglrx_updates is not the alternative in use
2013-04-24 16:14:08,337 DEBUG: fglrx.enabled(fglrx_experimental_9): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2013-04-24 16:14:08,338 DEBUG: fglrx_experimental_9 is not the alternative in use
2013-04-24 16:14:18,671 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2013-04-24 16:14:18,671 DEBUG: fglrx_updates is not the alternative in use
2013-04-24 16:14:20,653 DEBUG: Shutting down
2013-04-24 16:23:04,135 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x9465a0c>
2013-04-24 16:23:05,155 DEBUG: reading modalias file /lib/modules/3.5.0-23-generic/modules.alias
2013-04-24 16:23:05,653 DEBUG: reading modalias file /usr/share/jockey/modaliases/b43
2013-04-24 16:23:05,743 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2013-04-24 16:23:05,784 DEBUG: loading custom handler /usr/share/jockey/handlers/cdv.py
2013-04-24 16:23:06,078 WARNING: modinfo for module cedarview_gfx failed: ERROR: modinfo: could not find module cedarview_gfx


2013-04-24 16:23:06,078 DEBUG: Instantiated Handler subclass __builtin__.CdvDriver from name CdvDriver
2013-04-24 16:23:06,078 DEBUG: cdv.available: falling back to default
2013-04-24 16:23:06,263 DEBUG: XorgDriverHandler(cedarview_gfx, cedarview-graphics-drivers, None): Disabling as package is not compatible with Q-LTS X.org
2013-04-24 16:23:06,264 DEBUG: Intel Cedarview graphics driver not available
2013-04-24 16:23:06,264 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2013-04-24 16:23:06,311 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl


2013-04-24 16:23:06,323 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2013-04-24 16:23:06,323 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2013-04-24 16:23:06,323 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2013-04-24 16:23:06,457 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates


2013-04-24 16:23:06,460 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriverUpdate from name FglrxDriverUpdate
2013-04-24 16:23:06,460 DEBUG: fglrx.available: falling back to default
2013-04-24 16:23:06,659 DEBUG: ATI/AMD proprietary FGLRX graphics driver (post-release updates) availability undetermined, adding to pool
2013-04-24 16:23:06,661 WARNING: modinfo for module fglrx_experimental_9 failed: ERROR: modinfo: could not find module fglrx_experimental_9


2013-04-24 16:23:06,682 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriverExperimental9 from name FglrxDriverExperimental9
2013-04-24 16:23:06,682 DEBUG: fglrx.available: falling back to default
2013-04-24 16:23:06,907 DEBUG: ATI/AMD proprietary FGLRX graphics driver (**experimental** beta) availability undetermined, adding to pool
2013-04-24 16:23:06,911 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx


2013-04-24 16:23:06,916 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2013-04-24 16:23:06,916 DEBUG: fglrx.available: falling back to default
2013-04-24 16:23:07,039 DEBUG: XorgDriverHandler(fglrx, fglrx, None): Disabling as package is not compatible with Q-LTS X.org
2013-04-24 16:23:07,040 DEBUG: ATI/AMD proprietary FGLRX graphics driver not available
2013-04-24 16:23:07,040 DEBUG: loading custom handler /usr/share/jockey/handlers/pvr-omap4.py
2013-04-24 16:23:07,091 WARNING: modinfo for module omapdrm_pvr failed: ERROR: modinfo: could not find module omapdrm_pvr


2013-04-24 16:23:07,094 DEBUG: Instantiated Handler subclass __builtin__.PVROmap4Driver from name PVROmap4Driver
2013-04-24 16:23:07,216 DEBUG: XorgDriverHandler(omapdrm_pvr, pvr-omap4, None): Disabling as package is not compatible with Q-LTS X.org
2013-04-24 16:23:07,216 DEBUG: PowerVR SGX proprietary graphics driver for OMAP 4 not available
2013-04-24 16:23:07,216 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2013-04-24 16:23:07,455 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96


2013-04-24 16:23:07,460 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2013-04-24 16:23:07,461 DEBUG: Disabling Nvidia driver on intel/hybrid system
2013-04-24 16:23:07,462 DEBUG: NVIDIA accelerated graphics driver not available
2013-04-24 16:23:07,464 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current


2013-04-24 16:23:07,468 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2013-04-24 16:23:07,469 DEBUG: Disabling Nvidia driver on intel/hybrid system
2013-04-24 16:23:07,469 DEBUG: NVIDIA accelerated graphics driver not available
2013-04-24 16:23:07,473 WARNING: modinfo for module nvidia_current_updates failed: ERROR: modinfo: could not find module nvidia_current_updates


2013-04-24 16:23:07,477 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrentUpdates from name NvidiaDriverCurrentUpdates
2013-04-24 16:23:07,478 DEBUG: Disabling Nvidia driver on intel/hybrid system
2013-04-24 16:23:07,478 DEBUG: NVIDIA accelerated graphics driver (post-release updates) not available
2013-04-24 16:23:07,482 WARNING: modinfo for module nvidia_96_updates failed: ERROR: modinfo: could not find module nvidia_96_updates


2013-04-24 16:23:07,485 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96Updates from name NvidiaDriver96Updates
2013-04-24 16:23:07,486 DEBUG: Disabling Nvidia driver on intel/hybrid system
2013-04-24 16:23:07,486 DEBUG: NVIDIA accelerated graphics driver (post-release updates) not available
2013-04-24 16:23:07,490 WARNING: modinfo for module nvidia_173_updates failed: ERROR: modinfo: could not find module nvidia_173_updates


2013-04-24 16:23:07,495 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173Updates from name NvidiaDriver173Updates
2013-04-24 16:23:07,496 DEBUG: Disabling Nvidia driver on intel/hybrid system
2013-04-24 16:23:07,496 DEBUG: NVIDIA accelerated graphics driver (post-release updates) not available
2013-04-24 16:23:07,499 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173


2013-04-24 16:23:07,504 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2013-04-24 16:23:07,505 DEBUG: Disabling Nvidia driver on intel/hybrid system
2013-04-24 16:23:07,505 DEBUG: NVIDIA accelerated graphics driver not available
2013-04-24 16:23:07,508 WARNING: modinfo for module nvidia_experimental_310 failed: ERROR: modinfo: could not find module nvidia_experimental_310


2013-04-24 16:23:07,525 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverExperimental310 from name NvidiaDriverExperimental310
2013-04-24 16:23:07,526 DEBUG: Disabling Nvidia driver on intel/hybrid system
2013-04-24 16:23:07,527 DEBUG: NVIDIA accelerated graphics driver (**experimental** beta) not available
2013-04-24 16:23:07,531 WARNING: modinfo for module nvidia_experimental_304 failed: ERROR: modinfo: could not find module nvidia_experimental_304


2013-04-24 16:23:07,555 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverExperimental304 from name NvidiaDriverExperimental304
2013-04-24 16:23:07,556 DEBUG: Disabling Nvidia driver on intel/hybrid system
2013-04-24 16:23:07,556 DEBUG: NVIDIA accelerated graphics driver (**experimental** beta) not available
2013-04-24 16:23:07,556 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2013-04-24 16:23:07,575 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2013-04-24 16:23:07,809 DEBUG: Software modem not available
2013-04-24 16:23:07,809 DEBUG: loading custom handler /usr/share/jockey/handlers/vmware-client.py
2013-04-24 16:23:07,812 WARNING: modinfo for module vmxnet failed: ERROR: modinfo: could not find module vmxnet


2013-04-24 16:23:07,812 DEBUG: Instantiated Handler subclass __builtin__.VmwareClientHandler from name VmwareClientHandler
2013-04-24 16:23:07,825 DEBUG: VMWare Client Tools availability undetermined, adding to pool
2013-04-24 16:23:07,826 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2013-04-24 16:23:08,454 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2013-04-24 16:23:08,454 DEBUG: Firmware for DVB cards not available
2013-04-24 16:23:08,454 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2013-04-24 16:23:08,597 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci


2013-04-24 16:23:08,597 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2013-04-24 16:23:08,597 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2013-04-24 16:23:08,597 DEBUG: all custom handlers loaded
2013-04-24 16:23:08,597 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9465a0c> about HardwareID('modalias', 'pci:v00008086d00000154sv0000144Dsd0000C0D8bc06sc00i00')
2013-04-24 16:23:08,784 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9465a0c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2013-04-24 16:23:08,786 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-04-24 16:23:08,835 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-04-24 16:23:08,835 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9465a0c> about HardwareID('modalias', 'acpi:PNP0B00:')
2013-04-24 16:23:08,836 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9465a0c> about HardwareID('modalias', 'pci:v00008086d00001E20sv0000144Dsd0000C0D8bc04sc03i00')
2013-04-24 16:23:08,838 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2013-04-24 16:23:08,838 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2013-04-24 16:23:08,838 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2013-04-24 16:23:08,838 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2013-04-24 16:23:08,838 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9465a0c> about HardwareID('modalias', 'pci:v00008086d00001E2Dsv0000144Dsd0000C0D8bc0Csc03i20')
2013-04-24 16:23:08,840 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9465a0c> about HardwareID('modalias', 'platform:pcspkr')
2013-04-24 16:23:08,840 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr'}
2013-04-24 16:23:08,840 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2013-04-24 16:23:08,840 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp'}
2013-04-24 16:23:08,840 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2013-04-24 16:23:08,840 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9465a0c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2013-04-24 16:23:08,841 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-04-24 16:23:08,841 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-04-24 16:23:08,841 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9465a0c> about HardwareID('modalias', 'usb:v1D6Bp0003d0305dc09dsc00dp03ic09isc00ip00')
2013-04-24 16:23:08,850 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9465a0c> about HardwareID('modalias', 'usb:v8087p0024d0000dc09dsc00dp01ic09isc00ip00')
2013-04-24 16:23:08,850 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9465a0c> about HardwareID('modalias', 'input:b0003v045Ep0745e0111-e0,1,2,3,4,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,8B,8C,8E,8F,90,94,96,98,9B,9C,9E,9F,A1,A3,A4,A5,A6,A7,A8,A9,AB,AC,AD,AE,B0,B1,B2,B3,B4,B5,B6,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,CE,CF,D0,D1,D2,D4,D8,D9,DB,DF,E4,E7,E8,E9,EA,EB,F0,F1,100,13A,13B,161,162,164,166,16A,16E,172,174,176,178,179,17A,17B,17C,17D,17F,180,182,183,185,188,189,18C,18D,18E,18F,190,191,192,193,195,198,199,19A,1A0,1A1,1A2,1A3,1A4,1A5,1A6,1A7,1A8,1A9,1AA,1AB,1AC,1AD,1AE,1B0,1B1,1B6,1B7,1BA,r6,a0,1,2,3,4,5,6,7,8,10,11,12,20,28,29,2A,2B,2C,2D,2E,2F,30,31,32,33,34,35,36,37,38,39,3A,3B,3C,3D,3E,m4,lsfw')
2013-04-24 16:23:08,850 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-04-24 16:23:08,850 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-04-24 16:23:08,850 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2013-04-24 16:23:08,850 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2013-04-24 16:23:08,850 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2013-04-24 16:23:08,850 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2013-04-24 16:23:08,851 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2013-04-24 16:23:08,851 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2013-04-24 16:23:08,851 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-04-24 16:23:08,851 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-04-24 16:23:08,851 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9465a0c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2013-04-24 16:23:08,851 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9465a0c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2013-04-24 16:23:08,851 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9465a0c> about HardwareID('modalias', 'usb:v1D6Bp0002d0305dc09dsc00dp00ic09isc00ip00')
2013-04-24 16:23:08,851 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9465a0c> about HardwareID('modalias', 'acpi:PNP0100:')
2013-04-24 16:23:08,851 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9465a0c> about HardwareID('modalias', 'input:b0011v0002p0007e01B1-e0,1,3,k110,111,145,14A,14D,14E,ra0,1,18,1C,2F,35,36,39,mlsfw')
2013-04-24 16:23:08,851 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-04-24 16:23:08,851 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-04-24 16:23:08,851 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2013-04-24 16:23:08,852 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2013-04-24 16:23:08,852 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2013-04-24 16:23:08,852 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2013-04-24 16:23:08,852 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2013-04-24 16:23:08,852 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2013-04-24 16:23:08,852 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-04-24 16:23:08,852 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-04-24 16:23:08,852 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9465a0c> about HardwareID('modalias', 'wmi:C16C47BA-50E3-444A-AF3A-B1C348380000')
2013-04-24 16:23:08,852 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9465a0c> about HardwareID('modalias', 'pci:v00008086d00001E3Asv0000144Dsd0000C0D8bc07sc80i00')
2013-04-24 16:23:08,854 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mei'}
2013-04-24 16:23:08,854 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mei', 'jockey_handler': 'KernelModuleHandler'}
2013-04-24 16:23:08,854 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9465a0c> about HardwareID('modalias', 'wmi:C16C47BA-50E3-444A-AF3A-B1C348380001')
2013-04-24 16:23:08,854 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9465a0c> about HardwareID('modalias', 'usb:v0C45pC35Ad0300dcEFdsc02dp01ic0Eisc01ip00')
2013-04-24 16:23:08,872 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo'}
2013-04-24 16:23:08,872 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo', 'jockey_handler': 'KernelModuleHandler'}
2013-04-24 16:23:08,872 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9465a0c> about HardwareID('modalias', 'pci:v00008086d00001E03sv0000144Dsd0000C0D8bc01sc06i01')
2013-04-24 16:23:08,874 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9465a0c> about HardwareID('modalias', 'pci:v00008086d00001E22sv0000144Dsd0000C0D8bc0Csc05i00')
2013-04-24 16:23:08,876 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801'}
2013-04-24 16:23:08,876 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801', 'jockey_handler': 'KernelModuleHandler'}
2013-04-24 16:23:08,876 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9465a0c> about HardwareID('modalias', 'pci:v00008086d00001E31sv0000144Dsd0000C0D8bc0Csc03i30')
2013-04-24 16:23:08,878 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9465a0c> about HardwareID('modalias', 'acpi:PNP0303:PNP030B:')
2013-04-24 16:23:08,878 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9465a0c> about HardwareID('modalias', 'acpi:PNP0C04:')
2013-04-24 16:23:08,878 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9465a0c> about HardwareID('modalias', 'acpi:PNP0C02:')
2013-04-24 16:23:08,878 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9465a0c> about HardwareID('modalias', 'pci:v00008086d00001E26sv0000144Dsd0000C0D8bc0Csc03i20')
2013-04-24 16:23:08,880 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9465a0c> about HardwareID('modalias', 'usb:v045Ep0745d0634dc00dsc00dp00ic03isc01ip02')
2013-04-24 16:23:08,912 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2013-04-24 16:23:08,913 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2013-04-24 16:23:08,913 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse'}
2013-04-24 16:23:08,913 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse', 'jockey_handler': 'KernelModuleHandler'}
2013-04-24 16:23:08,913 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9465a0c> about HardwareID('modalias', 'acpi:INT3F0D:PNP0C02:')
2013-04-24 16:23:08,913 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9465a0c> about HardwareID('modalias', 'platform:microcode')
2013-04-24 16:23:08,913 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9465a0c> about HardwareID('modalias', 'input:b0003v0C45pC35Ae0300-e0,1,kD4,ramlsfw')
2013-04-24 16:23:08,913 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-04-24 16:23:08,913 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-04-24 16:23:08,913 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-04-24 16:23:08,913 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-04-24 16:23:08,913 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9465a0c> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8E,8F,94,95,96,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,C0,C1,CA,D9,E0,E1,E2,E3,EC,EE,ram4,l0,1,2,sfw')
2013-04-24 16:23:08,914 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-04-24 16:23:08,914 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-04-24 16:23:08,914 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-04-24 16:23:08,914 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-04-24 16:23:08,914 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9465a0c> about HardwareID('modalias', 'usb:v0CF3p3004d0002dcE0dsc01dp01icE0isc01ip01')
2013-04-24 16:23:08,918 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'ath3k'}
2013-04-24 16:23:08,918 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ath3k', 'jockey_handler': 'KernelModuleHandler'}
2013-04-24 16:23:08,918 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'btusb'}
2013-04-24 16:23:08,918 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'btusb', 'jockey_handler': 'KernelModuleHandler'}
2013-04-24 16:23:08,918 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9465a0c> about HardwareID('modalias', 'input:b0003v045Ep0745e0111-e0,1,2,3,4,k71,72,73,74,77,80,82,83,85,86,87,88,89,8A,8B,8C,8E,90,96,98,9B,9C,9E,9F,A1,A3,A4,A5,A6,A7,A8,A9,AB,AC,AD,AE,B0,B1,B2,B5,B6,CE,CF,D0,D1,D2,D4,D8,D9,DB,DF,E4,E7,E8,E9,EA,EB,F1,100,110,111,112,113,114,161,162,166,16A,16E,172,174,176,178,179,17A,17B,17C,17D,17F,180,182,183,185,188,189,18C,18D,18E,18F,190,191,192,193,195,198,199,19A,1A0,1A1,1A2,1A3,1A4,1A5,1A6,1A7,1A8,1A9,1AA,1AB,1AC,1AD,1AE,1B0,1B1,1B7,1BA,r0,1,6,7,8,9,a20,m4,lsfw')
2013-04-24 16:23:08,918 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-04-24 16:23:08,918 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-04-24 16:23:08,918 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2013-04-24 16:23:08,918 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2013-04-24 16:23:08,919 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-04-24 16:23:08,919 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-04-24 16:23:08,919 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9465a0c> about HardwareID('modalias', 'acpi:PNP0F03:PNP0F13:')
2013-04-24 16:23:08,919 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9465a0c> about HardwareID('modalias', 'dmi:bvnAmericanMegatrendsInc.:bvrP03ABE:bd09/20/2012:svnSAMSUNGELECTRONICSCO.,LTD.:pn350V5C/350V5X/350V4C/350V4X/351V5C/351V5X/351V4C/351V4X/3540VC/3540VX/3440VC/3440VX:pvrP03ABE.006.CP:rvnSAMSUNGELECTRONICSCO.,LTD.:rnNP350V5C-S04PT:rvrBOARDREVISION00:cvnSAMSUNGELECTRONICSCO.,LTD.:ct9:cvr0.1:')
2013-04-24 16:23:08,927 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9465a0c> about HardwareID('modalias', 'pci:v000010ECd00008168sv0000144Dsd0000C0D8bc02sc00i00')
2013-04-24 16:23:08,932 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'r8169'}
2013-04-24 16:23:08,932 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'r8169', 'jockey_handler': 'KernelModuleHandler'}
2013-04-24 16:23:08,932 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9465a0c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,8,')
2013-04-24 16:23:08,932 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-04-24 16:23:08,932 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-04-24 16:23:08,932 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9465a0c> about HardwareID('modalias', 'usb:v1D6Bp0002d0305dc09dsc00dp01ic09isc00ip00')
2013-04-24 16:23:08,933 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9465a0c> about HardwareID('modalias', 'usb:v045Ep0745d0634dc00dsc00dp00ic03isc00ip00')
2013-04-24 16:23:08,933 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2013-04-24 16:23:08,933 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2013-04-24 16:23:08,933 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9465a0c> about HardwareID('modalias', 'pci:v00008086d00001E59sv0000144Dsd0000C0D8bc06sc01i00')
2013-04-24 16:23:08,935 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'lpc_ich'}
2013-04-24 16:23:08,935 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'lpc_ich', 'jockey_handler': 'KernelModuleHandler'}
2013-04-24 16:23:08,935 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9465a0c> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2013-04-24 16:23:08,935 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-04-24 16:23:08,935 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-04-24 16:23:08,935 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9465a0c> about HardwareID('modalias', 'pci:v0000168Cd00000032sv0000144Dsd00004105bc02sc80i00')
2013-04-24 16:23:08,941 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'ath9k'}
2013-04-24 16:23:08,941 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ath9k', 'jockey_handler': 'KernelModuleHandler'}
2013-04-24 16:23:08,941 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9465a0c> about HardwareID('modalias', 'acpi:PNP0C01:')
2013-04-24 16:23:08,941 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9465a0c> about HardwareID('modalias', 'usb:v0C45pC35Ad0300dcEFdsc02dp01ic0Eisc02ip00')
2013-04-24 16:23:08,942 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9465a0c> about HardwareID('modalias', 'pci:v00001002d00006840sv0000144Dsd0000C0D8bc03sc00i00')
2013-04-24 16:23:09,153 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'radeon'}
2013-04-24 16:23:09,153 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'radeon', 'jockey_handler': 'KernelModuleHandler'}
2013-04-24 16:23:09,153 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx_experimental_12', 'package': 'fglrx-experimental-12'}
2013-04-24 16:23:09,156 WARNING: modinfo for module fglrx_experimental_12 failed: ERROR: modinfo: could not find module fglrx_experimental_12


2013-04-24 16:23:09,178 WARNING: modinfo for module fglrx_experimental_12 failed: ERROR: modinfo: could not find module fglrx_experimental_12


2013-04-24 16:23:09,179 DEBUG: got handler kmod:fglrx_experimental_12([KernelModuleHandler, nonfree, disabled] Experimental AMD binary Xorg driver and kernel module)
2013-04-24 16:23:09,179 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx_experimental_9', 'package': 'fglrx-experimental-9'}
2013-04-24 16:23:09,192 DEBUG: fglrx.enabled(fglrx_experimental_9): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2013-04-24 16:23:09,192 DEBUG: fglrx_experimental_9 is not the alternative in use
2013-04-24 16:23:09,179 DEBUG: found match in handler pool xorg:fglrx_experimental_9([FglrxDriverExperimental9, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (**experimental** beta))
2013-04-24 16:23:09,196 WARNING: modinfo for module fglrx_experimental_9 failed: ERROR: modinfo: could not find module fglrx_experimental_9


2013-04-24 16:23:09,201 DEBUG: fglrx.available: falling back to default
2013-04-24 16:23:09,328 DEBUG: fglrx.enabled(fglrx_experimental_9): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2013-04-24 16:23:09,328 DEBUG: fglrx_experimental_9 is not the alternative in use
2013-04-24 16:23:09,314 DEBUG: got handler xorg:fglrx_experimental_9([FglrxDriverExperimental9, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (**experimental** beta))
2013-04-24 16:23:09,329 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx_updates', 'package': 'fglrx-updates'}
2013-04-24 16:23:09,342 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2013-04-24 16:23:09,342 DEBUG: fglrx_updates is not the alternative in use
2013-04-24 16:23:09,329 DEBUG: found match in handler pool xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2013-04-24 16:23:09,346 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates


2013-04-24 16:23:09,350 DEBUG: fglrx.available: falling back to default
2013-04-24 16:23:09,479 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2013-04-24 16:23:09,480 DEBUG: fglrx_updates is not the alternative in use
2013-04-24 16:23:09,466 DEBUG: got handler xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2013-04-24 16:23:09,480 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx', 'package': 'fglrx'}
2013-04-24 16:23:09,493 DEBUG: fglrx.enabled(fglrx): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2013-04-24 16:23:09,494 DEBUG: fglrx is not the alternative in use
2013-04-24 16:23:09,480 DEBUG: found match in handler pool xorg:fglrx([FglrxDriver, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver)
2013-04-24 16:23:09,498 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx


2013-04-24 16:23:09,503 DEBUG: fglrx.available: falling back to default
2013-04-24 16:23:09,633 DEBUG: XorgDriverHandler(fglrx, fglrx, None): Disabling as package is not compatible with Q-LTS X.org
2013-04-24 16:23:09,646 DEBUG: fglrx.enabled(fglrx): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2013-04-24 16:23:09,646 DEBUG: fglrx is not the alternative in use
2013-04-24 16:23:09,634 DEBUG: ignoring unavailable handler xorg:fglrx([FglrxDriver, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver)
2013-04-24 16:23:09,646 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9465a0c> about HardwareID('modalias', 'acpi:PNP0200:')
2013-04-24 16:23:09,647 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9465a0c> about HardwareID('modalias', 'acpi:INT0800:')
2013-04-24 16:23:09,647 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9465a0c> about HardwareID('modalias', 'platform:eisa')
2013-04-24 16:23:09,647 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9465a0c> about HardwareID('modalias', 'pci:v00008086d00000166sv0000144Dsd0000C0D8bc03sc00i00')
2013-04-24 16:23:09,649 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'i915'}
2013-04-24 16:23:09,649 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i915', 'jockey_handler': 'KernelModuleHandler'}
2013-04-24 16:23:09,650 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9465a0c> about HardwareID('modalias', 'hid:b0003g0001v0000045Ep00000745')
2013-04-24 16:23:09,676 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'hid_generic'}
2013-04-24 16:23:09,676 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'hid_generic', 'jockey_handler': 'KernelModuleHandler'}
2013-04-24 16:23:09,676 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9465a0c> about HardwareID('modalias', 'usb:v045Ep0745d0634dc00dsc00dp00ic03isc01ip01')
2013-04-24 16:23:09,676 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2013-04-24 16:23:09,676 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2013-04-24 16:23:09,676 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd'}
2013-04-24 16:23:09,676 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd', 'jockey_handler': 'KernelModuleHandler'}
2013-04-24 16:23:09,676 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9465a0c> about HardwareID('modalias', 'acpi:PNP0000:')
2013-04-24 16:23:09,676 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9465a0c> about HardwareID('modalias', 'platform:samsung')
2013-04-24 16:23:09,677 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9465a0c> about HardwareID('modalias', 'platform:regulatory')
2013-04-24 16:23:09,677 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9465a0c> about HardwareID('modalias', 'x86cpu:vendor:0000:family:0006:model:003A:feature:,0000,0001,0002,0003,0004,0005,0006,0007,0008,0009,000B,000C,000D,000E,000F,0010,0011,0013,0015,0016,0017,0018,0019,001A,001B,001C,001D,001F,0034,003B,003D,0066,0068,006B,006C,006D,0072,0076,0078,007C,0080,0081,0082,0083,0084,0085,0087,0088,0089,008D,008E,008F,0091,0093,0094,0095,0097,0098,0099,009A,009B,009C,009D,009E,00C0,00E0,00E1,00E3,00E4,00E5,00E6,00E7,0100,0101,0102,0103,0104,0120,0127,0129')
2013-04-24 16:23:09,681 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'aesni_intel'}
2013-04-24 16:23:09,681 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'aesni_intel', 'jockey_handler': 'KernelModuleHandler'}
2013-04-24 16:23:09,681 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'kvm_intel'}
2013-04-24 16:23:09,681 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'kvm_intel', 'jockey_handler': 'KernelModuleHandler'}
2013-04-24 16:23:09,681 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'microcode'}
2013-04-24 16:23:09,681 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'microcode', 'jockey_handler': 'KernelModuleHandler'}
2013-04-24 16:23:09,681 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'coretemp'}
2013-04-24 16:23:09,681 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'coretemp', 'jockey_handler': 'KernelModuleHandler'}
2013-04-24 16:23:09,681 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9465a0c> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2013-04-24 16:23:09,686 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw'}
2013-04-24 16:23:09,686 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2013-04-24 16:23:09,686 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'psmouse'}
2013-04-24 16:23:09,686 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2013-04-24 16:23:09,686 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9465a0c> about HardwareID('modalias', 'platform:coretemp')
2013-04-24 16:23:09,686 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9465a0c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2013-04-24 16:23:09,686 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-04-24 16:23:09,687 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-04-24 16:23:09,687 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-04-24 16:23:09,687 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-04-24 16:23:09,687 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9465a0c> about HardwareID('modalias', 'acpi:PNP0103:')
2013-04-24 16:23:09,687 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9465a0c> about HardwareID('modalias', 'input:b0003v045Ep0745e0111-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,sfw')
2013-04-24 16:23:09,687 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-04-24 16:23:09,687 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-04-24 16:23:09,687 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-04-24 16:23:09,687 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-04-24 16:23:09,687 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9465a0c> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2013-04-24 16:23:09,687 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-04-24 16:23:09,687 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-04-24 16:23:09,687 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-04-24 16:23:09,687 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-04-24 16:23:09,687 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9465a0c> about HardwareID('modalias', 'acpi:INT340E:PNP0C02:')
2013-04-24 16:23:09,687 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x96fd60c> about HardwareID('modalias', 'pci:v00008086d00000154sv0000144Dsd0000C0D8bc06sc00i00')
2013-04-24 16:23:09,687 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x96fd60c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2013-04-24 16:23:09,687 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x96fd60c> about HardwareID('modalias', 'acpi:PNP0B00:')
2013-04-24 16:23:09,687 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x96fd60c> about HardwareID('modalias', 'pci:v00008086d00001E20sv0000144Dsd0000C0D8bc04sc03i00')
2013-04-24 16:23:09,688 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x96fd60c> about HardwareID('modalias', 'pci:v00008086d00001E2Dsv0000144Dsd0000C0D8bc0Csc03i20')
2013-04-24 16:23:09,688 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x96fd60c> about HardwareID('modalias', 'platform:pcspkr')
2013-04-24 16:23:09,688 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x96fd60c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2013-04-24 16:23:09,688 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x96fd60c> about HardwareID('modalias', 'usb:v1D6Bp0003d0305dc09dsc00dp03ic09isc00ip00')
2013-04-24 16:23:09,688 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x96fd60c> about HardwareID('modalias', 'usb:v8087p0024d0000dc09dsc00dp01ic09isc00ip00')
2013-04-24 16:23:09,688 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x96fd60c> about HardwareID('modalias', 'input:b0003v045Ep0745e0111-e0,1,2,3,4,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,8B,8C,8E,8F,90,94,96,98,9B,9C,9E,9F,A1,A3,A4,A5,A6,A7,A8,A9,AB,AC,AD,AE,B0,B1,B2,B3,B4,B5,B6,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,CE,CF,D0,D1,D2,D4,D8,D9,DB,DF,E4,E7,E8,E9,EA,EB,F0,F1,100,13A,13B,161,162,164,166,16A,16E,172,174,176,178,179,17A,17B,17C,17D,17F,180,182,183,185,188,189,18C,18D,18E,18F,190,191,192,193,195,198,199,19A,1A0,1A1,1A2,1A3,1A4,1A5,1A6,1A7,1A8,1A9,1AA,1AB,1AC,1AD,1AE,1B0,1B1,1B6,1B7,1BA,r6,a0,1,2,3,4,5,6,7,8,10,11,12,20,28,29,2A,2B,2C,2D,2E,2F,30,31,32,33,34,35,36,37,38,39,3A,3B,3C,3D,3E,m4,lsfw')
2013-04-24 16:23:09,688 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x96fd60c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2013-04-24 16:23:09,688 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x96fd60c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2013-04-24 16:23:09,688 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x96fd60c> about HardwareID('modalias', 'usb:v1D6Bp0002d0305dc09dsc00dp00ic09isc00ip00')
2013-04-24 16:23:09,688 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x96fd60c> about HardwareID('modalias', 'acpi:PNP0100:')
2013-04-24 16:23:09,688 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x96fd60c> about HardwareID('modalias', 'input:b0011v0002p0007e01B1-e0,1,3,k110,111,145,14A,14D,14E,ra0,1,18,1C,2F,35,36,39,mlsfw')
2013-04-24 16:23:09,688 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x96fd60c> about HardwareID('modalias', 'wmi:C16C47BA-50E3-444A-AF3A-B1C348380000')
2013-04-24 16:23:09,688 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x96fd60c> about HardwareID('modalias', 'pci:v00008086d00001E3Asv0000144Dsd0000C0D8bc07sc80i00')
2013-04-24 16:23:09,688 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x96fd60c> about HardwareID('modalias', 'wmi:C16C47BA-50E3-444A-AF3A-B1C348380001')
2013-04-24 16:23:09,688 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x96fd60c> about HardwareID('modalias', 'usb:v0C45pC35Ad0300dcEFdsc02dp01ic0Eisc01ip00')
2013-04-24 16:23:09,688 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x96fd60c> about HardwareID('modalias', 'pci:v00008086d00001E03sv0000144Dsd0000C0D8bc01sc06i01')
2013-04-24 16:23:09,688 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x96fd60c> about HardwareID('modalias', 'pci:v00008086d00001E22sv0000144Dsd0000C0D8bc0Csc05i00')
2013-04-24 16:23:09,688 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x96fd60c> about HardwareID('modalias', 'pci:v00008086d00001E31sv0000144Dsd0000C0D8bc0Csc03i30')
2013-04-24 16:23:09,688 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x96fd60c> about HardwareID('modalias', 'acpi:PNP0303:PNP030B:')
2013-04-24 16:23:09,688 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x96fd60c> about HardwareID('modalias', 'acpi:PNP0C04:')
2013-04-24 16:23:09,688 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x96fd60c> about HardwareID('modalias', 'acpi:PNP0C02:')
2013-04-24 16:23:09,688 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x96fd60c> about HardwareID('modalias', 'pci:v00008086d00001E26sv0000144Dsd0000C0D8bc0Csc03i20')
2013-04-24 16:23:09,688 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x96fd60c> about HardwareID('modalias', 'usb:v045Ep0745d0634dc00dsc00dp00ic03isc01ip02')
2013-04-24 16:23:09,688 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x96fd60c> about HardwareID('modalias', 'acpi:INT3F0D:PNP0C02:')
2013-04-24 16:23:09,688 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x96fd60c> about HardwareID('modalias', 'platform:microcode')
2013-04-24 16:23:09,689 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x96fd60c> about HardwareID('modalias', 'input:b0003v0C45pC35Ae0300-e0,1,kD4,ramlsfw')
2013-04-24 16:23:09,689 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x96fd60c> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8E,8F,94,95,96,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,C0,C1,CA,D9,E0,E1,E2,E3,EC,EE,ram4,l0,1,2,sfw')
2013-04-24 16:23:09,689 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x96fd60c> about HardwareID('modalias', 'usb:v0CF3p3004d0002dcE0dsc01dp01icE0isc01ip01')
2013-04-24 16:23:09,689 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x96fd60c> about HardwareID('modalias', 'input:b0003v045Ep0745e0111-e0,1,2,3,4,k71,72,73,74,77,80,82,83,85,86,87,88,89,8A,8B,8C,8E,90,96,98,9B,9C,9E,9F,A1,A3,A4,A5,A6,A7,A8,A9,AB,AC,AD,AE,B0,B1,B2,B5,B6,CE,CF,D0,D1,D2,D4,D8,D9,DB,DF,E4,E7,E8,E9,EA,EB,F1,100,110,111,112,113,114,161,162,166,16A,16E,172,174,176,178,179,17A,17B,17C,17D,17F,180,182,183,185,188,189,18C,18D,18E,18F,190,191,192,193,195,198,199,19A,1A0,1A1,1A2,1A3,1A4,1A5,1A6,1A7,1A8,1A9,1AA,1AB,1AC,1AD,1AE,1B0,1B1,1B7,1BA,r0,1,6,7,8,9,a20,m4,lsfw')
2013-04-24 16:23:09,689 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x96fd60c> about HardwareID('modalias', 'acpi:PNP0F03:PNP0F13:')
2013-04-24 16:23:09,689 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x96fd60c> about HardwareID('modalias', 'dmi:bvnAmericanMegatrendsInc.:bvrP03ABE:bd09/20/2012:svnSAMSUNGELECTRONICSCO.,LTD.:pn350V5C/350V5X/350V4C/350V4X/351V5C/351V5X/351V4C/351V4X/3540VC/3540VX/3440VC/3440VX:pvrP03ABE.006.CP:rvnSAMSUNGELECTRONICSCO.,LTD.:rnNP350V5C-S04PT:rvrBOARDREVISION00:cvnSAMSUNGELECTRONICSCO.,LTD.:ct9:cvr0.1:')
2013-04-24 16:23:09,689 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x96fd60c> about HardwareID('modalias', 'pci:v000010ECd00008168sv0000144Dsd0000C0D8bc02sc00i00')
2013-04-24 16:23:09,689 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x96fd60c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,8,')
2013-04-24 16:23:09,689 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x96fd60c> about HardwareID('modalias', 'usb:v1D6Bp0002d0305dc09dsc00dp01ic09isc00ip00')
2013-04-24 16:23:09,689 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x96fd60c> about HardwareID('modalias', 'usb:v045Ep0745d0634dc00dsc00dp00ic03isc00ip00')
2013-04-24 16:23:09,689 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x96fd60c> about HardwareID('modalias', 'pci:v00008086d00001E59sv0000144Dsd0000C0D8bc06sc01i00')
2013-04-24 16:23:09,689 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x96fd60c> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2013-04-24 16:23:09,689 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x96fd60c> about HardwareID('modalias', 'pci:v0000168Cd00000032sv0000144Dsd00004105bc02sc80i00')
2013-04-24 16:23:09,689 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x96fd60c> about HardwareID('modalias', 'acpi:PNP0C01:')
2013-04-24 16:23:09,689 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x96fd60c> about HardwareID('modalias', 'usb:v0C45pC35Ad0300dcEFdsc02dp01ic0Eisc02ip00')
2013-04-24 16:23:09,689 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x96fd60c> about HardwareID('modalias', 'pci:v00001002d00006840sv0000144Dsd0000C0D8bc03sc00i00')
2013-04-24 16:23:09,689 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x96fd60c> about HardwareID('modalias', 'acpi:PNP0200:')
2013-04-24 16:23:09,689 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x96fd60c> about HardwareID('modalias', 'acpi:INT0800:')
2013-04-24 16:23:09,689 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x96fd60c> about HardwareID('modalias', 'platform:eisa')
2013-04-24 16:23:09,689 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x96fd60c> about HardwareID('modalias', 'pci:v00008086d00000166sv0000144Dsd0000C0D8bc03sc00i00')
2013-04-24 16:23:09,689 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x96fd60c> about HardwareID('modalias', 'hid:b0003g0001v0000045Ep00000745')
2013-04-24 16:23:09,689 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x96fd60c> about HardwareID('modalias', 'usb:v045Ep0745d0634dc00dsc00dp00ic03isc01ip01')
2013-04-24 16:23:09,689 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x96fd60c> about HardwareID('modalias', 'acpi:PNP0000:')
2013-04-24 16:23:09,689 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x96fd60c> about HardwareID('modalias', 'platform:samsung')
2013-04-24 16:23:09,689 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x96fd60c> about HardwareID('modalias', 'platform:regulatory')
2013-04-24 16:23:09,690 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x96fd60c> about HardwareID('modalias', 'x86cpu:vendor:0000:family:0006:model:003A:feature:,0000,0001,0002,0003,0004,0005,0006,0007,0008,0009,000B,000C,000D,000E,000F,0010,0011,0013,0015,0016,0017,0018,0019,001A,001B,001C,001D,001F,0034,003B,003D,0066,0068,006B,006C,006D,0072,0076,0078,007C,0080,0081,0082,0083,0084,0085,0087,0088,0089,008D,008E,008F,0091,0093,0094,0095,0097,0098,0099,009A,009B,009C,009D,009E,00C0,00E0,00E1,00E3,00E4,00E5,00E6,00E7,0100,0101,0102,0103,0104,0120,0127,0129')
2013-04-24 16:23:09,690 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x96fd60c> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2013-04-24 16:23:09,690 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x96fd60c> about HardwareID('modalias', 'platform:coretemp')
2013-04-24 16:23:09,690 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x96fd60c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2013-04-24 16:23:09,690 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x96fd60c> about HardwareID('modalias', 'acpi:PNP0103:')
2013-04-24 16:23:09,690 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x96fd60c> about HardwareID('modalias', 'input:b0003v045Ep0745e0111-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,sfw')
2013-04-24 16:23:09,690 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x96fd60c> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2013-04-24 16:23:09,690 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x96fd60c> about HardwareID('modalias', 'acpi:INT340E:PNP0C02:')
2013-04-24 16:23:09,741 DEBUG: fglrx.enabled(fglrx_experimental_9): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2013-04-24 16:23:09,741 DEBUG: fglrx_experimental_9 is not the alternative in use
2013-04-24 16:23:09,763 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2013-04-24 16:23:09,763 DEBUG: fglrx_updates is not the alternative in use
2013-04-24 16:23:09,816 DEBUG: fglrx.enabled(fglrx_experimental_9): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2013-04-24 16:23:09,816 DEBUG: fglrx_experimental_9 is not the alternative in use
2013-04-24 16:23:09,831 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2013-04-24 16:23:09,831 DEBUG: fglrx_updates is not the alternative in use
2013-04-24 16:23:11,132 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2013-04-24 16:23:11,132 DEBUG: fglrx_updates is not the alternative in use
2013-04-24 16:23:12,253 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2013-04-24 16:23:12,253 DEBUG: fglrx_updates is not the alternative in use
2013-04-24 16:23:16,563 DEBUG: Installing package: linux-headers-generic
2013-04-24 16:23:17,447 DEBUG: install progress dpkg-exec 0.000000
2013-04-24 16:23:17,550 DEBUG: dpkg: error: dpkg status database is locked by another process
Error in function: 
SystemError: E:Sub-process /usr/bin/dpkg returned an error code (2)


2013-04-24 16:23:17,550 ERROR: Package failed to install:
dpkg: error: dpkg status database is locked by another process
Error in function: 
SystemError: E:Sub-process /usr/bin/dpkg returned an error code (2)


2013-04-24 16:23:17,648 DEBUG: Installing package: fglrx-updates
2013-04-24 16:23:17,906 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 0.000000
2013-04-24 16:23:17,907 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 0.000000
2013-04-24 16:23:17,912 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 0.000000
2013-04-24 16:23:17,918 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 0.000000
2013-04-24 16:23:17,946 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 0.004810
2013-04-24 16:23:18,049 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 0.138295
2013-04-24 16:23:18,058 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 0.140881
2013-04-24 16:23:18,268 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 0.304348
2013-04-24 16:23:18,273 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 0.306416
2013-04-24 16:23:18,774 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 0.448611
2013-04-24 16:23:19,275 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 0.686514
2013-04-24 16:23:19,776 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 0.908010
2013-04-24 16:23:20,277 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 1.072082
2013-04-24 16:23:20,778 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 1.195135
2013-04-24 16:23:21,278 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 1.299047
2013-04-24 16:23:21,779 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 1.361941
2013-04-24 16:23:22,280 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 1.405693
2013-04-24 16:23:22,781 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 1.446711
2013-04-24 16:23:23,282 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 1.536950
2013-04-24 16:23:23,783 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 1.599844
2013-04-24 16:23:24,284 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 1.711960
2013-04-24 16:23:24,785 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 1.870562
2013-04-24 16:23:25,287 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 2.045571
2013-04-24 16:23:25,788 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 2.196032
2013-04-24 16:23:26,289 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 2.332758
2013-04-24 16:23:26,790 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 2.447608
2013-04-24 16:23:27,291 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 2.614414
2013-04-24 16:23:27,792 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 2.775751
2013-04-24 16:23:28,293 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 2.972636
2013-04-24 16:23:28,794 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 3.172256
2013-04-24 16:23:29,294 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 3.265230
2013-04-24 16:23:29,795 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 3.401956
2013-04-24 16:23:30,296 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 3.533213
2013-04-24 16:23:30,797 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 3.637125
2013-04-24 16:23:31,298 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 3.771116
2013-04-24 16:23:31,799 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 3.880497
2013-04-24 16:23:32,300 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 3.888701
2013-04-24 16:23:32,801 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 3.888701
2013-04-24 16:23:33,302 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 3.888701
2013-04-24 16:23:33,803 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 3.888701
2013-04-24 16:23:34,304 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 3.981674
2013-04-24 16:23:34,805 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 4.080117
2013-04-24 16:23:35,307 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 4.159418
2013-04-24 16:23:35,808 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 4.312552
2013-04-24 16:23:36,309 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 4.501234
2013-04-24 16:23:36,810 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 4.673508
2013-04-24 16:23:37,311 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 4.777420
2013-04-24 16:23:37,812 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 5.064545
2013-04-24 16:23:38,314 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 5.324324
2013-04-24 16:23:38,815 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 5.422767
2013-04-24 16:23:39,316 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 5.668874
2013-04-24 16:23:39,817 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 5.698954
2013-04-24 16:23:40,318 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 5.772786
2013-04-24 16:23:40,819 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 5.852087
2013-04-24 16:23:41,319 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 5.947795
2013-04-24 16:23:41,820 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 5.947795
2013-04-24 16:23:42,321 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 5.947795
2013-04-24 16:23:42,822 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 6.076318
2013-04-24 16:23:43,323 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 6.218513
2013-04-24 16:23:43,824 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 6.221247
2013-04-24 16:23:44,324 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 6.221247
2013-04-24 16:23:44,825 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 6.352504
2013-04-24 16:23:45,326 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 6.440009
2013-04-24 16:23:45,827 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 6.481027
2013-04-24 16:23:46,328 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 6.481027
2013-04-24 16:23:46,829 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 6.481027
2013-04-24 16:23:47,329 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 6.481027
2013-04-24 16:23:47,830 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 6.481027
2013-04-24 16:23:48,331 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 6.481027
2013-04-24 16:23:48,832 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 6.481027
2013-04-24 16:23:49,333 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 6.481027
2013-04-24 16:23:49,834 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 6.481027
2013-04-24 16:23:50,335 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 6.481027
2013-04-24 16:23:50,835 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 6.541186
2013-04-24 16:23:51,336 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 6.810982
2013-04-24 16:23:51,837 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 7.128187
2013-04-24 16:23:52,338 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 7.456329
2013-04-24 16:23:52,839 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 7.781737
2013-04-24 16:23:53,340 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 8.066128
2013-04-24 16:23:53,841 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 8.306766
2013-04-24 16:23:54,342 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 8.514589
2013-04-24 16:23:54,843 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 8.757962
2013-04-24 16:23:55,344 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 9.050555
2013-04-24 16:23:55,846 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 9.370494
2013-04-24 16:23:56,347 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 9.708880
2013-04-24 16:23:56,848 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 10.020615
2013-04-24 16:23:57,349 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 10.337820
2013-04-24 16:23:57,850 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 10.630414
2013-04-24 16:23:58,352 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 10.923007
2013-04-24 16:23:58,853 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 11.228821
2013-04-24 16:23:59,354 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 11.502273
2013-04-24 16:23:59,855 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 11.742306
2013-04-24 16:24:00,356 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 11.990619
2013-04-24 16:24:00,857 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 12.236726
2013-04-24 16:24:01,358 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 12.488302
2013-04-24 16:24:01,859 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 12.759019
2013-04-24 16:24:02,360 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 12.999657
2013-04-24 16:24:02,861 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 13.317406
2013-04-24 16:24:03,363 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 13.591658
2013-04-24 16:24:03,864 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 13.832296
2013-04-24 16:24:04,364 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 14.067465
2013-04-24 16:24:04,866 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 14.275289
2013-04-24 16:24:05,367 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 14.275289
2013-04-24 16:24:05,868 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 14.768424
2013-04-24 16:24:06,369 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 15.014471
2013-04-24 16:24:06,870 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 15.320737
2013-04-24 16:24:07,371 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 15.550437
2013-04-24 16:24:07,872 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 15.843031
2013-04-24 16:24:08,373 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 16.086403
2013-04-24 16:24:08,874 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 16.182111
2013-04-24 16:24:09,375 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 16.381731
2013-04-24 16:24:09,876 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 16.584086
2013-04-24 16:24:10,376 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 16.827458
2013-04-24 16:24:10,878 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 17.068096
2013-04-24 16:24:11,378 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 17.273185
2013-04-24 16:24:11,879 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 17.489212
2013-04-24 16:24:12,380 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 17.754461
2013-04-24 16:24:12,881 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 18.019710
2013-04-24 16:24:13,382 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 18.301365
2013-04-24 16:24:13,883 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 18.588490
2013-04-24 16:24:14,384 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 18.872880
2013-04-24 16:24:14,885 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 19.118987
2013-04-24 16:24:15,386 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 19.370563
2013-04-24 16:24:15,887 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 19.521989
2013-04-24 16:24:16,388 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 19.655210
2013-04-24 16:24:16,889 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 19.780998
2013-04-24 16:24:17,391 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 19.875467
2013-04-24 16:24:17,892 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 19.941096
2013-04-24 16:24:18,393 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 20.006725
2013-04-24 16:24:18,894 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 20.088760
2013-04-24 16:24:19,395 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 20.154389
2013-04-24 16:24:19,896 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 20.285646
2013-04-24 16:24:20,397 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 20.433310
2013-04-24 16:24:20,898 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 20.523549
2013-04-24 16:24:21,400 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 20.556363
2013-04-24 16:24:21,901 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 20.586443
2013-04-24 16:24:22,402 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 20.678133
2013-04-24 16:24:22,903 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 20.852371
2013-04-24 16:24:23,404 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 21.048018
2013-04-24 16:24:23,905 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 21.173806
2013-04-24 16:24:24,406 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 21.272249
2013-04-24 16:24:24,908 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 21.439055
2013-04-24 16:24:25,408 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 21.592188
2013-04-24 16:24:25,909 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 21.702385
2013-04-24 16:24:26,411 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 21.848341
2013-04-24 16:24:26,912 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 21.996006
2013-04-24 16:24:27,413 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 22.106414
2013-04-24 16:24:27,914 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 22.106414
2013-04-24 16:24:28,415 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 22.106414
2013-04-24 16:24:28,916 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 22.106414
2013-04-24 16:24:29,417 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 22.554875
2013-04-24 16:24:29,925 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 22.579486
2013-04-24 16:24:30,426 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 22.715623
2013-04-24 16:24:30,927 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 22.806572
2013-04-24 16:24:31,429 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 22.847590
2013-04-24 16:24:31,930 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 22.847590
2013-04-24 16:24:32,431 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 22.847590
2013-04-24 16:24:32,932 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 22.847590
2013-04-24 16:24:33,433 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 22.847590
2013-04-24 16:24:33,934 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 22.847590
2013-04-24 16:24:34,435 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 23.222219
2013-04-24 16:24:34,936 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 23.375353
2013-04-24 16:24:35,437 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 23.408167
2013-04-24 16:24:35,938 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 23.506610
2013-04-24 16:24:36,439 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 23.657008
2013-04-24 16:24:36,940 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 23.676150
2013-04-24 16:24:37,442 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 23.681619
2013-04-24 16:24:37,943 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 23.791000
2013-04-24 16:24:38,444 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 23.949602
2013-04-24 16:24:38,945 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 23.952337
2013-04-24 16:24:39,446 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 23.960540
2013-04-24 16:24:39,947 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 23.963275
2013-04-24 16:24:40,448 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 24.075390
2013-04-24 16:24:40,949 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 24.231258
2013-04-24 16:24:41,450 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 24.247665
2013-04-24 16:24:41,951 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 24.247665
2013-04-24 16:24:42,452 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 24.406267
2013-04-24 16:24:42,953 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 24.477365
2013-04-24 16:24:43,454 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 24.540259
2013-04-24 16:24:43,955 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 24.545728
2013-04-24 16:24:44,456 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 24.553931
2013-04-24 16:24:44,957 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 24.553931
2013-04-24 16:24:45,458 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 24.718002
2013-04-24 16:24:45,959 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 24.893012
2013-04-24 16:24:46,460 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 24.934030
2013-04-24 16:24:46,961 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 24.939499
2013-04-24 16:24:47,462 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 25.111774
2013-04-24 16:24:47,963 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 25.363350
2013-04-24 16:24:48,464 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 25.363350
2013-04-24 16:24:48,965 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 25.428978
2013-04-24 16:24:49,466 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 25.519217
2013-04-24 16:24:49,967 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 25.792669
2013-04-24 16:24:50,468 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 25.798138
2013-04-24 16:24:50,970 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 25.798138
2013-04-24 16:24:51,471 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 25.798138
2013-04-24 16:24:51,972 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 25.897140
2013-04-24 16:24:52,473 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 25.905344
2013-04-24 16:24:52,974 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 25.905344
2013-04-24 16:24:53,475 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 25.905344
2013-04-24 16:24:53,976 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 26.450012
2013-04-24 16:24:54,477 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 26.562127
2013-04-24 16:24:54,978 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 26.930064
2013-04-24 16:24:55,479 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 27.236330
2013-04-24 16:24:55,980 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 27.534393
2013-04-24 16:24:56,481 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 27.805111
2013-04-24 16:24:56,983 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 28.056687
2013-04-24 16:24:57,484 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 28.406705
2013-04-24 16:24:57,985 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 28.752993
2013-04-24 16:24:58,486 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 29.152233
2013-04-24 16:24:58,987 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 29.406543
2013-04-24 16:24:59,488 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 29.742889
2013-04-24 16:24:59,989 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 30.172209
2013-04-24 16:25:00,490 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 30.519493
2013-04-24 16:25:00,991 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 30.853105
2013-04-24 16:25:01,492 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 31.200389
2013-04-24 16:25:01,994 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 31.523063
2013-04-24 16:25:02,495 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 31.840267
2013-04-24 16:25:02,996 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 32.182082
2013-04-24 16:25:03,497 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 32.502021
2013-04-24 16:25:03,998 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 32.835633
2013-04-24 16:25:04,499 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 33.182932
2013-04-24 16:25:05,001 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 33.494849
2013-04-24 16:25:05,502 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 33.792534
2013-04-24 16:25:06,003 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 34.016855
2013-04-24 16:25:06,504 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 34.276257
2013-04-24 16:25:07,005 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 34.519252
2013-04-24 16:25:07,506 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 34.737636
2013-04-24 16:25:08,007 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 34.994303
2013-04-24 16:25:08,508 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 35.190343
2013-04-24 16:25:09,009 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 35.375444
2013-04-24 16:25:09,511 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 35.634378
2013-04-24 16:25:10,012 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 35.890577
2013-04-24 16:25:10,512 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 36.192794
2013-04-24 16:25:11,013 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 36.463512
2013-04-24 16:25:11,514 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 36.731495
2013-04-24 16:25:12,015 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 36.992800
2013-04-24 16:25:12,516 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 37.264938
2013-04-24 16:25:13,017 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 37.547168
2013-04-24 16:25:13,519 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 37.769057
2013-04-24 16:25:14,020 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 37.922190
2013-04-24 16:25:14,521 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 37.922190
2013-04-24 16:25:15,022 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 38.474760
2013-04-24 16:25:15,523 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 38.684245
2013-04-24 16:25:16,024 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 38.758077
2013-04-24 16:25:16,525 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 39.209273
2013-04-24 16:25:17,026 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 39.479991
2013-04-24 16:25:17,527 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 39.712425
2013-04-24 16:25:18,028 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 39.980408
2013-04-24 16:25:18,530 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 40.300347
2013-04-24 16:25:19,031 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 40.625755
2013-04-24 16:25:19,532 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 40.910145
2013-04-24 16:25:20,033 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 41.227350
2013-04-24 16:25:20,534 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 41.476191
2013-04-24 16:25:21,035 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 41.741440
2013-04-24 16:25:21,536 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 41.960202
2013-04-24 16:25:22,037 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 42.222716
2013-04-24 16:25:22,538 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 42.446946
2013-04-24 16:25:23,039 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 42.605549
2013-04-24 16:25:23,540 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 42.630159
2013-04-24 16:25:24,041 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 42.630159
2013-04-24 16:25:24,542 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 43.073152
2013-04-24 16:25:25,043 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 43.073152
2013-04-24 16:25:25,544 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 43.494268
2013-04-24 16:25:26,046 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 43.587242
2013-04-24 16:25:26,547 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 43.885305
2013-04-24 16:25:27,047 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 44.175164
2013-04-24 16:25:27,548 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 44.514244
2013-04-24 16:25:28,049 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 44.746679
2013-04-24 16:25:28,550 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 45.072087
2013-04-24 16:25:29,051 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 45.419371
2013-04-24 16:25:29,552 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 45.750248
2013-04-24 16:25:30,053 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 45.971744
2013-04-24 16:25:30,555 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 46.144019
2013-04-24 16:25:31,056 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 46.409268
2013-04-24 16:25:31,557 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 46.805773
2013-04-24 16:25:32,058 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 47.194075
2013-04-24 16:25:32,559 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 47.656209
2013-04-24 16:25:33,060 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 48.003494
2013-04-24 16:25:33,561 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 48.298822
2013-04-24 16:25:34,063 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 48.700796
2013-04-24 16:25:34,564 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 49.089098
2013-04-24 16:25:35,065 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 49.335205
2013-04-24 16:25:35,565 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 49.556702
2013-04-24 16:25:36,066 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 49.838357
2013-04-24 16:25:36,567 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 50.212987
2013-04-24 16:25:37,068 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 50.576678
2013-04-24 16:25:37,569 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 50.957064
2013-04-24 16:25:38,070 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 51.272954
2013-04-24 16:25:38,570 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 51.563765
2013-04-24 16:25:39,071 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 51.953034
2013-04-24 16:25:39,572 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 52.297598
2013-04-24 16:25:40,073 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 52.494031
2013-04-24 16:25:40,574 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 52.739684
2013-04-24 16:25:41,074 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 52.931101
2013-04-24 16:25:41,575 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 53.297013
2013-04-24 16:25:42,076 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 53.658846
2013-04-24 16:25:42,577 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 53.711391
2013-04-24 16:25:43,349 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 54.591137
2013-04-24 16:25:43,850 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 55.071657
2013-04-24 16:25:44,351 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 55.462406
2013-04-24 16:25:44,852 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 55.771256
2013-04-24 16:25:45,353 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 56.171297
2013-04-24 16:25:45,854 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 56.630500
2013-04-24 16:25:46,355 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 56.824651
2013-04-24 16:25:46,856 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 57.236098
2013-04-24 16:25:47,358 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 57.599593
2013-04-24 16:25:47,859 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 58.032448
2013-04-24 16:25:48,360 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 58.453897
2013-04-24 16:25:48,861 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 58.855267
2013-04-24 16:25:49,362 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 59.172336
2013-04-24 16:25:49,863 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 59.467060
2013-04-24 16:25:50,364 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 59.767857
2013-04-24 16:25:50,865 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 60.139858
2013-04-24 16:25:51,366 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 60.544446
2013-04-24 16:25:51,867 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 60.906113
2013-04-24 16:25:52,368 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 61.095279
2013-04-24 16:25:52,869 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 61.286695
2013-04-24 16:25:53,370 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 61.591738
2013-04-24 16:25:53,872 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 61.901071
2013-04-24 16:25:54,373 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 62.209860
2013-04-24 16:25:54,874 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 62.470350
2013-04-24 16:25:55,375 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 62.752262
2013-04-24 16:25:55,876 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 63.005183
2013-04-24 16:25:56,377 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 63.172699
2013-04-24 16:25:56,878 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 63.172699
2013-04-24 16:25:57,379 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 63.172699
2013-04-24 16:25:57,881 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 63.172699
2013-04-24 16:25:58,382 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 63.172699
2013-04-24 16:25:58,883 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 63.172699
2013-04-24 16:25:59,384 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 64.180529
2013-04-24 16:25:59,885 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 64.180529
2013-04-24 16:26:00,386 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 64.180529
2013-04-24 16:26:00,887 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 64.180529
2013-04-24 16:26:01,388 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 64.180529
2013-04-24 16:26:01,889 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 64.180529
2013-04-24 16:26:02,390 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 64.180529
2013-04-24 16:26:02,891 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 64.470388
2013-04-24 16:26:03,392 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 64.738371
2013-04-24 16:26:03,893 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 64.916115
2013-04-24 16:26:04,394 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 65.091124
2013-04-24 16:26:04,895 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 65.211443
2013-04-24 16:26:05,397 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 65.422001
2013-04-24 16:26:05,898 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 65.799365
2013-04-24 16:26:06,399 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 66.067348
2013-04-24 16:26:06,900 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 66.283375
2013-04-24 16:26:07,401 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 66.608783
2013-04-24 16:26:07,902 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 66.999820
2013-04-24 16:26:08,403 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 67.420936
2013-04-24 16:26:08,904 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 67.874867
2013-04-24 16:26:09,405 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 68.432709
2013-04-24 16:26:09,906 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 68.930392
2013-04-24 16:26:10,407 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 69.573005
2013-04-24 16:26:10,908 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 70.273042
2013-04-24 16:26:11,409 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 70.910185
2013-04-24 16:26:11,910 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 71.571940
2013-04-24 16:26:12,411 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 72.250101
2013-04-24 16:26:12,913 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 72.838023
2013-04-24 16:26:13,414 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 73.409538
2013-04-24 16:26:13,915 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 73.819716
2013-04-24 16:26:14,416 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 73.929580
2013-04-24 16:26:14,917 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 74.356815
2013-04-24 16:26:15,419 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 75.122481
2013-04-24 16:26:15,920 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 75.228161
2013-04-24 16:26:16,421 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 75.228161
2013-04-24 16:26:16,922 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 75.941584
2013-04-24 16:26:17,423 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 76.209567
2013-04-24 16:26:17,924 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 76.368169
2013-04-24 16:26:18,425 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 76.617449
2013-04-24 16:26:18,926 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 76.798637
2013-04-24 16:26:19,427 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 77.348276
2013-04-24 16:26:19,929 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 77.665480
2013-04-24 16:26:20,429 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 77.769392
2013-04-24 16:26:20,931 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 78.045579
2013-04-24 16:26:21,432 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 78.395597
2013-04-24 16:26:21,933 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 78.783899
2013-04-24 16:26:22,434 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 79.136653
2013-04-24 16:26:22,936 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 79.738247
2013-04-24 16:26:23,437 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 80.514851
2013-04-24 16:26:23,938 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 81.067225
2013-04-24 16:26:24,439 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 81.794607
2013-04-24 16:26:24,940 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 82.418078
2013-04-24 16:26:25,441 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 83.082567
2013-04-24 16:26:25,942 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 83.615799
2013-04-24 16:26:26,443 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 84.362323
2013-04-24 16:26:26,945 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 84.786174
2013-04-24 16:26:27,446 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 85.182679
2013-04-24 16:26:27,947 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 85.666690
2013-04-24 16:26:28,448 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 85.983894
2013-04-24 16:26:28,949 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 86.503453
2013-04-24 16:26:29,450 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 87.014808
2013-04-24 16:26:29,951 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 87.504288
2013-04-24 16:26:30,453 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 87.960953
2013-04-24 16:26:30,954 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 88.371131
2013-04-24 16:26:31,455 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 88.934442
2013-04-24 16:26:31,786 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 89.217769
2013-04-24 16:26:31,786 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 89.223641
2013-04-24 16:26:32,287 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 89.825235
2013-04-24 16:26:32,788 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 90.413157
2013-04-24 16:26:33,289 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 90.888964
2013-04-24 16:26:33,790 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 91.476886
2013-04-24 16:26:34,291 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 91.963631
2013-04-24 16:26:34,792 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 92.439438
2013-04-24 16:26:35,293 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 92.637205
2013-04-24 16:26:35,794 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 92.637205
2013-04-24 16:26:36,295 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 93.557772
2013-04-24 16:26:36,796 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 93.954927
2013-04-24 16:26:37,298 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 93.954927
2013-04-24 16:26:37,799 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 94.342625
2013-04-24 16:26:38,300 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 95.033688
2013-04-24 16:26:38,801 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 95.263388
2013-04-24 16:26:39,302 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 95.703646
2013-04-24 16:26:39,803 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 96.031789
2013-04-24 16:26:40,304 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 96.559551
2013-04-24 16:26:40,805 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 97.202164
2013-04-24 16:26:41,306 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 97.672501
2013-04-24 16:26:41,808 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 98.093618
2013-04-24 16:26:42,309 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 98.692478
2013-04-24 16:26:42,810 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 99.318683
2013-04-24 16:26:43,311 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 99.873791
2013-04-24 16:26:43,402 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12326L> 100.000000
2013-04-24 16:26:45,515 DEBUG: install progress dpkg-exec 0.000000
2013-04-24 16:26:45,619 DEBUG: dpkg: error: dpkg status database is locked by another process
Error in function: 
SystemError: E:Sub-process /usr/bin/dpkg returned an error code (2)


2013-04-24 16:26:45,619 ERROR: Package failed to install:
dpkg: error: dpkg status database is locked by another process
Error in function: 
SystemError: E:Sub-process /usr/bin/dpkg returned an error code (2)


2013-04-24 16:26:46,007 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates


2013-04-24 16:26:46,008 WARNING: /sys/module/fglrx_updates/drivers does not exist, cannot rebind fglrx_updates driver
2013-04-24 16:26:46,008 ERROR: XorgDriverHandler.enable(): package or module not installed, aborting
2013-04-24 16:26:46,013 ERROR: xorg:fglrx_updates: get_alternative_by_name(fglrx-updates) returned nothing
2013-04-24 16:26:46,155 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2013-04-24 16:26:46,155 DEBUG: fglrx_updates is not the alternative in use
2013-04-24 16:33:39,708 DEBUG: fglrx.enabled(fglrx_experimental_9): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2013-04-24 16:33:39,708 DEBUG: fglrx_experimental_9 is not the alternative in use
2013-04-24 16:33:39,741 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2013-04-24 16:33:39,741 DEBUG: fglrx_updates is not the alternative in use
2013-04-24 16:33:39,783 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2013-04-24 16:33:39,783 DEBUG: fglrx_updates is not the alternative in use
2013-04-24 16:33:39,842 DEBUG: fglrx.enabled(fglrx_experimental_9): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2013-04-24 16:33:39,843 DEBUG: fglrx_experimental_9 is not the alternative in use
2013-04-24 16:33:39,870 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2013-04-24 16:33:39,870 DEBUG: fglrx_updates is not the alternative in use
2013-04-24 16:33:41,983 DEBUG: Shutting down
2013-04-24 16:55:58,944 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x85a7a0c>
2013-04-24 16:55:59,965 DEBUG: reading modalias file /lib/modules/3.5.0-23-generic/modules.alias
2013-04-24 16:56:00,024 DEBUG: reading modalias file /usr/share/jockey/modaliases/b43
2013-04-24 16:56:00,024 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2013-04-24 16:56:00,053 DEBUG: loading custom handler /usr/share/jockey/handlers/cdv.py
2013-04-24 16:56:00,056 WARNING: modinfo for module cedarview_gfx failed: ERROR: modinfo: could not find module cedarview_gfx


2013-04-24 16:56:00,056 DEBUG: Instantiated Handler subclass __builtin__.CdvDriver from name CdvDriver
2013-04-24 16:56:00,056 DEBUG: cdv.available: falling back to default
2013-04-24 16:56:00,638 DEBUG: XorgDriverHandler(cedarview_gfx, cedarview-graphics-drivers, None): Disabling as package is not compatible with Q-LTS X.org
2013-04-24 16:56:00,638 DEBUG: Intel Cedarview graphics driver not available
2013-04-24 16:56:00,638 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2013-04-24 16:56:00,693 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl


2013-04-24 16:56:00,701 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2013-04-24 16:56:00,702 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2013-04-24 16:56:00,702 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2013-04-24 16:56:00,812 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates


2013-04-24 16:56:00,814 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriverUpdate from name FglrxDriverUpdate
2013-04-24 16:56:00,814 DEBUG: fglrx.available: falling back to default
2013-04-24 16:56:00,965 DEBUG: ATI/AMD proprietary FGLRX graphics driver (post-release updates) availability undetermined, adding to pool
2013-04-24 16:56:00,967 WARNING: modinfo for module fglrx_experimental_9 failed: ERROR: modinfo: could not find module fglrx_experimental_9


2013-04-24 16:56:00,976 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriverExperimental9 from name FglrxDriverExperimental9
2013-04-24 16:56:00,976 DEBUG: fglrx.available: falling back to default
2013-04-24 16:56:01,093 DEBUG: ATI/AMD proprietary FGLRX graphics driver (**experimental** beta) availability undetermined, adding to pool
2013-04-24 16:56:01,094 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx


2013-04-24 16:56:01,096 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2013-04-24 16:56:01,096 DEBUG: fglrx.available: falling back to default
2013-04-24 16:56:01,213 DEBUG: XorgDriverHandler(fglrx, fglrx, None): Disabling as package is not compatible with Q-LTS X.org
2013-04-24 16:56:01,213 DEBUG: ATI/AMD proprietary FGLRX graphics driver not available
2013-04-24 16:56:01,213 DEBUG: loading custom handler /usr/share/jockey/handlers/pvr-omap4.py
2013-04-24 16:56:01,216 WARNING: modinfo for module omapdrm_pvr failed: ERROR: modinfo: could not find module omapdrm_pvr


2013-04-24 16:56:01,218 DEBUG: Instantiated Handler subclass __builtin__.PVROmap4Driver from name PVROmap4Driver
2013-04-24 16:56:01,328 DEBUG: XorgDriverHandler(omapdrm_pvr, pvr-omap4, None): Disabling as package is not compatible with Q-LTS X.org
2013-04-24 16:56:01,328 DEBUG: PowerVR SGX proprietary graphics driver for OMAP 4 not available
2013-04-24 16:56:01,329 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2013-04-24 16:56:01,332 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96


2013-04-24 16:56:01,334 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2013-04-24 16:56:01,354 DEBUG: Disabling Nvidia driver on intel/hybrid system
2013-04-24 16:56:01,354 DEBUG: NVIDIA accelerated graphics driver not available
2013-04-24 16:56:01,356 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current


2013-04-24 16:56:01,358 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2013-04-24 16:56:01,358 DEBUG: Disabling Nvidia driver on intel/hybrid system
2013-04-24 16:56:01,358 DEBUG: NVIDIA accelerated graphics driver not available
2013-04-24 16:56:01,360 WARNING: modinfo for module nvidia_current_updates failed: ERROR: modinfo: could not find module nvidia_current_updates


2013-04-24 16:56:01,361 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrentUpdates from name NvidiaDriverCurrentUpdates
2013-04-24 16:56:01,362 DEBUG: Disabling Nvidia driver on intel/hybrid system
2013-04-24 16:56:01,362 DEBUG: NVIDIA accelerated graphics driver (post-release updates) not available
2013-04-24 16:56:01,364 WARNING: modinfo for module nvidia_96_updates failed: ERROR: modinfo: could not find module nvidia_96_updates


2013-04-24 16:56:01,365 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96Updates from name NvidiaDriver96Updates
2013-04-24 16:56:01,366 DEBUG: Disabling Nvidia driver on intel/hybrid system
2013-04-24 16:56:01,366 DEBUG: NVIDIA accelerated graphics driver (post-release updates) not available
2013-04-24 16:56:01,367 WARNING: modinfo for module nvidia_173_updates failed: ERROR: modinfo: could not find module nvidia_173_updates


2013-04-24 16:56:01,369 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173Updates from name NvidiaDriver173Updates
2013-04-24 16:56:01,370 DEBUG: Disabling Nvidia driver on intel/hybrid system
2013-04-24 16:56:01,370 DEBUG: NVIDIA accelerated graphics driver (post-release updates) not available
2013-04-24 16:56:01,371 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173


2013-04-24 16:56:01,373 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2013-04-24 16:56:01,374 DEBUG: Disabling Nvidia driver on intel/hybrid system
2013-04-24 16:56:01,374 DEBUG: NVIDIA accelerated graphics driver not available
2013-04-24 16:56:01,375 WARNING: modinfo for module nvidia_experimental_310 failed: ERROR: modinfo: could not find module nvidia_experimental_310


2013-04-24 16:56:01,385 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverExperimental310 from name NvidiaDriverExperimental310
2013-04-24 16:56:01,385 DEBUG: Disabling Nvidia driver on intel/hybrid system
2013-04-24 16:56:01,385 DEBUG: NVIDIA accelerated graphics driver (**experimental** beta) not available
2013-04-24 16:56:01,387 WARNING: modinfo for module nvidia_experimental_304 failed: ERROR: modinfo: could not find module nvidia_experimental_304


2013-04-24 16:56:01,396 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverExperimental304 from name NvidiaDriverExperimental304
2013-04-24 16:56:01,397 DEBUG: Disabling Nvidia driver on intel/hybrid system
2013-04-24 16:56:01,397 DEBUG: NVIDIA accelerated graphics driver (**experimental** beta) not available
2013-04-24 16:56:01,397 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2013-04-24 16:56:01,406 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2013-04-24 16:56:01,410 DEBUG: Software modem not available
2013-04-24 16:56:01,411 DEBUG: loading custom handler /usr/share/jockey/handlers/vmware-client.py
2013-04-24 16:56:01,413 WARNING: modinfo for module vmxnet failed: ERROR: modinfo: could not find module vmxnet


2013-04-24 16:56:01,413 DEBUG: Instantiated Handler subclass __builtin__.VmwareClientHandler from name VmwareClientHandler
2013-04-24 16:56:01,420 DEBUG: VMWare Client Tools availability undetermined, adding to pool
2013-04-24 16:56:01,420 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2013-04-24 16:56:01,431 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2013-04-24 16:56:01,432 DEBUG: Firmware for DVB cards not available
2013-04-24 16:56:01,432 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2013-04-24 16:56:01,434 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci


2013-04-24 16:56:01,434 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2013-04-24 16:56:01,434 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2013-04-24 16:56:01,434 DEBUG: all custom handlers loaded
2013-04-24 16:56:01,434 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x85a7a0c> about HardwareID('modalias', 'pci:v00008086d00000154sv0000144Dsd0000C0D8bc06sc00i00')
2013-04-24 16:56:01,622 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x85a7a0c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2013-04-24 16:56:01,624 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-04-24 16:56:01,675 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-04-24 16:56:01,675 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x85a7a0c> about HardwareID('modalias', 'acpi:PNP0B00:')
2013-04-24 16:56:01,675 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x85a7a0c> about HardwareID('modalias', 'pci:v00008086d00001E20sv0000144Dsd0000C0D8bc04sc03i00')
2013-04-24 16:56:01,677 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2013-04-24 16:56:01,677 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2013-04-24 16:56:01,677 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2013-04-24 16:56:01,677 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2013-04-24 16:56:01,677 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x85a7a0c> about HardwareID('modalias', 'pci:v00008086d00001E2Dsv0000144Dsd0000C0D8bc0Csc03i20')
2013-04-24 16:56:01,679 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x85a7a0c> about HardwareID('modalias', 'platform:pcspkr')
2013-04-24 16:56:01,679 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr'}
2013-04-24 16:56:01,680 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2013-04-24 16:56:01,680 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp'}
2013-04-24 16:56:01,680 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2013-04-24 16:56:01,680 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x85a7a0c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2013-04-24 16:56:01,680 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-04-24 16:56:01,680 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-04-24 16:56:01,680 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x85a7a0c> about HardwareID('modalias', 'usb:v1D6Bp0003d0305dc09dsc00dp03ic09isc00ip00')
2013-04-24 16:56:01,688 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x85a7a0c> about HardwareID('modalias', 'usb:v8087p0024d0000dc09dsc00dp01ic09isc00ip00')
2013-04-24 16:56:01,689 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x85a7a0c> about HardwareID('modalias', 'input:b0003v045Ep0745e0111-e0,1,2,3,4,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,8B,8C,8E,8F,90,94,96,98,9B,9C,9E,9F,A1,A3,A4,A5,A6,A7,A8,A9,AB,AC,AD,AE,B0,B1,B2,B3,B4,B5,B6,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,CE,CF,D0,D1,D2,D4,D8,D9,DB,DF,E4,E7,E8,E9,EA,EB,F0,F1,100,13A,13B,161,162,164,166,16A,16E,172,174,176,178,179,17A,17B,17C,17D,17F,180,182,183,185,188,189,18C,18D,18E,18F,190,191,192,193,195,198,199,19A,1A0,1A1,1A2,1A3,1A4,1A5,1A6,1A7,1A8,1A9,1AA,1AB,1AC,1AD,1AE,1B0,1B1,1B6,1B7,1BA,r6,a0,1,2,3,4,5,6,7,8,10,11,12,20,28,29,2A,2B,2C,2D,2E,2F,30,31,32,33,34,35,36,37,38,39,3A,3B,3C,3D,3E,m4,lsfw')
2013-04-24 16:56:01,689 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-04-24 16:56:01,689 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-04-24 16:56:01,689 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2013-04-24 16:56:01,689 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2013-04-24 16:56:01,689 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2013-04-24 16:56:01,689 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2013-04-24 16:56:01,689 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2013-04-24 16:56:01,689 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2013-04-24 16:56:01,689 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-04-24 16:56:01,689 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-04-24 16:56:01,689 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x85a7a0c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2013-04-24 16:56:01,690 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x85a7a0c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2013-04-24 16:56:01,690 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x85a7a0c> about HardwareID('modalias', 'usb:v1D6Bp0002d0305dc09dsc00dp00ic09isc00ip00')
2013-04-24 16:56:01,690 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x85a7a0c> about HardwareID('modalias', 'acpi:PNP0100:')
2013-04-24 16:56:01,690 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x85a7a0c> about HardwareID('modalias', 'input:b0011v0002p0007e01B1-e0,1,3,k110,111,145,14A,14D,14E,ra0,1,18,1C,2F,35,36,39,mlsfw')
2013-04-24 16:56:01,690 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-04-24 16:56:01,690 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-04-24 16:56:01,690 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2013-04-24 16:56:01,690 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2013-04-24 16:56:01,690 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2013-04-24 16:56:01,690 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2013-04-24 16:56:01,690 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2013-04-24 16:56:01,690 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2013-04-24 16:56:01,691 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-04-24 16:56:01,691 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-04-24 16:56:01,691 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x85a7a0c> about HardwareID('modalias', 'wmi:C16C47BA-50E3-444A-AF3A-B1C348380000')
2013-04-24 16:56:01,691 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x85a7a0c> about HardwareID('modalias', 'pci:v00008086d00001E3Asv0000144Dsd0000C0D8bc07sc80i00')
2013-04-24 16:56:01,693 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mei'}
2013-04-24 16:56:01,693 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mei', 'jockey_handler': 'KernelModuleHandler'}
2013-04-24 16:56:01,693 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x85a7a0c> about HardwareID('modalias', 'wmi:C16C47BA-50E3-444A-AF3A-B1C348380001')
2013-04-24 16:56:01,693 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x85a7a0c> about HardwareID('modalias', 'usb:v0C45pC35Ad0300dcEFdsc02dp01ic0Eisc01ip00')
2013-04-24 16:56:01,710 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo'}
2013-04-24 16:56:01,711 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo', 'jockey_handler': 'KernelModuleHandler'}
2013-04-24 16:56:01,711 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x85a7a0c> about HardwareID('modalias', 'pci:v00008086d00001E03sv0000144Dsd0000C0D8bc01sc06i01')
2013-04-24 16:56:01,713 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x85a7a0c> about HardwareID('modalias', 'pci:v00008086d00001E22sv0000144Dsd0000C0D8bc0Csc05i00')
2013-04-24 16:56:01,714 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801'}
2013-04-24 16:56:01,714 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801', 'jockey_handler': 'KernelModuleHandler'}
2013-04-24 16:56:01,714 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x85a7a0c> about HardwareID('modalias', 'pci:v00008086d00001E31sv0000144Dsd0000C0D8bc0Csc03i30')
2013-04-24 16:56:01,716 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x85a7a0c> about HardwareID('modalias', 'acpi:PNP0303:PNP030B:')
2013-04-24 16:56:01,716 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x85a7a0c> about HardwareID('modalias', 'acpi:PNP0C04:')
2013-04-24 16:56:01,716 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x85a7a0c> about HardwareID('modalias', 'acpi:PNP0C02:')
2013-04-24 16:56:01,716 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x85a7a0c> about HardwareID('modalias', 'pci:v00008086d00001E26sv0000144Dsd0000C0D8bc0Csc03i20')
2013-04-24 16:56:01,718 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x85a7a0c> about HardwareID('modalias', 'usb:v045Ep0745d0634dc00dsc00dp00ic03isc01ip02')
2013-04-24 16:56:01,749 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2013-04-24 16:56:01,749 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2013-04-24 16:56:01,749 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse'}
2013-04-24 16:56:01,749 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse', 'jockey_handler': 'KernelModuleHandler'}
2013-04-24 16:56:01,749 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x85a7a0c> about HardwareID('modalias', 'acpi:INT3F0D:PNP0C02:')
2013-04-24 16:56:01,749 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x85a7a0c> about HardwareID('modalias', 'platform:microcode')
2013-04-24 16:56:01,750 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x85a7a0c> about HardwareID('modalias', 'input:b0003v0C45pC35Ae0300-e0,1,kD4,ramlsfw')
2013-04-24 16:56:01,750 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-04-24 16:56:01,750 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-04-24 16:56:01,750 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-04-24 16:56:01,750 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-04-24 16:56:01,750 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x85a7a0c> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8E,8F,94,95,96,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,C0,C1,CA,D9,E0,E1,E2,E3,EC,EE,ram4,l0,1,2,sfw')
2013-04-24 16:56:01,750 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-04-24 16:56:01,750 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-04-24 16:56:01,750 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-04-24 16:56:01,750 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-04-24 16:56:01,750 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x85a7a0c> about HardwareID('modalias', 'usb:v0CF3p3004d0002dcE0dsc01dp01icE0isc01ip01')
2013-04-24 16:56:01,755 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'ath3k'}
2013-04-24 16:56:01,755 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ath3k', 'jockey_handler': 'KernelModuleHandler'}
2013-04-24 16:56:01,755 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'btusb'}
2013-04-24 16:56:01,755 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'btusb', 'jockey_handler': 'KernelModuleHandler'}
2013-04-24 16:56:01,755 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x85a7a0c> about HardwareID('modalias', 'input:b0003v045Ep0745e0111-e0,1,2,3,4,k71,72,73,74,77,80,82,83,85,86,87,88,89,8A,8B,8C,8E,90,96,98,9B,9C,9E,9F,A1,A3,A4,A5,A6,A7,A8,A9,AB,AC,AD,AE,B0,B1,B2,B5,B6,CE,CF,D0,D1,D2,D4,D8,D9,DB,DF,E4,E7,E8,E9,EA,EB,F1,100,110,111,112,113,114,161,162,166,16A,16E,172,174,176,178,179,17A,17B,17C,17D,17F,180,182,183,185,188,189,18C,18D,18E,18F,190,191,192,193,195,198,199,19A,1A0,1A1,1A2,1A3,1A4,1A5,1A6,1A7,1A8,1A9,1AA,1AB,1AC,1AD,1AE,1B0,1B1,1B7,1BA,r0,1,6,7,8,9,a20,m4,lsfw')
2013-04-24 16:56:01,755 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-04-24 16:56:01,755 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-04-24 16:56:01,755 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2013-04-24 16:56:01,755 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2013-04-24 16:56:01,755 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-04-24 16:56:01,755 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-04-24 16:56:01,755 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x85a7a0c> about HardwareID('modalias', 'acpi:PNP0F03:PNP0F13:')
2013-04-24 16:56:01,755 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x85a7a0c> about HardwareID('modalias', 'dmi:bvnAmericanMegatrendsInc.:bvrP03ABE:bd09/20/2012:svnSAMSUNGELECTRONICSCO.,LTD.:pn350V5C/350V5X/350V4C/350V4X/351V5C/351V5X/351V4C/351V4X/3540VC/3540VX/3440VC/3440VX:pvrP03ABE.006.CP:rvnSAMSUNGELECTRONICSCO.,LTD.:rnNP350V5C-S04PT:rvrBOARDREVISION00:cvnSAMSUNGELECTRONICSCO.,LTD.:ct9:cvr0.1:')
2013-04-24 16:56:01,763 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x85a7a0c> about HardwareID('modalias', 'pci:v000010ECd00008168sv0000144Dsd0000C0D8bc02sc00i00')
2013-04-24 16:56:01,768 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'r8169'}
2013-04-24 16:56:01,768 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'r8169', 'jockey_handler': 'KernelModuleHandler'}
2013-04-24 16:56:01,768 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x85a7a0c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,8,')
2013-04-24 16:56:01,768 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-04-24 16:56:01,768 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-04-24 16:56:01,768 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x85a7a0c> about HardwareID('modalias', 'usb:v1D6Bp0002d0305dc09dsc00dp01ic09isc00ip00')
2013-04-24 16:56:01,769 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x85a7a0c> about HardwareID('modalias', 'usb:v045Ep0745d0634dc00dsc00dp00ic03isc00ip00')
2013-04-24 16:56:01,769 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2013-04-24 16:56:01,769 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2013-04-24 16:56:01,769 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x85a7a0c> about HardwareID('modalias', 'pci:v00008086d00001E59sv0000144Dsd0000C0D8bc06sc01i00')
2013-04-24 16:56:01,771 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'lpc_ich'}
2013-04-24 16:56:01,771 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'lpc_ich', 'jockey_handler': 'KernelModuleHandler'}
2013-04-24 16:56:01,771 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x85a7a0c> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2013-04-24 16:56:01,771 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-04-24 16:56:01,771 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-04-24 16:56:01,771 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x85a7a0c> about HardwareID('modalias', 'pci:v0000168Cd00000032sv0000144Dsd00004105bc02sc80i00')
2013-04-24 16:56:01,778 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'ath9k'}
2013-04-24 16:56:01,778 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ath9k', 'jockey_handler': 'KernelModuleHandler'}
2013-04-24 16:56:01,778 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x85a7a0c> about HardwareID('modalias', 'acpi:PNP0C01:')
2013-04-24 16:56:01,778 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x85a7a0c> about HardwareID('modalias', 'usb:v0C45pC35Ad0300dcEFdsc02dp01ic0Eisc02ip00')
2013-04-24 16:56:01,778 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x85a7a0c> about HardwareID('modalias', 'pci:v00001002d00006840sv0000144Dsd0000C0D8bc03sc00i00')
2013-04-24 16:56:01,998 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'radeon'}
2013-04-24 16:56:01,998 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'radeon', 'jockey_handler': 'KernelModuleHandler'}
2013-04-24 16:56:01,998 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx_experimental_12', 'package': 'fglrx-experimental-12'}
2013-04-24 16:56:02,000 WARNING: modinfo for module fglrx_experimental_12 failed: ERROR: modinfo: could not find module fglrx_experimental_12


2013-04-24 16:56:02,009 WARNING: modinfo for module fglrx_experimental_12 failed: ERROR: modinfo: could not find module fglrx_experimental_12


2013-04-24 16:56:02,009 DEBUG: got handler kmod:fglrx_experimental_12([KernelModuleHandler, nonfree, disabled] Experimental AMD binary Xorg driver and kernel module)
2013-04-24 16:56:02,009 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx_experimental_9', 'package': 'fglrx-experimental-9'}
2013-04-24 16:56:02,015 DEBUG: fglrx.enabled(fglrx_experimental_9): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2013-04-24 16:56:02,015 DEBUG: fglrx_experimental_9 is not the alternative in use
2013-04-24 16:56:02,010 DEBUG: found match in handler pool xorg:fglrx_experimental_9([FglrxDriverExperimental9, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (**experimental** beta))
2013-04-24 16:56:02,017 WARNING: modinfo for module fglrx_experimental_9 failed: ERROR: modinfo: could not find module fglrx_experimental_9


2013-04-24 16:56:02,019 DEBUG: fglrx.available: falling back to default
2013-04-24 16:56:02,136 DEBUG: fglrx.enabled(fglrx_experimental_9): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2013-04-24 16:56:02,137 DEBUG: fglrx_experimental_9 is not the alternative in use
2013-04-24 16:56:02,131 DEBUG: got handler xorg:fglrx_experimental_9([FglrxDriverExperimental9, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (**experimental** beta))
2013-04-24 16:56:02,137 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx_updates', 'package': 'fglrx-updates'}
2013-04-24 16:56:02,142 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2013-04-24 16:56:02,142 DEBUG: fglrx_updates is not the alternative in use
2013-04-24 16:56:02,137 DEBUG: found match in handler pool xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2013-04-24 16:56:02,144 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates


2013-04-24 16:56:02,146 DEBUG: fglrx.available: falling back to default
2013-04-24 16:56:02,263 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2013-04-24 16:56:02,263 DEBUG: fglrx_updates is not the alternative in use
2013-04-24 16:56:02,257 DEBUG: got handler xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2013-04-24 16:56:02,263 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx', 'package': 'fglrx'}
2013-04-24 16:56:02,269 DEBUG: fglrx.enabled(fglrx): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2013-04-24 16:56:02,269 DEBUG: fglrx is not the alternative in use
2013-04-24 16:56:02,263 DEBUG: found match in handler pool xorg:fglrx([FglrxDriver, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver)
2013-04-24 16:56:02,271 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx


2013-04-24 16:56:02,273 DEBUG: fglrx.available: falling back to default
2013-04-24 16:56:02,386 DEBUG: XorgDriverHandler(fglrx, fglrx, None): Disabling as package is not compatible with Q-LTS X.org
2013-04-24 16:56:02,392 DEBUG: fglrx.enabled(fglrx): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2013-04-24 16:56:02,392 DEBUG: fglrx is not the alternative in use
2013-04-24 16:56:02,386 DEBUG: ignoring unavailable handler xorg:fglrx([FglrxDriver, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver)
2013-04-24 16:56:02,392 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x85a7a0c> about HardwareID('modalias', 'acpi:PNP0200:')
2013-04-24 16:56:02,392 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x85a7a0c> about HardwareID('modalias', 'acpi:INT0800:')
2013-04-24 16:56:02,392 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x85a7a0c> about HardwareID('modalias', 'platform:eisa')
2013-04-24 16:56:02,393 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x85a7a0c> about HardwareID('modalias', 'pci:v00008086d00000166sv0000144Dsd0000C0D8bc03sc00i00')
2013-04-24 16:56:02,395 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'i915'}
2013-04-24 16:56:02,395 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i915', 'jockey_handler': 'KernelModuleHandler'}
2013-04-24 16:56:02,395 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x85a7a0c> about HardwareID('modalias', 'hid:b0003g0001v0000045Ep00000745')
2013-04-24 16:56:02,421 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'hid_generic'}
2013-04-24 16:56:02,421 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'hid_generic', 'jockey_handler': 'KernelModuleHandler'}
2013-04-24 16:56:02,421 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x85a7a0c> about HardwareID('modalias', 'usb:v045Ep0745d0634dc00dsc00dp00ic03isc01ip01')
2013-04-24 16:56:02,422 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2013-04-24 16:56:02,422 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2013-04-24 16:56:02,422 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd'}
2013-04-24 16:56:02,422 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd', 'jockey_handler': 'KernelModuleHandler'}
2013-04-24 16:56:02,422 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x85a7a0c> about HardwareID('modalias', 'acpi:PNP0000:')
2013-04-24 16:56:02,422 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x85a7a0c> about HardwareID('modalias', 'platform:samsung')
2013-04-24 16:56:02,422 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x85a7a0c> about HardwareID('modalias', 'platform:regulatory')
2013-04-24 16:56:02,423 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x85a7a0c> about HardwareID('modalias', 'x86cpu:vendor:0000:family:0006:model:003A:feature:,0000,0001,0002,0003,0004,0005,0006,0007,0008,0009,000B,000C,000D,000E,000F,0010,0011,0013,0015,0016,0017,0018,0019,001A,001B,001C,001D,001F,0034,003B,003D,0066,0068,006B,006C,006D,0072,0076,0078,007C,0080,0081,0082,0083,0084,0085,0087,0088,0089,008D,008E,008F,0091,0093,0094,0095,0097,0098,0099,009A,009B,009C,009D,009E,00C0,00E0,00E1,00E3,00E4,00E5,00E6,00E7,0100,0101,0102,0103,0104,0120,0127,0129')
2013-04-24 16:56:02,426 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'aesni_intel'}
2013-04-24 16:56:02,426 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'aesni_intel', 'jockey_handler': 'KernelModuleHandler'}
2013-04-24 16:56:02,426 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'kvm_intel'}
2013-04-24 16:56:02,426 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'kvm_intel', 'jockey_handler': 'KernelModuleHandler'}
2013-04-24 16:56:02,427 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'microcode'}
2013-04-24 16:56:02,427 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'microcode', 'jockey_handler': 'KernelModuleHandler'}
2013-04-24 16:56:02,427 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'coretemp'}
2013-04-24 16:56:02,427 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'coretemp', 'jockey_handler': 'KernelModuleHandler'}
2013-04-24 16:56:02,427 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x85a7a0c> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2013-04-24 16:56:02,431 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw'}
2013-04-24 16:56:02,431 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2013-04-24 16:56:02,431 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'psmouse'}
2013-04-24 16:56:02,432 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2013-04-24 16:56:02,432 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x85a7a0c> about HardwareID('modalias', 'platform:coretemp')
2013-04-24 16:56:02,432 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x85a7a0c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2013-04-24 16:56:02,432 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-04-24 16:56:02,432 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-04-24 16:56:02,432 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-04-24 16:56:02,432 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-04-24 16:56:02,432 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x85a7a0c> about HardwareID('modalias', 'acpi:PNP0103:')
2013-04-24 16:56:02,432 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x85a7a0c> about HardwareID('modalias', 'input:b0003v045Ep0745e0111-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,sfw')
2013-04-24 16:56:02,432 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-04-24 16:56:02,432 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-04-24 16:56:02,432 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-04-24 16:56:02,433 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-04-24 16:56:02,433 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x85a7a0c> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2013-04-24 16:56:02,433 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-04-24 16:56:02,433 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-04-24 16:56:02,433 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-04-24 16:56:02,433 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-04-24 16:56:02,433 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x85a7a0c> about HardwareID('modalias', 'acpi:INT340E:PNP0C02:')
2013-04-24 16:56:02,433 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x883f60c> about HardwareID('modalias', 'pci:v00008086d00000154sv0000144Dsd0000C0D8bc06sc00i00')
2013-04-24 16:56:02,433 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x883f60c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2013-04-24 16:56:02,433 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x883f60c> about HardwareID('modalias', 'acpi:PNP0B00:')
2013-04-24 16:56:02,433 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x883f60c> about HardwareID('modalias', 'pci:v00008086d00001E20sv0000144Dsd0000C0D8bc04sc03i00')
2013-04-24 16:56:02,433 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x883f60c> about HardwareID('modalias', 'pci:v00008086d00001E2Dsv0000144Dsd0000C0D8bc0Csc03i20')
2013-04-24 16:56:02,433 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x883f60c> about HardwareID('modalias', 'platform:pcspkr')
2013-04-24 16:56:02,433 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x883f60c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2013-04-24 16:56:02,433 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x883f60c> about HardwareID('modalias', 'usb:v1D6Bp0003d0305dc09dsc00dp03ic09isc00ip00')
2013-04-24 16:56:02,433 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x883f60c> about HardwareID('modalias', 'usb:v8087p0024d0000dc09dsc00dp01ic09isc00ip00')
2013-04-24 16:56:02,433 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x883f60c> about HardwareID('modalias', 'input:b0003v045Ep0745e0111-e0,1,2,3,4,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,8B,8C,8E,8F,90,94,96,98,9B,9C,9E,9F,A1,A3,A4,A5,A6,A7,A8,A9,AB,AC,AD,AE,B0,B1,B2,B3,B4,B5,B6,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,CE,CF,D0,D1,D2,D4,D8,D9,DB,DF,E4,E7,E8,E9,EA,EB,F0,F1,100,13A,13B,161,162,164,166,16A,16E,172,174,176,178,179,17A,17B,17C,17D,17F,180,182,183,185,188,189,18C,18D,18E,18F,190,191,192,193,195,198,199,19A,1A0,1A1,1A2,1A3,1A4,1A5,1A6,1A7,1A8,1A9,1AA,1AB,1AC,1AD,1AE,1B0,1B1,1B6,1B7,1BA,r6,a0,1,2,3,4,5,6,7,8,10,11,12,20,28,29,2A,2B,2C,2D,2E,2F,30,31,32,33,34,35,36,37,38,39,3A,3B,3C,3D,3E,m4,lsfw')
2013-04-24 16:56:02,433 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x883f60c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2013-04-24 16:56:02,433 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x883f60c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2013-04-24 16:56:02,433 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x883f60c> about HardwareID('modalias', 'usb:v1D6Bp0002d0305dc09dsc00dp00ic09isc00ip00')
2013-04-24 16:56:02,433 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x883f60c> about HardwareID('modalias', 'acpi:PNP0100:')
2013-04-24 16:56:02,433 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x883f60c> about HardwareID('modalias', 'input:b0011v0002p0007e01B1-e0,1,3,k110,111,145,14A,14D,14E,ra0,1,18,1C,2F,35,36,39,mlsfw')
2013-04-24 16:56:02,434 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x883f60c> about HardwareID('modalias', 'wmi:C16C47BA-50E3-444A-AF3A-B1C348380000')
2013-04-24 16:56:02,434 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x883f60c> about HardwareID('modalias', 'pci:v00008086d00001E3Asv0000144Dsd0000C0D8bc07sc80i00')
2013-04-24 16:56:02,434 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x883f60c> about HardwareID('modalias', 'wmi:C16C47BA-50E3-444A-AF3A-B1C348380001')
2013-04-24 16:56:02,434 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x883f60c> about HardwareID('modalias', 'usb:v0C45pC35Ad0300dcEFdsc02dp01ic0Eisc01ip00')
2013-04-24 16:56:02,434 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x883f60c> about HardwareID('modalias', 'pci:v00008086d00001E03sv0000144Dsd0000C0D8bc01sc06i01')
2013-04-24 16:56:02,434 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x883f60c> about HardwareID('modalias', 'pci:v00008086d00001E22sv0000144Dsd0000C0D8bc0Csc05i00')
2013-04-24 16:56:02,434 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x883f60c> about HardwareID('modalias', 'pci:v00008086d00001E31sv0000144Dsd0000C0D8bc0Csc03i30')
2013-04-24 16:56:02,434 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x883f60c> about HardwareID('modalias', 'acpi:PNP0303:PNP030B:')
2013-04-24 16:56:02,434 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x883f60c> about HardwareID('modalias', 'acpi:PNP0C04:')
2013-04-24 16:56:02,434 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x883f60c> about HardwareID('modalias', 'acpi:PNP0C02:')
2013-04-24 16:56:02,434 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x883f60c> about HardwareID('modalias', 'pci:v00008086d00001E26sv0000144Dsd0000C0D8bc0Csc03i20')
2013-04-24 16:56:02,434 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x883f60c> about HardwareID('modalias', 'usb:v045Ep0745d0634dc00dsc00dp00ic03isc01ip02')
2013-04-24 16:56:02,434 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x883f60c> about HardwareID('modalias', 'acpi:INT3F0D:PNP0C02:')
2013-04-24 16:56:02,434 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x883f60c> about HardwareID('modalias', 'platform:microcode')
2013-04-24 16:56:02,434 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x883f60c> about HardwareID('modalias', 'input:b0003v0C45pC35Ae0300-e0,1,kD4,ramlsfw')
2013-04-24 16:56:02,434 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x883f60c> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8E,8F,94,95,96,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,C0,C1,CA,D9,E0,E1,E2,E3,EC,EE,ram4,l0,1,2,sfw')
2013-04-24 16:56:02,434 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x883f60c> about HardwareID('modalias', 'usb:v0CF3p3004d0002dcE0dsc01dp01icE0isc01ip01')
2013-04-24 16:56:02,434 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x883f60c> about HardwareID('modalias', 'input:b0003v045Ep0745e0111-e0,1,2,3,4,k71,72,73,74,77,80,82,83,85,86,87,88,89,8A,8B,8C,8E,90,96,98,9B,9C,9E,9F,A1,A3,A4,A5,A6,A7,A8,A9,AB,AC,AD,AE,B0,B1,B2,B5,B6,CE,CF,D0,D1,D2,D4,D8,D9,DB,DF,E4,E7,E8,E9,EA,EB,F1,100,110,111,112,113,114,161,162,166,16A,16E,172,174,176,178,179,17A,17B,17C,17D,17F,180,182,183,185,188,189,18C,18D,18E,18F,190,191,192,193,195,198,199,19A,1A0,1A1,1A2,1A3,1A4,1A5,1A6,1A7,1A8,1A9,1AA,1AB,1AC,1AD,1AE,1B0,1B1,1B7,1BA,r0,1,6,7,8,9,a20,m4,lsfw')
2013-04-24 16:56:02,434 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x883f60c> about HardwareID('modalias', 'acpi:PNP0F03:PNP0F13:')
2013-04-24 16:56:02,434 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x883f60c> about HardwareID('modalias', 'dmi:bvnAmericanMegatrendsInc.:bvrP03ABE:bd09/20/2012:svnSAMSUNGELECTRONICSCO.,LTD.:pn350V5C/350V5X/350V4C/350V4X/351V5C/351V5X/351V4C/351V4X/3540VC/3540VX/3440VC/3440VX:pvrP03ABE.006.CP:rvnSAMSUNGELECTRONICSCO.,LTD.:rnNP350V5C-S04PT:rvrBOARDREVISION00:cvnSAMSUNGELECTRONICSCO.,LTD.:ct9:cvr0.1:')
2013-04-24 16:56:02,434 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x883f60c> about HardwareID('modalias', 'pci:v000010ECd00008168sv0000144Dsd0000C0D8bc02sc00i00')
2013-04-24 16:56:02,434 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x883f60c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,8,')
2013-04-24 16:56:02,434 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x883f60c> about HardwareID('modalias', 'usb:v1D6Bp0002d0305dc09dsc00dp01ic09isc00ip00')
2013-04-24 16:56:02,434 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x883f60c> about HardwareID('modalias', 'usb:v045Ep0745d0634dc00dsc00dp00ic03isc00ip00')
2013-04-24 16:56:02,434 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x883f60c> about HardwareID('modalias', 'pci:v00008086d00001E59sv0000144Dsd0000C0D8bc06sc01i00')
2013-04-24 16:56:02,434 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x883f60c> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2013-04-24 16:56:02,435 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x883f60c> about HardwareID('modalias', 'pci:v0000168Cd00000032sv0000144Dsd00004105bc02sc80i00')
2013-04-24 16:56:02,435 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x883f60c> about HardwareID('modalias', 'acpi:PNP0C01:')
2013-04-24 16:56:02,435 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x883f60c> about HardwareID('modalias', 'usb:v0C45pC35Ad0300dcEFdsc02dp01ic0Eisc02ip00')
2013-04-24 16:56:02,435 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x883f60c> about HardwareID('modalias', 'pci:v00001002d00006840sv0000144Dsd0000C0D8bc03sc00i00')
2013-04-24 16:56:02,435 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x883f60c> about HardwareID('modalias', 'acpi:PNP0200:')
2013-04-24 16:56:02,435 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x883f60c> about HardwareID('modalias', 'acpi:INT0800:')
2013-04-24 16:56:02,435 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x883f60c> about HardwareID('modalias', 'platform:eisa')
2013-04-24 16:56:02,435 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x883f60c> about HardwareID('modalias', 'pci:v00008086d00000166sv0000144Dsd0000C0D8bc03sc00i00')
2013-04-24 16:56:02,435 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x883f60c> about HardwareID('modalias', 'hid:b0003g0001v0000045Ep00000745')
2013-04-24 16:56:02,435 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x883f60c> about HardwareID('modalias', 'usb:v045Ep0745d0634dc00dsc00dp00ic03isc01ip01')
2013-04-24 16:56:02,435 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x883f60c> about HardwareID('modalias', 'acpi:PNP0000:')
2013-04-24 16:56:02,435 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x883f60c> about HardwareID('modalias', 'platform:samsung')
2013-04-24 16:56:02,435 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x883f60c> about HardwareID('modalias', 'platform:regulatory')
2013-04-24 16:56:02,435 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x883f60c> about HardwareID('modalias', 'x86cpu:vendor:0000:family:0006:model:003A:feature:,0000,0001,0002,0003,0004,0005,0006,0007,0008,0009,000B,000C,000D,000E,000F,0010,0011,0013,0015,0016,0017,0018,0019,001A,001B,001C,001D,001F,0034,003B,003D,0066,0068,006B,006C,006D,0072,0076,0078,007C,0080,0081,0082,0083,0084,0085,0087,0088,0089,008D,008E,008F,0091,0093,0094,0095,0097,0098,0099,009A,009B,009C,009D,009E,00C0,00E0,00E1,00E3,00E4,00E5,00E6,00E7,0100,0101,0102,0103,0104,0120,0127,0129')
2013-04-24 16:56:02,435 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x883f60c> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2013-04-24 16:56:02,435 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x883f60c> about HardwareID('modalias', 'platform:coretemp')
2013-04-24 16:56:02,435 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x883f60c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2013-04-24 16:56:02,435 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x883f60c> about HardwareID('modalias', 'acpi:PNP0103:')
2013-04-24 16:56:02,435 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x883f60c> about HardwareID('modalias', 'input:b0003v045Ep0745e0111-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,sfw')
2013-04-24 16:56:02,435 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x883f60c> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2013-04-24 16:56:02,435 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x883f60c> about HardwareID('modalias', 'acpi:INT340E:PNP0C02:')
2013-04-24 16:56:02,597 DEBUG: fglrx.enabled(fglrx_experimental_9): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2013-04-24 16:56:02,598 DEBUG: fglrx_experimental_9 is not the alternative in use
2013-04-24 16:56:02,611 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2013-04-24 16:56:02,611 DEBUG: fglrx_updates is not the alternative in use
2013-04-24 16:56:02,641 DEBUG: fglrx.enabled(fglrx_experimental_9): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2013-04-24 16:56:02,642 DEBUG: fglrx_experimental_9 is not the alternative in use
2013-04-24 16:56:02,653 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2013-04-24 16:56:02,653 DEBUG: fglrx_updates is not the alternative in use
2013-04-24 16:56:30,126 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2013-04-24 16:56:30,126 DEBUG: fglrx_updates is not the alternative in use
2013-04-24 16:56:30,854 DEBUG: fglrx.enabled(fglrx_experimental_9): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2013-04-24 16:56:30,854 DEBUG: fglrx_experimental_9 is not the alternative in use
2013-04-24 16:56:33,668 DEBUG: fglrx.enabled(fglrx_experimental_9): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2013-04-24 16:56:33,669 DEBUG: fglrx_experimental_9 is not the alternative in use
2013-04-24 16:56:34,101 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2013-04-24 16:56:34,101 DEBUG: fglrx_updates is not the alternative in use
2013-04-24 16:56:47,898 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2013-04-24 16:56:47,899 DEBUG: fglrx_updates is not the alternative in use
2013-04-24 16:56:52,821 DEBUG: Installing package: linux-headers-generic
2013-04-24 16:56:57,972 DEBUG: install progress dpkg-exec 0.000000
2013-04-24 16:56:58,273 DEBUG: dpkg: error: dpkg status database is locked by another process
Error in function: 
SystemError: E:Sub-process /usr/bin/dpkg returned an error code (2)


2013-04-24 16:56:58,274 ERROR: Package failed to install:
dpkg: error: dpkg status database is locked by another process
Error in function: 
SystemError: E:Sub-process /usr/bin/dpkg returned an error code (2)


2013-04-24 16:56:58,574 DEBUG: Installing package: fglrx-updates
2013-04-24 16:56:59,366 DEBUG: install progress dpkg-exec 0.000000
2013-04-24 16:56:59,467 DEBUG: dpkg: error: dpkg status database is locked by another process
Error in function: 
SystemError: E:Sub-process /usr/bin/dpkg returned an error code (2)


2013-04-24 16:56:59,467 ERROR: Package failed to install:
dpkg: error: dpkg status database is locked by another process
Error in function: 
SystemError: E:Sub-process /usr/bin/dpkg returned an error code (2)


2013-04-24 16:56:59,720 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates


2013-04-24 16:56:59,721 WARNING: /sys/module/fglrx_updates/drivers does not exist, cannot rebind fglrx_updates driver
2013-04-24 16:56:59,721 ERROR: XorgDriverHandler.enable(): package or module not installed, aborting
2013-04-24 16:56:59,725 ERROR: xorg:fglrx_updates: get_alternative_by_name(fglrx-updates) returned nothing
2013-04-24 16:57:00,006 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2013-04-24 16:57:00,006 DEBUG: fglrx_updates is not the alternative in use
2013-04-24 17:03:34,991 DEBUG: fglrx.enabled(fglrx_experimental_9): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2013-04-24 17:03:34,991 DEBUG: fglrx_experimental_9 is not the alternative in use
2013-04-24 17:03:35,025 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2013-04-24 17:03:35,025 DEBUG: fglrx_updates is not the alternative in use
2013-04-24 17:03:35,066 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2013-04-24 17:03:35,067 DEBUG: fglrx_updates is not the alternative in use
2013-04-24 17:03:35,126 DEBUG: fglrx.enabled(fglrx_experimental_9): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2013-04-24 17:03:35,126 DEBUG: fglrx_experimental_9 is not the alternative in use
2013-04-24 17:03:35,150 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2013-04-24 17:03:35,150 DEBUG: fglrx_updates is not the alternative in use
2013-04-24 17:03:36,421 DEBUG: Shutting down

```

---

### Post by Bucky Ball on 2013-04-24
I have removed the large image from the body of your post and attached it instead. Please refrain from putting big images in the body of the post. Cheers. ;)

What happens when you do a regular update? Try these two, one after the other. 

```
sudo apt-get update
sudo apt-get upgrade
```

What's got me curious is these two lines, before anything else happens:

```

2013-04-24 16:32:46,523 DEBUG: Updating repository indexes...
2013-04-24 16:32:46,669 DEBUG: ... fail!
```

Seems to loose it about here:

```
2013-04-24 16:56:58,273 DEBUG: dpkg: error: dpkg status database is locked by another process
Error in function: 
SystemError: E:Sub-process /usr/bin/dpkg returned an error code (2)
```

... toward the end so that may have more to do with your problem. After all the fglrx stuff.

---

