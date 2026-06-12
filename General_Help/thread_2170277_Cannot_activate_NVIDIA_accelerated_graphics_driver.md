---
title: "Cannot activate NVIDIA accelerated graphics driver (version 304)"
date: 2013-08-25
forum: General Help
---

### Post by Naygral on 2013-08-25
I just installed Xubuntu 12.04.3 and used the option to dual boot it with Lubuntu 13.04 (that I had installed entirely on my harddrive). The installation went without any problem until I had to install the proprietary driver needed to get my proper resolution. When I tried to install the recommended version (304), I got this error:

[I]Sorry, installation of this driver failed.
Please have a look at the log file for details: /var/log/jockey.log

[/I]This is the jockey.log:

```
                 
[LIST=1]
[*]2013-08-25 20:56:29,555 DEBUG: Comparing 3.2.0-52 with 
2013-08-25 20:56:29,559 DEBUG: Comparing 3.2.0-52 with 3.2.0-52
2013-08-25 20:56:30,449 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0xa0e3fec>
2013-08-25 20:56:32,430 DEBUG: reading modalias file /lib/modules/3.2.0-52-generic-pae/modules.alias
2013-08-25 20:56:32,630 DEBUG: reading modalias file /usr/share/jockey/modaliases/b43
2013-08-25 20:56:32,658 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2013-08-25 20:56:32,732 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2013-08-25 20:56:32,878 WARNING: modinfo for module  fglrx_experimental_12 failed: ERROR: modinfo: could not find module  fglrx_experimental_12
 
2013-08-25 20:56:34,489 DEBUG: linux-lts-raring installed: False
linux-lts-saucy installed: False
linux minor version: 2
xserver ABI: 11
xserver-lts-quantal: False
2013-08-25 20:56:34,508 DEBUG: Instantiated Handler  subclass __builtin__.FglrxDriverExperimental12 from name  FglrxDriverExperimental12
2013-08-25 20:56:34,508 DEBUG: fglrx.available: falling back to default
2013-08-25 20:56:36,260 DEBUG: ATI/AMD proprietary  FGLRX graphics driver (**experimental** beta) availability undetermined,  adding to pool
2013-08-25 20:56:36,262 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates
 
2013-08-25 20:56:36,266 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriverUpdate from name FglrxDriverUpdate
2013-08-25 20:56:36,266 DEBUG: fglrx.available: falling back to default
2013-08-25 20:56:40,543 DEBUG: ATI/AMD proprietary  FGLRX graphics driver (post-release updates) availability undetermined,  adding to pool
2013-08-25 20:56:40,546 WARNING: modinfo for module  fglrx_experimental_9 failed: ERROR: modinfo: could not find module  fglrx_experimental_9
 
2013-08-25 20:56:40,563 DEBUG: Instantiated Handler  subclass __builtin__.FglrxDriverExperimental9 from name  FglrxDriverExperimental9
2013-08-25 20:56:40,564 DEBUG: fglrx.available: falling back to default
2013-08-25 20:56:42,316 DEBUG: ATI/AMD proprietary  FGLRX graphics driver (**experimental** beta) availability undetermined,  adding to pool
2013-08-25 20:56:42,319 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx
 
2013-08-25 20:56:42,323 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriverHybrid from name FglrxDriverHybrid
2013-08-25 20:56:42,323 DEBUG: fglrx.available: falling back to default
2013-08-25 20:56:46,992 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2013-08-25 20:56:46,995 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx
 
2013-08-25 20:56:46,999 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2013-08-25 20:56:46,999 DEBUG: fglrx.available: falling back to default
2013-08-25 20:56:51,833 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2013-08-25 20:56:51,836 WARNING: modinfo for module  fglrx_experimental_13 failed: ERROR: modinfo: could not find module  fglrx_experimental_13
 
2013-08-25 20:56:51,854 DEBUG: Instantiated Handler  subclass __builtin__.FglrxDriverExperimental13 from name  FglrxDriverExperimental13
2013-08-25 20:56:51,854 DEBUG: fglrx.available: falling back to default
2013-08-25 20:58:04,623 DEBUG: Comparing 3.2.0-52 with 
2013-08-25 20:58:04,627 DEBUG: Comparing 3.2.0-52 with 3.2.0-52
2013-08-25 20:58:05,024 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x971ffec>
2013-08-25 20:58:07,016 DEBUG: reading modalias file /lib/modules/3.2.0-52-generic-pae/modules.alias
2013-08-25 20:58:07,134 DEBUG: reading modalias file /usr/share/jockey/modaliases/b43
2013-08-25 20:58:07,134 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2013-08-25 20:58:07,189 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2013-08-25 20:58:07,195 WARNING: modinfo for module  fglrx_experimental_12 failed: ERROR: modinfo: could not find module  fglrx_experimental_12
 
2013-08-25 20:58:07,609 DEBUG: linux-lts-raring installed: False
linux-lts-saucy installed: False
linux minor version: 2
xserver ABI: 11
xserver-lts-quantal: False
2013-08-25 20:58:07,628 DEBUG: Instantiated Handler  subclass __builtin__.FglrxDriverExperimental12 from name  FglrxDriverExperimental12
2013-08-25 20:58:07,628 DEBUG: fglrx.available: falling back to default
2013-08-25 20:58:09,411 DEBUG: ATI/AMD proprietary  FGLRX graphics driver (**experimental** beta) availability undetermined,  adding to pool
2013-08-25 20:58:09,413 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates
 
2013-08-25 20:58:09,417 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriverUpdate from name FglrxDriverUpdate
2013-08-25 20:58:09,418 DEBUG: fglrx.available: falling back to default
2013-08-25 20:58:13,445 DEBUG: ATI/AMD proprietary  FGLRX graphics driver (post-release updates) availability undetermined,  adding to pool
2013-08-25 20:58:13,448 WARNING: modinfo for module  fglrx_experimental_9 failed: ERROR: modinfo: could not find module  fglrx_experimental_9
 
2013-08-25 20:58:13,467 DEBUG: Instantiated Handler  subclass __builtin__.FglrxDriverExperimental9 from name  FglrxDriverExperimental9
2013-08-25 20:58:13,467 DEBUG: fglrx.available: falling back to default
2013-08-25 20:58:15,241 DEBUG: ATI/AMD proprietary  FGLRX graphics driver (**experimental** beta) availability undetermined,  adding to pool
2013-08-25 20:58:15,244 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx
 
2013-08-25 20:58:15,248 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriverHybrid from name FglrxDriverHybrid
2013-08-25 20:58:15,248 DEBUG: fglrx.available: falling back to default
2013-08-25 20:58:20,196 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2013-08-25 20:58:20,199 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx
 
2013-08-25 20:58:20,203 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2013-08-25 20:58:20,203 DEBUG: fglrx.available: falling back to default
2013-08-25 20:58:24,945 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2013-08-25 20:58:24,948 WARNING: modinfo for module  fglrx_experimental_13 failed: ERROR: modinfo: could not find module  fglrx_experimental_13
 
2013-08-25 20:58:24,966 DEBUG: Instantiated Handler  subclass __builtin__.FglrxDriverExperimental13 from name  FglrxDriverExperimental13
2013-08-25 20:58:24,966 DEBUG: fglrx.available: falling back to default
2013-08-25 20:58:26,942 DEBUG: ATI/AMD proprietary  FGLRX graphics driver (**experimental** beta) availability undetermined,  adding to pool
2013-08-25 20:58:26,942 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2013-08-25 20:58:26,976 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2013-08-25 20:58:27,000 DEBUG: Software modem not available
2013-08-25 20:58:27,000 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2013-08-25 20:58:27,007 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl
 
2013-08-25 20:58:27,023 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2013-08-25 20:58:27,023 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2013-08-25 20:58:27,023 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2013-08-25 20:58:27,027 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci
 
2013-08-25 20:58:27,027 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2013-08-25 20:58:27,028 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2013-08-25 20:58:27,028 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2013-08-25 20:58:27,083 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2013-08-25 20:58:27,083 DEBUG: Firmware for DVB cards not available
2013-08-25 20:58:27,083 DEBUG: loading custom handler /usr/share/jockey/handlers/vmware-client.py
2013-08-25 20:58:27,093 WARNING: modinfo for module vmxnet failed: ERROR: modinfo: could not find module vmxnet
 
2013-08-25 20:58:27,093 DEBUG: Instantiated Handler subclass __builtin__.VmwareClientHandler from name VmwareClientHandler
2013-08-25 20:58:27,107 DEBUG: VMWare Client Tools availability undetermined, adding to pool
2013-08-25 20:58:27,107 DEBUG: loading custom handler /usr/share/jockey/handlers/pvr-omap4.py
2013-08-25 20:58:27,112 WARNING: modinfo for module omapdrm_pvr failed: ERROR: modinfo: could not find module omapdrm_pvr
 
2013-08-25 20:58:27,116 DEBUG: Instantiated Handler subclass __builtin__.PVROmap4Driver from name PVROmap4Driver
2013-08-25 20:58:27,455 DEBUG: PowerVR SGX proprietary graphics driver for OMAP 4 not available
2013-08-25 20:58:27,455 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2013-08-25 20:58:27,478 WARNING: modinfo for module nvidia_304 failed: ERROR: modinfo: could not find module nvidia_304
 
2013-08-25 20:58:27,482 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver304 from name NvidiaDriver304
2013-08-25 20:58:27,482 DEBUG: nvidia.available: falling back to default
2013-08-25 20:58:33,680 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2013-08-25 20:58:33,683 WARNING: modinfo for module  nvidia_304_updates failed: ERROR: modinfo: could not find module  nvidia_304_updates
 
2013-08-25 20:58:33,686 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver304Updates from name NvidiaDriver304Updates
2013-08-25 20:58:33,687 DEBUG: nvidia.available: falling back to default
2013-08-25 20:58:39,954 DEBUG: NVIDIA accelerated  graphics driver (post-release updates) availability undetermined, adding  to pool
2013-08-25 20:58:39,957 WARNING: modinfo for module  nvidia_current_updates failed: ERROR: modinfo: could not find module  nvidia_current_updates
 
2013-08-25 20:58:39,961 DEBUG: Instantiated Handler  subclass __builtin__.NvidiaDriverCurrentUpdates from name  NvidiaDriverCurrentUpdates
2013-08-25 20:58:39,961 DEBUG: nvidia.available: falling back to default
2013-08-25 20:58:39,978 DEBUG: NVIDIA accelerated graphics driver (post-release updates) not available
2013-08-25 20:58:39,981 WARNING: modinfo for module  nvidia_experimental_304 failed: ERROR: modinfo: could not find module  nvidia_experimental_304
 
2013-08-25 20:58:39,999 DEBUG: Instantiated Handler  subclass __builtin__.NvidiaDriverExperimental304 from name  NvidiaDriverExperimental304
2013-08-25 20:58:40,000 DEBUG: nvidia.available: falling back to default
2013-08-25 20:58:40,014 DEBUG: NVIDIA accelerated graphics driver (**experimental** beta) not available
2013-08-25 20:58:40,017 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current
 
2013-08-25 20:58:40,021 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2013-08-25 20:58:40,021 DEBUG: nvidia.available: falling back to default
2013-08-25 20:58:40,038 DEBUG: NVIDIA accelerated graphics driver not available
2013-08-25 20:58:40,041 WARNING: modinfo for module nvidia_319 failed: ERROR: modinfo: could not find module nvidia_319
 
2013-08-25 20:58:40,045 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver319 from name NvidiaDriver319
2013-08-25 20:58:40,046 DEBUG: nvidia.available: falling back to default
2013-08-25 20:58:47,994 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2013-08-25 20:58:47,997 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173
 
2013-08-25 20:58:48,001 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2013-08-25 20:58:48,001 DEBUG: nvidia.available: falling back to default
2013-08-25 20:58:55,785 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2013-08-25 20:58:55,791 WARNING: modinfo for module  nvidia_173_updates failed: ERROR: modinfo: could not find module  nvidia_173_updates
 
2013-08-25 20:58:55,798 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173Updates from name NvidiaDriver173Updates
2013-08-25 20:58:55,798 DEBUG: nvidia.available: falling back to default
2013-08-25 20:59:06,564 DEBUG: NVIDIA accelerated  graphics driver (post-release updates) availability undetermined, adding  to pool
2013-08-25 20:59:06,569 WARNING: modinfo for module  nvidia_experimental_310 failed: ERROR: modinfo: could not find module  nvidia_experimental_310
 
2013-08-25 20:59:06,602 DEBUG: Instantiated Handler  subclass __builtin__.NvidiaDriverExperimental310 from name  NvidiaDriverExperimental310
2013-08-25 20:59:06,602 DEBUG: nvidia.available: falling back to default
2013-08-25 20:59:06,628 DEBUG: NVIDIA accelerated graphics driver (**experimental** beta) not available
2013-08-25 20:59:06,634 WARNING: modinfo for module  nvidia_319_updates failed: ERROR: modinfo: could not find module  nvidia_319_updates
 
2013-08-25 20:59:06,641 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver319Updates from name NvidiaDriver319Updates
2013-08-25 20:59:06,641 DEBUG: nvidia.available: falling back to default
2013-08-25 20:59:11,043 DEBUG: NVIDIA accelerated  graphics driver (post-release updates) availability undetermined, adding  to pool
2013-08-25 20:59:11,048 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96
 
2013-08-25 20:59:11,055 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2013-08-25 20:59:11,055 DEBUG: nvidia.available: falling back to default
2013-08-25 20:59:14,735 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2013-08-25 20:59:14,740 WARNING: modinfo for module  nvidia_96_updates failed: ERROR: modinfo: could not find module  nvidia_96_updates
 
2013-08-25 20:59:14,747 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96Updates from name NvidiaDriver96Updates
2013-08-25 20:59:14,747 DEBUG: nvidia.available: falling back to default
2013-08-25 20:59:16,861 DEBUG:  XorgDriverHandler(nvidia_96_updates, nvidia-96-updates, None): Disabling  as package video ABI(s) xorg-video-abi-10 not compatible with X.org  video ABI xorg-video-abi-11
2013-08-25 20:59:16,861 DEBUG: NVIDIA accelerated graphics driver (post-release updates) not available
2013-08-25 20:59:16,861 DEBUG: loading custom handler /usr/share/jockey/handlers/cdv.py
2013-08-25 20:59:16,882 WARNING: modinfo for module cedarview_gfx failed: ERROR: modinfo: could not find module cedarview_gfx
 
2013-08-25 20:59:16,883 DEBUG: Instantiated Handler subclass __builtin__.CdvDriver from name CdvDriver
2013-08-25 20:59:16,883 DEBUG: cdv.available: falling back to default
2013-08-25 20:59:17,388 DEBUG: Intel Cedarview graphics driver availability undetermined, adding to pool
2013-08-25 20:59:17,389 DEBUG: all custom handlers loaded
2013-08-25 20:59:17,389 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x971ffec> about HardwareID('modalias',  'pci:v0000197Bd00002363sv00001458sd0000B000bc01sc01i85')
2013-08-25 20:59:17,403 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pata_jmicron'}
2013-08-25 20:59:17,556 DEBUG: no corresponding handler  available for {'driver_type': 'kernel_module', 'kernel_module':  'pata_jmicron', 'jockey_handler': 'KernelModuleHandler'}
2013-08-25 20:59:17,556 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x971ffec> about HardwareID('modalias',  'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2013-08-25 20:59:17,561 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-08-25 20:59:17,561 DEBUG: no corresponding handler  available for {'driver_type': 'kernel_module', 'kernel_module':  'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-08-25 20:59:17,561 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x971ffec> about HardwareID('modalias',  'pci:v00001022d00001204sv00000000sd00000000bc06sc00i00')
2013-08-25 20:59:17,577 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x971ffec> about HardwareID('modalias',  'pci:v00001022d00001203sv00000000sd00000000bc06sc00i00')
2013-08-25 20:59:17,577 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'k10temp'}
2013-08-25 20:59:17,577 DEBUG: no corresponding handler  available for {'driver_type': 'kernel_module', 'kernel_module':  'k10temp', 'jockey_handler': 'KernelModuleHandler'}
2013-08-25 20:59:17,577 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x971ffec> about HardwareID('modalias', 'acpi:PNP0C02:')
2013-08-25 20:59:17,577 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x971ffec> about HardwareID('modalias', 'acpi:PNP0103:')
2013-08-25 20:59:17,577 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x971ffec> about HardwareID('modalias',  'pci:v000010ECd00008168sv00001458sd0000E000bc02sc00i00')
2013-08-25 20:59:17,586 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'r8169'}
2013-08-25 20:59:17,586 DEBUG: no corresponding handler  available for {'driver_type': 'kernel_module', 'kernel_module':  'r8169', 'jockey_handler': 'KernelModuleHandler'}
2013-08-25 20:59:17,586 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x971ffec> about HardwareID('modalias',  'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2013-08-25 20:59:17,587 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-08-25 20:59:17,587 DEBUG: no corresponding handler  available for {'driver_type': 'kernel_module', 'kernel_module':  'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-08-25 20:59:17,587 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x971ffec> about HardwareID('modalias', 'platform:eisa')
2013-08-25 20:59:17,587 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x971ffec> about HardwareID('modalias',  'usb:v1D6Bp0001d0302dc09dsc00dp00ic09isc00ip00')
2013-08-25 20:59:17,601 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x971ffec> about HardwareID('modalias',  'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2013-08-25 20:59:17,602 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-08-25 20:59:17,602 DEBUG: no corresponding handler  available for {'driver_type': 'kernel_module', 'kernel_module':  'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-08-25 20:59:17,602 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-08-25 20:59:17,602 DEBUG: no corresponding handler  available for {'driver_type': 'kernel_module', 'kernel_module':  'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-08-25 20:59:17,602 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x971ffec> about HardwareID('modalias', 'acpi:PNP0800:')
2013-08-25 20:59:17,602 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x971ffec> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2013-08-25 20:59:17,603 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x971ffec> about HardwareID('modalias',  'pci:v00001002d00004384sv00000000sd00000000bc06sc04i01')
2013-08-25 20:59:17,960 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x971ffec> about HardwareID('modalias', 'platform:SP5100 TCO timer')
2013-08-25 20:59:17,961 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x971ffec> about HardwareID('modalias',  'wmi:ABBC0F6A-8EA1-11D1-00A0-C90629100000')
2013-08-25 20:59:17,961 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x971ffec> about HardwareID('modalias',  'pci:v00001002d00005958sv00001002sd00005958bc06sc00i00')
2013-08-25 20:59:17,965 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'ati_agp'}
2013-08-25 20:59:17,965 DEBUG: no corresponding handler  available for {'driver_type': 'kernel_module', 'kernel_module':  'ati_agp', 'jockey_handler': 'KernelModuleHandler'}
2013-08-25 20:59:17,965 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x971ffec> about HardwareID('modalias',  'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2013-08-25 20:59:17,965 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x971ffec> about HardwareID('modalias', 'acpi:LNXSYBUS:')
2013-08-25 20:59:17,965 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x971ffec> about HardwareID('modalias', 'acpi:PNP0000:')
2013-08-25 20:59:17,966 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x971ffec> about HardwareID('modalias',  'pci:v000010DEd00000290sv000010DEsd00000343bc03sc00i00')
2013-08-25 20:59:18,264 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidiafb'}
2013-08-25 20:59:18,264 DEBUG: no corresponding handler  available for {'driver_type': 'kernel_module', 'kernel_module':  'nvidiafb', 'jockey_handler': 'KernelModuleHandler'}
2013-08-25 20:59:18,264 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nouveau'}
2013-08-25 20:59:18,264 DEBUG: no corresponding handler  available for {'driver_type': 'kernel_module', 'kernel_module':  'nouveau', 'jockey_handler': 'KernelModuleHandler'}
2013-08-25 20:59:18,264 DEBUG: searching handler for  driver ID {'driver_type': 'kernel_module', 'kernel_module':  'nvidia_173_updates', 'package': 'nvidia-173-updates'}
2013-08-25 20:59:18,308 DEBUG:  NVidia(nvidia_173_updates).enabled(): target_alt None current_alt  /usr/lib/nvidia-304/ld.so.conf other target alt None other current alt  /usr/lib/nvidia-304/alt_ld.so.conf
2013-08-25 20:59:18,308 DEBUG: nvidia_173_updates is not the alternative in use
2013-08-25 20:59:18,264 DEBUG: found match in handler  pool xorg:nvidia_173_updates([NvidiaDriver173Updates, nonfree, disabled]  NVIDIA accelerated graphics driver (post-release updates))
2013-08-25 20:59:18,314 WARNING: modinfo for module  nvidia_173_updates failed: ERROR: modinfo: could not find module  nvidia_173_updates
 
2013-08-25 20:59:18,321 DEBUG: nvidia.available: falling back to default
2013-08-25 20:59:28,984 DEBUG:  NVidia(nvidia_173_updates).enabled(): target_alt None current_alt  /usr/lib/nvidia-304/ld.so.conf other target alt None other current alt  /usr/lib/nvidia-304/alt_ld.so.conf
2013-08-25 20:59:28,984 DEBUG: nvidia_173_updates is not the alternative in use
2013-08-25 20:59:28,965 DEBUG: got handler  xorg:nvidia_173_updates([NvidiaDriver173Updates, nonfree, disabled]  NVIDIA accelerated graphics driver (post-release updates))
2013-08-25 20:59:28,984 DEBUG: searching handler for  driver ID {'driver_type': 'kernel_module', 'kernel_module':  'nvidia_96_updates', 'package': 'nvidia-96-updates'}
2013-08-25 20:59:29,003 DEBUG:  NVidia(nvidia_96_updates).enabled(): target_alt None current_alt  /usr/lib/nvidia-304/ld.so.conf other target alt None other current alt  /usr/lib/nvidia-304/alt_ld.so.conf
2013-08-25 20:59:29,004 DEBUG: nvidia_96_updates is not the alternative in use
2013-08-25 20:59:28,985 DEBUG: found match in handler  pool xorg:nvidia_96_updates([NvidiaDriver96Updates, nonfree, disabled]  NVIDIA accelerated graphics driver (post-release updates))
2013-08-25 20:59:29,009 WARNING: modinfo for module  nvidia_96_updates failed: ERROR: modinfo: could not find module  nvidia_96_updates
 
2013-08-25 20:59:29,016 DEBUG: nvidia.available: falling back to default
2013-08-25 20:59:30,898 DEBUG:  XorgDriverHandler(nvidia_96_updates, nvidia-96-updates, None): Disabling  as package video ABI(s) xorg-video-abi-10 not compatible with X.org  video ABI xorg-video-abi-11
2013-08-25 20:59:30,918 DEBUG:  NVidia(nvidia_96_updates).enabled(): target_alt None current_alt  /usr/lib/nvidia-304/ld.so.conf other target alt None other current alt  /usr/lib/nvidia-304/alt_ld.so.conf
2013-08-25 20:59:30,918 DEBUG: nvidia_96_updates is not the alternative in use
2013-08-25 20:59:30,898 DEBUG: ignoring unavailable  handler xorg:nvidia_96_updates([NvidiaDriver96Updates, nonfree,  disabled] NVIDIA accelerated graphics driver (post-release updates))
2013-08-25 20:59:30,918 DEBUG: searching handler for  driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidia_96',  'package': 'nvidia-96'}
2013-08-25 20:59:30,937 DEBUG:  NVidia(nvidia_96).enabled(): target_alt None current_alt  /usr/lib/nvidia-304/ld.so.conf other target alt None other current alt  /usr/lib/nvidia-304/alt_ld.so.conf
2013-08-25 20:59:30,937 DEBUG: nvidia_96 is not the alternative in use
2013-08-25 20:59:30,918 DEBUG: found match in handler  pool xorg:nvidia_96([NvidiaDriver96, nonfree, disabled] NVIDIA  accelerated graphics driver)
2013-08-25 20:59:30,943 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96
 
2013-08-25 20:59:30,950 DEBUG: nvidia.available: falling back to default
2013-08-25 20:59:34,810 DEBUG:  NVidia(nvidia_96).enabled(): target_alt None current_alt  /usr/lib/nvidia-304/ld.so.conf other target alt None other current alt  /usr/lib/nvidia-304/alt_ld.so.conf
2013-08-25 20:59:34,810 DEBUG: nvidia_96 is not the alternative in use
2013-08-25 20:59:34,791 DEBUG: got handler  xorg:nvidia_96([NvidiaDriver96, nonfree, disabled] NVIDIA accelerated  graphics driver)
2013-08-25 20:59:34,811 DEBUG: searching handler for  driver ID {'driver_type': 'kernel_module', 'kernel_module':  'nvidia_173', 'package': 'nvidia-173'}
2013-08-25 20:59:34,830 DEBUG:  NVidia(nvidia_173).enabled(): target_alt None current_alt  /usr/lib/nvidia-304/ld.so.conf other target alt None other current alt  /usr/lib/nvidia-304/alt_ld.so.conf
2013-08-25 20:59:34,830 DEBUG: nvidia_173 is not the alternative in use
2013-08-25 20:59:34,811 DEBUG: found match in handler  pool xorg:nvidia_173([NvidiaDriver173, nonfree, disabled] NVIDIA  accelerated graphics driver)
2013-08-25 20:59:34,835 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173
 
2013-08-25 20:59:34,843 DEBUG: nvidia.available: falling back to default
2013-08-25 20:59:42,659 DEBUG:  NVidia(nvidia_173).enabled(): target_alt None current_alt  /usr/lib/nvidia-304/ld.so.conf other target alt None other current alt  /usr/lib/nvidia-304/alt_ld.so.conf
2013-08-25 20:59:42,660 DEBUG: nvidia_173 is not the alternative in use
2013-08-25 20:59:42,640 DEBUG: got handler  xorg:nvidia_173([NvidiaDriver173, nonfree, disabled] NVIDIA accelerated  graphics driver)
2013-08-25 20:59:42,660 DEBUG: searching handler for  driver ID {'driver_type': 'kernel_module', 'kernel_module':  'nvidia_304_updates', 'package': 'nvidia-304-updates'}
2013-08-25 20:59:42,678 DEBUG:  NVidia(nvidia_304_updates).enabled(): target_alt None current_alt  /usr/lib/nvidia-304/ld.so.conf other target alt None other current alt  /usr/lib/nvidia-304/alt_ld.so.conf
2013-08-25 20:59:42,679 DEBUG: nvidia_304_updates is not the alternative in use
2013-08-25 20:59:42,660 DEBUG: found match in handler  pool xorg:nvidia_304_updates([NvidiaDriver304Updates, nonfree, disabled]  NVIDIA accelerated graphics driver (post-release updates))
2013-08-25 20:59:42,684 WARNING: modinfo for module  nvidia_304_updates failed: ERROR: modinfo: could not find module  nvidia_304_updates
 
2013-08-25 20:59:42,691 DEBUG: nvidia.available: falling back to default
2013-08-25 20:59:49,235 DEBUG:  NVidia(nvidia_304_updates).enabled(): target_alt None current_alt  /usr/lib/nvidia-304/ld.so.conf other target alt None other current alt  /usr/lib/nvidia-304/alt_ld.so.conf
2013-08-25 20:59:49,235 DEBUG: nvidia_304_updates is not the alternative in use
2013-08-25 20:59:49,216 DEBUG: got handler  xorg:nvidia_304_updates([NvidiaDriver304Updates, nonfree, disabled]  NVIDIA accelerated graphics driver (post-release updates))
2013-08-25 20:59:49,235 DEBUG: searching handler for  driver ID {'driver_type': 'kernel_module', 'kernel_module':  'nvidia_304', 'package': 'nvidia-304'}
2013-08-25 20:59:49,254 DEBUG:  NVidia(nvidia_304).enabled(): target_alt /usr/lib/nvidia-304/ld.so.conf  current_alt /usr/lib/nvidia-304/ld.so.conf other target alt  /usr/lib/nvidia-304/alt_ld.so.conf other current alt  /usr/lib/nvidia-304/alt_ld.so.conf
2013-08-25 20:59:49,254 DEBUG: KMH enabled: False
2013-08-25 20:59:49,236 DEBUG: found match in handler  pool xorg:nvidia_304([NvidiaDriver304, nonfree, disabled] NVIDIA  accelerated graphics driver)
2013-08-25 20:59:49,260 WARNING: modinfo for module nvidia_304 failed: ERROR: modinfo: could not find module nvidia_304
 
2013-08-25 20:59:49,267 DEBUG: nvidia.available: falling back to default
2013-08-25 20:59:55,783 DEBUG:  NVidia(nvidia_304).enabled(): target_alt /usr/lib/nvidia-304/ld.so.conf  current_alt /usr/lib/nvidia-304/ld.so.conf other target alt  /usr/lib/nvidia-304/alt_ld.so.conf other current alt  /usr/lib/nvidia-304/alt_ld.so.conf
2013-08-25 20:59:55,784 DEBUG: KMH enabled: False
2013-08-25 20:59:55,764 DEBUG: got handler  xorg:nvidia_304([NvidiaDriver304, nonfree, disabled] NVIDIA accelerated  graphics driver)
2013-08-25 20:59:55,784 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x971ffec> about HardwareID('modalias', 'acpi:PNP0C04:')
2013-08-25 20:59:55,784 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x971ffec> about HardwareID('modalias',  'pci:v00001002d00004396sv00001458sd00005004bc0Csc03i20')
2013-08-25 20:59:55,793 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x971ffec> about HardwareID('modalias', 'acpi:PNP0200:')
2013-08-25 20:59:55,793 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x971ffec> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2013-08-25 20:59:55,793 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x971ffec> about HardwareID('modalias',  'usb:v1D6Bp0002d0302dc09dsc00dp00ic09isc00ip00')
2013-08-25 20:59:55,794 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x971ffec> about HardwareID('modalias',  'pci:v00001002d0000439Csv00001458sd00005002bc01sc01i8a')
2013-08-25 20:59:55,802 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pata_atiixp'}
2013-08-25 20:59:55,803 DEBUG: no corresponding handler  available for {'driver_type': 'kernel_module', 'kernel_module':  'pata_atiixp', 'jockey_handler': 'KernelModuleHandler'}
2013-08-25 20:59:55,803 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x971ffec> about HardwareID('modalias',  'pci:v00001022d00001202sv00000000sd00000000bc06sc00i00')
2013-08-25 20:59:55,803 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x971ffec> about HardwareID('modalias',  'input:b0003v09DAp000Ae0110-e0,1,2,4,k110,111,112,113,114,115,116,117,r0,1,6,8,9,am4,lsfw')
2013-08-25 20:59:55,804 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-08-25 20:59:55,804 DEBUG: no corresponding handler  available for {'driver_type': 'kernel_module', 'kernel_module':  'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-08-25 20:59:55,804 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-08-25 20:59:55,804 DEBUG: no corresponding handler  available for {'driver_type': 'kernel_module', 'kernel_module':  'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-08-25 20:59:55,804 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x971ffec> about HardwareID('modalias',  'input:b0000v0000p0000e0000-e0,5,kramlsfw6,')
2013-08-25 20:59:55,805 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-08-25 20:59:55,805 DEBUG: no corresponding handler  available for {'driver_type': 'kernel_module', 'kernel_module':  'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-08-25 20:59:55,805 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x971ffec> about HardwareID('modalias',  'usb:v0951p1624d0100dc00dsc00dp00ic08isc06ip50')
2013-08-25 20:59:55,807 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x971ffec> about HardwareID('modalias',  'input:b0003v1038p0210e0111-e0,1,4,k71,72,73,80,8C,90,9B,9C,9E,9F,A3,A4,A5,A6,AB,AC,AD,D9,ram4,lsfw')
2013-08-25 20:59:55,808 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-08-25 20:59:55,808 DEBUG: no corresponding handler  available for {'driver_type': 'kernel_module', 'kernel_module':  'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-08-25 20:59:55,808 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-08-25 20:59:55,808 DEBUG: no corresponding handler  available for {'driver_type': 'kernel_module', 'kernel_module':  'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-08-25 20:59:55,808 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x971ffec> about HardwareID('modalias',  'pci:v00001002d00004385sv00001458sd00004385bc0Csc05i00')
2013-08-25 20:59:55,817 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'i2c_piix4'}
2013-08-25 20:59:55,817 DEBUG: no corresponding handler  available for {'driver_type': 'kernel_module', 'kernel_module':  'i2c_piix4', 'jockey_handler': 'KernelModuleHandler'}
2013-08-25 20:59:55,817 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'sp5100_tco'}
2013-08-25 20:59:55,818 DEBUG: no corresponding handler  available for {'driver_type': 'kernel_module', 'kernel_module':  'sp5100_tco', 'jockey_handler': 'KernelModuleHandler'}
2013-08-25 20:59:55,818 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x971ffec> about HardwareID('modalias',  'dmi:bvnAwardSoftwareInternational,Inc.:bvrF6:bd11/20/2009:svnGigabyteTechnologyCo.,Ltd.:pnGA-MA790X-UD3P:pvr:rvnGigabyteTechnologyCo.,Ltd.:rnGA-MA790X-UD3P:rvrx.x:cvnGigabyteTechnologyCo.,Ltd.:ct3:cvr:')
2013-08-25 20:59:55,851 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x971ffec> about HardwareID('modalias', 'acpi:PNP0B00:')
2013-08-25 20:59:55,851 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x971ffec> about HardwareID('modalias',  'input:b0000v0000p0000e0000-e0,5,kramlsfwD,')
2013-08-25 20:59:55,851 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-08-25 20:59:55,852 DEBUG: no corresponding handler  available for {'driver_type': 'kernel_module', 'kernel_module':  'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-08-25 20:59:55,852 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x971ffec> about HardwareID('modalias',  'usb:v1038p0210d0170dc00dsc00dp00ic03isc01ip01')
2013-08-25 20:59:55,852 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2013-08-25 20:59:55,852 DEBUG: no corresponding handler  available for {'driver_type': 'kernel_module', 'kernel_module':  'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2013-08-25 20:59:55,852 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd'}
2013-08-25 20:59:55,852 DEBUG: no corresponding handler  available for {'driver_type': 'kernel_module', 'kernel_module':  'usbkbd', 'jockey_handler': 'KernelModuleHandler'}
2013-08-25 20:59:55,852 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x971ffec> about HardwareID('modalias',  'usb:v1038p0210d0170dc00dsc00dp00ic03isc00ip00')
2013-08-25 20:59:55,853 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2013-08-25 20:59:55,853 DEBUG: no corresponding handler  available for {'driver_type': 'kernel_module', 'kernel_module':  'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2013-08-25 20:59:55,853 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x971ffec> about HardwareID('modalias', 'acpi:PNP0700:')
2013-08-25 20:59:55,853 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x971ffec> about HardwareID('modalias', 'acpi:PNP0C01:')
2013-08-25 20:59:55,853 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x971ffec> about HardwareID('modalias',  'pci:v00001022d00001201sv00000000sd00000000bc06sc00i00')
2013-08-25 20:59:55,853 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x971ffec> about HardwareID('modalias',  'usb:v0FCEp0170d0231dc00dsc00dp00icFFiscFFip00')
2013-08-25 20:59:55,853 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x971ffec> about HardwareID('modalias',  'pci:v00001002d00004390sv00001458sd0000B002bc01sc06i01')
2013-08-25 20:59:55,858 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x971ffec> about HardwareID('modalias',  'pci:v00001022d00001200sv00000000sd00000000bc06sc00i00')
2013-08-25 20:59:55,858 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x971ffec> about HardwareID('modalias',  'pci:v00001002d00004383sv00001458sd0000A002bc04sc03i00')
2013-08-25 20:59:55,862 DEBUG: searching handler for  driver ID {'driver_type': 'kernel_module', 'kernel_module':  'snd_hda_intel'}
2013-08-25 20:59:55,863 DEBUG: no corresponding handler  available for {'driver_type': 'kernel_module', 'kernel_module':  'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2013-08-25 20:59:55,863 DEBUG: searching handler for  driver ID {'driver_type': 'kernel_module', 'kernel_module':  'snd_hda_intel'}
2013-08-25 20:59:55,863 DEBUG: no corresponding handler  available for {'driver_type': 'kernel_module', 'kernel_module':  'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2013-08-25 20:59:55,863 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x971ffec> about HardwareID('modalias',  'pci:v0000197Bd00002363sv00001458sd0000B000bc01sc06i01')
2013-08-25 20:59:55,863 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x971ffec> about HardwareID('modalias', 'acpi:PNP0100:')
2013-08-25 20:59:55,863 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x971ffec> about HardwareID('modalias',  'usb:v09DAp000Ad0014dc00dsc00dp00ic03isc01ip02')
2013-08-25 20:59:55,863 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2013-08-25 20:59:55,863 DEBUG: no corresponding handler  available for {'driver_type': 'kernel_module', 'kernel_module':  'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2013-08-25 20:59:55,864 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse'}
2013-08-25 20:59:55,864 DEBUG: no corresponding handler  available for {'driver_type': 'kernel_module', 'kernel_module':  'usbmouse', 'jockey_handler': 'KernelModuleHandler'}
2013-08-25 20:59:55,864 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x971ffec> about HardwareID('modalias',  'pci:v00001002d0000439Dsv00001002sd0000439Dbc06sc01i00')
2013-08-25 20:59:55,868 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x971ffec> about HardwareID('modalias', 'platform:pcspkr')
2013-08-25 20:59:55,869 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr'}
2013-08-25 20:59:55,869 DEBUG: no corresponding handler  available for {'driver_type': 'kernel_module', 'kernel_module':  'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2013-08-25 20:59:55,869 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp'}
2013-08-25 20:59:55,869 DEBUG: no corresponding handler  available for {'driver_type': 'kernel_module', 'kernel_module':  'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2013-08-25 20:59:55,869 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x971ffec> about HardwareID('modalias', 'serio:ty06pr00id00ex00')
2013-08-25 20:59:55,878 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw'}
2013-08-25 20:59:55,878 DEBUG: no corresponding handler  available for {'driver_type': 'kernel_module', 'kernel_module':  'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2013-08-25 20:59:55,878 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x971ffec> about HardwareID('modalias',  'pci:v0000104Cd00008024sv00001458sd00001000bc0Csc00i10')
2013-08-25 20:59:55,890 DEBUG: searching handler for  driver ID {'driver_type': 'kernel_module', 'kernel_module':  'firewire_ohci'}
2013-08-25 20:59:55,890 DEBUG: no corresponding handler  available for {'driver_type': 'kernel_module', 'kernel_module':  'firewire_ohci', 'jockey_handler': 'KernelModuleHandler'}
2013-08-25 20:59:55,890 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x971ffec> about HardwareID('modalias',  'input:b0003v1038p0210e0111-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,8C,8E,96,98,9E,9F,A1,A3,A4,A5,A6,AD,B0,B1,B2,B3,B4,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,sfw')
2013-08-25 20:59:55,891 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-08-25 20:59:55,891 DEBUG: no corresponding handler  available for {'driver_type': 'kernel_module', 'kernel_module':  'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-08-25 20:59:55,891 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-08-25 20:59:55,891 DEBUG: no corresponding handler  available for {'driver_type': 'kernel_module', 'kernel_module':  'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-08-25 20:59:55,891 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x971ffec> about HardwareID('modalias', 'acpi:PNP0501:')
2013-08-25 20:59:55,891 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x97275cc>  about HardwareID('modalias',  'pci:v0000197Bd00002363sv00001458sd0000B000bc01sc01i85')
2013-08-25 20:59:55,891 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x97275cc>  about HardwareID('modalias',  'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2013-08-25 20:59:55,891 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x97275cc>  about HardwareID('modalias',  'pci:v00001022d00001204sv00000000sd00000000bc06sc00i00')
2013-08-25 20:59:55,891 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x97275cc>  about HardwareID('modalias',  'pci:v00001022d00001203sv00000000sd00000000bc06sc00i00')
2013-08-25 20:59:55,891 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x97275cc>  about HardwareID('modalias', 'acpi:PNP0C02:')
2013-08-25 20:59:55,891 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x97275cc>  about HardwareID('modalias', 'acpi:PNP0103:')
2013-08-25 20:59:55,892 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x97275cc>  about HardwareID('modalias',  'pci:v000010ECd00008168sv00001458sd0000E000bc02sc00i00')
2013-08-25 20:59:55,892 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x97275cc>  about HardwareID('modalias',  'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2013-08-25 20:59:55,892 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x97275cc>  about HardwareID('modalias', 'platform:eisa')
2013-08-25 20:59:55,892 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x97275cc>  about HardwareID('modalias',  'usb:v1D6Bp0001d0302dc09dsc00dp00ic09isc00ip00')
2013-08-25 20:59:55,892 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x97275cc>  about HardwareID('modalias',  'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2013-08-25 20:59:55,892 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x97275cc>  about HardwareID('modalias', 'acpi:PNP0800:')
2013-08-25 20:59:55,892 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x97275cc>  about HardwareID('modalias', 'platform:Fixed MDIO bus')
2013-08-25 20:59:55,892 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x97275cc>  about HardwareID('modalias',  'pci:v00001002d00004384sv00000000sd00000000bc06sc04i01')
2013-08-25 20:59:55,892 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x97275cc>  about HardwareID('modalias', 'platform:SP5100 TCO timer')
2013-08-25 20:59:55,892 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x97275cc>  about HardwareID('modalias', 'wmi:ABBC0F6A-8EA1-11D1-00A0-C90629100000')
2013-08-25 20:59:55,892 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x97275cc>  about HardwareID('modalias',  'pci:v00001002d00005958sv00001002sd00005958bc06sc00i00')
2013-08-25 20:59:55,892 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x97275cc>  about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2013-08-25 20:59:55,892 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x97275cc>  about HardwareID('modalias', 'acpi:LNXSYBUS:')
2013-08-25 20:59:55,892 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x97275cc>  about HardwareID('modalias', 'acpi:PNP0000:')
2013-08-25 20:59:55,892 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x97275cc>  about HardwareID('modalias',  'pci:v000010DEd00000290sv000010DEsd00000343bc03sc00i00')
2013-08-25 20:59:55,893 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x97275cc>  about HardwareID('modalias', 'acpi:PNP0C04:')
2013-08-25 20:59:55,893 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x97275cc>  about HardwareID('modalias',  'pci:v00001002d00004396sv00001458sd00005004bc0Csc03i20')
2013-08-25 20:59:55,893 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x97275cc>  about HardwareID('modalias', 'acpi:PNP0200:')
2013-08-25 20:59:55,893 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x97275cc>  about HardwareID('modalias', 'acpi:LNXSYSTM:')
2013-08-25 20:59:55,893 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x97275cc>  about HardwareID('modalias',  'usb:v1D6Bp0002d0302dc09dsc00dp00ic09isc00ip00')
2013-08-25 20:59:55,893 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x97275cc>  about HardwareID('modalias',  'pci:v00001002d0000439Csv00001458sd00005002bc01sc01i8a')
2013-08-25 20:59:55,893 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x97275cc>  about HardwareID('modalias',  'pci:v00001022d00001202sv00000000sd00000000bc06sc00i00')
2013-08-25 20:59:55,893 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x97275cc>  about HardwareID('modalias',  'input:b0003v09DAp000Ae0110-e0,1,2,4,k110,111,112,113,114,115,116,117,r0,1,6,8,9,am4,lsfw')
2013-08-25 20:59:55,893 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x97275cc>  about HardwareID('modalias',  'input:b0000v0000p0000e0000-e0,5,kramlsfw6,')
2013-08-25 20:59:55,893 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x97275cc>  about HardwareID('modalias',  'usb:v0951p1624d0100dc00dsc00dp00ic08isc06ip50')
2013-08-25 20:59:55,893 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x97275cc>  about HardwareID('modalias',  'input:b0003v1038p0210e0111-e0,1,4,k71,72,73,80,8C,90,9B,9C,9E,9F,A3,A4,A5,A6,AB,AC,AD,D9,ram4,lsfw')
2013-08-25 20:59:55,893 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x97275cc>  about HardwareID('modalias',  'pci:v00001002d00004385sv00001458sd00004385bc0Csc05i00')
2013-08-25 20:59:55,893 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x97275cc>  about HardwareID('modalias',  'dmi:bvnAwardSoftwareInternational,Inc.:bvrF6:bd11/20/2009:svnGigabyteTechnologyCo.,Ltd.:pnGA-MA790X-UD3P:pvr:rvnGigabyteTechnologyCo.,Ltd.:rnGA-MA790X-UD3P:rvrx.x:cvnGigabyteTechnologyCo.,Ltd.:ct3:cvr:')
2013-08-25 20:59:55,893 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x97275cc>  about HardwareID('modalias', 'acpi:PNP0B00:')
2013-08-25 20:59:55,893 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x97275cc>  about HardwareID('modalias',  'input:b0000v0000p0000e0000-e0,5,kramlsfwD,')
2013-08-25 20:59:55,894 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x97275cc>  about HardwareID('modalias',  'usb:v1038p0210d0170dc00dsc00dp00ic03isc01ip01')
2013-08-25 20:59:55,894 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x97275cc>  about HardwareID('modalias',  'usb:v1038p0210d0170dc00dsc00dp00ic03isc00ip00')
2013-08-25 20:59:55,894 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x97275cc>  about HardwareID('modalias', 'acpi:PNP0700:')
2013-08-25 20:59:55,894 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x97275cc>  about HardwareID('modalias', 'acpi:PNP0C01:')
2013-08-25 20:59:55,894 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x97275cc>  about HardwareID('modalias',  'pci:v00001022d00001201sv00000000sd00000000bc06sc00i00')
2013-08-25 20:59:55,894 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x97275cc>  about HardwareID('modalias',  'usb:v0FCEp0170d0231dc00dsc00dp00icFFiscFFip00')
2013-08-25 20:59:55,894 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x97275cc>  about HardwareID('modalias',  'pci:v00001002d00004390sv00001458sd0000B002bc01sc06i01')
2013-08-25 20:59:55,894 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x97275cc>  about HardwareID('modalias',  'pci:v00001022d00001200sv00000000sd00000000bc06sc00i00')
2013-08-25 20:59:55,894 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x97275cc>  about HardwareID('modalias',  'pci:v00001002d00004383sv00001458sd0000A002bc04sc03i00')
2013-08-25 20:59:55,894 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x97275cc>  about HardwareID('modalias',  'pci:v0000197Bd00002363sv00001458sd0000B000bc01sc06i01')
2013-08-25 20:59:55,894 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x97275cc>  about HardwareID('modalias', 'acpi:PNP0100:')
2013-08-25 20:59:55,894 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x97275cc>  about HardwareID('modalias',  'usb:v09DAp000Ad0014dc00dsc00dp00ic03isc01ip02')
2013-08-25 20:59:55,894 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x97275cc>  about HardwareID('modalias',  'pci:v00001002d0000439Dsv00001002sd0000439Dbc06sc01i00')
2013-08-25 20:59:55,894 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x97275cc>  about HardwareID('modalias', 'platform:pcspkr')
2013-08-25 20:59:55,894 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x97275cc>  about HardwareID('modalias', 'serio:ty06pr00id00ex00')
2013-08-25 20:59:55,895 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x97275cc>  about HardwareID('modalias',  'pci:v0000104Cd00008024sv00001458sd00001000bc0Csc00i10')
2013-08-25 20:59:55,895 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x97275cc>  about HardwareID('modalias',  'input:b0003v1038p0210e0111-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,8C,8E,96,98,9E,9F,A1,A3,A4,A5,A6,AD,B0,B1,B2,B3,B4,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,sfw')
2013-08-25 20:59:55,895 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x97275cc>  about HardwareID('modalias', 'acpi:PNP0501:')
2013-08-25 20:59:55,959 DEBUG: handler xorg:nvidia_173 previously unseen
2013-08-25 20:59:55,960 DEBUG: handler xorg:nvidia_304 previously unseen
2013-08-25 20:59:55,960 DEBUG: handler xorg:nvidia_304_updates previously unseen
2013-08-25 20:59:55,960 DEBUG: handler xorg:nvidia_96 previously unseen
2013-08-25 20:59:55,960 DEBUG: handler xorg:nvidia_173_updates previously unseen
2013-08-25 20:59:55,961 DEBUG: writing back check cache /var/cache/jockey/check
2013-08-25 20:59:55,979 DEBUG:  NVidia(nvidia_173).enabled(): target_alt None current_alt  /usr/lib/nvidia-304/ld.so.conf other target alt None other current alt  /usr/lib/nvidia-304/alt_ld.so.conf
2013-08-25 20:59:55,980 DEBUG: nvidia_173 is not the alternative in use
2013-08-25 20:59:55,998 DEBUG:  NVidia(nvidia_304).enabled(): target_alt /usr/lib/nvidia-304/ld.so.conf  current_alt /usr/lib/nvidia-304/ld.so.conf other target alt  /usr/lib/nvidia-304/alt_ld.so.conf other current alt  /usr/lib/nvidia-304/alt_ld.so.conf
2013-08-25 20:59:55,999 DEBUG: KMH enabled: False
2013-08-25 20:59:56,017 DEBUG:  NVidia(nvidia_304_updates).enabled(): target_alt None current_alt  /usr/lib/nvidia-304/ld.so.conf other target alt None other current alt  /usr/lib/nvidia-304/alt_ld.so.conf
2013-08-25 20:59:56,017 DEBUG: nvidia_304_updates is not the alternative in use
2013-08-25 20:59:56,036 DEBUG:  NVidia(nvidia_96).enabled(): target_alt None current_alt  /usr/lib/nvidia-304/ld.so.conf other target alt None other current alt  /usr/lib/nvidia-304/alt_ld.so.conf
2013-08-25 20:59:56,036 DEBUG: nvidia_96 is not the alternative in use
2013-08-25 20:59:56,054 DEBUG:  NVidia(nvidia_173_updates).enabled(): target_alt None current_alt  /usr/lib/nvidia-304/ld.so.conf other target alt None other current alt  /usr/lib/nvidia-304/alt_ld.so.conf
2013-08-25 20:59:56,055 DEBUG: nvidia_173_updates is not the alternative in use
2013-08-25 20:59:56,089 DEBUG:  NVidia(nvidia_173).enabled(): target_alt None current_alt  /usr/lib/nvidia-304/ld.so.conf other target alt None other current alt  /usr/lib/nvidia-304/alt_ld.so.conf
2013-08-25 20:59:56,089 DEBUG: nvidia_173 is not the alternative in use
2013-08-25 21:00:35,819 DEBUG:  NVidia(nvidia_173).enabled(): target_alt None current_alt  /usr/lib/nvidia-304/ld.so.conf other target alt None other current alt  /usr/lib/nvidia-304/alt_ld.so.conf
2013-08-25 21:00:35,820 DEBUG: nvidia_173 is not the alternative in use
2013-08-25 21:00:35,896 DEBUG:  NVidia(nvidia_173_updates).enabled(): target_alt None current_alt  /usr/lib/nvidia-304/ld.so.conf other target alt None other current alt  /usr/lib/nvidia-304/alt_ld.so.conf
2013-08-25 21:00:35,896 DEBUG: nvidia_173_updates is not the alternative in use
2013-08-25 21:00:36,972 DEBUG:  NVidia(nvidia_304).enabled(): target_alt /usr/lib/nvidia-304/ld.so.conf  current_alt /usr/lib/nvidia-304/ld.so.conf other target alt  /usr/lib/nvidia-304/alt_ld.so.conf other current alt  /usr/lib/nvidia-304/alt_ld.so.conf
2013-08-25 21:00:36,972 DEBUG: KMH enabled: False
2013-08-25 21:00:38,067 DEBUG:  NVidia(nvidia_304_updates).enabled(): target_alt None current_alt  /usr/lib/nvidia-304/ld.so.conf other target alt None other current alt  /usr/lib/nvidia-304/alt_ld.so.conf
2013-08-25 21:00:38,067 DEBUG: nvidia_304_updates is not the alternative in use
2013-08-25 21:00:39,153 DEBUG:  NVidia(nvidia_96).enabled(): target_alt None current_alt  /usr/lib/nvidia-304/ld.so.conf other target alt None other current alt  /usr/lib/nvidia-304/alt_ld.so.conf
2013-08-25 21:00:39,153 DEBUG: nvidia_96 is not the alternative in use
2013-08-25 21:00:40,256 DEBUG:  NVidia(nvidia_173).enabled(): target_alt None current_alt  /usr/lib/nvidia-304/ld.so.conf other target alt None other current alt  /usr/lib/nvidia-304/alt_ld.so.conf
2013-08-25 21:00:40,257 DEBUG: nvidia_173 is not the alternative in use
2013-08-25 21:00:40,319 DEBUG:  NVidia(nvidia_173).enabled(): target_alt None current_alt  /usr/lib/nvidia-304/ld.so.conf other target alt None other current alt  /usr/lib/nvidia-304/alt_ld.so.conf
2013-08-25 21:00:40,319 DEBUG: nvidia_173 is not the alternative in use
2013-08-25 21:00:40,365 DEBUG:  NVidia(nvidia_173_updates).enabled(): target_alt None current_alt  /usr/lib/nvidia-304/ld.so.conf other target alt None other current alt  /usr/lib/nvidia-304/alt_ld.so.conf
2013-08-25 21:00:40,365 DEBUG: nvidia_173_updates is not the alternative in use
2013-08-25 21:00:40,411 DEBUG:  NVidia(nvidia_304).enabled(): target_alt /usr/lib/nvidia-304/ld.so.conf  current_alt /usr/lib/nvidia-304/ld.so.conf other target alt  /usr/lib/nvidia-304/alt_ld.so.conf other current alt  /usr/lib/nvidia-304/alt_ld.so.conf
2013-08-25 21:00:40,411 DEBUG: KMH enabled: False
2013-08-25 21:00:40,456 DEBUG:  NVidia(nvidia_304_updates).enabled(): target_alt None current_alt  /usr/lib/nvidia-304/ld.so.conf other target alt None other current alt  /usr/lib/nvidia-304/alt_ld.so.conf
2013-08-25 21:00:40,457 DEBUG: nvidia_304_updates is not the alternative in use
2013-08-25 21:00:40,502 DEBUG:  NVidia(nvidia_96).enabled(): target_alt None current_alt  /usr/lib/nvidia-304/ld.so.conf other target alt None other current alt  /usr/lib/nvidia-304/alt_ld.so.conf
2013-08-25 21:00:40,502 DEBUG: nvidia_96 is not the alternative in use
2013-08-25 21:00:50,501 DEBUG:  NVidia(nvidia_304).enabled(): target_alt /usr/lib/nvidia-304/ld.so.conf  current_alt /usr/lib/nvidia-304/ld.so.conf other target alt  /usr/lib/nvidia-304/alt_ld.so.conf other current alt  /usr/lib/nvidia-304/alt_ld.so.conf
2013-08-25 21:00:50,502 DEBUG: KMH enabled: False
2013-08-25 21:00:51,149 DEBUG:  NVidia(nvidia_304_updates).enabled(): target_alt None current_alt  /usr/lib/nvidia-304/ld.so.conf other target alt None other current alt  /usr/lib/nvidia-304/alt_ld.so.conf
2013-08-25 21:00:51,149 DEBUG: nvidia_304_updates is not the alternative in use
2013-08-25 21:00:51,812 DEBUG:  NVidia(nvidia_173_updates).enabled(): target_alt None current_alt  /usr/lib/nvidia-304/ld.so.conf other target alt None other current alt  /usr/lib/nvidia-304/alt_ld.so.conf
2013-08-25 21:00:51,813 DEBUG: nvidia_173_updates is not the alternative in use
2013-08-25 21:00:52,212 DEBUG:  NVidia(nvidia_173).enabled(): target_alt None current_alt  /usr/lib/nvidia-304/ld.so.conf other target alt None other current alt  /usr/lib/nvidia-304/alt_ld.so.conf
2013-08-25 21:00:52,212 DEBUG: nvidia_173 is not the alternative in use
2013-08-25 21:00:52,875 DEBUG:  NVidia(nvidia_304).enabled(): target_alt /usr/lib/nvidia-304/ld.so.conf  current_alt /usr/lib/nvidia-304/ld.so.conf other target alt  /usr/lib/nvidia-304/alt_ld.so.conf other current alt  /usr/lib/nvidia-304/alt_ld.so.conf
2013-08-25 21:00:52,876 DEBUG: KMH enabled: False
2013-08-25 21:00:59,164 DEBUG:  NVidia(nvidia_304).enabled(): target_alt /usr/lib/nvidia-304/ld.so.conf  current_alt /usr/lib/nvidia-304/ld.so.conf other target alt  /usr/lib/nvidia-304/alt_ld.so.conf other current alt  /usr/lib/nvidia-304/alt_ld.so.conf
2013-08-25 21:00:59,165 DEBUG: KMH enabled: False
2013-08-25 21:01:04,463 WARNING: modinfo for module nvidia_304 failed: ERROR: modinfo: could not find module nvidia_304
 
2013-08-25 21:01:04,464 ERROR: XorgDriverHandler.enable(): package or module not installed, aborting
2013-08-25 21:01:30,966 DEBUG:  NVidia(nvidia_304).enabled(): target_alt /usr/lib/nvidia-304/ld.so.conf  current_alt /usr/lib/nvidia-304/ld.so.conf other target alt  /usr/lib/nvidia-304/alt_ld.so.conf other current alt  /usr/lib/nvidia-304/alt_ld.so.conf
2013-08-25 21:01:30,967 DEBUG: KMH enabled: False
2013-08-25 21:01:30,996 DEBUG:  NVidia(nvidia_304).enabled(): target_alt /usr/lib/nvidia-304/ld.so.conf  current_alt /usr/lib/nvidia-304/ld.so.conf other target alt  /usr/lib/nvidia-304/alt_ld.so.conf other current alt  /usr/lib/nvidia-304/alt_ld.so.conf
2013-08-25 21:01:30,996 DEBUG: KMH enabled: False
2013-08-25 21:02:22,709 DEBUG:  NVidia(nvidia_173).enabled(): target_alt None current_alt  /usr/lib/nvidia-304/ld.so.conf other target alt None other current alt  /usr/lib/nvidia-304/alt_ld.so.conf
2013-08-25 21:02:22,709 DEBUG: nvidia_173 is not the alternative in use
2013-08-25 21:02:22,760 DEBUG:  NVidia(nvidia_173_updates).enabled(): target_alt None current_alt  /usr/lib/nvidia-304/ld.so.conf other target alt None other current alt  /usr/lib/nvidia-304/alt_ld.so.conf
2013-08-25 21:02:22,760 DEBUG: nvidia_173_updates is not the alternative in use
2013-08-25 21:02:22,811 DEBUG:  NVidia(nvidia_304).enabled(): target_alt /usr/lib/nvidia-304/ld.so.conf  current_alt /usr/lib/nvidia-304/ld.so.conf other target alt  /usr/lib/nvidia-304/alt_ld.so.conf other current alt  /usr/lib/nvidia-304/alt_ld.so.conf
2013-08-25 21:02:22,811 DEBUG: KMH enabled: False
2013-08-25 21:02:22,841 DEBUG:  NVidia(nvidia_304).enabled(): target_alt /usr/lib/nvidia-304/ld.so.conf  current_alt /usr/lib/nvidia-304/ld.so.conf other target alt  /usr/lib/nvidia-304/alt_ld.so.conf other current alt  /usr/lib/nvidia-304/alt_ld.so.conf
2013-08-25 21:02:22,841 DEBUG: KMH enabled: False
2013-08-25 21:02:22,891 DEBUG:  NVidia(nvidia_304_updates).enabled(): target_alt None current_alt  /usr/lib/nvidia-304/ld.so.conf other target alt None other current alt  /usr/lib/nvidia-304/alt_ld.so.conf
2013-08-25 21:02:22,892 DEBUG: nvidia_304_updates is not the alternative in use
2013-08-25 21:02:22,942 DEBUG:  NVidia(nvidia_96).enabled(): target_alt None current_alt  /usr/lib/nvidia-304/ld.so.conf other target alt None other current alt  /usr/lib/nvidia-304/alt_ld.so.conf
2013-08-25 21:02:22,942 DEBUG: nvidia_96 is not the alternative in use
2013-08-25 21:02:23,000 DEBUG:  NVidia(nvidia_304).enabled(): target_alt /usr/lib/nvidia-304/ld.so.conf  current_alt /usr/lib/nvidia-304/ld.so.conf other target alt  /usr/lib/nvidia-304/alt_ld.so.conf other current alt  /usr/lib/nvidia-304/alt_ld.so.conf
2013-08-25 21:02:23,001 DEBUG: KMH enabled: False
2013-08-25 21:02:23,030 DEBUG:  NVidia(nvidia_304).enabled(): target_alt /usr/lib/nvidia-304/ld.so.conf  current_alt /usr/lib/nvidia-304/ld.so.conf other target alt  /usr/lib/nvidia-304/alt_ld.so.conf other current alt  /usr/lib/nvidia-304/alt_ld.so.conf
2013-08-25 21:02:23,030 DEBUG: KMH enabled: False
2013-08-25 21:02:23,098 DEBUG:  NVidia(nvidia_173).enabled(): target_alt None current_alt  /usr/lib/nvidia-304/ld.so.conf other target alt None other current alt  /usr/lib/nvidia-304/alt_ld.so.conf
2013-08-25 21:02:23,098 DEBUG: nvidia_173 is not the alternative in use
2013-08-25 21:02:23,144 DEBUG:  NVidia(nvidia_173_updates).enabled(): target_alt None current_alt  /usr/lib/nvidia-304/ld.so.conf other target alt None other current alt  /usr/lib/nvidia-304/alt_ld.so.conf
2013-08-25 21:02:23,144 DEBUG: nvidia_173_updates is not the alternative in use
2013-08-25 21:02:23,189 DEBUG:  NVidia(nvidia_304).enabled(): target_alt /usr/lib/nvidia-304/ld.so.conf  current_alt /usr/lib/nvidia-304/ld.so.conf other target alt  /usr/lib/nvidia-304/alt_ld.so.conf other current alt  /usr/lib/nvidia-304/alt_ld.so.conf
2013-08-25 21:02:23,190 DEBUG: KMH enabled: False
2013-08-25 21:02:23,219 DEBUG:  NVidia(nvidia_304).enabled(): target_alt /usr/lib/nvidia-304/ld.so.conf  current_alt /usr/lib/nvidia-304/ld.so.conf other target alt  /usr/lib/nvidia-304/alt_ld.so.conf other current alt  /usr/lib/nvidia-304/alt_ld.so.conf
2013-08-25 21:02:23,219 DEBUG: KMH enabled: False
2013-08-25 21:02:23,264 DEBUG:  NVidia(nvidia_304_updates).enabled(): target_alt None current_alt  /usr/lib/nvidia-304/ld.so.conf other target alt None other current alt  /usr/lib/nvidia-304/alt_ld.so.conf
2013-08-25 21:02:23,265 DEBUG: nvidia_304_updates is not the alternative in use
2013-08-25 21:02:23,310 DEBUG:  NVidia(nvidia_96).enabled(): target_alt None current_alt  /usr/lib/nvidia-304/ld.so.conf other target alt None other current alt  /usr/lib/nvidia-304/alt_ld.so.conf
2013-08-25 21:02:23,310 DEBUG: nvidia_96 is not the alternative in use
2013-08-25 21:02:26,526 DEBUG: Shutting down
2013-08-25 21:02:29,824 DEBUG: Comparing 3.2.0-52 with 
2013-08-25 21:02:29,831 DEBUG: Comparing 3.2.0-52 with 3.2.0-52
2013-08-25 21:02:30,300 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x9e41fec>
2013-08-25 21:02:32,062 DEBUG: reading modalias file /lib/modules/3.2.0-52-generic-pae/modules.alias
2013-08-25 21:02:32,165 DEBUG: reading modalias file /usr/share/jockey/modaliases/b43
2013-08-25 21:02:32,165 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2013-08-25 21:02:32,228 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2013-08-25 21:02:32,235 WARNING: modinfo for module  fglrx_experimental_12 failed: ERROR: modinfo: could not find module  fglrx_experimental_12
 
2013-08-25 21:02:32,772 DEBUG: linux-lts-raring installed: False
linux-lts-saucy installed: False
linux minor version: 2
xserver ABI: 11
xserver-lts-quantal: False
2013-08-25 21:02:32,803 DEBUG: Instantiated Handler  subclass __builtin__.FglrxDriverExperimental12 from name  FglrxDriverExperimental12
2013-08-25 21:02:32,803 DEBUG: fglrx.available: falling back to default
2013-08-25 21:02:34,777 DEBUG: ATI/AMD proprietary  FGLRX graphics driver (**experimental** beta) availability undetermined,  adding to pool
2013-08-25 21:02:34,783 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates
 
2013-08-25 21:02:34,789 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriverUpdate from name FglrxDriverUpdate
2013-08-25 21:02:34,789 DEBUG: fglrx.available: falling back to default
2013-08-25 21:02:39,070 DEBUG: ATI/AMD proprietary  FGLRX graphics driver (post-release updates) availability undetermined,  adding to pool
2013-08-25 21:02:39,076 WARNING: modinfo for module  fglrx_experimental_9 failed: ERROR: modinfo: could not find module  fglrx_experimental_9
 
2013-08-25 21:02:39,108 DEBUG: Instantiated Handler  subclass __builtin__.FglrxDriverExperimental9 from name  FglrxDriverExperimental9
2013-08-25 21:02:39,109 DEBUG: fglrx.available: falling back to default
2013-08-25 21:02:41,058 DEBUG: ATI/AMD proprietary  FGLRX graphics driver (**experimental** beta) availability undetermined,  adding to pool
2013-08-25 21:02:41,063 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx
 
2013-08-25 21:02:41,068 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriverHybrid from name FglrxDriverHybrid
2013-08-25 21:02:41,068 DEBUG: fglrx.available: falling back to default
2013-08-25 21:02:46,068 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2013-08-25 21:02:46,073 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx
 
2013-08-25 21:02:46,081 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2013-08-25 21:02:46,081 DEBUG: fglrx.available: falling back to default
2013-08-25 21:02:51,064 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2013-08-25 21:02:51,068 WARNING: modinfo for module  fglrx_experimental_13 failed: ERROR: modinfo: could not find module  fglrx_experimental_13
 
2013-08-25 21:02:51,092 DEBUG: Instantiated Handler  subclass __builtin__.FglrxDriverExperimental13 from name  FglrxDriverExperimental13
2013-08-25 21:02:51,093 DEBUG: fglrx.available: falling back to default
2013-08-25 21:02:53,262 DEBUG: ATI/AMD proprietary  FGLRX graphics driver (**experimental** beta) availability undetermined,  adding to pool
2013-08-25 21:02:53,262 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2013-08-25 21:02:53,290 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2013-08-25 21:02:53,303 DEBUG: Software modem not available
2013-08-25 21:02:53,304 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2013-08-25 21:02:53,310 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl
 
2013-08-25 21:02:53,339 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2013-08-25 21:02:53,339 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2013-08-25 21:02:53,340 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2013-08-25 21:02:53,346 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci
 
2013-08-25 21:02:53,347 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2013-08-25 21:02:53,347 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2013-08-25 21:02:53,347 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2013-08-25 21:02:53,383 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2013-08-25 21:02:53,384 DEBUG: Firmware for DVB cards not available
2013-08-25 21:02:53,384 DEBUG: loading custom handler /usr/share/jockey/handlers/vmware-client.py
2013-08-25 21:02:53,390 WARNING: modinfo for module vmxnet failed: ERROR: modinfo: could not find module vmxnet
 
2013-08-25 21:02:53,390 DEBUG: Instantiated Handler subclass __builtin__.VmwareClientHandler from name VmwareClientHandler
2013-08-25 21:02:53,416 DEBUG: VMWare Client Tools availability undetermined, adding to pool
2013-08-25 21:02:53,416 DEBUG: loading custom handler /usr/share/jockey/handlers/pvr-omap4.py
2013-08-25 21:02:53,425 WARNING: modinfo for module omapdrm_pvr failed: ERROR: modinfo: could not find module omapdrm_pvr
 
2013-08-25 21:02:53,433 DEBUG: Instantiated Handler subclass __builtin__.PVROmap4Driver from name PVROmap4Driver
2013-08-25 21:02:53,909 DEBUG: PowerVR SGX proprietary graphics driver for OMAP 4 not available
2013-08-25 21:02:53,910 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2013-08-25 21:02:53,922 WARNING: modinfo for module nvidia_304 failed: ERROR: modinfo: could not find module nvidia_304
 
2013-08-25 21:02:53,929 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver304 from name NvidiaDriver304
2013-08-25 21:02:53,929 DEBUG: nvidia.available: falling back to default
2013-08-25 21:03:00,251 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2013-08-25 21:03:00,257 WARNING: modinfo for module  nvidia_304_updates failed: ERROR: modinfo: could not find module  nvidia_304_updates
 
2013-08-25 21:03:00,264 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver304Updates from name NvidiaDriver304Updates
2013-08-25 21:03:00,264 DEBUG: nvidia.available: falling back to default
2013-08-25 21:03:06,588 DEBUG: NVIDIA accelerated  graphics driver (post-release updates) availability undetermined, adding  to pool
2013-08-25 21:03:06,594 WARNING: modinfo for module  nvidia_current_updates failed: ERROR: modinfo: could not find module  nvidia_current_updates
 
2013-08-25 21:03:06,601 DEBUG: Instantiated Handler  subclass __builtin__.NvidiaDriverCurrentUpdates from name  NvidiaDriverCurrentUpdates
2013-08-25 21:03:06,601 DEBUG: nvidia.available: falling back to default
2013-08-25 21:03:06,633 DEBUG: NVIDIA accelerated graphics driver (post-release updates) not available
2013-08-25 21:03:06,638 WARNING: modinfo for module  nvidia_experimental_304 failed: ERROR: modinfo: could not find module  nvidia_experimental_304
 
2013-08-25 21:03:06,671 DEBUG: Instantiated Handler  subclass __builtin__.NvidiaDriverExperimental304 from name  NvidiaDriverExperimental304
2013-08-25 21:03:06,671 DEBUG: nvidia.available: falling back to default
2013-08-25 21:03:06,698 DEBUG: NVIDIA accelerated graphics driver (**experimental** beta) not available
2013-08-25 21:03:06,703 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current
 
2013-08-25 21:03:06,710 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2013-08-25 21:03:06,711 DEBUG: nvidia.available: falling back to default
2013-08-25 21:03:06,742 DEBUG: NVIDIA accelerated graphics driver not available
2013-08-25 21:03:06,748 WARNING: modinfo for module nvidia_319 failed: ERROR: modinfo: could not find module nvidia_319
 
2013-08-25 21:03:06,755 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver319 from name NvidiaDriver319
2013-08-25 21:03:06,755 DEBUG: nvidia.available: falling back to default
2013-08-25 21:03:11,227 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2013-08-25 21:03:11,233 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173
 
2013-08-25 21:03:11,240 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2013-08-25 21:03:11,240 DEBUG: nvidia.available: falling back to default
2013-08-25 21:03:18,960 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2013-08-25 21:03:18,966 WARNING: modinfo for module  nvidia_173_updates failed: ERROR: modinfo: could not find module  nvidia_173_updates
 
2013-08-25 21:03:18,973 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173Updates from name NvidiaDriver173Updates
2013-08-25 21:03:18,973 DEBUG: nvidia.available: falling back to default
2013-08-25 21:03:30,285 DEBUG: NVIDIA accelerated  graphics driver (post-release updates) availability undetermined, adding  to pool
2013-08-25 21:03:30,290 WARNING: modinfo for module  nvidia_experimental_310 failed: ERROR: modinfo: could not find module  nvidia_experimental_310
 
2013-08-25 21:03:30,323 DEBUG: Instantiated Handler  subclass __builtin__.NvidiaDriverExperimental310 from name  NvidiaDriverExperimental310
2013-08-25 21:03:30,323 DEBUG: nvidia.available: falling back to default
2013-08-25 21:03:30,350 DEBUG: NVIDIA accelerated graphics driver (**experimental** beta) not available
2013-08-25 21:03:30,355 WARNING: modinfo for module  nvidia_319_updates failed: ERROR: modinfo: could not find module  nvidia_319_updates
 
2013-08-25 21:03:30,362 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver319Updates from name NvidiaDriver319Updates
2013-08-25 21:03:30,363 DEBUG: nvidia.available: falling back to default
2013-08-25 21:03:34,951 DEBUG: NVIDIA accelerated  graphics driver (post-release updates) availability undetermined, adding  to pool
2013-08-25 21:03:34,956 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96
 
2013-08-25 21:03:34,963 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2013-08-25 21:03:34,964 DEBUG: nvidia.available: falling back to default
2013-08-25 21:03:38,654 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2013-08-25 21:03:38,659 WARNING: modinfo for module  nvidia_96_updates failed: ERROR: modinfo: could not find module  nvidia_96_updates
 
2013-08-25 21:03:38,666 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96Updates from name NvidiaDriver96Updates
2013-08-25 21:03:38,666 DEBUG: nvidia.available: falling back to default
2013-08-25 21:03:40,574 DEBUG:  XorgDriverHandler(nvidia_96_updates, nvidia-96-updates, None): Disabling  as package video ABI(s) xorg-video-abi-10 not compatible with X.org  video ABI xorg-video-abi-11
2013-08-25 21:03:40,574 DEBUG: NVIDIA accelerated graphics driver (post-release updates) not available
2013-08-25 21:03:40,575 DEBUG: loading custom handler /usr/share/jockey/handlers/cdv.py
2013-08-25 21:03:40,581 WARNING: modinfo for module cedarview_gfx failed: ERROR: modinfo: could not find module cedarview_gfx
 
2013-08-25 21:03:40,582 DEBUG: Instantiated Handler subclass __builtin__.CdvDriver from name CdvDriver
2013-08-25 21:03:40,583 DEBUG: cdv.available: falling back to default
2013-08-25 21:03:41,091 DEBUG: Intel Cedarview graphics driver availability undetermined, adding to pool
2013-08-25 21:03:41,092 DEBUG: all custom handlers loaded
2013-08-25 21:03:41,092 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x9e41fec> about HardwareID('modalias',  'pci:v0000197Bd00002363sv00001458sd0000B000bc01sc01i85')
2013-08-25 21:03:41,106 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pata_jmicron'}
2013-08-25 21:03:41,198 DEBUG: no corresponding handler  available for {'driver_type': 'kernel_module', 'kernel_module':  'pata_jmicron', 'jockey_handler': 'KernelModuleHandler'}
2013-08-25 21:03:41,198 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x9e41fec> about HardwareID('modalias',  'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2013-08-25 21:03:41,203 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-08-25 21:03:41,204 DEBUG: no corresponding handler  available for {'driver_type': 'kernel_module', 'kernel_module':  'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-08-25 21:03:41,204 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x9e41fec> about HardwareID('modalias',  'pci:v00001022d00001204sv00000000sd00000000bc06sc00i00')
2013-08-25 21:03:41,219 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x9e41fec> about HardwareID('modalias',  'pci:v00001022d00001203sv00000000sd00000000bc06sc00i00')
2013-08-25 21:03:41,219 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'k10temp'}
2013-08-25 21:03:41,219 DEBUG: no corresponding handler  available for {'driver_type': 'kernel_module', 'kernel_module':  'k10temp', 'jockey_handler': 'KernelModuleHandler'}
2013-08-25 21:03:41,219 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x9e41fec> about HardwareID('modalias', 'acpi:PNP0C02:')
2013-08-25 21:03:41,219 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x9e41fec> about HardwareID('modalias', 'acpi:PNP0103:')
2013-08-25 21:03:41,220 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x9e41fec> about HardwareID('modalias',  'pci:v000010ECd00008168sv00001458sd0000E000bc02sc00i00')
2013-08-25 21:03:41,229 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'r8169'}
2013-08-25 21:03:41,229 DEBUG: no corresponding handler  available for {'driver_type': 'kernel_module', 'kernel_module':  'r8169', 'jockey_handler': 'KernelModuleHandler'}
2013-08-25 21:03:41,229 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x9e41fec> about HardwareID('modalias',  'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2013-08-25 21:03:41,229 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-08-25 21:03:41,229 DEBUG: no corresponding handler  available for {'driver_type': 'kernel_module', 'kernel_module':  'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-08-25 21:03:41,229 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x9e41fec> about HardwareID('modalias', 'platform:eisa')
2013-08-25 21:03:41,230 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x9e41fec> about HardwareID('modalias',  'usb:v1D6Bp0001d0302dc09dsc00dp00ic09isc00ip00')
2013-08-25 21:03:41,244 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x9e41fec> about HardwareID('modalias',  'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2013-08-25 21:03:41,244 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-08-25 21:03:41,244 DEBUG: no corresponding handler  available for {'driver_type': 'kernel_module', 'kernel_module':  'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-08-25 21:03:41,244 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-08-25 21:03:41,244 DEBUG: no corresponding handler  available for {'driver_type': 'kernel_module', 'kernel_module':  'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-08-25 21:03:41,244 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x9e41fec> about HardwareID('modalias', 'acpi:PNP0800:')
2013-08-25 21:03:41,244 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x9e41fec> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2013-08-25 21:03:41,245 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x9e41fec> about HardwareID('modalias',  'pci:v00001002d00004384sv00000000sd00000000bc06sc04i01')
2013-08-25 21:03:41,608 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x9e41fec> about HardwareID('modalias', 'platform:SP5100 TCO timer')
2013-08-25 21:03:41,609 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x9e41fec> about HardwareID('modalias',  'wmi:ABBC0F6A-8EA1-11D1-00A0-C90629100000')
2013-08-25 21:03:41,609 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x9e41fec> about HardwareID('modalias',  'pci:v00001002d00005958sv00001002sd00005958bc06sc00i00')
2013-08-25 21:03:41,613 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'ati_agp'}
2013-08-25 21:03:41,613 DEBUG: no corresponding handler  available for {'driver_type': 'kernel_module', 'kernel_module':  'ati_agp', 'jockey_handler': 'KernelModuleHandler'}
2013-08-25 21:03:41,613 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x9e41fec> about HardwareID('modalias',  'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2013-08-25 21:03:41,613 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x9e41fec> about HardwareID('modalias',  'usb:v0951p1624d0100dc00dsc00dp00ic08isc06ip50')
2013-08-25 21:03:41,614 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x9e41fec> about HardwareID('modalias', 'acpi:LNXSYBUS:')
2013-08-25 21:03:41,615 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x9e41fec> about HardwareID('modalias', 'acpi:PNP0000:')
2013-08-25 21:03:41,615 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x9e41fec> about HardwareID('modalias',  'pci:v000010DEd00000290sv000010DEsd00000343bc03sc00i00')
2013-08-25 21:03:41,916 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidiafb'}
2013-08-25 21:03:41,916 DEBUG: no corresponding handler  available for {'driver_type': 'kernel_module', 'kernel_module':  'nvidiafb', 'jockey_handler': 'KernelModuleHandler'}
2013-08-25 21:03:41,916 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nouveau'}
2013-08-25 21:03:41,916 DEBUG: no corresponding handler  available for {'driver_type': 'kernel_module', 'kernel_module':  'nouveau', 'jockey_handler': 'KernelModuleHandler'}
2013-08-25 21:03:41,916 DEBUG: searching handler for  driver ID {'driver_type': 'kernel_module', 'kernel_module':  'nvidia_173_updates', 'package': 'nvidia-173-updates'}
2013-08-25 21:03:41,934 DEBUG:  NVidia(nvidia_173_updates).enabled(): target_alt None current_alt  /usr/lib/nvidia-304/ld.so.conf other target alt None other current alt  /usr/lib/nvidia-304/alt_ld.so.conf
2013-08-25 21:03:41,934 DEBUG: nvidia_173_updates is not the alternative in use
2013-08-25 21:03:41,916 DEBUG: found match in handler  pool xorg:nvidia_173_updates([NvidiaDriver173Updates, nonfree, disabled]  NVIDIA accelerated graphics driver (post-release updates))
2013-08-25 21:03:41,939 WARNING: modinfo for module  nvidia_173_updates failed: ERROR: modinfo: could not find module  nvidia_173_updates
 
2013-08-25 21:03:41,945 DEBUG: nvidia.available: falling back to default
2013-08-25 21:03:53,374 DEBUG:  NVidia(nvidia_173_updates).enabled(): target_alt None current_alt  /usr/lib/nvidia-304/ld.so.conf other target alt None other current alt  /usr/lib/nvidia-304/alt_ld.so.conf
2013-08-25 21:03:53,374 DEBUG: nvidia_173_updates is not the alternative in use
2013-08-25 21:03:53,354 DEBUG: got handler  xorg:nvidia_173_updates([NvidiaDriver173Updates, nonfree, disabled]  NVIDIA accelerated graphics driver (post-release updates))
2013-08-25 21:03:53,375 DEBUG: searching handler for  driver ID {'driver_type': 'kernel_module', 'kernel_module':  'nvidia_96_updates', 'package': 'nvidia-96-updates'}
2013-08-25 21:03:53,394 DEBUG:  NVidia(nvidia_96_updates).enabled(): target_alt None current_alt  /usr/lib/nvidia-304/ld.so.conf other target alt None other current alt  /usr/lib/nvidia-304/alt_ld.so.conf
2013-08-25 21:03:53,395 DEBUG: nvidia_96_updates is not the alternative in use
2013-08-25 21:03:53,375 DEBUG: found match in handler  pool xorg:nvidia_96_updates([NvidiaDriver96Updates, nonfree, disabled]  NVIDIA accelerated graphics driver (post-release updates))
2013-08-25 21:03:53,400 WARNING: modinfo for module  nvidia_96_updates failed: ERROR: modinfo: could not find module  nvidia_96_updates
 
2013-08-25 21:03:53,407 DEBUG: nvidia.available: falling back to default
2013-08-25 21:03:55,233 DEBUG:  XorgDriverHandler(nvidia_96_updates, nvidia-96-updates, None): Disabling  as package video ABI(s) xorg-video-abi-10 not compatible with X.org  video ABI xorg-video-abi-11
2013-08-25 21:03:55,252 DEBUG:  NVidia(nvidia_96_updates).enabled(): target_alt None current_alt  /usr/lib/nvidia-304/ld.so.conf other target alt None other current alt  /usr/lib/nvidia-304/alt_ld.so.conf
2013-08-25 21:03:55,252 DEBUG: nvidia_96_updates is not the alternative in use
2013-08-25 21:03:55,233 DEBUG: ignoring unavailable  handler xorg:nvidia_96_updates([NvidiaDriver96Updates, nonfree,  disabled] NVIDIA accelerated graphics driver (post-release updates))
2013-08-25 21:03:55,253 DEBUG: searching handler for  driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidia_96',  'package': 'nvidia-96'}
2013-08-25 21:03:55,272 DEBUG:  NVidia(nvidia_96).enabled(): target_alt None current_alt  /usr/lib/nvidia-304/ld.so.conf other target alt None other current alt  /usr/lib/nvidia-304/alt_ld.so.conf
2013-08-25 21:03:55,272 DEBUG: nvidia_96 is not the alternative in use
2013-08-25 21:03:55,253 DEBUG: found match in handler  pool xorg:nvidia_96([NvidiaDriver96, nonfree, disabled] NVIDIA  accelerated graphics driver)
2013-08-25 21:03:55,278 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96
 
2013-08-25 21:03:55,285 DEBUG: nvidia.available: falling back to default
2013-08-25 21:03:58,915 DEBUG:  NVidia(nvidia_96).enabled(): target_alt None current_alt  /usr/lib/nvidia-304/ld.so.conf other target alt None other current alt  /usr/lib/nvidia-304/alt_ld.so.conf
2013-08-25 21:03:58,915 DEBUG: nvidia_96 is not the alternative in use
2013-08-25 21:03:58,896 DEBUG: got handler  xorg:nvidia_96([NvidiaDriver96, nonfree, disabled] NVIDIA accelerated  graphics driver)
2013-08-25 21:03:58,916 DEBUG: searching handler for  driver ID {'driver_type': 'kernel_module', 'kernel_module':  'nvidia_173', 'package': 'nvidia-173'}
2013-08-25 21:03:58,935 DEBUG:  NVidia(nvidia_173).enabled(): target_alt None current_alt  /usr/lib/nvidia-304/ld.so.conf other target alt None other current alt  /usr/lib/nvidia-304/alt_ld.so.conf
2013-08-25 21:03:58,936 DEBUG: nvidia_173 is not the alternative in use
2013-08-25 21:03:58,916 DEBUG: found match in handler  pool xorg:nvidia_173([NvidiaDriver173, nonfree, disabled] NVIDIA  accelerated graphics driver)
2013-08-25 21:03:58,941 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173
 
2013-08-25 21:03:58,948 DEBUG: nvidia.available: falling back to default
2013-08-25 21:04:06,366 DEBUG:  NVidia(nvidia_173).enabled(): target_alt None current_alt  /usr/lib/nvidia-304/ld.so.conf other target alt None other current alt  /usr/lib/nvidia-304/alt_ld.so.conf
2013-08-25 21:04:06,366 DEBUG: nvidia_173 is not the alternative in use
2013-08-25 21:04:06,347 DEBUG: got handler  xorg:nvidia_173([NvidiaDriver173, nonfree, disabled] NVIDIA accelerated  graphics driver)
2013-08-25 21:04:06,367 DEBUG: searching handler for  driver ID {'driver_type': 'kernel_module', 'kernel_module':  'nvidia_304_updates', 'package': 'nvidia-304-updates'}
2013-08-25 21:04:06,386 DEBUG:  NVidia(nvidia_304_updates).enabled(): target_alt None current_alt  /usr/lib/nvidia-304/ld.so.conf other target alt None other current alt  /usr/lib/nvidia-304/alt_ld.so.conf
2013-08-25 21:04:06,386 DEBUG: nvidia_304_updates is not the alternative in use
2013-08-25 21:04:06,367 DEBUG: found match in handler  pool xorg:nvidia_304_updates([NvidiaDriver304Updates, nonfree, disabled]  NVIDIA accelerated graphics driver (post-release updates))
2013-08-25 21:04:06,391 WARNING: modinfo for module  nvidia_304_updates failed: ERROR: modinfo: could not find module  nvidia_304_updates
 
2013-08-25 21:04:06,399 DEBUG: nvidia.available: falling back to default
2013-08-25 21:04:12,587 DEBUG:  NVidia(nvidia_304_updates).enabled(): target_alt None current_alt  /usr/lib/nvidia-304/ld.so.conf other target alt None other current alt  /usr/lib/nvidia-304/alt_ld.so.conf
2013-08-25 21:04:12,588 DEBUG: nvidia_304_updates is not the alternative in use
2013-08-25 21:04:12,568 DEBUG: got handler  xorg:nvidia_304_updates([NvidiaDriver304Updates, nonfree, disabled]  NVIDIA accelerated graphics driver (post-release updates))
2013-08-25 21:04:12,588 DEBUG: searching handler for  driver ID {'driver_type': 'kernel_module', 'kernel_module':  'nvidia_304', 'package': 'nvidia-304'}
2013-08-25 21:04:12,607 DEBUG:  NVidia(nvidia_304).enabled(): target_alt /usr/lib/nvidia-304/ld.so.conf  current_alt /usr/lib/nvidia-304/ld.so.conf other target alt  /usr/lib/nvidia-304/alt_ld.so.conf other current alt  /usr/lib/nvidia-304/alt_ld.so.conf
2013-08-25 21:04:12,608 DEBUG: KMH enabled: False
2013-08-25 21:04:12,588 DEBUG: found match in handler  pool xorg:nvidia_304([NvidiaDriver304, nonfree, disabled] NVIDIA  accelerated graphics driver)
2013-08-25 21:04:12,613 WARNING: modinfo for module nvidia_304 failed: ERROR: modinfo: could not find module nvidia_304
 
2013-08-25 21:04:12,620 DEBUG: nvidia.available: falling back to default
2013-08-25 21:04:19,338 DEBUG:  NVidia(nvidia_304).enabled(): target_alt /usr/lib/nvidia-304/ld.so.conf  current_alt /usr/lib/nvidia-304/ld.so.conf other target alt  /usr/lib/nvidia-304/alt_ld.so.conf other current alt  /usr/lib/nvidia-304/alt_ld.so.conf
2013-08-25 21:04:19,339 DEBUG: KMH enabled: False
2013-08-25 21:04:19,319 DEBUG: got handler  xorg:nvidia_304([NvidiaDriver304, nonfree, disabled] NVIDIA accelerated  graphics driver)
2013-08-25 21:04:19,339 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x9e41fec> about HardwareID('modalias', 'acpi:PNP0C04:')
2013-08-25 21:04:19,339 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x9e41fec> about HardwareID('modalias',  'pci:v00001002d00004396sv00001458sd00005004bc0Csc03i20')
2013-08-25 21:04:19,348 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x9e41fec> about HardwareID('modalias', 'acpi:PNP0200:')
2013-08-25 21:04:19,348 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x9e41fec> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2013-08-25 21:04:19,348 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x9e41fec> about HardwareID('modalias',  'usb:v1D6Bp0002d0302dc09dsc00dp00ic09isc00ip00')
2013-08-25 21:04:19,349 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x9e41fec> about HardwareID('modalias',  'pci:v00001002d0000439Csv00001458sd00005002bc01sc01i8a')
2013-08-25 21:04:19,357 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pata_atiixp'}
2013-08-25 21:04:19,358 DEBUG: no corresponding handler  available for {'driver_type': 'kernel_module', 'kernel_module':  'pata_atiixp', 'jockey_handler': 'KernelModuleHandler'}
2013-08-25 21:04:19,358 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x9e41fec> about HardwareID('modalias',  'pci:v00001022d00001202sv00000000sd00000000bc06sc00i00')
2013-08-25 21:04:19,359 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x9e41fec> about HardwareID('modalias',  'input:b0003v09DAp000Ae0110-e0,1,2,4,k110,111,112,113,114,115,116,117,r0,1,6,8,9,am4,lsfw')
2013-08-25 21:04:19,359 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-08-25 21:04:19,359 DEBUG: no corresponding handler  available for {'driver_type': 'kernel_module', 'kernel_module':  'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-08-25 21:04:19,359 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-08-25 21:04:19,360 DEBUG: no corresponding handler  available for {'driver_type': 'kernel_module', 'kernel_module':  'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-08-25 21:04:19,360 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x9e41fec> about HardwareID('modalias',  'input:b0000v0000p0000e0000-e0,5,kramlsfw6,')
2013-08-25 21:04:19,360 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-08-25 21:04:19,360 DEBUG: no corresponding handler  available for {'driver_type': 'kernel_module', 'kernel_module':  'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-08-25 21:04:19,360 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x9e41fec> about HardwareID('modalias',  'usb:v0FCEp7170d0231dc00dsc00dp00ic0Aisc00ip00')
2013-08-25 21:04:19,361 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x9e41fec> about HardwareID('modalias',  'input:b0003v1038p0210e0111-e0,1,4,k71,72,73,80,8C,90,9B,9C,9E,9F,A3,A4,A5,A6,AB,AC,AD,D9,ram4,lsfw')
2013-08-25 21:04:19,361 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-08-25 21:04:19,361 DEBUG: no corresponding handler  available for {'driver_type': 'kernel_module', 'kernel_module':  'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-08-25 21:04:19,361 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-08-25 21:04:19,362 DEBUG: no corresponding handler  available for {'driver_type': 'kernel_module', 'kernel_module':  'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-08-25 21:04:19,362 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x9e41fec> about HardwareID('modalias',  'pci:v00001002d00004385sv00001458sd00004385bc0Csc05i00')
2013-08-25 21:04:19,370 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'i2c_piix4'}
2013-08-25 21:04:19,371 DEBUG: no corresponding handler  available for {'driver_type': 'kernel_module', 'kernel_module':  'i2c_piix4', 'jockey_handler': 'KernelModuleHandler'}
2013-08-25 21:04:19,371 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'sp5100_tco'}
2013-08-25 21:04:19,371 DEBUG: no corresponding handler  available for {'driver_type': 'kernel_module', 'kernel_module':  'sp5100_tco', 'jockey_handler': 'KernelModuleHandler'}
2013-08-25 21:04:19,371 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x9e41fec> about HardwareID('modalias',  'dmi:bvnAwardSoftwareInternational,Inc.:bvrF6:bd11/20/2009:svnGigabyteTechnologyCo.,Ltd.:pnGA-MA790X-UD3P:pvr:rvnGigabyteTechnologyCo.,Ltd.:rnGA-MA790X-UD3P:rvrx.x:cvnGigabyteTechnologyCo.,Ltd.:ct3:cvr:')
2013-08-25 21:04:19,396 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x9e41fec> about HardwareID('modalias', 'acpi:PNP0B00:')
2013-08-25 21:04:19,396 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x9e41fec> about HardwareID('modalias',  'input:b0000v0000p0000e0000-e0,5,kramlsfwD,')
2013-08-25 21:04:19,396 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-08-25 21:04:19,396 DEBUG: no corresponding handler  available for {'driver_type': 'kernel_module', 'kernel_module':  'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-08-25 21:04:19,396 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x9e41fec> about HardwareID('modalias',  'usb:v1038p0210d0170dc00dsc00dp00ic03isc01ip01')
2013-08-25 21:04:19,397 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2013-08-25 21:04:19,397 DEBUG: no corresponding handler  available for {'driver_type': 'kernel_module', 'kernel_module':  'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2013-08-25 21:04:19,397 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd'}
2013-08-25 21:04:19,397 DEBUG: no corresponding handler  available for {'driver_type': 'kernel_module', 'kernel_module':  'usbkbd', 'jockey_handler': 'KernelModuleHandler'}
2013-08-25 21:04:19,397 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x9e41fec> about HardwareID('modalias',  'usb:v1038p0210d0170dc00dsc00dp00ic03isc00ip00')
2013-08-25 21:04:19,397 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2013-08-25 21:04:19,398 DEBUG: no corresponding handler  available for {'driver_type': 'kernel_module', 'kernel_module':  'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2013-08-25 21:04:19,398 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x9e41fec> about HardwareID('modalias', 'acpi:PNP0700:')
2013-08-25 21:04:19,398 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x9e41fec> about HardwareID('modalias', 'acpi:PNP0C01:')
2013-08-25 21:04:19,398 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x9e41fec> about HardwareID('modalias',  'pci:v00001022d00001201sv00000000sd00000000bc06sc00i00')
2013-08-25 21:04:19,398 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x9e41fec> about HardwareID('modalias',  'usb:v0FCEp7170d0231dc00dsc00dp00icE0isc01ip03')
2013-08-25 21:04:19,398 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'rndis_host'}
2013-08-25 21:04:19,398 DEBUG: no corresponding handler  available for {'driver_type': 'kernel_module', 'kernel_module':  'rndis_host', 'jockey_handler': 'KernelModuleHandler'}
2013-08-25 21:04:19,399 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x9e41fec> about HardwareID('modalias',  'pci:v00001002d00004390sv00001458sd0000B002bc01sc06i01')
2013-08-25 21:04:19,403 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x9e41fec> about HardwareID('modalias',  'pci:v00001022d00001200sv00000000sd00000000bc06sc00i00')
2013-08-25 21:04:19,403 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x9e41fec> about HardwareID('modalias',  'pci:v00001002d00004383sv00001458sd0000A002bc04sc03i00')
2013-08-25 21:04:19,407 DEBUG: searching handler for  driver ID {'driver_type': 'kernel_module', 'kernel_module':  'snd_hda_intel'}
2013-08-25 21:04:19,408 DEBUG: no corresponding handler  available for {'driver_type': 'kernel_module', 'kernel_module':  'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2013-08-25 21:04:19,408 DEBUG: searching handler for  driver ID {'driver_type': 'kernel_module', 'kernel_module':  'snd_hda_intel'}
2013-08-25 21:04:19,408 DEBUG: no corresponding handler  available for {'driver_type': 'kernel_module', 'kernel_module':  'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2013-08-25 21:04:19,408 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x9e41fec> about HardwareID('modalias',  'pci:v0000197Bd00002363sv00001458sd0000B000bc01sc06i01')
2013-08-25 21:04:19,408 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x9e41fec> about HardwareID('modalias', 'acpi:PNP0100:')
2013-08-25 21:04:19,408 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x9e41fec> about HardwareID('modalias',  'usb:v09DAp000Ad0014dc00dsc00dp00ic03isc01ip02')
2013-08-25 21:04:19,408 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2013-08-25 21:04:19,409 DEBUG: no corresponding handler  available for {'driver_type': 'kernel_module', 'kernel_module':  'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2013-08-25 21:04:19,409 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse'}
2013-08-25 21:04:19,409 DEBUG: no corresponding handler  available for {'driver_type': 'kernel_module', 'kernel_module':  'usbmouse', 'jockey_handler': 'KernelModuleHandler'}
2013-08-25 21:04:19,409 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x9e41fec> about HardwareID('modalias',  'pci:v00001002d0000439Dsv00001002sd0000439Dbc06sc01i00')
2013-08-25 21:04:19,413 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x9e41fec> about HardwareID('modalias', 'platform:pcspkr')
2013-08-25 21:04:19,414 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr'}
2013-08-25 21:04:19,414 DEBUG: no corresponding handler  available for {'driver_type': 'kernel_module', 'kernel_module':  'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2013-08-25 21:04:19,414 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp'}
2013-08-25 21:04:19,414 DEBUG: no corresponding handler  available for {'driver_type': 'kernel_module', 'kernel_module':  'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2013-08-25 21:04:19,414 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x9e41fec> about HardwareID('modalias', 'serio:ty06pr00id00ex00')
2013-08-25 21:04:19,423 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw'}
2013-08-25 21:04:19,423 DEBUG: no corresponding handler  available for {'driver_type': 'kernel_module', 'kernel_module':  'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2013-08-25 21:04:19,423 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x9e41fec> about HardwareID('modalias',  'pci:v0000104Cd00008024sv00001458sd00001000bc0Csc00i10')
2013-08-25 21:04:19,436 DEBUG: searching handler for  driver ID {'driver_type': 'kernel_module', 'kernel_module':  'firewire_ohci'}
2013-08-25 21:04:19,436 DEBUG: no corresponding handler  available for {'driver_type': 'kernel_module', 'kernel_module':  'firewire_ohci', 'jockey_handler': 'KernelModuleHandler'}
2013-08-25 21:04:19,436 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x9e41fec> about HardwareID('modalias',  'input:b0003v1038p0210e0111-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,8C,8E,96,98,9E,9F,A1,A3,A4,A5,A6,AD,B0,B1,B2,B3,B4,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,sfw')
2013-08-25 21:04:19,436 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-08-25 21:04:19,436 DEBUG: no corresponding handler  available for {'driver_type': 'kernel_module', 'kernel_module':  'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-08-25 21:04:19,436 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-08-25 21:04:19,436 DEBUG: no corresponding handler  available for {'driver_type': 'kernel_module', 'kernel_module':  'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-08-25 21:04:19,436 DEBUG: querying driver db  <jockey.detection.LocalKernelModulesDriverDB instance at  0x9e41fec> about HardwareID('modalias', 'acpi:PNP0501:')
2013-08-25 21:04:19,436 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x9e4976c>  about HardwareID('modalias',  'pci:v0000197Bd00002363sv00001458sd0000B000bc01sc01i85')
2013-08-25 21:04:19,436 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x9e4976c>  about HardwareID('modalias',  'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2013-08-25 21:04:19,437 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x9e4976c>  about HardwareID('modalias',  'pci:v00001022d00001204sv00000000sd00000000bc06sc00i00')
2013-08-25 21:04:19,437 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x9e4976c>  about HardwareID('modalias',  'pci:v00001022d00001203sv00000000sd00000000bc06sc00i00')
2013-08-25 21:04:19,437 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x9e4976c>  about HardwareID('modalias', 'acpi:PNP0C02:')
2013-08-25 21:04:19,437 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x9e4976c>  about HardwareID('modalias', 'acpi:PNP0103:')
2013-08-25 21:04:19,437 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x9e4976c>  about HardwareID('modalias',  'pci:v000010ECd00008168sv00001458sd0000E000bc02sc00i00')
2013-08-25 21:04:19,437 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x9e4976c>  about HardwareID('modalias',  'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2013-08-25 21:04:19,437 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x9e4976c>  about HardwareID('modalias', 'platform:eisa')
2013-08-25 21:04:19,437 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x9e4976c>  about HardwareID('modalias',  'usb:v1D6Bp0001d0302dc09dsc00dp00ic09isc00ip00')
2013-08-25 21:04:19,437 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x9e4976c>  about HardwareID('modalias',  'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2013-08-25 21:04:19,437 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x9e4976c>  about HardwareID('modalias', 'acpi:PNP0800:')
2013-08-25 21:04:19,437 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x9e4976c>  about HardwareID('modalias', 'platform:Fixed MDIO bus')
2013-08-25 21:04:19,437 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x9e4976c>  about HardwareID('modalias',  'pci:v00001002d00004384sv00000000sd00000000bc06sc04i01')
2013-08-25 21:04:19,437 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x9e4976c>  about HardwareID('modalias', 'platform:SP5100 TCO timer')
2013-08-25 21:04:19,437 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x9e4976c>  about HardwareID('modalias', 'wmi:ABBC0F6A-8EA1-11D1-00A0-C90629100000')
2013-08-25 21:04:19,437 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x9e4976c>  about HardwareID('modalias',  'pci:v00001002d00005958sv00001002sd00005958bc06sc00i00')
2013-08-25 21:04:19,438 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x9e4976c>  about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2013-08-25 21:04:19,438 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x9e4976c>  about HardwareID('modalias',  'usb:v0951p1624d0100dc00dsc00dp00ic08isc06ip50')
2013-08-25 21:04:19,438 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x9e4976c>  about HardwareID('modalias', 'acpi:LNXSYBUS:')
2013-08-25 21:04:19,438 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x9e4976c>  about HardwareID('modalias', 'acpi:PNP0000:')
2013-08-25 21:04:19,438 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x9e4976c>  about HardwareID('modalias',  'pci:v000010DEd00000290sv000010DEsd00000343bc03sc00i00')
2013-08-25 21:04:19,438 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x9e4976c>  about HardwareID('modalias', 'acpi:PNP0C04:')
2013-08-25 21:04:19,438 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x9e4976c>  about HardwareID('modalias',  'pci:v00001002d00004396sv00001458sd00005004bc0Csc03i20')
2013-08-25 21:04:19,438 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x9e4976c>  about HardwareID('modalias', 'acpi:PNP0200:')
2013-08-25 21:04:19,438 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x9e4976c>  about HardwareID('modalias', 'acpi:LNXSYSTM:')
2013-08-25 21:04:19,438 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x9e4976c>  about HardwareID('modalias',  'usb:v1D6Bp0002d0302dc09dsc00dp00ic09isc00ip00')
2013-08-25 21:04:19,438 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x9e4976c>  about HardwareID('modalias',  'pci:v00001002d0000439Csv00001458sd00005002bc01sc01i8a')
2013-08-25 21:04:19,438 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x9e4976c>  about HardwareID('modalias',  'pci:v00001022d00001202sv00000000sd00000000bc06sc00i00')
2013-08-25 21:04:19,438 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x9e4976c>  about HardwareID('modalias',  'input:b0003v09DAp000Ae0110-e0,1,2,4,k110,111,112,113,114,115,116,117,r0,1,6,8,9,am4,lsfw')
2013-08-25 21:04:19,438 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x9e4976c>  about HardwareID('modalias',  'input:b0000v0000p0000e0000-e0,5,kramlsfw6,')
2013-08-25 21:04:19,438 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x9e4976c>  about HardwareID('modalias',  'usb:v0FCEp7170d0231dc00dsc00dp00ic0Aisc00ip00')
2013-08-25 21:04:19,439 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x9e4976c>  about HardwareID('modalias',  'input:b0003v1038p0210e0111-e0,1,4,k71,72,73,80,8C,90,9B,9C,9E,9F,A3,A4,A5,A6,AB,AC,AD,D9,ram4,lsfw')
2013-08-25 21:04:19,439 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x9e4976c>  about HardwareID('modalias',  'pci:v00001002d00004385sv00001458sd00004385bc0Csc05i00')
2013-08-25 21:04:19,439 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x9e4976c>  about HardwareID('modalias',  'dmi:bvnAwardSoftwareInternational,Inc.:bvrF6:bd11/20/2009:svnGigabyteTechnologyCo.,Ltd.:pnGA-MA790X-UD3P:pvr:rvnGigabyteTechnologyCo.,Ltd.:rnGA-MA790X-UD3P:rvrx.x:cvnGigabyteTechnologyCo.,Ltd.:ct3:cvr:')
2013-08-25 21:04:19,439 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x9e4976c>  about HardwareID('modalias', 'acpi:PNP0B00:')
2013-08-25 21:04:19,439 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x9e4976c>  about HardwareID('modalias',  'input:b0000v0000p0000e0000-e0,5,kramlsfwD,')
2013-08-25 21:04:19,439 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x9e4976c>  about HardwareID('modalias',  'usb:v1038p0210d0170dc00dsc00dp00ic03isc01ip01')
2013-08-25 21:04:19,439 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x9e4976c>  about HardwareID('modalias',  'usb:v1038p0210d0170dc00dsc00dp00ic03isc00ip00')
2013-08-25 21:04:19,439 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x9e4976c>  about HardwareID('modalias', 'acpi:PNP0700:')
2013-08-25 21:04:19,439 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x9e4976c>  about HardwareID('modalias', 'acpi:PNP0C01:')
2013-08-25 21:04:19,439 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x9e4976c>  about HardwareID('modalias',  'pci:v00001022d00001201sv00000000sd00000000bc06sc00i00')
2013-08-25 21:04:19,439 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x9e4976c>  about HardwareID('modalias',  'usb:v0FCEp7170d0231dc00dsc00dp00icE0isc01ip03')
2013-08-25 21:04:19,439 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x9e4976c>  about HardwareID('modalias',  'pci:v00001002d00004390sv00001458sd0000B002bc01sc06i01')
2013-08-25 21:04:19,439 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x9e4976c>  about HardwareID('modalias',  'pci:v00001022d00001200sv00000000sd00000000bc06sc00i00')
2013-08-25 21:04:19,439 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x9e4976c>  about HardwareID('modalias',  'pci:v00001002d00004383sv00001458sd0000A002bc04sc03i00')
2013-08-25 21:04:19,439 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x9e4976c>  about HardwareID('modalias',  'pci:v0000197Bd00002363sv00001458sd0000B000bc01sc06i01')
2013-08-25 21:04:19,440 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x9e4976c>  about HardwareID('modalias', 'acpi:PNP0100:')
2013-08-25 21:04:19,440 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x9e4976c>  about HardwareID('modalias',  'usb:v09DAp000Ad0014dc00dsc00dp00ic03isc01ip02')
2013-08-25 21:04:19,440 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x9e4976c>  about HardwareID('modalias',  'pci:v00001002d0000439Dsv00001002sd0000439Dbc06sc01i00')
2013-08-25 21:04:19,440 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x9e4976c>  about HardwareID('modalias', 'platform:pcspkr')
2013-08-25 21:04:19,440 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x9e4976c>  about HardwareID('modalias', 'serio:ty06pr00id00ex00')
2013-08-25 21:04:19,440 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x9e4976c>  about HardwareID('modalias',  'pci:v0000104Cd00008024sv00001458sd00001000bc0Csc00i10')
2013-08-25 21:04:19,440 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x9e4976c>  about HardwareID('modalias',  'input:b0003v1038p0210e0111-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,8C,8E,96,98,9E,9F,A1,A3,A4,A5,A6,AD,B0,B1,B2,B3,B4,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,sfw')
2013-08-25 21:04:19,440 DEBUG: querying driver db  <jockey.detection.OpenPrintingDriverDB instance at 0x9e4976c>  about HardwareID('modalias', 'acpi:PNP0501:')
2013-08-25 21:04:19,526 DEBUG:  NVidia(nvidia_173).enabled(): target_alt None current_alt  /usr/lib/nvidia-304/ld.so.conf other target alt None other current alt  /usr/lib/nvidia-304/alt_ld.so.conf
2013-08-25 21:04:19,526 DEBUG: nvidia_173 is not the alternative in use
2013-08-25 21:04:20,622 DEBUG:  NVidia(nvidia_173_updates).enabled(): target_alt None current_alt  /usr/lib/nvidia-304/ld.so.conf other target alt None other current alt  /usr/lib/nvidia-304/alt_ld.so.conf
2013-08-25 21:04:20,622 DEBUG: nvidia_173_updates is not the alternative in use
2013-08-25 21:04:21,727 DEBUG:  NVidia(nvidia_304).enabled(): target_alt /usr/lib/nvidia-304/ld.so.conf  current_alt /usr/lib/nvidia-304/ld.so.conf other target alt  /usr/lib/nvidia-304/alt_ld.so.conf other current alt  /usr/lib/nvidia-304/alt_ld.so.conf
2013-08-25 21:04:21,728 DEBUG: KMH enabled: False
2013-08-25 21:04:22,829 DEBUG:  NVidia(nvidia_304_updates).enabled(): target_alt None current_alt  /usr/lib/nvidia-304/ld.so.conf other target alt None other current alt  /usr/lib/nvidia-304/alt_ld.so.conf
2013-08-25 21:04:22,830 DEBUG: nvidia_304_updates is not the alternative in use
2013-08-25 21:04:23,936 DEBUG:  NVidia(nvidia_96).enabled(): target_alt None current_alt  /usr/lib/nvidia-304/ld.so.conf other target alt None other current alt  /usr/lib/nvidia-304/alt_ld.so.conf
2013-08-25 21:04:23,937 DEBUG: nvidia_96 is not the alternative in use
2013-08-25 21:04:25,051 DEBUG:  NVidia(nvidia_173).enabled(): target_alt None current_alt  /usr/lib/nvidia-304/ld.so.conf other target alt None other current alt  /usr/lib/nvidia-304/alt_ld.so.conf
2013-08-25 21:04:25,052 DEBUG: nvidia_173 is not the alternative in use
2013-08-25 21:04:25,115 DEBUG:  NVidia(nvidia_173).enabled(): target_alt None current_alt  /usr/lib/nvidia-304/ld.so.conf other target alt None other current alt  /usr/lib/nvidia-304/alt_ld.so.conf
2013-08-25 21:04:25,116 DEBUG: nvidia_173 is not the alternative in use
2013-08-25 21:04:25,161 DEBUG:  NVidia(nvidia_173_updates).enabled(): target_alt None current_alt  /usr/lib/nvidia-304/ld.so.conf other target alt None other current alt  /usr/lib/nvidia-304/alt_ld.so.conf
2013-08-25 21:04:25,162 DEBUG: nvidia_173_updates is not the alternative in use
2013-08-25 21:04:25,207 DEBUG:  NVidia(nvidia_304).enabled(): target_alt /usr/lib/nvidia-304/ld.so.conf  current_alt /usr/lib/nvidia-304/ld.so.conf other target alt  /usr/lib/nvidia-304/alt_ld.so.conf other current alt  /usr/lib/nvidia-304/alt_ld.so.conf
2013-08-25 21:04:25,207 DEBUG: KMH enabled: False
2013-08-25 21:04:25,252 DEBUG:  NVidia(nvidia_304_updates).enabled(): target_alt None current_alt  /usr/lib/nvidia-304/ld.so.conf other target alt None other current alt  /usr/lib/nvidia-304/alt_ld.so.conf
2013-08-25 21:04:25,252 DEBUG: nvidia_304_updates is not the alternative in use
2013-08-25 21:04:25,297 DEBUG:  NVidia(nvidia_96).enabled(): target_alt None current_alt  /usr/lib/nvidia-304/ld.so.conf other target alt None other current alt  /usr/lib/nvidia-304/alt_ld.so.conf
2013-08-25 21:04:25,297 DEBUG: nvidia_96 is not the alternative in use
2013-08-25 21:04:30,296 DEBUG:  NVidia(nvidia_304).enabled(): target_alt /usr/lib/nvidia-304/ld.so.conf  current_alt /usr/lib/nvidia-304/ld.so.conf other target alt  /usr/lib/nvidia-304/alt_ld.so.conf other current alt  /usr/lib/nvidia-304/alt_ld.so.conf
2013-08-25 21:04:30,297 DEBUG: KMH enabled: False
2013-08-25 21:04:31,739 DEBUG:  NVidia(nvidia_304).enabled(): target_alt /usr/lib/nvidia-304/ld.so.conf  current_alt /usr/lib/nvidia-304/ld.so.conf other target alt  /usr/lib/nvidia-304/alt_ld.so.conf other current alt  /usr/lib/nvidia-304/alt_ld.so.conf
2013-08-25 21:04:31,739 DEBUG: KMH enabled: False
2013-08-25 21:04:38,252 WARNING: modinfo for module nvidia_304 failed: ERROR: modinfo: could not find module nvidia_304
 
2013-08-25 21:04:38,253 ERROR: XorgDriverHandler.enable(): package or module not installed, aborting
2013-08-25 21:04:59,783 DEBUG:  NVidia(nvidia_304).enabled(): target_alt /usr/lib/nvidia-304/ld.so.conf  current_alt /usr/lib/nvidia-304/ld.so.conf other target alt  /usr/lib/nvidia-304/alt_ld.so.conf other current alt  /usr/lib/nvidia-304/alt_ld.so.conf
2013-08-25 21:04:59,783 DEBUG: KMH enabled: False
2013-08-25 21:04:59,813 DEBUG:  NVidia(nvidia_304).enabled(): target_alt /usr/lib/nvidia-304/ld.so.conf  current_alt /usr/lib/nvidia-304/ld.so.conf other target alt  /usr/lib/nvidia-304/alt_ld.so.conf other current alt  /usr/lib/nvidia-304/alt_ld.so.conf
2013-08-25 21:04:59,813 DEBUG: KMH enabled: False
2013-08-25 21:05:40,013 DEBUG:  NVidia(nvidia_173).enabled(): target_alt None current_alt  /usr/lib/nvidia-304/ld.so.conf other target alt None other current alt  /usr/lib/nvidia-304/alt_ld.so.conf
2013-08-25 21:05:40,013 DEBUG: nvidia_173 is not the alternative in use
2013-08-25 21:05:40,064 DEBUG:  NVidia(nvidia_173_updates).enabled(): target_alt None current_alt  /usr/lib/nvidia-304/ld.so.conf other target alt None other current alt  /usr/lib/nvidia-304/alt_ld.so.conf
2013-08-25 21:05:40,064 DEBUG: nvidia_173_updates is not the alternative in use
2013-08-25 21:05:40,115 DEBUG:  NVidia(nvidia_304).enabled(): target_alt /usr/lib/nvidia-304/ld.so.conf  current_alt /usr/lib/nvidia-304/ld.so.conf other target alt  /usr/lib/nvidia-304/alt_ld.so.conf other current alt  /usr/lib/nvidia-304/alt_ld.so.conf
2013-08-25 21:05:40,115 DEBUG: KMH enabled: False
2013-08-25 21:05:40,145 DEBUG:  NVidia(nvidia_304).enabled(): target_alt /usr/lib/nvidia-304/ld.so.conf  current_alt /usr/lib/nvidia-304/ld.so.conf other target alt  /usr/lib/nvidia-304/alt_ld.so.conf other current alt  /usr/lib/nvidia-304/alt_ld.so.conf
2013-08-25 21:05:40,145 DEBUG: KMH enabled: False
2013-08-25 21:05:40,196 DEBUG:  NVidia(nvidia_304_updates).enabled(): target_alt None current_alt  /usr/lib/nvidia-304/ld.so.conf other target alt None other current alt  /usr/lib/nvidia-304/alt_ld.so.conf
2013-08-25 21:05:40,196 DEBUG: nvidia_304_updates is not the alternative in use
2013-08-25 21:05:40,248 DEBUG:  NVidia(nvidia_96).enabled(): target_alt None current_alt  /usr/lib/nvidia-304/ld.so.conf other target alt None other current alt  /usr/lib/nvidia-304/alt_ld.so.conf
2013-08-25 21:05:40,248 DEBUG: nvidia_96 is not the alternative in use
2013-08-25 21:05:40,307 DEBUG:  NVidia(nvidia_304).enabled(): target_alt /usr/lib/nvidia-304/ld.so.conf  current_alt /usr/lib/nvidia-304/ld.so.conf other target alt  /usr/lib/nvidia-304/alt_ld.so.conf other current alt  /usr/lib/nvidia-304/alt_ld.so.conf
2013-08-25 21:05:40,307 DEBUG: KMH enabled: False
2013-08-25 21:05:40,337 DEBUG:  NVidia(nvidia_304).enabled(): target_alt /usr/lib/nvidia-304/ld.so.conf  current_alt /usr/lib/nvidia-304/ld.so.conf other target alt  /usr/lib/nvidia-304/alt_ld.so.conf other current alt  /usr/lib/nvidia-304/alt_ld.so.conf
2013-08-25 21:05:40,338 DEBUG: KMH enabled: False
2013-08-25 21:05:40,405 DEBUG:  NVidia(nvidia_173).enabled(): target_alt None current_alt  /usr/lib/nvidia-304/ld.so.conf other target alt None other current alt  /usr/lib/nvidia-304/alt_ld.so.conf
2013-08-25 21:05:40,406 DEBUG: nvidia_173 is not the alternative in use
2013-08-25 21:05:40,451 DEBUG:  NVidia(nvidia_173_updates).enabled(): target_alt None current_alt  /usr/lib/nvidia-304/ld.so.conf other target alt None other current alt  /usr/lib/nvidia-304/alt_ld.so.conf
2013-08-25 21:05:40,452 DEBUG: nvidia_173_updates is not the alternative in use
2013-08-25 21:05:40,497 DEBUG:  NVidia(nvidia_304).enabled(): target_alt /usr/lib/nvidia-304/ld.so.conf  current_alt /usr/lib/nvidia-304/ld.so.conf other target alt  /usr/lib/nvidia-304/alt_ld.so.conf other current alt  /usr/lib/nvidia-304/alt_ld.so.conf
2013-08-25 21:05:40,498 DEBUG: KMH enabled: False
2013-08-25 21:05:40,528 DEBUG:  NVidia(nvidia_304).enabled(): target_alt /usr/lib/nvidia-304/ld.so.conf  current_alt /usr/lib/nvidia-304/ld.so.conf other target alt  /usr/lib/nvidia-304/alt_ld.so.conf other current alt  /usr/lib/nvidia-304/alt_ld.so.conf
2013-08-25 21:05:40,528 DEBUG: KMH enabled: False
2013-08-25 21:05:40,573 DEBUG:  NVidia(nvidia_304_updates).enabled(): target_alt None current_alt  /usr/lib/nvidia-304/ld.so.conf other target alt None other current alt  /usr/lib/nvidia-304/alt_ld.so.conf
2013-08-25 21:05:40,574 DEBUG: nvidia_304_updates is not the alternative in use
2013-08-25 21:05:40,620 DEBUG:  NVidia(nvidia_96).enabled(): target_alt None current_alt  /usr/lib/nvidia-304/ld.so.conf other target alt None other current alt  /usr/lib/nvidia-304/alt_ld.so.conf
2013-08-25 21:05:40,620 DEBUG: nvidia_96 is not the alternative in use 
[/LIST]

         

```

Thanks for any assistance you guys can provide!

---

### Post by rai_shu2 on 2013-08-25
Looks like the same thing happened to this guy:

[http://dragly.org/2012/05/04/installing-the-nvidia-driver-in-kubuntu-12-04/](http://dragly.org/2012/05/04/installing-the-nvidia-driver-in-kubuntu-12-04/)

---

