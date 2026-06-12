---
title: "Unsupported event"
date: 2019-11-11
forum: General Help
---

### Post by azkov on 2019-11-11
Dear everyone,

I am writing you these few lines because I am currently facing some issues. 

I bought a Dell G 15 already prepared in Linux 16.04. 

I decided to upgrade to 18.04. But now I am facing two problems : 

_Double identification, I am writing the right password, black screen then it asks a second time to write my password. 
_Some error problems appears when I put my PC asleep and then come back. 

The lines are too fast to be seen. Does anyone have a tips to get this information through the terminal ? 

Does anyone faces these issues ? 

Thanks for your time. 

Best regards, 

AZK

---

### Post by TheFu on 2019-11-11
All Unix systems log stuff.  Usually, into log files in /var/log/.  Check those files for what you want.
The 'dmesg' command holds any boot messages.  We can look at those using a pager like less or more.
```
dmesg|less
```
Or we can search for text using grep
```
dmesg |egrep -i 'err|warn'
```

syslog is another important logfile worth grepping.
```
egrep -i 'err|warn' /var/log/syslog 
```

---

### Post by azkov on 2019-11-11
Dear The FU,

Here are information provided thanks to the following code : " dmesg |egrep -i 'err|warn' "
I don't a clue about what it means because I am not very familiar with ubuntu 

```

[21007.802247] ACPI: EC: interrupt blocked
[21008.256936] ACPI: EC: interrupt unblocked
[21038.088420] ACPI: EC: interrupt blocked
[21038.535094] ACPI: EC: interrupt unblocked
[21062.055096] ACPI: EC: interrupt blocked
[21062.257454] ACPI: EC: interrupt unblocked
[21067.603955] ACPI: EC: interrupt blocked
[21068.039281] ACPI: EC: interrupt unblocked
[21222.116053] ACPI Error: [LCD_] Namespace lookup failure, AE_NOT_FOUND (20170831/psargs-364)
[21222.116086] ACPI Error: Method parse/execution failed \_SB.PCI0.PEG0.PEGP.BRT6, AE_NOT_FOUND (20170831/psparse-550)
[21222.116095] ACPI Error: Method parse/execution failed \EV5, AE_NOT_FOUND (20170831/psparse-550)
[21222.116102] ACPI Error: Method parse/execution failed \SMEE, AE_NOT_FOUND (20170831/psparse-550)
[21222.116109] ACPI Error: Method parse/execution failed \SMIE, AE_NOT_FOUND (20170831/psparse-550)
[21222.116115] ACPI Error: Method parse/execution failed \NEVT, AE_NOT_FOUND (20170831/psparse-550)
[21222.116270] ACPI Error: Method parse/execution failed \_SB.PCI0.LPCB.ECDV._Q66, AE_NOT_FOUND (20170831/psparse-550)
[21222.290466] ACPI Error: [LCD_] Namespace lookup failure, AE_NOT_FOUND (20170831/psargs-364)
[21222.290503] ACPI Error: Method parse/execution failed \_SB.PCI0.PEG0.PEGP.BRT6, AE_NOT_FOUND (20170831/psparse-550)
[21222.290570] ACPI Error: Method parse/execution failed \EV5, AE_NOT_FOUND (20170831/psparse-550)
[21222.290634] ACPI Error: Method parse/execution failed \SMEE, AE_NOT_FOUND (20170831/psparse-550)
[21222.290694] ACPI Error: Method parse/execution failed \SMIE, AE_NOT_FOUND (20170831/psparse-550)
[21222.290758] ACPI Error: Method parse/execution failed \NEVT, AE_NOT_FOUND (20170831/psparse-550)
[21222.290826] ACPI Error: Method parse/execution failed \_SB.PCI0.LPCB.ECDV._Q66, AE_NOT_FOUND (20170831/psparse-550)
[21222.466872] ACPI Error: [LCD_] Namespace lookup failure, AE_NOT_FOUND (20170831/psargs-364)
[21222.466899] ACPI Error: Method parse/execution failed \_SB.PCI0.PEG0.PEGP.BRT6, AE_NOT_FOUND (20170831/psparse-550)
[21222.466906] ACPI Error: Method parse/execution failed \EV5, AE_NOT_FOUND (20170831/psparse-550)
[21222.466911] ACPI Error: Method parse/execution failed \SMEE, AE_NOT_FOUND (20170831/psparse-550)
[21222.466917] ACPI Error: Method parse/execution failed \SMIE, AE_NOT_FOUND (20170831/psparse-550)
[21222.466922] ACPI Error: Method parse/execution failed \NEVT, AE_NOT_FOUND (20170831/psparse-550)
[21222.467048] ACPI Error: Method parse/execution failed \_SB.PCI0.LPCB.ECDV._Q66, AE_NOT_FOUND (20170831/psparse-550)
[21222.599366] ACPI Error: [LCD_] Namespace lookup failure, AE_NOT_FOUND (20170831/psargs-364)
[21222.602694] ACPI Error: Method parse/execution failed \_SB.PCI0.PEG0.PEGP.BRT6, AE_NOT_FOUND (20170831/psparse-550)
[21222.602706] ACPI Error: Method parse/execution failed \EV5, AE_NOT_FOUND (20170831/psparse-550)
[21222.602771] ACPI Error: Method parse/execution failed \SMEE, AE_NOT_FOUND (20170831/psparse-550)
[21222.602776] ACPI Error: Method parse/execution failed \SMIE, AE_NOT_FOUND (20170831/psparse-550)
[21222.602833] ACPI Error: Method parse/execution failed \NEVT, AE_NOT_FOUND (20170831/psparse-550)
[21222.603637] ACPI Error: Method parse/execution failed \_SB.PCI0.LPCB.ECDV._Q66, AE_NOT_FOUND (20170831/psparse-550)
[21222.762281] ACPI Error: [LCD_] Namespace lookup failure, AE_NOT_FOUND (20170831/psargs-364)
[21222.762326] ACPI Error: Method parse/execution failed \_SB.PCI0.PEG0.PEGP.BRT6, AE_NOT_FOUND (20170831/psparse-550)
[21222.762459] ACPI Error: Method parse/execution failed \EV5, AE_NOT_FOUND (20170831/psparse-550)
[21222.762586] ACPI Error: Method parse/execution failed \SMEE, AE_NOT_FOUND (20170831/psparse-550)
[21222.762742] ACPI Error: Method parse/execution failed \SMIE, AE_NOT_FOUND (20170831/psparse-550)
[21222.762936] ACPI Error: Method parse/execution failed \NEVT, AE_NOT_FOUND (20170831/psparse-550)
[21222.763095] ACPI Error: Method parse/execution failed \_SB.PCI0.LPCB.ECDV._Q66, AE_NOT_FOUND (20170831/psparse-550)
[21222.924207] ACPI Error: [LCD_] Namespace lookup failure, AE_NOT_FOUND (20170831/psargs-364)
[21222.924240] ACPI Error: Method parse/execution failed \_SB.PCI0.PEG0.PEGP.BRT6, AE_NOT_FOUND (20170831/psparse-550)
[21222.924248] ACPI Error: Method parse/execution failed \EV5, AE_NOT_FOUND (20170831/psparse-550)
[21222.924255] ACPI Error: Method parse/execution failed \SMEE, AE_NOT_FOUND (20170831/psparse-550)
[21222.924262] ACPI Error: Method parse/execution failed \SMIE, AE_NOT_FOUND (20170831/psparse-550)
[21222.924269] ACPI Error: Method parse/execution failed \NEVT, AE_NOT_FOUND (20170831/psparse-550)
[21222.924484] ACPI Error: Method parse/execution failed \_SB.PCI0.LPCB.ECDV._Q66, AE_NOT_FOUND (20170831/psparse-550)
[21223.059847] ACPI Error: [LCD_] Namespace lookup failure, AE_NOT_FOUND (20170831/psargs-364)
[21223.065441] ACPI Error: Method parse/execution failed \_SB.PCI0.PEG0.PEGP.BRT6, AE_NOT_FOUND (20170831/psparse-550)
[21223.065455] ACPI Error: Method parse/execution failed \EV5, AE_NOT_FOUND (20170831/psparse-550)
[21223.065462] ACPI Error: Method parse/execution failed \SMEE, AE_NOT_FOUND (20170831/psparse-550)
[21223.065470] ACPI Error: Method parse/execution failed \SMIE, AE_NOT_FOUND (20170831/psparse-550)
[21223.065476] ACPI Error: Method parse/execution failed \NEVT, AE_NOT_FOUND (20170831/psparse-550)
[21223.065833] ACPI Error: Method parse/execution failed \_SB.PCI0.LPCB.ECDV._Q66, AE_NOT_FOUND (20170831/psparse-550)
[21223.202054] ACPI Error: [LCD_] Namespace lookup failure, AE_NOT_FOUND (20170831/psargs-364)
[21223.202073] ACPI Error: Method parse/execution failed \_SB.PCI0.PEG0.PEGP.BRT6, AE_NOT_FOUND (20170831/psparse-550)
[21223.202128] ACPI Error: Method parse/execution failed \EV5, AE_NOT_FOUND (20170831/psparse-550)
[21223.202179] ACPI Error: Method parse/execution failed \SMEE, AE_NOT_FOUND (20170831/psparse-550)
[21223.202231] ACPI Error: Method parse/execution failed \SMIE, AE_NOT_FOUND (20170831/psparse-550)
[21223.202283] ACPI Error: Method parse/execution failed \NEVT, AE_NOT_FOUND (20170831/psparse-550)
[21223.202335] ACPI Error: Method parse/execution failed \_SB.PCI0.LPCB.ECDV._Q66, AE_NOT_FOUND (20170831/psparse-550)
[21223.358132] ACPI Error: [LCD_] Namespace lookup failure, AE_NOT_FOUND (20170831/psargs-364)
[21223.358165] ACPI Error: Method parse/execution failed \_SB.PCI0.PEG0.PEGP.BRT6, AE_NOT_FOUND (20170831/psparse-550)
[21223.358174] ACPI Error: Method parse/execution failed \EV5, AE_NOT_FOUND (20170831/psparse-550)
[21223.358181] ACPI Error: Method parse/execution failed \SMEE, AE_NOT_FOUND (20170831/psparse-550)
[21223.358188] ACPI Error: Method parse/execution failed \SMIE, AE_NOT_FOUND (20170831/psparse-550)
[21223.358195] ACPI Error: Method parse/execution failed \NEVT, AE_NOT_FOUND (20170831/psparse-550)
[21223.358203] ACPI Error: Method parse/execution failed \_SB.PCI0.LPCB.ECDV._Q66, AE_NOT_FOUND (20170831/psparse-550)
[21223.496458] ACPI Error: [LCD_] Namespace lookup failure, AE_NOT_FOUND (20170831/psargs-364)
[21223.496527] ACPI Error: Method parse/execution failed \_SB.PCI0.PEG0.PEGP.BRT6, AE_NOT_FOUND (20170831/psparse-550)
[21223.496736] ACPI Error: Method parse/execution failed \EV5, AE_NOT_FOUND (20170831/psparse-550)
[21223.496933] ACPI Error: Method parse/execution failed \SMEE, AE_NOT_FOUND (20170831/psparse-550)
[21223.497130] ACPI Error: Method parse/execution failed \SMIE, AE_NOT_FOUND (20170831/psparse-550)
[21223.497326] ACPI Error: Method parse/execution failed \NEVT, AE_NOT_FOUND (20170831/psparse-550)
[21223.497530] ACPI Error: Method parse/execution failed \_SB.PCI0.LPCB.ECDV._Q66, AE_NOT_FOUND (20170831/psparse-550)
[21223.605410] ACPI Error: [LCD_] Namespace lookup failure, AE_NOT_FOUND (20170831/psargs-364)
[21223.605426] ACPI Error: Method parse/execution failed \_SB.PCI0.PEG0.PEGP.BRT6, AE_NOT_FOUND (20170831/psparse-550)
[21223.605469] ACPI Error: Method parse/execution failed \EV5, AE_NOT_FOUND (20170831/psparse-550)
[21223.605510] ACPI Error: Method parse/execution failed \SMEE, AE_NOT_FOUND (20170831/psparse-550)
[21223.605551] ACPI Error: Method parse/execution failed \SMIE, AE_NOT_FOUND (20170831/psparse-550)
[21223.605592] ACPI Error: Method parse/execution failed \NEVT, AE_NOT_FOUND (20170831/psparse-550)
[21223.605633] ACPI Error: Method parse/execution failed \_SB.PCI0.LPCB.ECDV._Q66, AE_NOT_FOUND (20170831/psparse-550)
[21223.771100] ACPI Error: [LCD_] Namespace lookup failure, AE_NOT_FOUND (20170831/psargs-364)
[21223.771123] ACPI Error: Method parse/execution failed \_SB.PCI0.PEG0.PEGP.BRT6, AE_NOT_FOUND (20170831/psparse-550)
[21223.771129] ACPI Error: Method parse/execution failed \EV5, AE_NOT_FOUND (20170831/psparse-550)
[21223.771134] ACPI Error: Method parse/execution failed \SMEE, AE_NOT_FOUND (20170831/psparse-550)
[21223.771139] ACPI Error: Method parse/execution failed \SMIE, AE_NOT_FOUND (20170831/psparse-550)
[21223.771144] ACPI Error: Method parse/execution failed \NEVT, AE_NOT_FOUND (20170831/psparse-550)
[21223.772464] ACPI Error: Method parse/execution failed \_SB.PCI0.LPCB.ECDV._Q66, AE_NOT_FOUND (20170831/psparse-550)
[21223.877366] ACPI Error: [LCD_] Namespace lookup failure, AE_NOT_FOUND (20170831/psargs-364)
[21223.877388] ACPI Error: Method parse/execution failed \_SB.PCI0.PEG0.PEGP.BRT6, AE_NOT_FOUND (20170831/psparse-550)
[21223.877431] ACPI Error: Method parse/execution failed \EV5, AE_NOT_FOUND (20170831/psparse-550)
[21223.877472] ACPI Error: Method parse/execution failed \SMEE, AE_NOT_FOUND (20170831/psparse-550)
[21223.877514] ACPI Error: Method parse/execution failed \SMIE, AE_NOT_FOUND (20170831/psparse-550)
[21223.877555] ACPI Error: Method parse/execution failed \NEVT, AE_NOT_FOUND (20170831/psparse-550)
[21223.877598] ACPI Error: Method parse/execution failed \_SB.PCI0.LPCB.ECDV._Q66, AE_NOT_FOUND (20170831/psparse-550)
[21224.005757] ACPI Error: [LCD_] Namespace lookup failure, AE_NOT_FOUND (20170831/psargs-364)
[21224.005781] ACPI Error: Method parse/execution failed \_SB.PCI0.PEG0.PEGP.BRT6, AE_NOT_FOUND (20170831/psparse-550)
[21224.005787] ACPI Error: Method parse/execution failed \EV5, AE_NOT_FOUND (20170831/psparse-550)
[21224.005792] ACPI Error: Method parse/execution failed \SMEE, AE_NOT_FOUND (20170831/psparse-550)
[21224.005797] ACPI Error: Method parse/execution failed \SMIE, AE_NOT_FOUND (20170831/psparse-550)
[21224.005801] ACPI Error: Method parse/execution failed \NEVT, AE_NOT_FOUND (20170831/psparse-550)
[21224.005910] ACPI Error: Method parse/execution failed \_SB.PCI0.LPCB.ECDV._Q66, AE_NOT_FOUND (20170831/psparse-550)
[24747.664116] ACPI: EC: interrupt blocked
[24748.114878] ACPI: EC: interrupt unblocked
[28063.298526] ACPI: EC: interrupt blocked
[28063.756828] ACPI: EC: interrupt unblocked
[29863.259260] ACPI: EC: interrupt blocked
[29863.704589] ACPI: EC: interrupt unblocked
[52829.187092] ACPI: EC: interrupt blocked
[52829.639335] ACPI: EC: interrupt unblocked
[56195.389054] ACPI: EC: interrupt blocked
[56195.835941] ACPI: EC: interrupt unblocked
[57153.115039] ACPI: EC: interrupt blocked
[57153.565088] ACPI: EC: interrupt unblocked
[59090.137551] ACPI: EC: interrupt blocked
[59090.583648] ACPI: EC: interrupt unblocked
[61308.877825] ACPI: EC: interrupt blocked
[61309.080518] ACPI: EC: interrupt unblocked
[61314.126752] ACPI: EC: interrupt blocked
[61314.597800] ACPI: EC: interrupt unblocked
[64001.945953] ACPI: EC: interrupt blocked
[64002.365894] ACPI: EC: interrupt unblocked
[68583.099753] ACPI: EC: interrupt blocked
[68583.525339] ACPI: EC: interrupt unblocked

_**dell@dell-G5-5587:~$ egrep -i 'err|warn' /var/log/syslog**_
Nov 11 18:11:52 dell-G5-5587 systemd-resolved[806]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Nov 11 18:11:52 dell-G5-5587 systemd-resolved[806]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Nov 11 18:21:56 dell-G5-5587 org.gnome.Shell.desktop[2444]: #32 0x559f3d37c3c0 i   resource:///org/gnome/gjs/modules/overrides/Gio.js:117 (0x7fc9a84e0ab0 @ 39)
Nov 11 18:21:56 dell-G5-5587 org.gnome.Shell.desktop[2444]: #32 0x559f3d37c3c0 i   resource:///org/gnome/gjs/modules/overrides/Gio.js:117 (0x7fc9a84e0ab0 @ 39)
Nov 11 18:21:56 dell-G5-5587 NetworkManager[1103]: <warn>  [1573492916.7226] sup-iface[0x5624dcea8800,wlp0s20f3]: connection disconnected (reason -3)
Nov 11 18:21:56 dell-G5-5587 gsd-sharing[2558]: Failed to StopUnit service: GDBus.Error:org.freedesktop.systemd1.NoSuchUnit: Unit rygel.service not loaded.
Nov 11 18:21:56 dell-G5-5587 gsd-sharing[2558]: Failed to StopUnit service: GDBus.Error:org.freedesktop.systemd1.NoSuchUnit: Unit gnome-remote-desktop.service not loaded.
Nov 11 18:26:38 dell-G5-5587 kernel: [68583.099753] ACPI: EC: interrupt blocked
Nov 11 18:26:38 dell-G5-5587 kernel: [68583.525339] ACPI: EC: interrupt unblocked
Nov 11 18:26:42 dell-G5-5587 gsd-sharing[2558]: Failed to StopUnit service: GDBus.Error:org.freedesktop.systemd1.NoSuchUnit: Unit rygel.service not loaded.
Nov 11 18:26:42 dell-G5-5587 gsd-sharing[2558]: Failed to StopUnit service: GDBus.Error:org.freedesktop.systemd1.NoSuchUnit: Unit gnome-remote-desktop.service not loaded.
Nov 11 18:26:52 dell-G5-5587 gdm-session-worker[2193]: rmmod: ERROR: Module nvidia_drm is not currently loaded
Nov 11 18:26:52 dell-G5-5587 gdm-session-worker[2193]: rmmod: ERROR: Module nvidia_uvm is not currently loaded
Nov 11 18:26:52 dell-G5-5587 gdm-session-worker[2193]: rmmod: ERROR: Module nvidia_modeset is not currently loaded
Nov 11 18:26:52 dell-G5-5587 gdm-session-worker[2193]: rmmod: ERROR: Module nvidia is in use
Nov 11 18:26:56 dell-G5-5587 ModemManager[1039]: <warn>  Could not grab port (tty/ttyACM0): 'Cannot add port 'tty/ttyACM0', unhandled serial type'
Nov 11 18:26:56 dell-G5-5587 ModemManager[1039]: <warn>  Couldn't create modem for device '/sys/devices/pci0000:00/0000:00:14.0/usb1/1-9': Failed to find primary AT port
Nov 11 18:27:00 dell-G5-5587 gdm-session-worker[2193]: rmmod: ERROR: Module nvidia_drm is not currently loaded
Nov 11 18:27:00 dell-G5-5587 gdm-session-worker[2193]: rmmod: ERROR: Module nvidia_uvm is not currently loaded
Nov 11 18:27:00 dell-G5-5587 gdm-session-worker[2193]: rmmod: ERROR: Module nvidia_modeset is not currently loaded
Nov 11 18:27:00 dell-G5-5587 gdm-session-worker[2193]: rmmod: ERROR: Module nvidia is in use
Nov 11 18:27:07 dell-G5-5587 gdm-session-worker[2193]: rmmod: ERROR: Module nvidia_drm is not currently loaded
Nov 11 18:27:07 dell-G5-5587 gdm-session-worker[2193]: rmmod: ERROR: Module nvidia_uvm is not currently loaded
Nov 11 18:27:07 dell-G5-5587 gdm-session-worker[2193]: rmmod: ERROR: Module nvidia_modeset is not currently loaded
Nov 11 18:27:07 dell-G5-5587 gdm-session-worker[2193]: rmmod: ERROR: Module nvidia is in use
Nov 11 18:27:18 dell-G5-5587 gdm-session-worker[2193]: rmmod: ERROR: Module nvidia_drm is not currently loaded
Nov 11 18:27:18 dell-G5-5587 gdm-session-worker[2193]: rmmod: ERROR: Module nvidia_uvm is not currently loaded
Nov 11 18:27:18 dell-G5-5587 gdm-session-worker[2193]: rmmod: ERROR: Module nvidia_modeset is not currently loaded
Nov 11 18:27:18 dell-G5-5587 gdm-session-worker[2193]: rmmod: ERROR: Module nvidia is in use
Nov 11 18:33:50 dell-G5-5587 kernel: [69016.549266] ecryptfs_encrypt_page: Error attempting to write lower page; rc = [-4]
Nov 11 18:33:50 dell-G5-5587 kernel: [69016.549278] ecryptfs_write_end: Error encrypting page (upper index [0x0000000000000000])
```


So, I don't have any idea if it is bad for my computer or not. Don't know how to fix it too ! 

Best, 

AZK

---

### Post by TheFu on 2019-11-11
Take each line.  Remove the parts that seem very specific to your system.  Put what is left into google. Hit <enter>  
Learn.

You might need to look at the lines a little before and after each error/warning line to get some context.

Repeat for each line.

---

