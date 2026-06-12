---
title: "pm-hibernate doesn't work (uswsusp and zram)"
date: 2013-02-01
forum: General Help
---

### Post by Terraman on 2013-02-01
I have the same problem after upgrading from Ubuntu 12.04 to 12.10. Both pm-suspend and pm-hibernate had worked fine in Ubuntu 12.04. I am trying every thing from many pages and I could not find out how can it be solved so far.

There are my out puts:

sudo debconf-show uswsusp:

```
herman@patricia-laptop:~$ sudo debconf-show uswsusp
  uswsusp/RSA_passphrase: (password omitted)
  uswsusp/RSA_passphrase_v: (password omitted)
* uswsusp/compute_checksum: false
  uswsusp/no_snapshot:
* uswsusp/suspend_loglevel: 7
  uswsusp/no_swap:
  uswsusp/resume_offset: 0
* uswsusp/early_writeout: true
* uswsusp/image_size: 1500000000
* uswsusp/compress: true
  uswsusp/create_RSA_key: false
* uswsusp/snapshot_device:
  uswsusp/RSA_key_file: /etc/uswsusp.key
* uswsusp/max_loglevel: 7
* uswsusp/resume_device: /dev/sda6
* uswsusp/shutdown_method: platform
* uswsusp/encrypt: false
* uswsusp/splash: false
  uswsusp/RSA_key_bits: 1024
* uswsusp/continue_without_swap: false
herman@patricia-laptop:~$ 
```

cat /proc/cmdline:

```
herman@patricia-laptop:~$ cat /proc/cmdline
BOOT_IMAGE=/boot/vmlinuz-3.5.0-23-generic root=UUID=66050dc2-96e5-4054-90de-8b12e00235d5 ro reboot=efi quiet splash resume=/dev/sda6 vt.handoff=7
herman@patricia-laptop:~$ 
```

sudo blkid:

```
herman@patricia-laptop:~$ sudo blkid
/dev/sda1: LABEL="Recovery" UUID="9A6839AF68398B51" TYPE="ntfs" 
/dev/sda2: UUID="a408efbc-dbf6-406c-b94b-bcc514058936" TYPE="ext3" 
/dev/sda3: UUID="E2BED980BED94E23" TYPE="ntfs" 
/dev/sda5: UUID="66050dc2-96e5-4054-90de-8b12e00235d5" TYPE="ext4" 
/dev/sda6: UUID="84c2098a-83b5-4a83-a053-8c9277da2941" TYPE="swap" 
/dev/zram0: UUID="440ebdad-6ca1-4ef6-b5cd-a692764a9cf8" TYPE="swap" 
/dev/zram1: UUID="908b7557-f921-4326-9068-f3db683dc5be" TYPE="swap" 
herman@patricia-laptop:~$ 
```

/etc/fstab:

```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0

# / was on /dev/sda5 during installation
UUID=66050dc2-96e5-4054-90de-8b12e00235d5 /               ext4    errors=remount-ro 0       1

# swap was on /dev/sda6 during installation
UUID=84c2098a-83b5-4a83-a053-8c9277da2941 none            swap    sw              0       0

# swap on usb stick
# UUID=7bbbe625-03ba-4bff-b51a-3ba9164ce2b6 none swap sw,pri=5 0 0

#/.hibernate.img   swap  swap	noauto,defaults	0	0

/dev/sda2 /home ext3 nodev,nosuid,user_xattr 0 2

# Move /tmp to RAM
tmpfs /tmp tmpfs defaults,noexec,nosuid 0 0


```

swapon -s:

```
herman@patricia-laptop:~$ swapon -s
Filename				Type		Size	Used	Priority
/dev/sda6                               partition	987960	0	-1
/dev/zram0                              partition	513648	0	100
/dev/zram1                              partition	513648	0	100
herman@patricia-laptop:~$

```

Finally, I get this warning when I run sudo update-initramfs -k `uname -r`.

```
herman@patricia-laptop:~$ sudo update-initramfs -k `uname -r` -uupdate-initramfs: Generating /boot/initrd.img-3.5.0-23-generic
cryptsetup: WARNING: failed to detect canonical device of /dev/sda6
W: TMPDIR is mounted noexec, will not cache run scripts.
herman@patricia-laptop:~$ 

```

Thanks in advance!

---

### Post by Toz on 2013-02-02
Originally posted in [http://ubuntuforums.org/showthread.php?t=2107061]("http://ubuntuforums.org/showthread.php?t=2107061") but moved to its own thread.

---

### Post by Toz on 2013-02-02
Did you use uswsusp in 12.04? If so, why? Did the kernel suspend/hibernate not work?

Were you using zram in 12.04 when hibernation was successful?

Did you at one time have an encrypted swap file?

I think that zram is interfering with your hibernate process. Try disabling the zram swaps and then hibernating. These commands should disable them. As root,:
```

swapoff /dev/zram0
umount /dev/zram0
echo 1 > /sys/block/zram0/reset

swapoff /dev/zram1
umount /dev/zram1
echo 1 > /sys/block/zram1/reset
```

---

### Post by Terraman on 2013-02-02
Thank you Toz for your reply!

```
Did you use uswsusp in 12.04? If so, why? Did the kernel suspend/hibernate not work?
```

No, I did not use uswusp in 12.04. Both pm-hinernate and pm-suspend worked fine in 12.04.

```
Were you using zram in 12.04 when hibernation was successful?
```

I was not using zram in 12.04.

```
Did you at one time have an encrypted swap file?

```

As far as I know, there is not an encrypted swap file. However, how can I be sure of that?

```
I think that zram is interfering with your hibernate process. Try disabling the zram swaps and then hibernating.
```

I have just removed zram. Unfortunately, hibernate is still having the same problem.

```
herman@patricia-laptop:~$ cat /proc/swaps 
Filename				Type		Size	Used	Priority
/dev/sda6                               partition	5219324	0	-1
herman@patricia-laptop:~$ 

```

---

### Post by Toz on 2013-02-02
Can you post back the contents of your /var/log/pm-suspend.log file? Easiest way it to run:
```
pastebinit /var/log/pm-suspend.log
```
...and post back the link that is generated.

---

### Post by Terraman on 2013-02-02
> **Toz said:**
> Can you post back the contents of your /var/log/pm-suspend.log file? Easiest way it to run:
```
pastebinit /var/log/pm-suspend.log
```
...and post back the link that is generated.

Here it is: [http://paste.ubuntu.com/1603352/]("http://paste.ubuntu.com/1603352/")

---

### Post by Toz on 2013-02-03
What is the make and model of your laptop?

If uswsusp is new and not working, I would suggest removing:
```
sudo apt-get purge uswsusp
sudo update-initramfs -u
```

Then reboot.

Then, disable zram swaps:
```
swapoff /dev/zram0
umount /dev/zram0
echo 1 > /sys/block/zram0/reset

swapoff /dev/zram1
umount /dev/zram1
echo 1 > /sys/block/zram1/reset
```
...and try hibernate again with a debug log:
```
sudo bash
mv /var/log/pm-suspend.log /var/log/pm-suspend.log.BAK
export PM_DEBUG=true
pm-hibernate
```

Then again post back the contents of the more detailed /var/log/pm-suspend.log:
```
pastebinit /var/log/pm-suspend.log
```
...as well as the results of this command:
```
cat /var/log/syslog* | grep PM:
```

---

### Post by Terraman on 2013-02-03
```
What is the make and model of your laptop?
```

```
herman@patricia-laptop:~$ sudo dmidecode
[sudo] password for herman: 
# dmidecode 2.11
SMBIOS 2.6 present.
16 structures occupying 653 bytes.
Table at 0x000FEC60.

Handle 0x0000, DMI type 0, 24 bytes
BIOS Information
	Vendor: INSYDE
	Version: R0240E2
	Release Date: 12/07/2009
	ROM Size: 1024 kB
	Characteristics:
		PCI is supported
		PNP is supported
		BIOS is upgradeable
		BIOS shadowing is allowed
		Boot from CD is supported
		Selectable boot is supported
		EDD is supported
		8042 keyboard services are supported (int 9h)
		CGA/mono video services are supported (int 10h)
		ACPI is supported
		USB legacy is supported
		Smart battery is supported
		BIOS boot specification is supported
		Function key-initiated network boot is supported
		Targeted content distribution is supported
	BIOS Revision: 2.40
	Firmware Revision: 2.40

Handle 0x0001, DMI type 1, 27 bytes
System Information
	Manufacturer: Sony Corporation
	Product Name: VPCW210AL
	Version: C1041ZPT
	Serial Number: 27518040-3009948
	UUID: 20B4150A-C1DD-DE11-8336-0024BE5AC042
	Wake-up Type: Power Switch
	SKU Number: N/A
	Family: VAIO

Handle 0x0002, DMI type 2, 10 bytes
Base Board Information
	Manufacturer: Sony Corporation
	Product Name: VAIO
	Version: N/A
	Serial Number: C1041ZPT
	Asset Tag: N/A
	Features:
		Board is a hosting board

Handle 0x0003, DMI type 3, 17 bytes
Chassis Information
	Manufacturer: Sony Corporation
	Type: Notebook
	Lock: Not Present
	Version: N/A
	Serial Number: N/A
	Asset Tag: N/A
	Boot-up State: Safe
	Power Supply State: Safe
	Thermal State: Safe
	Security Status: None
	OEM Information: 0x00000000

Handle 0x0004, DMI type 11, 5 bytes
OEM Strings
	String 1: 0000061634L
	String 2: FNC-EXTB
	String 3: 91RM36i2@lM@wcV5C2@GbfQmBv2Gbh0lhv2Mi30la9QMi2@Ga9
	String 4: Reserved
	String 5: Reserved

Handle 0x0005, DMI type 32, 20 bytes
System Boot Information
	Status: No errors detected

Handle 0x0006, DMI type 136, 6 bytes
OEM-specific Type
	Header and Data:
		88 06 06 00 02 00

Handle 0x0007, DMI type 16, 15 bytes
Physical Memory Array
	Location: System Board Or Motherboard
	Use: System Memory
	Error Correction Type: None
	Maximum Capacity: Unknown
	Error Information Handle: Not Provided
	Number Of Devices: 1

Handle 0x0008, DMI type 17, 21 bytes
Memory Device
	Array Handle: 0x0007
	Error Information Handle: Not Provided
	Total Width: 64 bits
	Data Width: 64 bits
	Size: 2048 MB
	Form Factor: SODIMM
	Set: None
	Locator: SODIMM1
	Bank Locator: Bank 0
	Type: DDR2
	Type Detail: Unknown

Handle 0x0009, DMI type 20, 19 bytes
Memory Device Mapped Address
	Starting Address: 0x00000000000
	Ending Address: 0x0007FFFFFFF
	Range Size: 2 GB
	Physical Device Handle: 0x0008
	Memory Array Mapped Address Handle: 0x000A
	Partition Row Position: Unknown
	Interleave Position: Unknown
	Interleaved Data Depth: Unknown

Handle 0x000A, DMI type 19, 15 bytes
Memory Array Mapped Address
	Starting Address: 0x00000000000
	Ending Address: 0x0007FFFFFFF
	Range Size: 2 GB
	Physical Array Handle: 0x0007
	Partition Width: 1

Handle 0x000B, DMI type 4, 35 bytes
Processor Information
	Socket Designation: N/A
	Type: Central Processor
	Family: Other
	Manufacturer: GenuineIntel
	ID: CA 06 01 00 FF FB E9 BF
	Version: Intel(R) Atom(TM) CPU N450   @ 1.66GHz
	Voltage: 1.2 V
	External Clock: 667 MHz
	Max Speed: 1666 MHz
	Current Speed: 1666 MHz
	Status: Populated, Enabled
	Upgrade: None
	L1 Cache Handle: 0x000C
	L2 Cache Handle: 0x000D
	L3 Cache Handle: 0x000E
	Serial Number: N/A
	Asset Tag: N/A
	Part Number: N/A

Handle 0x000C, DMI type 7, 19 bytes
Cache Information
	Socket Designation: L1 Cache
	Configuration: Enabled, Socketed, Level 1
	Operational Mode: Write Back
	Location: Internal
	Installed Size: 56 kB
	Maximum Size: 56 kB
	Supported SRAM Types:
		Other
	Installed SRAM Type: Other
	Speed: Unknown
	Error Correction Type: Single-bit ECC
	System Type: Other
	Associativity: Other

Handle 0x000D, DMI type 7, 19 bytes
Cache Information
	Socket Designation: L2 Cache
	Configuration: Enabled, Socketed, Level 2
	Operational Mode: Write Back
	Location: Internal
	Installed Size: 512 kB
	Maximum Size: 512 kB
	Supported SRAM Types:
		Other
	Installed SRAM Type: Burst
	Speed: Unknown
	Error Correction Type: Single-bit ECC
	System Type: Unified
	Associativity: 8-way Set-associative

Handle 0x000E, DMI type 7, 19 bytes
Cache Information
	Socket Designation: L3 Cache
	Configuration: Disabled, Not Socketed, Level 3
	Operational Mode: Unknown
	Location: Unknown
	Installed Size: 0 kB
	Maximum Size: 0 kB
	Supported SRAM Types:
		Unknown
	Installed SRAM Type: Unknown
	Speed: Unknown
	Error Correction Type: Unknown
	System Type: Unknown
	Associativity: Unknown

Handle 0x000F, DMI type 127, 4 bytes
End Of Table

```

```
If uswsusp is new and not working, I would suggest removing:
Code:

sudo apt-get purge uswsusp
sudo update-initramfs -u

Then reboot.
```

Done!

```
Then, disable zram swaps:
```

I have removed zram!

```
...and try hibernate again with a debug log:
Code:

sudo bash
mv /var/log/pm-suspend.log /var/log/pm-suspend.log.BAK
export PM_DEBUG=true
pm-hibernate


```

Done!

```
Then again post back the contents of the more detailed /var/log/pm-suspend.log:
```

Which is: [http://paste.ubuntu.com/1604850/]("http://paste.ubuntu.com/1604850/")

```
...as well as the results of this command:
```

```
herman@patricia-laptop:~$ cat /var/log/syslog* | grep PM:
Feb  1 11:34:34 patricia-laptop kernel: [ 4093.638920] PM: Marking nosave pages: [mem 0x0009f000-0x000fffff]
Feb  1 11:34:34 patricia-laptop kernel: [ 4093.638934] PM: Basic memory bitmaps created
Feb  1 11:36:57 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Feb  1 11:36:57 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Feb  1 11:36:57 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Feb  1 11:36:57 patricia-laptop kernel: [    0.096603] PM: Registering ACPI NVS region [mem 0x7f577000-0x7f5befff] (294912 bytes)
Feb  1 11:36:57 patricia-laptop kernel: [    1.485965] PM: Checking hibernation image partition /dev/sda5
Feb  1 11:36:57 patricia-laptop kernel: [    1.732185] PM: Hibernation image partition 8:5 present
Feb  1 11:36:57 patricia-laptop kernel: [    1.732189] PM: Looking for hibernation image.
Feb  1 11:36:57 patricia-laptop kernel: [    1.747101] PM: Image not found (code -22)
Feb  1 11:36:57 patricia-laptop kernel: [    1.747106] PM: Hibernation image not present or could not be loaded.
Feb  1 11:36:57 patricia-laptop kernel: [    3.883253] PM: Marking nosave pages: [mem 0x0009f000-0x000fffff]
Feb  1 11:36:57 patricia-laptop kernel: [    3.883264] PM: Basic memory bitmaps created
Feb  1 11:36:57 patricia-laptop kernel: [    3.930680] PM: Basic memory bitmaps freed
Feb  1 12:07:54 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Feb  1 12:07:54 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Feb  1 12:07:54 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Feb  1 12:07:54 patricia-laptop kernel: [    0.096601] PM: Registering ACPI NVS region [mem 0x7f577000-0x7f5befff] (294912 bytes)
Feb  1 12:07:54 patricia-laptop kernel: [    1.485649] PM: Checking hibernation image partition /dev/sda5
Feb  1 12:07:54 patricia-laptop kernel: [    1.716633] PM: Hibernation image partition 8:5 present
Feb  1 12:07:54 patricia-laptop kernel: [    1.716638] PM: Looking for hibernation image.
Feb  1 12:07:54 patricia-laptop kernel: [    1.731620] PM: Image not found (code -22)
Feb  1 12:07:54 patricia-laptop kernel: [    1.731624] PM: Hibernation image not present or could not be loaded.
Feb  1 12:07:54 patricia-laptop kernel: [    3.819473] PM: Marking nosave pages: [mem 0x0009f000-0x000fffff]
Feb  1 12:07:54 patricia-laptop kernel: [    3.819485] PM: Basic memory bitmaps created
Feb  1 12:07:54 patricia-laptop kernel: [    3.870607] PM: Basic memory bitmaps freed
Feb  1 12:17:13 patricia-laptop kernel: [  578.824332] PM: Hibernation mode set to 'platform'
Feb  1 12:17:25 patricia-laptop kernel: [  590.405735] PM: Marking nosave pages: [mem 0x0009f000-0x000fffff]
Feb  1 12:17:25 patricia-laptop kernel: [  590.405746] PM: Basic memory bitmaps created
Feb  1 12:19:12 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Feb  1 12:19:12 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Feb  1 12:19:12 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Feb  1 12:19:12 patricia-laptop kernel: [    0.096589] PM: Registering ACPI NVS region [mem 0x7f577000-0x7f5befff] (294912 bytes)
Feb  1 12:19:12 patricia-laptop kernel: [    1.489865] PM: Checking hibernation image partition /dev/sda5
Feb  1 12:19:12 patricia-laptop kernel: [    1.724454] PM: Hibernation image partition 8:5 present
Feb  1 12:19:12 patricia-laptop kernel: [    1.724459] PM: Looking for hibernation image.
Feb  1 12:19:12 patricia-laptop kernel: [    1.739398] PM: Image not found (code -22)
Feb  1 12:19:12 patricia-laptop kernel: [    1.739402] PM: Hibernation image not present or could not be loaded.
Feb  1 12:19:12 patricia-laptop kernel: [    3.839177] PM: Marking nosave pages: [mem 0x0009f000-0x000fffff]
Feb  1 12:19:12 patricia-laptop kernel: [    3.839187] PM: Basic memory bitmaps created
Feb  1 12:19:12 patricia-laptop kernel: [    3.889559] PM: Basic memory bitmaps freed
Feb  1 12:29:04 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Feb  1 12:29:04 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Feb  1 12:29:04 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Feb  1 12:29:04 patricia-laptop kernel: [    0.096607] PM: Registering ACPI NVS region [mem 0x7f577000-0x7f5befff] (294912 bytes)
Feb  1 12:29:04 patricia-laptop kernel: [    1.491220] PM: Checking hibernation image partition /dev/sda5
Feb  1 12:29:04 patricia-laptop kernel: [    1.731187] PM: Hibernation image partition 8:5 present
Feb  1 12:29:04 patricia-laptop kernel: [    1.731192] PM: Looking for hibernation image.
Feb  1 12:29:04 patricia-laptop kernel: [    1.746170] PM: Image not found (code -22)
Feb  1 12:29:04 patricia-laptop kernel: [    1.746175] PM: Hibernation image not present or could not be loaded.
Feb  1 12:29:04 patricia-laptop kernel: [    3.847429] PM: Marking nosave pages: [mem 0x0009f000-0x000fffff]
Feb  1 12:29:04 patricia-laptop kernel: [    3.847440] PM: Basic memory bitmaps created
Feb  1 12:29:04 patricia-laptop kernel: [    3.872753] PM: Basic memory bitmaps freed
Feb  1 12:32:24 patricia-laptop kernel: [  214.508215] PM: Marking nosave pages: [mem 0x0009f000-0x000fffff]
Feb  1 12:32:24 patricia-laptop kernel: [  214.508229] PM: Basic memory bitmaps created
Feb  1 12:34:18 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Feb  1 12:34:18 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Feb  1 12:34:18 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Feb  1 12:34:18 patricia-laptop kernel: [    0.100582] PM: Registering ACPI NVS region [mem 0x7f577000-0x7f5befff] (294912 bytes)
Feb  1 12:34:18 patricia-laptop kernel: [    1.497692] PM: Checking hibernation image partition /dev/sda5
Feb  1 12:34:18 patricia-laptop kernel: [    1.725882] PM: Hibernation image partition 8:5 present
Feb  1 12:34:18 patricia-laptop kernel: [    1.725887] PM: Looking for hibernation image.
Feb  1 12:34:18 patricia-laptop kernel: [    1.740866] PM: Image not found (code -22)
Feb  1 12:34:18 patricia-laptop kernel: [    1.740871] PM: Hibernation image not present or could not be loaded.
Feb  1 12:34:18 patricia-laptop kernel: [    3.752334] PM: Marking nosave pages: [mem 0x0009f000-0x000fffff]
Feb  1 12:34:18 patricia-laptop kernel: [    3.752344] PM: Basic memory bitmaps created
Feb  1 12:34:18 patricia-laptop kernel: [    3.783685] PM: Basic memory bitmaps freed
Feb  1 13:57:14 patricia-laptop kernel: [ 5042.399023] PM: Marking nosave pages: [mem 0x0009f000-0x000fffff]
Feb  1 13:57:14 patricia-laptop kernel: [ 5042.399036] PM: Basic memory bitmaps created
Feb  1 13:59:42 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Feb  1 13:59:42 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Feb  1 13:59:42 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Feb  1 13:59:42 patricia-laptop kernel: [    0.100599] PM: Registering ACPI NVS region [mem 0x7f577000-0x7f5befff] (294912 bytes)
Feb  1 13:59:42 patricia-laptop kernel: [    1.327545] PM: Checking hibernation image partition /dev/sda5
Feb  1 13:59:42 patricia-laptop kernel: [    1.571669] PM: Hibernation image partition 8:5 present
Feb  1 13:59:42 patricia-laptop kernel: [    1.571675] PM: Looking for hibernation image.
Feb  1 13:59:42 patricia-laptop kernel: [    1.586689] PM: Image not found (code -22)
Feb  1 13:59:42 patricia-laptop kernel: [    1.586694] PM: Hibernation image not present or could not be loaded.
Feb  1 13:59:42 patricia-laptop kernel: [    3.691609] PM: Marking nosave pages: [mem 0x0009f000-0x000fffff]
Feb  1 13:59:42 patricia-laptop kernel: [    3.691620] PM: Basic memory bitmaps created
Feb  1 13:59:42 patricia-laptop kernel: [    3.723157] PM: Basic memory bitmaps freed
Feb  1 14:13:58 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Feb  1 14:13:58 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Feb  1 14:13:58 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Feb  1 14:13:58 patricia-laptop kernel: [    0.100587] PM: Registering ACPI NVS region [mem 0x7f577000-0x7f5befff] (294912 bytes)
Feb  1 14:13:58 patricia-laptop kernel: [    1.319972] PM: Checking hibernation image partition /dev/sda6
Feb  1 14:13:58 patricia-laptop kernel: [    1.557777] PM: Hibernation image partition 8:6 present
Feb  1 14:13:58 patricia-laptop kernel: [    1.557783] PM: Looking for hibernation image.
Feb  1 14:13:58 patricia-laptop kernel: [    1.558102] PM: Image not found (code -22)
Feb  1 14:13:58 patricia-laptop kernel: [    1.558107] PM: Hibernation image not present or could not be loaded.
Feb  1 14:38:42 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Feb  1 14:38:42 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Feb  1 14:38:42 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Feb  1 14:38:42 patricia-laptop kernel: [    0.108594] PM: Registering ACPI NVS region [mem 0x7f577000-0x7f5befff] (294912 bytes)
Feb  1 14:38:42 patricia-laptop kernel: [    1.331678] PM: Checking hibernation image partition /dev/sda6
Feb  1 14:38:42 patricia-laptop kernel: [    1.571237] PM: Hibernation image partition 8:6 present
Feb  1 14:38:42 patricia-laptop kernel: [    1.571243] PM: Looking for hibernation image.
Feb  1 14:38:42 patricia-laptop kernel: [    1.571526] PM: Image not found (code -22)
Feb  1 14:38:42 patricia-laptop kernel: [    1.571531] PM: Hibernation image not present or could not be loaded.
Feb  1 15:52:50 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Feb  1 15:52:50 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Feb  1 15:52:50 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Feb  1 15:52:50 patricia-laptop kernel: [    0.096601] PM: Registering ACPI NVS region [mem 0x7f577000-0x7f5befff] (294912 bytes)
Feb  1 15:52:50 patricia-laptop kernel: [    1.470234] PM: Checking hibernation image partition /dev/sda6
Feb  1 15:52:50 patricia-laptop kernel: [    1.712947] PM: Hibernation image partition 8:6 present
Feb  1 15:52:50 patricia-laptop kernel: [    1.712952] PM: Looking for hibernation image.
Feb  1 15:52:50 patricia-laptop kernel: [    1.713266] PM: Image not found (code -22)
Feb  1 15:52:50 patricia-laptop kernel: [    1.713270] PM: Hibernation image not present or could not be loaded.
Feb  1 17:06:21 patricia-laptop kernel: [ 4431.470879] PM: Marking nosave pages: [mem 0x0009f000-0x000fffff]
Feb  1 17:06:21 patricia-laptop kernel: [ 4431.470893] PM: Basic memory bitmaps created
Feb  1 17:08:42 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Feb  1 17:08:42 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Feb  1 17:08:42 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Feb  1 17:08:42 patricia-laptop kernel: [    0.100583] PM: Registering ACPI NVS region [mem 0x7f577000-0x7f5befff] (294912 bytes)
Feb  1 17:08:42 patricia-laptop kernel: [    1.483918] PM: Checking hibernation image partition /dev/sda6
Feb  1 17:08:42 patricia-laptop kernel: [    1.731403] PM: Hibernation image partition 8:6 present
Feb  1 17:08:42 patricia-laptop kernel: [    1.731408] PM: Looking for hibernation image.
Feb  1 17:08:42 patricia-laptop kernel: [    1.731715] PM: Image not found (code -22)
Feb  1 17:08:42 patricia-laptop kernel: [    1.731720] PM: Hibernation image not present or could not be loaded.
Feb  1 17:08:42 patricia-laptop kernel: [    3.880475] PM: Marking nosave pages: [mem 0x0009f000-0x000fffff]
Feb  1 17:08:42 patricia-laptop kernel: [    3.880485] PM: Basic memory bitmaps created
Feb  1 17:08:42 patricia-laptop kernel: [    3.910789] PM: Basic memory bitmaps freed
Feb  1 17:42:46 patricia-laptop kernel: [ 2119.892045] PM: Marking nosave pages: [mem 0x0009f000-0x000fffff]
Feb  1 17:42:46 patricia-laptop kernel: [ 2119.892058] PM: Basic memory bitmaps created
Feb  1 17:44:56 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Feb  1 17:44:56 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Feb  1 17:44:56 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Feb  1 17:44:56 patricia-laptop kernel: [    0.100589] PM: Registering ACPI NVS region [mem 0x7f577000-0x7f5befff] (294912 bytes)
Feb  1 17:44:56 patricia-laptop kernel: [    1.489708] PM: Checking hibernation image partition UUID=84c2098a-83b5-4a83-a053-8c9277da2941
Feb  1 17:44:56 patricia-laptop kernel: [    1.732758] PM: Hibernation image not present or could not be loaded.
Feb  1 17:44:56 patricia-laptop kernel: [    3.891652] PM: Marking nosave pages: [mem 0x0009f000-0x000fffff]
Feb  1 17:44:56 patricia-laptop kernel: [    3.891662] PM: Basic memory bitmaps created
Feb  1 17:44:56 patricia-laptop kernel: [    3.923250] PM: Basic memory bitmaps freed
Feb  1 18:26:52 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Feb  1 18:26:52 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Feb  1 18:26:52 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Feb  1 18:26:52 patricia-laptop kernel: [    0.096595] PM: Registering ACPI NVS region [mem 0x7f577000-0x7f5befff] (294912 bytes)
Feb  1 18:26:52 patricia-laptop kernel: [    1.474272] PM: Checking hibernation image partition UUID=84c2098a-83b5-4a83-a053-8c9277da2941
Feb  1 18:26:52 patricia-laptop kernel: [    1.710721] PM: Hibernation image not present or could not be loaded.
Feb  1 18:26:52 patricia-laptop kernel: [    3.768317] PM: Marking nosave pages: [mem 0x0009f000-0x000fffff]
Feb  1 18:26:52 patricia-laptop kernel: [    3.768328] PM: Basic memory bitmaps created
Feb  1 18:26:52 patricia-laptop kernel: [    3.798630] PM: Basic memory bitmaps freed
Feb  1 18:57:36 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Feb  1 18:57:36 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Feb  1 18:57:36 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Feb  1 18:57:36 patricia-laptop kernel: [    0.104589] PM: Registering ACPI NVS region [mem 0x7f577000-0x7f5befff] (294912 bytes)
Feb  1 18:57:36 patricia-laptop kernel: [    1.327798] PM: Checking hibernation image partition UUID=84c2098a-83b5-4a83-a053-8c9277da2941
Feb  1 18:57:36 patricia-laptop kernel: [    1.567235] PM: Hibernation image not present or could not be loaded.
Feb  1 18:57:36 patricia-laptop kernel: [    3.583308] PM: Marking nosave pages: [mem 0x0009f000-0x000fffff]
Feb  1 18:57:36 patricia-laptop kernel: [    3.583320] PM: Basic memory bitmaps created
Feb  1 18:57:36 patricia-laptop kernel: [    3.614729] PM: Basic memory bitmaps freed
Feb  2 13:33:30 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Feb  2 13:33:30 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Feb  2 13:33:30 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Feb  2 13:33:30 patricia-laptop kernel: [    0.100598] PM: Registering ACPI NVS region [mem 0x7f577000-0x7f5befff] (294912 bytes)
Feb  2 13:33:30 patricia-laptop kernel: [    1.323662] PM: Checking hibernation image partition UUID=84c2098a-83b5-4a83-a053-8c9277da2941
Feb  2 13:33:30 patricia-laptop kernel: [    1.545725] PM: Hibernation image not present or could not be loaded.
Feb  2 13:33:30 patricia-laptop kernel: [    8.656219] PM: Marking nosave pages: [mem 0x0009f000-0x000fffff]
Feb  2 13:33:30 patricia-laptop kernel: [    8.656232] PM: Basic memory bitmaps created
Feb  2 13:33:30 patricia-laptop kernel: [    8.967729] PM: Basic memory bitmaps freed
Feb  2 13:44:47 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Feb  2 13:44:47 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Feb  2 13:44:47 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Feb  2 13:44:47 patricia-laptop kernel: [    0.100591] PM: Registering ACPI NVS region [mem 0x7f577000-0x7f5befff] (294912 bytes)
Feb  2 13:44:47 patricia-laptop kernel: [    1.489810] PM: Checking hibernation image partition UUID=84c2098a-83b5-4a83-a053-8c9277da2941
Feb  2 13:44:47 patricia-laptop kernel: [    1.721220] PM: Hibernation image not present or could not be loaded.
Feb  2 13:44:47 patricia-laptop kernel: [    8.835130] PM: Marking nosave pages: [mem 0x0009f000-0x000fffff]
Feb  2 13:44:47 patricia-laptop kernel: [    8.835142] PM: Basic memory bitmaps created
Feb  2 13:44:47 patricia-laptop kernel: [    9.164258] PM: Basic memory bitmaps freed
Feb  2 14:01:21 patricia-laptop kernel: [ 1018.159796] PM: Marking nosave pages: [mem 0x0009f000-0x000fffff]
Feb  2 14:01:21 patricia-laptop kernel: [ 1018.159817] PM: Basic memory bitmaps created
Feb  2 14:03:13 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Feb  2 14:03:13 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Feb  2 14:03:13 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Feb  2 14:03:13 patricia-laptop kernel: [    0.096585] PM: Registering ACPI NVS region [mem 0x7f577000-0x7f5befff] (294912 bytes)
Feb  2 14:03:13 patricia-laptop kernel: [    1.491516] PM: Checking hibernation image partition UUID=5b29589b-9169-4676-94f4-b4718e39c4fd
Feb  2 14:03:13 patricia-laptop kernel: [    1.703421] PM: Hibernation image not present or could not be loaded.
Feb  2 14:03:13 patricia-laptop kernel: [    3.736477] PM: Marking nosave pages: [mem 0x0009f000-0x000fffff]
Feb  2 14:03:13 patricia-laptop kernel: [    3.736487] PM: Basic memory bitmaps created
Feb  2 14:03:13 patricia-laptop kernel: [    3.761810] PM: Basic memory bitmaps freed
Feb  2 14:09:02 patricia-laptop kernel: [  414.282877] PM: Marking nosave pages: [mem 0x0009f000-0x000fffff]
Feb  2 14:09:02 patricia-laptop kernel: [  414.282898] PM: Basic memory bitmaps created
Feb  2 14:10:47 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Feb  2 14:10:47 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Feb  2 14:10:47 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Feb  2 14:10:47 patricia-laptop kernel: [    0.096588] PM: Registering ACPI NVS region [mem 0x7f577000-0x7f5befff] (294912 bytes)
Feb  2 14:10:47 patricia-laptop kernel: [    1.475737] PM: Checking hibernation image partition UUID=5b29589b-9169-4676-94f4-b4718e39c4fd
Feb  2 14:10:47 patricia-laptop kernel: [    1.704607] PM: Hibernation image not present or could not be loaded.
Feb  2 14:10:47 patricia-laptop kernel: [    3.799809] PM: Marking nosave pages: [mem 0x0009f000-0x000fffff]
Feb  2 14:10:47 patricia-laptop kernel: [    3.799820] PM: Basic memory bitmaps created
Feb  2 14:10:47 patricia-laptop kernel: [    3.825521] PM: Basic memory bitmaps freed
Feb  3 00:04:16 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Feb  3 00:04:16 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Feb  3 00:04:16 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Feb  3 00:04:16 patricia-laptop kernel: [    0.100599] PM: Registering ACPI NVS region [mem 0x7f577000-0x7f5befff] (294912 bytes)
Feb  3 00:04:16 patricia-laptop kernel: [    1.481662] PM: Checking hibernation image partition UUID=5b29589b-9169-4676-94f4-b4718e39c4fd
Feb  3 00:04:16 patricia-laptop kernel: [    1.713021] PM: Hibernation image not present or could not be loaded.
Feb  3 00:04:16 patricia-laptop kernel: [    3.827408] PM: Marking nosave pages: [mem 0x0009f000-0x000fffff]
Feb  3 00:04:16 patricia-laptop kernel: [    3.827419] PM: Basic memory bitmaps created
Feb  3 00:04:16 patricia-laptop kernel: [    3.853303] PM: Basic memory bitmaps freed
Feb  3 12:09:29 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Feb  3 12:09:29 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Feb  3 12:09:29 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Feb  3 12:09:29 patricia-laptop kernel: [    0.096600] PM: Registering ACPI NVS region [mem 0x7f577000-0x7f5befff] (294912 bytes)
Feb  3 12:09:29 patricia-laptop kernel: [    1.485830] PM: Checking hibernation image partition UUID=5b29589b-9169-4676-94f4-b4718e39c4fd
Feb  3 12:09:29 patricia-laptop kernel: [    1.721319] PM: Hibernation image not present or could not be loaded.
Feb  3 12:09:29 patricia-laptop kernel: [    3.791398] PM: Marking nosave pages: [mem 0x0009f000-0x000fffff]
Feb  3 12:09:29 patricia-laptop kernel: [    3.791410] PM: Basic memory bitmaps created
Feb  3 12:09:29 patricia-laptop kernel: [    3.822573] PM: Basic memory bitmaps freed
Feb  3 12:31:35 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Feb  3 12:31:35 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Feb  3 12:31:35 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Feb  3 12:31:35 patricia-laptop kernel: [    0.096600] PM: Registering ACPI NVS region [mem 0x7f577000-0x7f5befff] (294912 bytes)
Feb  3 12:31:35 patricia-laptop kernel: [    1.491583] PM: Checking hibernation image partition UUID=5b29589b-9169-4676-94f4-b4718e39c4fd
Feb  3 12:31:35 patricia-laptop kernel: [    1.716389] PM: Hibernation image not present or could not be loaded.
Feb  3 12:48:02 patricia-laptop kernel: [ 1006.156422] PM: Marking nosave pages: [mem 0x0009f000-0x000fffff]
Feb  3 12:48:02 patricia-laptop kernel: [ 1006.156434] PM: Basic memory bitmaps created
Feb  3 12:50:09 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Feb  3 12:50:09 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Feb  3 12:50:09 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Feb  3 12:50:09 patricia-laptop kernel: [    0.100591] PM: Registering ACPI NVS region [mem 0x7f577000-0x7f5befff] (294912 bytes)
Feb  3 12:50:09 patricia-laptop kernel: [    1.486797] PM: Checking hibernation image partition UUID=5b29589b-9169-4676-94f4-b4718e39c4fd
Feb  3 12:50:09 patricia-laptop kernel: [    1.710673] PM: Hibernation image not present or could not be loaded.
Jan 31 11:47:23 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Jan 31 11:47:23 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Jan 31 11:47:23 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Jan 31 11:47:23 patricia-laptop kernel: [    0.096599] PM: Registering ACPI NVS region [mem 0x7f577000-0x7f5befff] (294912 bytes)
Jan 31 11:47:23 patricia-laptop kernel: [    1.471771] PM: Checking hibernation image partition /dev/sdb1
Jan 31 11:47:23 patricia-laptop kernel: [    1.699297] PM: Hibernation image not present or could not be loaded.
Jan 31 11:54:39 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Jan 31 11:54:39 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Jan 31 11:54:39 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Jan 31 11:54:39 patricia-laptop kernel: [    0.096601] PM: Registering ACPI NVS region [mem 0x7f577000-0x7f5befff] (294912 bytes)
Jan 31 11:54:39 patricia-laptop kernel: [    1.313859] PM: Checking hibernation image partition /dev/sdb1
Jan 31 11:54:39 patricia-laptop kernel: [    1.552433] PM: Hibernation image not present or could not be loaded.
Jan 31 12:43:35 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Jan 31 12:43:35 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Jan 31 12:43:35 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Jan 31 12:43:35 patricia-laptop kernel: [    0.096604] PM: Registering ACPI NVS region [mem 0x7f577000-0x7f5befff] (294912 bytes)
Jan 31 12:43:35 patricia-laptop kernel: [    1.469788] PM: Checking hibernation image partition /dev/sdb1
Jan 31 12:43:35 patricia-laptop kernel: [    1.709964] PM: Hibernation image not present or could not be loaded.
Jan 31 14:27:11 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Jan 31 14:27:11 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Jan 31 14:27:11 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Jan 31 14:27:11 patricia-laptop kernel: [    0.096607] PM: Registering ACPI NVS region [mem 0x7f577000-0x7f5befff] (294912 bytes)
Jan 31 14:27:11 patricia-laptop kernel: [    1.479086] PM: Checking hibernation image partition /dev/sdb1
Jan 31 14:27:11 patricia-laptop kernel: [    1.718589] PM: Hibernation image not present or could not be loaded.
Jan 31 14:41:27 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Jan 31 14:41:27 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Jan 31 14:41:27 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Jan 31 14:41:27 patricia-laptop kernel: [    0.104607] PM: Registering ACPI NVS region [mem 0x7f577000-0x7f5befff] (294912 bytes)
Jan 31 14:41:27 patricia-laptop kernel: [    1.479182] PM: Checking hibernation image partition /dev/sdb1
Jan 31 14:41:27 patricia-laptop kernel: [    1.721990] PM: Hibernation image not present or could not be loaded.
Jan 31 14:55:30 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Jan 31 14:55:30 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Jan 31 14:55:30 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Jan 31 14:55:30 patricia-laptop kernel: [    0.096604] PM: Registering ACPI NVS region [mem 0x7f577000-0x7f5befff] (294912 bytes)
Jan 31 14:55:30 patricia-laptop kernel: [    1.482304] PM: Checking hibernation image partition /dev/sda6
Jan 31 14:55:30 patricia-laptop kernel: [    1.721458] PM: Hibernation image partition 8:6 present
Jan 31 14:55:30 patricia-laptop kernel: [    1.721464] PM: Looking for hibernation image.
Jan 31 14:55:30 patricia-laptop kernel: [    1.721742] PM: Image not found (code -22)
Jan 31 14:55:30 patricia-laptop kernel: [    1.721747] PM: Hibernation image not present or could not be loaded.
Jan 31 15:16:53 patricia-laptop kernel: [ 1299.748737] PM: Marking nosave pages: [mem 0x0009f000-0x000fffff]
Jan 31 15:16:53 patricia-laptop kernel: [ 1299.748750] PM: Basic memory bitmaps created
Jan 31 15:19:00 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Jan 31 15:19:00 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Jan 31 15:19:00 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Jan 31 15:19:00 patricia-laptop kernel: [    0.100607] PM: Registering ACPI NVS region [mem 0x7f577000-0x7f5befff] (294912 bytes)
Jan 31 15:19:00 patricia-laptop kernel: [    1.481833] PM: Checking hibernation image partition /dev/sda6
Jan 31 15:19:00 patricia-laptop kernel: [    1.726286] PM: Hibernation image partition 8:6 present
Jan 31 15:19:00 patricia-laptop kernel: [    1.726292] PM: Looking for hibernation image.
Jan 31 15:19:00 patricia-laptop kernel: [    1.726592] PM: Image not found (code -22)
Jan 31 15:19:00 patricia-laptop kernel: [    1.726597] PM: Hibernation image not present or could not be loaded.
Jan 31 15:26:24 patricia-laptop kernel: [  512.909424] PM: Marking nosave pages: [mem 0x0009f000-0x000fffff]
Jan 31 15:26:24 patricia-laptop kernel: [  512.909438] PM: Basic memory bitmaps created
Jan 31 15:28:16 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Jan 31 15:28:16 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Jan 31 15:28:16 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Jan 31 15:28:16 patricia-laptop kernel: [    0.100604] PM: Registering ACPI NVS region [mem 0x7f577000-0x7f5befff] (294912 bytes)
Jan 31 15:28:16 patricia-laptop kernel: [    1.475109] PM: Checking hibernation image partition /dev/sda6
Jan 31 15:28:16 patricia-laptop kernel: [    1.722147] PM: Hibernation image partition 8:6 present
Jan 31 15:28:16 patricia-laptop kernel: [    1.722153] PM: Looking for hibernation image.
Jan 31 15:28:16 patricia-laptop kernel: [    1.722475] PM: Image not found (code -22)
Jan 31 15:28:16 patricia-laptop kernel: [    1.722479] PM: Hibernation image not present or could not be loaded.
Jan 31 15:50:56 patricia-laptop kernel: [ 1428.919280] PM: Marking nosave pages: [mem 0x0009f000-0x000fffff]
Jan 31 15:50:56 patricia-laptop kernel: [ 1428.919301] PM: Basic memory bitmaps created
Jan 31 15:53:36 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Jan 31 15:53:36 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Jan 31 15:53:36 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Jan 31 15:53:36 patricia-laptop kernel: [    0.100603] PM: Registering ACPI NVS region [mem 0x7f577000-0x7f5befff] (294912 bytes)
Jan 31 15:53:36 patricia-laptop kernel: [    1.475625] PM: Checking hibernation image partition /dev/sda6
Jan 31 15:53:36 patricia-laptop kernel: [    1.711791] PM: Hibernation image partition 8:6 present
Jan 31 15:53:36 patricia-laptop kernel: [    1.711796] PM: Looking for hibernation image.
Jan 31 15:53:36 patricia-laptop kernel: [    1.712113] PM: Image not found (code -22)
Jan 31 15:53:36 patricia-laptop kernel: [    1.712117] PM: Hibernation image not present or could not be loaded.
Jan 31 15:53:36 patricia-laptop kernel: [    3.759243] PM: Marking nosave pages: [mem 0x0009f000-0x000fffff]
Jan 31 15:53:36 patricia-laptop kernel: [    3.759254] PM: Basic memory bitmaps created
Jan 31 15:53:36 patricia-laptop kernel: [    3.806898] PM: Basic memory bitmaps freed
Jan 31 15:55:40 patricia-laptop kernel: [  199.684125] PM: Marking nosave pages: [mem 0x0009f000-0x000fffff]
Jan 31 15:55:40 patricia-laptop kernel: [  199.684139] PM: Basic memory bitmaps created
Jan 31 15:55:40 patricia-laptop kernel: [  199.718490] PM: Basic memory bitmaps freed
Jan 31 15:58:02 patricia-laptop kernel: [  341.335783] PM: Marking nosave pages: [mem 0x0009f000-0x000fffff]
Jan 31 15:58:02 patricia-laptop kernel: [  341.335804] PM: Basic memory bitmaps created
Jan 31 15:59:52 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Jan 31 15:59:52 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Jan 31 15:59:52 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Jan 31 15:59:52 patricia-laptop kernel: [    0.104598] PM: Registering ACPI NVS region [mem 0x7f577000-0x7f5befff] (294912 bytes)
Jan 31 15:59:52 patricia-laptop kernel: [    1.326316] PM: Checking hibernation image partition /dev/sda6
Jan 31 15:59:52 patricia-laptop kernel: [    1.569448] PM: Hibernation image partition 8:6 present
Jan 31 15:59:52 patricia-laptop kernel: [    1.569453] PM: Looking for hibernation image.
Jan 31 15:59:52 patricia-laptop kernel: [    1.569736] PM: Image not found (code -22)
Jan 31 15:59:52 patricia-laptop kernel: [    1.569740] PM: Hibernation image not present or could not be loaded.
Jan 31 15:59:52 patricia-laptop kernel: [    3.643265] PM: Marking nosave pages: [mem 0x0009f000-0x000fffff]
Jan 31 15:59:52 patricia-laptop kernel: [    3.643277] PM: Basic memory bitmaps created
Jan 31 15:59:52 patricia-laptop kernel: [    3.689645] PM: Basic memory bitmaps freed
Jan 31 16:13:32 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Jan 31 16:13:32 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Jan 31 16:13:32 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Jan 31 16:13:32 patricia-laptop kernel: [    0.096609] PM: Registering ACPI NVS region [mem 0x7f577000-0x7f5befff] (294912 bytes)
Jan 31 16:13:32 patricia-laptop kernel: [    1.481835] PM: Checking hibernation image partition /dev/sda6
Jan 31 16:13:32 patricia-laptop kernel: [    1.726537] PM: Hibernation image partition 8:6 present
Jan 31 16:13:32 patricia-laptop kernel: [    1.726543] PM: Looking for hibernation image.
Jan 31 16:13:32 patricia-laptop kernel: [    1.726847] PM: Image not found (code -22)
Jan 31 16:13:32 patricia-laptop kernel: [    1.726851] PM: Hibernation image not present or could not be loaded.
Jan 31 16:13:32 patricia-laptop kernel: [    3.847589] PM: Marking nosave pages: [mem 0x0009f000-0x000fffff]
Jan 31 16:13:32 patricia-laptop kernel: [    3.847599] PM: Basic memory bitmaps created
Jan 31 16:13:32 patricia-laptop kernel: [    3.890666] PM: Basic memory bitmaps freed
Jan 31 16:16:51 patricia-laptop kernel: [  216.311309] PM: Marking nosave pages: [mem 0x0009f000-0x000fffff]
Jan 31 16:16:51 patricia-laptop kernel: [  216.311321] PM: Basic memory bitmaps created
Jan 31 16:16:51 patricia-laptop kernel: [  216.342799] PM: Basic memory bitmaps freed
Jan 31 16:17:11 patricia-laptop kernel: [  237.006064] PM: Marking nosave pages: [mem 0x0009f000-0x000fffff]
Jan 31 16:17:11 patricia-laptop kernel: [  237.006084] PM: Basic memory bitmaps created
Jan 31 16:18:58 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Jan 31 16:18:58 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Jan 31 16:18:58 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Jan 31 16:18:58 patricia-laptop kernel: [    0.100589] PM: Registering ACPI NVS region [mem 0x7f577000-0x7f5befff] (294912 bytes)
Jan 31 16:18:58 patricia-laptop kernel: [    1.475000] PM: Checking hibernation image partition /dev/sda6
Jan 31 16:18:58 patricia-laptop kernel: [    1.718652] PM: Hibernation image partition 8:6 present
Jan 31 16:18:58 patricia-laptop kernel: [    1.718658] PM: Looking for hibernation image.
Jan 31 16:18:58 patricia-laptop kernel: [    1.718968] PM: Image not found (code -22)
Jan 31 16:18:58 patricia-laptop kernel: [    1.718973] PM: Hibernation image not present or could not be loaded.
Jan 31 16:18:58 patricia-laptop kernel: [    3.803338] PM: Marking nosave pages: [mem 0x0009f000-0x000fffff]
Jan 31 16:18:58 patricia-laptop kernel: [    3.803348] PM: Basic memory bitmaps created
Jan 31 16:18:58 patricia-laptop kernel: [    3.849688] PM: Basic memory bitmaps freed
Jan 31 16:33:54 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Jan 31 16:33:54 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Jan 31 16:33:54 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Jan 31 16:33:54 patricia-laptop kernel: [    0.096590] PM: Registering ACPI NVS region [mem 0x7f577000-0x7f5befff] (294912 bytes)
Jan 31 16:33:54 patricia-laptop kernel: [    1.490556] PM: Checking hibernation image partition /dev/sda6
Jan 31 16:33:54 patricia-laptop kernel: [    1.723506] PM: Hibernation image partition 8:6 present
Jan 31 16:33:54 patricia-laptop kernel: [    1.723512] PM: Looking for hibernation image.
Jan 31 16:33:54 patricia-laptop kernel: [    1.723823] PM: Image not found (code -22)
Jan 31 16:33:54 patricia-laptop kernel: [    1.723827] PM: Hibernation image not present or could not be loaded.
Jan 31 16:33:54 patricia-laptop kernel: [    3.859650] PM: Marking nosave pages: [mem 0x0009f000-0x000fffff]
Jan 31 16:33:54 patricia-laptop kernel: [    3.859661] PM: Basic memory bitmaps created
Jan 31 16:33:54 patricia-laptop kernel: [    3.912653] PM: Basic memory bitmaps freed
Jan 31 16:36:05 patricia-laptop kernel: [  147.414311] PM: Marking nosave pages: [mem 0x0009f000-0x000fffff]
Jan 31 16:36:05 patricia-laptop kernel: [  147.414323] PM: Basic memory bitmaps created
Jan 31 16:37:58 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Jan 31 16:37:58 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Jan 31 16:37:58 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Jan 31 16:37:58 patricia-laptop kernel: [    0.100603] PM: Registering ACPI NVS region [mem 0x7f577000-0x7f5befff] (294912 bytes)
Jan 31 16:37:58 patricia-laptop kernel: [    1.495248] PM: Checking hibernation image partition /dev/sda6
Jan 31 16:37:58 patricia-laptop kernel: [    1.738605] PM: Hibernation image partition 8:6 present
Jan 31 16:37:58 patricia-laptop kernel: [    1.738610] PM: Looking for hibernation image.
Jan 31 16:37:58 patricia-laptop kernel: [    1.738919] PM: Image not found (code -22)
Jan 31 16:37:58 patricia-laptop kernel: [    1.738924] PM: Hibernation image not present or could not be loaded.
Jan 31 16:37:58 patricia-laptop kernel: [    3.783247] PM: Marking nosave pages: [mem 0x0009f000-0x000fffff]
Jan 31 16:37:58 patricia-laptop kernel: [    3.783258] PM: Basic memory bitmaps created
Jan 31 16:37:58 patricia-laptop kernel: [    3.827549] PM: Basic memory bitmaps freed
Jan 31 17:06:25 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Jan 31 17:06:25 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Jan 31 17:06:25 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Jan 31 17:06:25 patricia-laptop kernel: [    0.104610] PM: Registering ACPI NVS region [mem 0x7f577000-0x7f5befff] (294912 bytes)
Jan 31 17:06:25 patricia-laptop kernel: [    1.478738] PM: Checking hibernation image partition /dev/sda6
Jan 31 17:06:25 patricia-laptop kernel: [    1.716470] PM: Hibernation image partition 8:6 present
Jan 31 17:06:25 patricia-laptop kernel: [    1.716476] PM: Looking for hibernation image.
Jan 31 17:06:25 patricia-laptop kernel: [    1.716791] PM: Image not found (code -22)
Jan 31 17:06:25 patricia-laptop kernel: [    1.716795] PM: Hibernation image not present or could not be loaded.
Jan 31 17:06:25 patricia-laptop kernel: [    3.767312] PM: Marking nosave pages: [mem 0x0009f000-0x000fffff]
Jan 31 17:06:25 patricia-laptop kernel: [    3.767322] PM: Basic memory bitmaps created
Jan 31 17:06:25 patricia-laptop kernel: [    3.816594] PM: Basic memory bitmaps freed
Jan 31 17:42:45 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Jan 31 17:42:45 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Jan 31 17:42:45 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Jan 31 17:42:45 patricia-laptop kernel: [    0.104601] PM: Registering ACPI NVS region [mem 0x7f577000-0x7f5befff] (294912 bytes)
Jan 31 17:42:45 patricia-laptop kernel: [    1.493717] PM: Checking hibernation image partition /dev/sda5
Jan 31 17:42:45 patricia-laptop kernel: [    1.731158] PM: Hibernation image partition 8:5 present
Jan 31 17:42:45 patricia-laptop kernel: [    1.731164] PM: Looking for hibernation image.
Jan 31 17:42:45 patricia-laptop kernel: [    1.746111] PM: Image not found (code -22)
Jan 31 17:42:45 patricia-laptop kernel: [    1.746116] PM: Hibernation image not present or could not be loaded.
Jan 31 17:42:45 patricia-laptop kernel: [    3.799224] PM: Marking nosave pages: [mem 0x0009f000-0x000fffff]
Jan 31 17:42:45 patricia-laptop kernel: [    3.799234] PM: Basic memory bitmaps created
Jan 31 17:42:45 patricia-laptop kernel: [    3.842582] PM: Basic memory bitmaps freed
Jan 31 17:45:11 patricia-laptop kernel: [  163.365863] PM: Marking nosave pages: [mem 0x0009f000-0x000fffff]
Jan 31 17:45:11 patricia-laptop kernel: [  163.365877] PM: Basic memory bitmaps created
Jan 31 17:47:28 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Jan 31 17:47:28 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Jan 31 17:47:28 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Jan 31 17:47:28 patricia-laptop kernel: [    0.100594] PM: Registering ACPI NVS region [mem 0x7f577000-0x7f5befff] (294912 bytes)
Jan 31 17:47:28 patricia-laptop kernel: [    1.487285] PM: Checking hibernation image partition /dev/sda5
Jan 31 17:47:28 patricia-laptop kernel: [    1.731027] PM: Hibernation image partition 8:5 present
Jan 31 17:47:28 patricia-laptop kernel: [    1.731033] PM: Looking for hibernation image.
Jan 31 17:47:28 patricia-laptop kernel: [    1.746002] PM: Image not found (code -22)
Jan 31 17:47:28 patricia-laptop kernel: [    1.746006] PM: Hibernation image not present or could not be loaded.
Jan 31 17:47:28 patricia-laptop kernel: [    3.896535] PM: Marking nosave pages: [mem 0x0009f000-0x000fffff]
Jan 31 17:47:28 patricia-laptop kernel: [    3.896545] PM: Basic memory bitmaps created
Jan 31 17:47:28 patricia-laptop kernel: [    3.942201] PM: Basic memory bitmaps freed
Jan 31 18:10:28 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Jan 31 18:10:28 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Jan 31 18:10:28 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Jan 31 18:10:28 patricia-laptop kernel: [    0.200477] PM: Registering ACPI NVS region [mem 0x7f577000-0x7f5befff] (294912 bytes)
Jan 31 18:10:28 patricia-laptop kernel: [    1.575283] PM: Checking hibernation image partition /dev/sda5
Jan 31 18:10:28 patricia-laptop kernel: [    1.813743] PM: Hibernation image partition 8:5 present
Jan 31 18:10:28 patricia-laptop kernel: [    1.813749] PM: Looking for hibernation image.
Jan 31 18:10:28 patricia-laptop kernel: [    1.828684] PM: Image not found (code -22)
Jan 31 18:10:28 patricia-laptop kernel: [    1.828689] PM: Hibernation image not present or could not be loaded.
Jan 31 18:10:28 patricia-laptop kernel: [    3.911257] PM: Marking nosave pages: [mem 0x0009f000-0x000fffff]
Jan 31 18:10:28 patricia-laptop kernel: [    3.911267] PM: Basic memory bitmaps created
Jan 31 18:10:28 patricia-laptop kernel: [    3.958238] PM: Basic memory bitmaps freed
Jan 31 18:15:36 patricia-laptop kernel: [  324.832725] PM: Marking nosave pages: [mem 0x0009f000-0x000fffff]
Jan 31 18:15:36 patricia-laptop kernel: [  324.832738] PM: Basic memory bitmaps created
Jan 31 18:30:53 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Jan 31 18:30:53 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Jan 31 18:30:53 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Jan 31 18:30:53 patricia-laptop kernel: [    0.104591] PM: Registering ACPI NVS region [mem 0x7f577000-0x7f5befff] (294912 bytes)
Jan 31 18:30:53 patricia-laptop kernel: [    1.497705] PM: Checking hibernation image partition /dev/sda5
Jan 31 18:30:53 patricia-laptop kernel: [    1.729167] PM: Hibernation image partition 8:5 present
Jan 31 18:30:53 patricia-laptop kernel: [    1.729173] PM: Looking for hibernation image.
Jan 31 18:30:53 patricia-laptop kernel: [    1.744127] PM: Image not found (code -22)
Jan 31 18:30:53 patricia-laptop kernel: [    1.744132] PM: Hibernation image not present or could not be loaded.
Jan 31 18:30:53 patricia-laptop kernel: [    3.882918] PM: Marking nosave pages: [mem 0x0009f000-0x000fffff]
Jan 31 18:30:53 patricia-laptop kernel: [    3.882929] PM: Basic memory bitmaps created
Jan 31 18:30:53 patricia-laptop kernel: [    3.929350] PM: Basic memory bitmaps freed
Jan 31 18:54:34 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Jan 31 18:54:34 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Jan 31 18:54:34 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Jan 31 18:54:34 patricia-laptop kernel: [    0.108610] PM: Registering ACPI NVS region [mem 0x7f577000-0x7f5befff] (294912 bytes)
Jan 31 18:54:34 patricia-laptop kernel: [    1.497849] PM: Checking hibernation image partition /dev/sda5
Jan 31 18:54:34 patricia-laptop kernel: [    1.740806] PM: Hibernation image partition 8:5 present
Jan 31 18:54:34 patricia-laptop kernel: [    1.740811] PM: Looking for hibernation image.
Jan 31 18:54:34 patricia-laptop kernel: [    1.755753] PM: Image not found (code -22)
Jan 31 18:54:34 patricia-laptop kernel: [    1.755758] PM: Hibernation image not present or could not be loaded.
Jan 31 18:54:34 patricia-laptop kernel: [    3.815324] PM: Marking nosave pages: [mem 0x0009f000-0x000fffff]
Jan 31 18:54:34 patricia-laptop kernel: [    3.815335] PM: Basic memory bitmaps created
Jan 31 18:54:34 patricia-laptop kernel: [    3.863196] PM: Basic memory bitmaps freed
Jan 31 18:57:29 patricia-laptop kernel: [  601.228965] PM: Marking nosave pages: [mem 0x0009f000-0x000fffff]
Jan 31 18:57:29 patricia-laptop kernel: [  601.228978] PM: Basic memory bitmaps created
Jan 31 18:57:29 patricia-laptop kernel: [  601.258662] PM: Basic memory bitmaps freed
Jan 31 18:58:03 patricia-laptop kernel: [  634.707568] PM: Marking nosave pages: [mem 0x0009f000-0x000fffff]
Jan 31 18:58:03 patricia-laptop kernel: [  634.707581] PM: Basic memory bitmaps created
Jan 31 18:58:03 patricia-laptop kernel: [  634.734600] PM: Basic memory bitmaps freed
Jan 31 19:09:09 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Jan 31 19:09:09 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Jan 31 19:09:09 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Jan 31 19:09:09 patricia-laptop kernel: [    0.100598] PM: Registering ACPI NVS region [mem 0x7f577000-0x7f5befff] (294912 bytes)
Jan 31 19:09:09 patricia-laptop kernel: [    1.481812] PM: Checking hibernation image partition /dev/sda5
Jan 31 19:09:09 patricia-laptop kernel: [    1.720543] PM: Hibernation image partition 8:5 present
Jan 31 19:09:09 patricia-laptop kernel: [    1.720548] PM: Looking for hibernation image.
Jan 31 19:09:09 patricia-laptop kernel: [    1.735508] PM: Image not found (code -22)
Jan 31 19:09:09 patricia-laptop kernel: [    1.735513] PM: Hibernation image not present or could not be loaded.
Jan 31 19:09:09 patricia-laptop kernel: [    3.835013] PM: Marking nosave pages: [mem 0x0009f000-0x000fffff]
Jan 31 19:09:09 patricia-laptop kernel: [    3.835024] PM: Basic memory bitmaps created
Jan 31 19:09:09 patricia-laptop kernel: [    3.885866] PM: Basic memory bitmaps freed
Jan 31 19:11:25 patricia-laptop kernel: [  153.992304] PM: Marking nosave pages: [mem 0x0009f000-0x000fffff]
Jan 31 19:11:25 patricia-laptop kernel: [  153.992318] PM: Basic memory bitmaps created
Feb  1 10:27:30 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Feb  1 10:27:30 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Feb  1 10:27:30 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Feb  1 10:27:30 patricia-laptop kernel: [    0.100735] PM: Registering ACPI NVS region [mem 0x7f577000-0x7f5befff] (294912 bytes)
Feb  1 10:27:30 patricia-laptop kernel: [    1.485668] PM: Checking hibernation image partition /dev/sda5
Feb  1 10:27:30 patricia-laptop kernel: [    1.719440] PM: Hibernation image partition 8:5 present
Feb  1 10:27:30 patricia-laptop kernel: [    1.719445] PM: Looking for hibernation image.
Feb  1 10:27:30 patricia-laptop kernel: [    1.734387] PM: Image not found (code -22)
Feb  1 10:27:30 patricia-laptop kernel: [    1.734392] PM: Hibernation image not present or could not be loaded.
Feb  1 10:27:30 patricia-laptop kernel: [    3.851032] PM: Marking nosave pages: [mem 0x0009f000-0x000fffff]
Feb  1 10:27:30 patricia-laptop kernel: [    3.851042] PM: Basic memory bitmaps created
Feb  1 10:27:30 patricia-laptop kernel: [    3.895376] PM: Basic memory bitmaps freed
herman@patricia-laptop:~$ 

```

Done!

Hibernate did not work.

---

### Post by Toz on 2013-02-03
> eb  1 10:27:30 patricia-laptop kernel: [    1.485668] PM: Checking hibernation image partition **[COLOR="Red"]/dev/sda5[/COLOR]**
Feb  1 10:27:30 patricia-laptop kernel: [    1.719440] PM: Hibernation image partition 8:5 present
Feb  1 10:27:30 patricia-laptop kernel: [    1.719445] PM: Looking for hibernation image.
Feb  1 10:27:30 patricia-laptop kernel: [    1.734387] PM: Image not found (code -22)
Feb  1 10:27:30 patricia-laptop kernel: [    1.734392] PM: Hibernation image not present or could not be loaded.

Its looking for the hibernation image on **/dev/sda5** and not finding it. However, you're swap file is on **/dev/sda6** !

Is there anything in /usr/share/initramfs-tools/conf-hooks.d that is referencing /dev/sda5 ?

Have any of the files from your original post changed?
```
cat /proc/cmdline
swapon -s
cat /etc/fstab
blkid
```
...plus
```
free
```

And, if you run:
```
sudo update-initramfs -u
```
...are you still getting error messages? Maybe try getting some extra logging there:
```
sudo update-initramfs -uv > /var/log/update-initramfs.log
```
...then:
```
pastebinit /var/log/update-initramfs.log
```

And finally, the extra debugging didn't work. Can you try this again?
```
sudo bash
mv /var/log/pm-suspend.log /var/log/pm-suspend.log.BAK
export PM_DEBUG=true
pm-hibernate
```

---

### Post by Terraman on 2013-02-03
Thank you Toz,

```
Its looking for the hibernation image on /dev/sda5 and not finding it. However, you're swap file is on /dev/sda6 !
```

Yes, I have seen that too, but I can not figure out where is the problem.

```
Is there anything in /usr/share/initramfs-tools/conf-hooks.d that is referencing /dev/sda5 ?
```

No, there is nothing. Only this file: <cryptsetup>

```
# This will setup non-us keyboards in early userspace,
# necessary for punching in passphrases.
KEYMAP=y

# force busybox on initramfs
BUSYBOX=y

# and for systems using plymouth instead, use the new option
FRAMEBUFFER=y

```

```
Have any of the files from your original post changed?
```

I have increased the swap size, but is still on /dev/sda6 and I have consecuently changed the UUID.

```
herman@patricia-laptop:~$ cat /proc/cmdline
BOOT_IMAGE=/boot/vmlinuz-3.5.0-23-generic root=UUID=66050dc2-96e5-4054-90de-8b12e00235d5 ro resume=UUID=5b29589b-9169-4676-94f4-b4718e39c4fd quiet splash vt.handoff=7
herman@patricia-laptop:~$

herman@patricia-laptop:~$ swapon -s
Filename				Type		Size	Used	Priority
/dev/sda6                               partition	5219324	0	-1
herman@patricia-laptop:~$ 

herman@patricia-laptop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0

# / was on /dev/sda5 during installation
UUID=66050dc2-96e5-4054-90de-8b12e00235d5 /               ext4    errors=remount-ro 0       1

# swap was on /dev/sda6 during installation
UUID=5b29589b-9169-4676-94f4-b4718e39c4fd none            swap    sw              0       0

# swap on usb stick
# UUID=7bbbe625-03ba-4bff-b51a-3ba9164ce2b6 none swap sw,pri=5 0 0

#/.hibernate.img   swap  swap	noauto,defaults	0	0

/dev/sda2 /home ext3 nodev,nosuid,user_xattr 0 2

# Move /tmp to RAM
tmpfs /tmp tmpfs defaults,noexec,nosuid 0 0
herman@patricia-laptop:~$ 

herman@patricia-laptop:~$ sudo blkid
/dev/sda1: LABEL="Recovery" UUID="9A6839AF68398B51" TYPE="ntfs" 
/dev/sda2: UUID="a408efbc-dbf6-406c-b94b-bcc514058936" TYPE="ext3" 
/dev/sda3: UUID="E2BED980BED94E23" TYPE="ntfs" 
/dev/sda5: UUID="66050dc2-96e5-4054-90de-8b12e00235d5" TYPE="ext4" 
/dev/sda6: UUID="5b29589b-9169-4676-94f4-b4718e39c4fd" TYPE="swap" 
herman@patricia-laptop:~$ 
herman@patricia-laptop:~$ free
             total       usado       libre     compart.    búffers     almac.
Mem:       2054600    1386572     668028          0     126392     857328
-/+ buffers/cache:     402852    1651748
Intercambio:    5219324          0    5219324
herman@patricia-laptop:~$

```

When I run sudo update-initramfs -u, I am not getting error messages:

```
herman@patricia-laptop:~$ sudo update-initramfs -u
update-initramfs: Generating /boot/initrd.img-3.5.0-23-generic
W: TMPDIR is mounted noexec, will not cache run scripts.
herman@patricia-laptop:~$ 
```

I have tried to get some extra logging as you have suggested, but I have got permission denied.

```
herman@patricia-laptop:~$ sudo update-initramfs -uv > /var/log/update-initramfs.log
bash: /var/log/update-initramfs.log: Permiso denegado
herman@patricia-laptop:~$ 
```

...and with pastebinit /var/log/update-initramfs.log, consequently, this message has shown up: "Unable to read from: /var/log/update-initramfs.log"

```
herman@patricia-laptop:~$ pastebinit /var/log/update-initramfs.log
Incapaz a leer desde: /var/log/update-initramfs.log
herman@patricia-laptop:~$
```

I have tried this again:

```
sudo bash
mv /var/log/pm-suspend.log /var/log/pm-suspend.log.BAK
export PM_DEBUG=true
pm-hibernate
```

...with the same result.

The output of pastebinit /var/log/pm-suspend.log:[http://paste.ubuntu.com/1606454/]("http://paste.ubuntu.com/1606454/")

---

### Post by Toz on 2013-02-03
> The output of pastebinit /var/log/pm-suspend.log:[http://paste.ubuntu.com/1606454/](http://paste.ubuntu.com/1606454/)
Okay - that's the log file that I wanted to get. Can you post back the contents of /etc/pm/sleep.d/20swapctl?

I'd still like to see the update-initramfs log. Can you try this instead?
```
sudo update-initramfs -uv > $HOME/update-initramfs.log
```
...then:
```
pastebinit $HOME/update-initramfs.log
```

---

### Post by Terraman on 2013-02-04
Toz,

The contents of /etc/pm/sleep.d/20swapctl are:

```
#!/bin/bash
#/etc/pm/sleep.d/20swapctl
case "$1" in
  hibernate|suspend)
    swapon /.hibernate.img
    ;;
  thaw|resume)
    swapoff /.hibernate.img
    ;;
  *)
    ;;
esac

```

That could be a problem which I have not changed in many tries I have done before this thread.

```
sudo update-initramfs -uv > $HOME/update-initramfs.log
```

Done!

Here is the output [http://paste.ubuntu.com/1609675/]("http://paste.ubuntu.com/1609675/").

---

### Post by Toz on 2013-02-04
Please delete the **/etc/pm/sleep.d/20swapctl** file and try hibernate again.

---

### Post by Terraman on 2013-02-04
> **Toz said:**
> Please delete the **/etc/pm/sleep.d/20swapctl** file and try hibernate again.

Done! Unfortunately, hibernate is still not working.

The output of pastebinit /var/log/pm-suspend.log is: [http://paste.ubuntu.com/1610873/]("http://paste.ubuntu.com/1610873/").

---

### Post by Toz on 2013-02-04
Can you show:
```
cat /var/log/syslog | grep PM:
```

---

### Post by Terraman on 2013-02-05
```
herman@patricia-laptop:~$ cat /var/log/syslog | grep PM:
Feb  1 11:34:34 patricia-laptop kernel: [ 4093.638920] PM: Marking nosave pages: [mem 0x0009f000-0x000fffff]
Feb  1 11:34:34 patricia-laptop kernel: [ 4093.638934] PM: Basic memory bitmaps created
Feb  1 11:36:57 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Feb  1 11:36:57 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Feb  1 11:36:57 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Feb  1 11:36:57 patricia-laptop kernel: [    0.096603] PM: Registering ACPI NVS region [mem 0x7f577000-0x7f5befff] (294912 bytes)
Feb  1 11:36:57 patricia-laptop kernel: [    1.485965] PM: Checking hibernation image partition /dev/sda5
Feb  1 11:36:57 patricia-laptop kernel: [    1.732185] PM: Hibernation image partition 8:5 present
Feb  1 11:36:57 patricia-laptop kernel: [    1.732189] PM: Looking for hibernation image.
Feb  1 11:36:57 patricia-laptop kernel: [    1.747101] PM: Image not found (code -22)
Feb  1 11:36:57 patricia-laptop kernel: [    1.747106] PM: Hibernation image not present or could not be loaded.
Feb  1 11:36:57 patricia-laptop kernel: [    3.883253] PM: Marking nosave pages: [mem 0x0009f000-0x000fffff]
Feb  1 11:36:57 patricia-laptop kernel: [    3.883264] PM: Basic memory bitmaps created
Feb  1 11:36:57 patricia-laptop kernel: [    3.930680] PM: Basic memory bitmaps freed
Feb  1 12:07:54 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Feb  1 12:07:54 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Feb  1 12:07:54 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Feb  1 12:07:54 patricia-laptop kernel: [    0.096601] PM: Registering ACPI NVS region [mem 0x7f577000-0x7f5befff] (294912 bytes)
Feb  1 12:07:54 patricia-laptop kernel: [    1.485649] PM: Checking hibernation image partition /dev/sda5
Feb  1 12:07:54 patricia-laptop kernel: [    1.716633] PM: Hibernation image partition 8:5 present
Feb  1 12:07:54 patricia-laptop kernel: [    1.716638] PM: Looking for hibernation image.
Feb  1 12:07:54 patricia-laptop kernel: [    1.731620] PM: Image not found (code -22)
Feb  1 12:07:54 patricia-laptop kernel: [    1.731624] PM: Hibernation image not present or could not be loaded.
Feb  1 12:07:54 patricia-laptop kernel: [    3.819473] PM: Marking nosave pages: [mem 0x0009f000-0x000fffff]
Feb  1 12:07:54 patricia-laptop kernel: [    3.819485] PM: Basic memory bitmaps created
Feb  1 12:07:54 patricia-laptop kernel: [    3.870607] PM: Basic memory bitmaps freed
Feb  1 12:17:13 patricia-laptop kernel: [  578.824332] PM: Hibernation mode set to 'platform'
Feb  1 12:17:25 patricia-laptop kernel: [  590.405735] PM: Marking nosave pages: [mem 0x0009f000-0x000fffff]
Feb  1 12:17:25 patricia-laptop kernel: [  590.405746] PM: Basic memory bitmaps created
Feb  1 12:19:12 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Feb  1 12:19:12 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Feb  1 12:19:12 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Feb  1 12:19:12 patricia-laptop kernel: [    0.096589] PM: Registering ACPI NVS region [mem 0x7f577000-0x7f5befff] (294912 bytes)
Feb  1 12:19:12 patricia-laptop kernel: [    1.489865] PM: Checking hibernation image partition /dev/sda5
Feb  1 12:19:12 patricia-laptop kernel: [    1.724454] PM: Hibernation image partition 8:5 present
Feb  1 12:19:12 patricia-laptop kernel: [    1.724459] PM: Looking for hibernation image.
Feb  1 12:19:12 patricia-laptop kernel: [    1.739398] PM: Image not found (code -22)
Feb  1 12:19:12 patricia-laptop kernel: [    1.739402] PM: Hibernation image not present or could not be loaded.
Feb  1 12:19:12 patricia-laptop kernel: [    3.839177] PM: Marking nosave pages: [mem 0x0009f000-0x000fffff]
Feb  1 12:19:12 patricia-laptop kernel: [    3.839187] PM: Basic memory bitmaps created
Feb  1 12:19:12 patricia-laptop kernel: [    3.889559] PM: Basic memory bitmaps freed
Feb  1 12:29:04 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Feb  1 12:29:04 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Feb  1 12:29:04 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Feb  1 12:29:04 patricia-laptop kernel: [    0.096607] PM: Registering ACPI NVS region [mem 0x7f577000-0x7f5befff] (294912 bytes)
Feb  1 12:29:04 patricia-laptop kernel: [    1.491220] PM: Checking hibernation image partition /dev/sda5
Feb  1 12:29:04 patricia-laptop kernel: [    1.731187] PM: Hibernation image partition 8:5 present
Feb  1 12:29:04 patricia-laptop kernel: [    1.731192] PM: Looking for hibernation image.
Feb  1 12:29:04 patricia-laptop kernel: [    1.746170] PM: Image not found (code -22)
Feb  1 12:29:04 patricia-laptop kernel: [    1.746175] PM: Hibernation image not present or could not be loaded.
Feb  1 12:29:04 patricia-laptop kernel: [    3.847429] PM: Marking nosave pages: [mem 0x0009f000-0x000fffff]
Feb  1 12:29:04 patricia-laptop kernel: [    3.847440] PM: Basic memory bitmaps created
Feb  1 12:29:04 patricia-laptop kernel: [    3.872753] PM: Basic memory bitmaps freed
Feb  1 12:32:24 patricia-laptop kernel: [  214.508215] PM: Marking nosave pages: [mem 0x0009f000-0x000fffff]
Feb  1 12:32:24 patricia-laptop kernel: [  214.508229] PM: Basic memory bitmaps created
Feb  1 12:34:18 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Feb  1 12:34:18 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Feb  1 12:34:18 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Feb  1 12:34:18 patricia-laptop kernel: [    0.100582] PM: Registering ACPI NVS region [mem 0x7f577000-0x7f5befff] (294912 bytes)
Feb  1 12:34:18 patricia-laptop kernel: [    1.497692] PM: Checking hibernation image partition /dev/sda5
Feb  1 12:34:18 patricia-laptop kernel: [    1.725882] PM: Hibernation image partition 8:5 present
Feb  1 12:34:18 patricia-laptop kernel: [    1.725887] PM: Looking for hibernation image.
Feb  1 12:34:18 patricia-laptop kernel: [    1.740866] PM: Image not found (code -22)
Feb  1 12:34:18 patricia-laptop kernel: [    1.740871] PM: Hibernation image not present or could not be loaded.
Feb  1 12:34:18 patricia-laptop kernel: [    3.752334] PM: Marking nosave pages: [mem 0x0009f000-0x000fffff]
Feb  1 12:34:18 patricia-laptop kernel: [    3.752344] PM: Basic memory bitmaps created
Feb  1 12:34:18 patricia-laptop kernel: [    3.783685] PM: Basic memory bitmaps freed
Feb  1 13:57:14 patricia-laptop kernel: [ 5042.399023] PM: Marking nosave pages: [mem 0x0009f000-0x000fffff]
Feb  1 13:57:14 patricia-laptop kernel: [ 5042.399036] PM: Basic memory bitmaps created
Feb  1 13:59:42 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Feb  1 13:59:42 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Feb  1 13:59:42 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Feb  1 13:59:42 patricia-laptop kernel: [    0.100599] PM: Registering ACPI NVS region [mem 0x7f577000-0x7f5befff] (294912 bytes)
Feb  1 13:59:42 patricia-laptop kernel: [    1.327545] PM: Checking hibernation image partition /dev/sda5
Feb  1 13:59:42 patricia-laptop kernel: [    1.571669] PM: Hibernation image partition 8:5 present
Feb  1 13:59:42 patricia-laptop kernel: [    1.571675] PM: Looking for hibernation image.
Feb  1 13:59:42 patricia-laptop kernel: [    1.586689] PM: Image not found (code -22)
Feb  1 13:59:42 patricia-laptop kernel: [    1.586694] PM: Hibernation image not present or could not be loaded.
Feb  1 13:59:42 patricia-laptop kernel: [    3.691609] PM: Marking nosave pages: [mem 0x0009f000-0x000fffff]
Feb  1 13:59:42 patricia-laptop kernel: [    3.691620] PM: Basic memory bitmaps created
Feb  1 13:59:42 patricia-laptop kernel: [    3.723157] PM: Basic memory bitmaps freed
Feb  1 14:13:58 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Feb  1 14:13:58 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Feb  1 14:13:58 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Feb  1 14:13:58 patricia-laptop kernel: [    0.100587] PM: Registering ACPI NVS region [mem 0x7f577000-0x7f5befff] (294912 bytes)
Feb  1 14:13:58 patricia-laptop kernel: [    1.319972] PM: Checking hibernation image partition /dev/sda6
Feb  1 14:13:58 patricia-laptop kernel: [    1.557777] PM: Hibernation image partition 8:6 present
Feb  1 14:13:58 patricia-laptop kernel: [    1.557783] PM: Looking for hibernation image.
Feb  1 14:13:58 patricia-laptop kernel: [    1.558102] PM: Image not found (code -22)
Feb  1 14:13:58 patricia-laptop kernel: [    1.558107] PM: Hibernation image not present or could not be loaded.
Feb  1 14:38:42 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Feb  1 14:38:42 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Feb  1 14:38:42 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Feb  1 14:38:42 patricia-laptop kernel: [    0.108594] PM: Registering ACPI NVS region [mem 0x7f577000-0x7f5befff] (294912 bytes)
Feb  1 14:38:42 patricia-laptop kernel: [    1.331678] PM: Checking hibernation image partition /dev/sda6
Feb  1 14:38:42 patricia-laptop kernel: [    1.571237] PM: Hibernation image partition 8:6 present
Feb  1 14:38:42 patricia-laptop kernel: [    1.571243] PM: Looking for hibernation image.
Feb  1 14:38:42 patricia-laptop kernel: [    1.571526] PM: Image not found (code -22)
Feb  1 14:38:42 patricia-laptop kernel: [    1.571531] PM: Hibernation image not present or could not be loaded.
Feb  1 15:52:50 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Feb  1 15:52:50 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Feb  1 15:52:50 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Feb  1 15:52:50 patricia-laptop kernel: [    0.096601] PM: Registering ACPI NVS region [mem 0x7f577000-0x7f5befff] (294912 bytes)
Feb  1 15:52:50 patricia-laptop kernel: [    1.470234] PM: Checking hibernation image partition /dev/sda6
Feb  1 15:52:50 patricia-laptop kernel: [    1.712947] PM: Hibernation image partition 8:6 present
Feb  1 15:52:50 patricia-laptop kernel: [    1.712952] PM: Looking for hibernation image.
Feb  1 15:52:50 patricia-laptop kernel: [    1.713266] PM: Image not found (code -22)
Feb  1 15:52:50 patricia-laptop kernel: [    1.713270] PM: Hibernation image not present or could not be loaded.
Feb  1 17:06:21 patricia-laptop kernel: [ 4431.470879] PM: Marking nosave pages: [mem 0x0009f000-0x000fffff]
Feb  1 17:06:21 patricia-laptop kernel: [ 4431.470893] PM: Basic memory bitmaps created
Feb  1 17:08:42 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Feb  1 17:08:42 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Feb  1 17:08:42 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Feb  1 17:08:42 patricia-laptop kernel: [    0.100583] PM: Registering ACPI NVS region [mem 0x7f577000-0x7f5befff] (294912 bytes)
Feb  1 17:08:42 patricia-laptop kernel: [    1.483918] PM: Checking hibernation image partition /dev/sda6
Feb  1 17:08:42 patricia-laptop kernel: [    1.731403] PM: Hibernation image partition 8:6 present
Feb  1 17:08:42 patricia-laptop kernel: [    1.731408] PM: Looking for hibernation image.
Feb  1 17:08:42 patricia-laptop kernel: [    1.731715] PM: Image not found (code -22)
Feb  1 17:08:42 patricia-laptop kernel: [    1.731720] PM: Hibernation image not present or could not be loaded.
Feb  1 17:08:42 patricia-laptop kernel: [    3.880475] PM: Marking nosave pages: [mem 0x0009f000-0x000fffff]
Feb  1 17:08:42 patricia-laptop kernel: [    3.880485] PM: Basic memory bitmaps created
Feb  1 17:08:42 patricia-laptop kernel: [    3.910789] PM: Basic memory bitmaps freed
Feb  1 17:42:46 patricia-laptop kernel: [ 2119.892045] PM: Marking nosave pages: [mem 0x0009f000-0x000fffff]
Feb  1 17:42:46 patricia-laptop kernel: [ 2119.892058] PM: Basic memory bitmaps created
Feb  1 17:44:56 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Feb  1 17:44:56 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Feb  1 17:44:56 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Feb  1 17:44:56 patricia-laptop kernel: [    0.100589] PM: Registering ACPI NVS region [mem 0x7f577000-0x7f5befff] (294912 bytes)
Feb  1 17:44:56 patricia-laptop kernel: [    1.489708] PM: Checking hibernation image partition UUID=84c2098a-83b5-4a83-a053-8c9277da2941
Feb  1 17:44:56 patricia-laptop kernel: [    1.732758] PM: Hibernation image not present or could not be loaded.
Feb  1 17:44:56 patricia-laptop kernel: [    3.891652] PM: Marking nosave pages: [mem 0x0009f000-0x000fffff]
Feb  1 17:44:56 patricia-laptop kernel: [    3.891662] PM: Basic memory bitmaps created
Feb  1 17:44:56 patricia-laptop kernel: [    3.923250] PM: Basic memory bitmaps freed
Feb  1 18:26:52 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Feb  1 18:26:52 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Feb  1 18:26:52 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Feb  1 18:26:52 patricia-laptop kernel: [    0.096595] PM: Registering ACPI NVS region [mem 0x7f577000-0x7f5befff] (294912 bytes)
Feb  1 18:26:52 patricia-laptop kernel: [    1.474272] PM: Checking hibernation image partition UUID=84c2098a-83b5-4a83-a053-8c9277da2941
Feb  1 18:26:52 patricia-laptop kernel: [    1.710721] PM: Hibernation image not present or could not be loaded.
Feb  1 18:26:52 patricia-laptop kernel: [    3.768317] PM: Marking nosave pages: [mem 0x0009f000-0x000fffff]
Feb  1 18:26:52 patricia-laptop kernel: [    3.768328] PM: Basic memory bitmaps created
Feb  1 18:26:52 patricia-laptop kernel: [    3.798630] PM: Basic memory bitmaps freed
Feb  1 18:57:36 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Feb  1 18:57:36 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Feb  1 18:57:36 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Feb  1 18:57:36 patricia-laptop kernel: [    0.104589] PM: Registering ACPI NVS region [mem 0x7f577000-0x7f5befff] (294912 bytes)
Feb  1 18:57:36 patricia-laptop kernel: [    1.327798] PM: Checking hibernation image partition UUID=84c2098a-83b5-4a83-a053-8c9277da2941
Feb  1 18:57:36 patricia-laptop kernel: [    1.567235] PM: Hibernation image not present or could not be loaded.
Feb  1 18:57:36 patricia-laptop kernel: [    3.583308] PM: Marking nosave pages: [mem 0x0009f000-0x000fffff]
Feb  1 18:57:36 patricia-laptop kernel: [    3.583320] PM: Basic memory bitmaps created
Feb  1 18:57:36 patricia-laptop kernel: [    3.614729] PM: Basic memory bitmaps freed
Feb  2 13:33:30 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Feb  2 13:33:30 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Feb  2 13:33:30 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Feb  2 13:33:30 patricia-laptop kernel: [    0.100598] PM: Registering ACPI NVS region [mem 0x7f577000-0x7f5befff] (294912 bytes)
Feb  2 13:33:30 patricia-laptop kernel: [    1.323662] PM: Checking hibernation image partition UUID=84c2098a-83b5-4a83-a053-8c9277da2941
Feb  2 13:33:30 patricia-laptop kernel: [    1.545725] PM: Hibernation image not present or could not be loaded.
Feb  2 13:33:30 patricia-laptop kernel: [    8.656219] PM: Marking nosave pages: [mem 0x0009f000-0x000fffff]
Feb  2 13:33:30 patricia-laptop kernel: [    8.656232] PM: Basic memory bitmaps created
Feb  2 13:33:30 patricia-laptop kernel: [    8.967729] PM: Basic memory bitmaps freed
Feb  2 13:44:47 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Feb  2 13:44:47 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Feb  2 13:44:47 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Feb  2 13:44:47 patricia-laptop kernel: [    0.100591] PM: Registering ACPI NVS region [mem 0x7f577000-0x7f5befff] (294912 bytes)
Feb  2 13:44:47 patricia-laptop kernel: [    1.489810] PM: Checking hibernation image partition UUID=84c2098a-83b5-4a83-a053-8c9277da2941
Feb  2 13:44:47 patricia-laptop kernel: [    1.721220] PM: Hibernation image not present or could not be loaded.
Feb  2 13:44:47 patricia-laptop kernel: [    8.835130] PM: Marking nosave pages: [mem 0x0009f000-0x000fffff]
Feb  2 13:44:47 patricia-laptop kernel: [    8.835142] PM: Basic memory bitmaps created
Feb  2 13:44:47 patricia-laptop kernel: [    9.164258] PM: Basic memory bitmaps freed
Feb  2 14:01:21 patricia-laptop kernel: [ 1018.159796] PM: Marking nosave pages: [mem 0x0009f000-0x000fffff]
Feb  2 14:01:21 patricia-laptop kernel: [ 1018.159817] PM: Basic memory bitmaps created
Feb  2 14:03:13 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Feb  2 14:03:13 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Feb  2 14:03:13 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Feb  2 14:03:13 patricia-laptop kernel: [    0.096585] PM: Registering ACPI NVS region [mem 0x7f577000-0x7f5befff] (294912 bytes)
Feb  2 14:03:13 patricia-laptop kernel: [    1.491516] PM: Checking hibernation image partition UUID=5b29589b-9169-4676-94f4-b4718e39c4fd
Feb  2 14:03:13 patricia-laptop kernel: [    1.703421] PM: Hibernation image not present or could not be loaded.
Feb  2 14:03:13 patricia-laptop kernel: [    3.736477] PM: Marking nosave pages: [mem 0x0009f000-0x000fffff]
Feb  2 14:03:13 patricia-laptop kernel: [    3.736487] PM: Basic memory bitmaps created
Feb  2 14:03:13 patricia-laptop kernel: [    3.761810] PM: Basic memory bitmaps freed
Feb  2 14:09:02 patricia-laptop kernel: [  414.282877] PM: Marking nosave pages: [mem 0x0009f000-0x000fffff]
Feb  2 14:09:02 patricia-laptop kernel: [  414.282898] PM: Basic memory bitmaps created
Feb  2 14:10:47 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Feb  2 14:10:47 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Feb  2 14:10:47 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Feb  2 14:10:47 patricia-laptop kernel: [    0.096588] PM: Registering ACPI NVS region [mem 0x7f577000-0x7f5befff] (294912 bytes)
Feb  2 14:10:47 patricia-laptop kernel: [    1.475737] PM: Checking hibernation image partition UUID=5b29589b-9169-4676-94f4-b4718e39c4fd
Feb  2 14:10:47 patricia-laptop kernel: [    1.704607] PM: Hibernation image not present or could not be loaded.
Feb  2 14:10:47 patricia-laptop kernel: [    3.799809] PM: Marking nosave pages: [mem 0x0009f000-0x000fffff]
Feb  2 14:10:47 patricia-laptop kernel: [    3.799820] PM: Basic memory bitmaps created
Feb  2 14:10:47 patricia-laptop kernel: [    3.825521] PM: Basic memory bitmaps freed
Feb  3 00:04:16 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Feb  3 00:04:16 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Feb  3 00:04:16 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Feb  3 00:04:16 patricia-laptop kernel: [    0.100599] PM: Registering ACPI NVS region [mem 0x7f577000-0x7f5befff] (294912 bytes)
Feb  3 00:04:16 patricia-laptop kernel: [    1.481662] PM: Checking hibernation image partition UUID=5b29589b-9169-4676-94f4-b4718e39c4fd
Feb  3 00:04:16 patricia-laptop kernel: [    1.713021] PM: Hibernation image not present or could not be loaded.
Feb  3 00:04:16 patricia-laptop kernel: [    3.827408] PM: Marking nosave pages: [mem 0x0009f000-0x000fffff]
Feb  3 00:04:16 patricia-laptop kernel: [    3.827419] PM: Basic memory bitmaps created
Feb  3 00:04:16 patricia-laptop kernel: [    3.853303] PM: Basic memory bitmaps freed
Feb  3 12:09:29 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Feb  3 12:09:29 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Feb  3 12:09:29 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Feb  3 12:09:29 patricia-laptop kernel: [    0.096600] PM: Registering ACPI NVS region [mem 0x7f577000-0x7f5befff] (294912 bytes)
Feb  3 12:09:29 patricia-laptop kernel: [    1.485830] PM: Checking hibernation image partition UUID=5b29589b-9169-4676-94f4-b4718e39c4fd
Feb  3 12:09:29 patricia-laptop kernel: [    1.721319] PM: Hibernation image not present or could not be loaded.
Feb  3 12:09:29 patricia-laptop kernel: [    3.791398] PM: Marking nosave pages: [mem 0x0009f000-0x000fffff]
Feb  3 12:09:29 patricia-laptop kernel: [    3.791410] PM: Basic memory bitmaps created
Feb  3 12:09:29 patricia-laptop kernel: [    3.822573] PM: Basic memory bitmaps freed
Feb  3 12:31:35 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Feb  3 12:31:35 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Feb  3 12:31:35 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Feb  3 12:31:35 patricia-laptop kernel: [    0.096600] PM: Registering ACPI NVS region [mem 0x7f577000-0x7f5befff] (294912 bytes)
Feb  3 12:31:35 patricia-laptop kernel: [    1.491583] PM: Checking hibernation image partition UUID=5b29589b-9169-4676-94f4-b4718e39c4fd
Feb  3 12:31:35 patricia-laptop kernel: [    1.716389] PM: Hibernation image not present or could not be loaded.
Feb  3 12:48:02 patricia-laptop kernel: [ 1006.156422] PM: Marking nosave pages: [mem 0x0009f000-0x000fffff]
Feb  3 12:48:02 patricia-laptop kernel: [ 1006.156434] PM: Basic memory bitmaps created
Feb  3 12:50:09 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Feb  3 12:50:09 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Feb  3 12:50:09 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Feb  3 12:50:09 patricia-laptop kernel: [    0.100591] PM: Registering ACPI NVS region [mem 0x7f577000-0x7f5befff] (294912 bytes)
Feb  3 12:50:09 patricia-laptop kernel: [    1.486797] PM: Checking hibernation image partition UUID=5b29589b-9169-4676-94f4-b4718e39c4fd
Feb  3 12:50:09 patricia-laptop kernel: [    1.710673] PM: Hibernation image not present or could not be loaded.
Feb  3 20:18:55 patricia-laptop kernel: [26992.240777] PM: Marking nosave pages: [mem 0x0009f000-0x000fffff]
Feb  3 20:18:55 patricia-laptop kernel: [26992.240789] PM: Basic memory bitmaps created
Feb  3 20:20:54 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Feb  3 20:20:54 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Feb  3 20:20:54 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Feb  3 20:20:54 patricia-laptop kernel: [    0.096596] PM: Registering ACPI NVS region [mem 0x7f577000-0x7f5befff] (294912 bytes)
Feb  3 20:20:54 patricia-laptop kernel: [    1.493792] PM: Checking hibernation image partition UUID=5b29589b-9169-4676-94f4-b4718e39c4fd
Feb  3 20:20:54 patricia-laptop kernel: [    1.717777] PM: Hibernation image not present or could not be loaded.
Feb  4 12:29:29 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Feb  4 12:29:29 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Feb  4 12:29:29 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Feb  4 12:29:29 patricia-laptop kernel: [    0.100602] PM: Registering ACPI NVS region [mem 0x7f577000-0x7f5befff] (294912 bytes)
Feb  4 12:29:29 patricia-laptop kernel: [    1.474779] PM: Checking hibernation image partition UUID=5b29589b-9169-4676-94f4-b4718e39c4fd
Feb  4 12:29:29 patricia-laptop kernel: [    1.710669] PM: Hibernation image not present or could not be loaded.
Feb  4 13:55:22 patricia-laptop kernel: [ 5170.616844] PM: Marking nosave pages: [mem 0x0009f000-0x000fffff]
Feb  4 13:55:22 patricia-laptop kernel: [ 5170.616856] PM: Basic memory bitmaps created
Feb  4 13:57:07 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Feb  4 13:57:07 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Feb  4 13:57:07 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Feb  4 13:57:07 patricia-laptop kernel: [    0.096594] PM: Registering ACPI NVS region [mem 0x7f577000-0x7f5befff] (294912 bytes)
Feb  4 13:57:07 patricia-laptop kernel: [    1.483246] PM: Checking hibernation image partition UUID=5b29589b-9169-4676-94f4-b4718e39c4fd
Feb  4 13:57:07 patricia-laptop kernel: [    1.708017] PM: Hibernation image not present or could not be loaded.
Feb  4 21:26:45 patricia-laptop kernel: [27048.348783] PM: Marking nosave pages: [mem 0x0009f000-0x000fffff]
Feb  4 21:26:45 patricia-laptop kernel: [27048.348795] PM: Basic memory bitmaps created
Feb  4 21:28:28 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Feb  4 21:28:28 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Feb  4 21:28:28 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Feb  4 21:28:28 patricia-laptop kernel: [    0.096594] PM: Registering ACPI NVS region [mem 0x7f577000-0x7f5befff] (294912 bytes)
Feb  4 21:28:28 patricia-laptop kernel: [    1.469827] PM: Checking hibernation image partition UUID=5b29589b-9169-4676-94f4-b4718e39c4fd
Feb  4 21:28:28 patricia-laptop kernel: [    1.698494] PM: Hibernation image not present or could not be loaded.
Feb  4 21:33:13 patricia-laptop kernel: [  352.494532] PM: Marking nosave pages: [mem 0x0009f000-0x000fffff]
Feb  4 21:33:13 patricia-laptop kernel: [  352.494545] PM: Basic memory bitmaps created
Feb  4 21:34:58 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Feb  4 21:34:58 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Feb  4 21:34:58 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Feb  4 21:34:58 patricia-laptop kernel: [    0.100582] PM: Registering ACPI NVS region [mem 0x7f577000-0x7f5befff] (294912 bytes)
Feb  4 21:34:58 patricia-laptop kernel: [    1.475715] PM: Checking hibernation image partition UUID=5b29589b-9169-4676-94f4-b4718e39c4fd
Feb  4 21:34:58 patricia-laptop kernel: [    1.708554] PM: Hibernation image not present or could not be loaded.
Feb  5 09:32:01 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Feb  5 09:32:01 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Feb  5 09:32:01 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Feb  5 09:32:01 patricia-laptop kernel: [    0.104587] PM: Registering ACPI NVS region [mem 0x7f577000-0x7f5befff] (294912 bytes)
Feb  5 09:32:01 patricia-laptop kernel: [    1.489778] PM: Checking hibernation image partition UUID=5b29589b-9169-4676-94f4-b4718e39c4fd
Feb  5 09:32:01 patricia-laptop kernel: [    1.709512] PM: Hibernation image not present or could not be loaded.
herman@patricia-laptop:~$ 

```

---

### Post by Toz on 2013-02-05
> Feb  5 09:32:01 patricia-laptop kernel: [    1.489778] PM: Checking hibernation image partition UUID=5b29589b-9169-4676-94f4-b4718e39c4fd
Feb  5 09:32:01 patricia-laptop kernel: [    1.709512] PM: Hibernation image not present or could not be loaded.

Hmmmm.

Lets try something a little different. First, remove the **resume=** parameter from your command line.

Then, create (or edit if it exists) the file **/etc/initramfs-tools/conf.d/resume** to include the line:
```
RESUME=/dev/disk/by-uuid/5b29589b-9169-4676-94f4-b4718e39c4fd
```
...then update initramfs:
```
sudo update-initramfs -u
```

Reboot.

Make sure that a swap file is enabled:
```
swapon -s
```

Make sure that you have no resume= parameter:
```
cat /proc/cmdline
```

Then try hibernate.

If no luck, post back again:
```
cat /var/log/syslog | grep PM:
```

---

### Post by Terraman on 2013-02-05
```
Then, create (or edit if it exists) the file /etc/initramfs-tools/conf.d/resume to include the line:
```

Done!

```
herman@patricia-laptop:~$ cat /proc/cmdline
BOOT_IMAGE=/boot/vmlinuz-3.5.0-23-generic root=UUID=66050dc2-96e5-4054-90de-8b12e00235d5 ro quiet splash vt.handoff=7
herman@patricia-laptop:~$
```

And... no luck! Thus:

```
herman@patricia-laptop:~$ cat /var/log/syslog | grep PM:
Feb  1 11:34:34 patricia-laptop kernel: [ 4093.638920] PM: Marking nosave pages: [mem 0x0009f000-0x000fffff]
Feb  1 11:34:34 patricia-laptop kernel: [ 4093.638934] PM: Basic memory bitmaps created
Feb  1 11:36:57 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Feb  1 11:36:57 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Feb  1 11:36:57 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Feb  1 11:36:57 patricia-laptop kernel: [    0.096603] PM: Registering ACPI NVS region [mem 0x7f577000-0x7f5befff] (294912 bytes)
Feb  1 11:36:57 patricia-laptop kernel: [    1.485965] PM: Checking hibernation image partition /dev/sda5
Feb  1 11:36:57 patricia-laptop kernel: [    1.732185] PM: Hibernation image partition 8:5 present
Feb  1 11:36:57 patricia-laptop kernel: [    1.732189] PM: Looking for hibernation image.
Feb  1 11:36:57 patricia-laptop kernel: [    1.747101] PM: Image not found (code -22)
Feb  1 11:36:57 patricia-laptop kernel: [    1.747106] PM: Hibernation image not present or could not be loaded.
Feb  1 11:36:57 patricia-laptop kernel: [    3.883253] PM: Marking nosave pages: [mem 0x0009f000-0x000fffff]
Feb  1 11:36:57 patricia-laptop kernel: [    3.883264] PM: Basic memory bitmaps created
Feb  1 11:36:57 patricia-laptop kernel: [    3.930680] PM: Basic memory bitmaps freed
Feb  1 12:07:54 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Feb  1 12:07:54 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Feb  1 12:07:54 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Feb  1 12:07:54 patricia-laptop kernel: [    0.096601] PM: Registering ACPI NVS region [mem 0x7f577000-0x7f5befff] (294912 bytes)
Feb  1 12:07:54 patricia-laptop kernel: [    1.485649] PM: Checking hibernation image partition /dev/sda5
Feb  1 12:07:54 patricia-laptop kernel: [    1.716633] PM: Hibernation image partition 8:5 present
Feb  1 12:07:54 patricia-laptop kernel: [    1.716638] PM: Looking for hibernation image.
Feb  1 12:07:54 patricia-laptop kernel: [    1.731620] PM: Image not found (code -22)
Feb  1 12:07:54 patricia-laptop kernel: [    1.731624] PM: Hibernation image not present or could not be loaded.
Feb  1 12:07:54 patricia-laptop kernel: [    3.819473] PM: Marking nosave pages: [mem 0x0009f000-0x000fffff]
Feb  1 12:07:54 patricia-laptop kernel: [    3.819485] PM: Basic memory bitmaps created
Feb  1 12:07:54 patricia-laptop kernel: [    3.870607] PM: Basic memory bitmaps freed
Feb  1 12:17:13 patricia-laptop kernel: [  578.824332] PM: Hibernation mode set to 'platform'
Feb  1 12:17:25 patricia-laptop kernel: [  590.405735] PM: Marking nosave pages: [mem 0x0009f000-0x000fffff]
Feb  1 12:17:25 patricia-laptop kernel: [  590.405746] PM: Basic memory bitmaps created
Feb  1 12:19:12 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Feb  1 12:19:12 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Feb  1 12:19:12 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Feb  1 12:19:12 patricia-laptop kernel: [    0.096589] PM: Registering ACPI NVS region [mem 0x7f577000-0x7f5befff] (294912 bytes)
Feb  1 12:19:12 patricia-laptop kernel: [    1.489865] PM: Checking hibernation image partition /dev/sda5
Feb  1 12:19:12 patricia-laptop kernel: [    1.724454] PM: Hibernation image partition 8:5 present
Feb  1 12:19:12 patricia-laptop kernel: [    1.724459] PM: Looking for hibernation image.
Feb  1 12:19:12 patricia-laptop kernel: [    1.739398] PM: Image not found (code -22)
Feb  1 12:19:12 patricia-laptop kernel: [    1.739402] PM: Hibernation image not present or could not be loaded.
Feb  1 12:19:12 patricia-laptop kernel: [    3.839177] PM: Marking nosave pages: [mem 0x0009f000-0x000fffff]
Feb  1 12:19:12 patricia-laptop kernel: [    3.839187] PM: Basic memory bitmaps created
Feb  1 12:19:12 patricia-laptop kernel: [    3.889559] PM: Basic memory bitmaps freed
Feb  1 12:29:04 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Feb  1 12:29:04 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Feb  1 12:29:04 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Feb  1 12:29:04 patricia-laptop kernel: [    0.096607] PM: Registering ACPI NVS region [mem 0x7f577000-0x7f5befff] (294912 bytes)
Feb  1 12:29:04 patricia-laptop kernel: [    1.491220] PM: Checking hibernation image partition /dev/sda5
Feb  1 12:29:04 patricia-laptop kernel: [    1.731187] PM: Hibernation image partition 8:5 present
Feb  1 12:29:04 patricia-laptop kernel: [    1.731192] PM: Looking for hibernation image.
Feb  1 12:29:04 patricia-laptop kernel: [    1.746170] PM: Image not found (code -22)
Feb  1 12:29:04 patricia-laptop kernel: [    1.746175] PM: Hibernation image not present or could not be loaded.
Feb  1 12:29:04 patricia-laptop kernel: [    3.847429] PM: Marking nosave pages: [mem 0x0009f000-0x000fffff]
Feb  1 12:29:04 patricia-laptop kernel: [    3.847440] PM: Basic memory bitmaps created
Feb  1 12:29:04 patricia-laptop kernel: [    3.872753] PM: Basic memory bitmaps freed
Feb  1 12:32:24 patricia-laptop kernel: [  214.508215] PM: Marking nosave pages: [mem 0x0009f000-0x000fffff]
Feb  1 12:32:24 patricia-laptop kernel: [  214.508229] PM: Basic memory bitmaps created
Feb  1 12:34:18 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Feb  1 12:34:18 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Feb  1 12:34:18 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Feb  1 12:34:18 patricia-laptop kernel: [    0.100582] PM: Registering ACPI NVS region [mem 0x7f577000-0x7f5befff] (294912 bytes)
Feb  1 12:34:18 patricia-laptop kernel: [    1.497692] PM: Checking hibernation image partition /dev/sda5
Feb  1 12:34:18 patricia-laptop kernel: [    1.725882] PM: Hibernation image partition 8:5 present
Feb  1 12:34:18 patricia-laptop kernel: [    1.725887] PM: Looking for hibernation image.
Feb  1 12:34:18 patricia-laptop kernel: [    1.740866] PM: Image not found (code -22)
Feb  1 12:34:18 patricia-laptop kernel: [    1.740871] PM: Hibernation image not present or could not be loaded.
Feb  1 12:34:18 patricia-laptop kernel: [    3.752334] PM: Marking nosave pages: [mem 0x0009f000-0x000fffff]
Feb  1 12:34:18 patricia-laptop kernel: [    3.752344] PM: Basic memory bitmaps created
Feb  1 12:34:18 patricia-laptop kernel: [    3.783685] PM: Basic memory bitmaps freed
Feb  1 13:57:14 patricia-laptop kernel: [ 5042.399023] PM: Marking nosave pages: [mem 0x0009f000-0x000fffff]
Feb  1 13:57:14 patricia-laptop kernel: [ 5042.399036] PM: Basic memory bitmaps created
Feb  1 13:59:42 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Feb  1 13:59:42 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Feb  1 13:59:42 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Feb  1 13:59:42 patricia-laptop kernel: [    0.100599] PM: Registering ACPI NVS region [mem 0x7f577000-0x7f5befff] (294912 bytes)
Feb  1 13:59:42 patricia-laptop kernel: [    1.327545] PM: Checking hibernation image partition /dev/sda5
Feb  1 13:59:42 patricia-laptop kernel: [    1.571669] PM: Hibernation image partition 8:5 present
Feb  1 13:59:42 patricia-laptop kernel: [    1.571675] PM: Looking for hibernation image.
Feb  1 13:59:42 patricia-laptop kernel: [    1.586689] PM: Image not found (code -22)
Feb  1 13:59:42 patricia-laptop kernel: [    1.586694] PM: Hibernation image not present or could not be loaded.
Feb  1 13:59:42 patricia-laptop kernel: [    3.691609] PM: Marking nosave pages: [mem 0x0009f000-0x000fffff]
Feb  1 13:59:42 patricia-laptop kernel: [    3.691620] PM: Basic memory bitmaps created
Feb  1 13:59:42 patricia-laptop kernel: [    3.723157] PM: Basic memory bitmaps freed
Feb  1 14:13:58 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Feb  1 14:13:58 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Feb  1 14:13:58 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Feb  1 14:13:58 patricia-laptop kernel: [    0.100587] PM: Registering ACPI NVS region [mem 0x7f577000-0x7f5befff] (294912 bytes)
Feb  1 14:13:58 patricia-laptop kernel: [    1.319972] PM: Checking hibernation image partition /dev/sda6
Feb  1 14:13:58 patricia-laptop kernel: [    1.557777] PM: Hibernation image partition 8:6 present
Feb  1 14:13:58 patricia-laptop kernel: [    1.557783] PM: Looking for hibernation image.
Feb  1 14:13:58 patricia-laptop kernel: [    1.558102] PM: Image not found (code -22)
Feb  1 14:13:58 patricia-laptop kernel: [    1.558107] PM: Hibernation image not present or could not be loaded.
Feb  1 14:38:42 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Feb  1 14:38:42 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Feb  1 14:38:42 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Feb  1 14:38:42 patricia-laptop kernel: [    0.108594] PM: Registering ACPI NVS region [mem 0x7f577000-0x7f5befff] (294912 bytes)
Feb  1 14:38:42 patricia-laptop kernel: [    1.331678] PM: Checking hibernation image partition /dev/sda6
Feb  1 14:38:42 patricia-laptop kernel: [    1.571237] PM: Hibernation image partition 8:6 present
Feb  1 14:38:42 patricia-laptop kernel: [    1.571243] PM: Looking for hibernation image.
Feb  1 14:38:42 patricia-laptop kernel: [    1.571526] PM: Image not found (code -22)
Feb  1 14:38:42 patricia-laptop kernel: [    1.571531] PM: Hibernation image not present or could not be loaded.
Feb  1 15:52:50 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Feb  1 15:52:50 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Feb  1 15:52:50 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Feb  1 15:52:50 patricia-laptop kernel: [    0.096601] PM: Registering ACPI NVS region [mem 0x7f577000-0x7f5befff] (294912 bytes)
Feb  1 15:52:50 patricia-laptop kernel: [    1.470234] PM: Checking hibernation image partition /dev/sda6
Feb  1 15:52:50 patricia-laptop kernel: [    1.712947] PM: Hibernation image partition 8:6 present
Feb  1 15:52:50 patricia-laptop kernel: [    1.712952] PM: Looking for hibernation image.
Feb  1 15:52:50 patricia-laptop kernel: [    1.713266] PM: Image not found (code -22)
Feb  1 15:52:50 patricia-laptop kernel: [    1.713270] PM: Hibernation image not present or could not be loaded.
Feb  1 17:06:21 patricia-laptop kernel: [ 4431.470879] PM: Marking nosave pages: [mem 0x0009f000-0x000fffff]
Feb  1 17:06:21 patricia-laptop kernel: [ 4431.470893] PM: Basic memory bitmaps created
Feb  1 17:08:42 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Feb  1 17:08:42 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Feb  1 17:08:42 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Feb  1 17:08:42 patricia-laptop kernel: [    0.100583] PM: Registering ACPI NVS region [mem 0x7f577000-0x7f5befff] (294912 bytes)
Feb  1 17:08:42 patricia-laptop kernel: [    1.483918] PM: Checking hibernation image partition /dev/sda6
Feb  1 17:08:42 patricia-laptop kernel: [    1.731403] PM: Hibernation image partition 8:6 present
Feb  1 17:08:42 patricia-laptop kernel: [    1.731408] PM: Looking for hibernation image.
Feb  1 17:08:42 patricia-laptop kernel: [    1.731715] PM: Image not found (code -22)
Feb  1 17:08:42 patricia-laptop kernel: [    1.731720] PM: Hibernation image not present or could not be loaded.
Feb  1 17:08:42 patricia-laptop kernel: [    3.880475] PM: Marking nosave pages: [mem 0x0009f000-0x000fffff]
Feb  1 17:08:42 patricia-laptop kernel: [    3.880485] PM: Basic memory bitmaps created
Feb  1 17:08:42 patricia-laptop kernel: [    3.910789] PM: Basic memory bitmaps freed
Feb  1 17:42:46 patricia-laptop kernel: [ 2119.892045] PM: Marking nosave pages: [mem 0x0009f000-0x000fffff]
Feb  1 17:42:46 patricia-laptop kernel: [ 2119.892058] PM: Basic memory bitmaps created
Feb  1 17:44:56 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Feb  1 17:44:56 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Feb  1 17:44:56 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Feb  1 17:44:56 patricia-laptop kernel: [    0.100589] PM: Registering ACPI NVS region [mem 0x7f577000-0x7f5befff] (294912 bytes)
Feb  1 17:44:56 patricia-laptop kernel: [    1.489708] PM: Checking hibernation image partition UUID=84c2098a-83b5-4a83-a053-8c9277da2941
Feb  1 17:44:56 patricia-laptop kernel: [    1.732758] PM: Hibernation image not present or could not be loaded.
Feb  1 17:44:56 patricia-laptop kernel: [    3.891652] PM: Marking nosave pages: [mem 0x0009f000-0x000fffff]
Feb  1 17:44:56 patricia-laptop kernel: [    3.891662] PM: Basic memory bitmaps created
Feb  1 17:44:56 patricia-laptop kernel: [    3.923250] PM: Basic memory bitmaps freed
Feb  1 18:26:52 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Feb  1 18:26:52 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Feb  1 18:26:52 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Feb  1 18:26:52 patricia-laptop kernel: [    0.096595] PM: Registering ACPI NVS region [mem 0x7f577000-0x7f5befff] (294912 bytes)
Feb  1 18:26:52 patricia-laptop kernel: [    1.474272] PM: Checking hibernation image partition UUID=84c2098a-83b5-4a83-a053-8c9277da2941
Feb  1 18:26:52 patricia-laptop kernel: [    1.710721] PM: Hibernation image not present or could not be loaded.
Feb  1 18:26:52 patricia-laptop kernel: [    3.768317] PM: Marking nosave pages: [mem 0x0009f000-0x000fffff]
Feb  1 18:26:52 patricia-laptop kernel: [    3.768328] PM: Basic memory bitmaps created
Feb  1 18:26:52 patricia-laptop kernel: [    3.798630] PM: Basic memory bitmaps freed
Feb  1 18:57:36 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Feb  1 18:57:36 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Feb  1 18:57:36 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Feb  1 18:57:36 patricia-laptop kernel: [    0.104589] PM: Registering ACPI NVS region [mem 0x7f577000-0x7f5befff] (294912 bytes)
Feb  1 18:57:36 patricia-laptop kernel: [    1.327798] PM: Checking hibernation image partition UUID=84c2098a-83b5-4a83-a053-8c9277da2941
Feb  1 18:57:36 patricia-laptop kernel: [    1.567235] PM: Hibernation image not present or could not be loaded.
Feb  1 18:57:36 patricia-laptop kernel: [    3.583308] PM: Marking nosave pages: [mem 0x0009f000-0x000fffff]
Feb  1 18:57:36 patricia-laptop kernel: [    3.583320] PM: Basic memory bitmaps created
Feb  1 18:57:36 patricia-laptop kernel: [    3.614729] PM: Basic memory bitmaps freed
Feb  2 13:33:30 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Feb  2 13:33:30 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Feb  2 13:33:30 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Feb  2 13:33:30 patricia-laptop kernel: [    0.100598] PM: Registering ACPI NVS region [mem 0x7f577000-0x7f5befff] (294912 bytes)
Feb  2 13:33:30 patricia-laptop kernel: [    1.323662] PM: Checking hibernation image partition UUID=84c2098a-83b5-4a83-a053-8c9277da2941
Feb  2 13:33:30 patricia-laptop kernel: [    1.545725] PM: Hibernation image not present or could not be loaded.
Feb  2 13:33:30 patricia-laptop kernel: [    8.656219] PM: Marking nosave pages: [mem 0x0009f000-0x000fffff]
Feb  2 13:33:30 patricia-laptop kernel: [    8.656232] PM: Basic memory bitmaps created
Feb  2 13:33:30 patricia-laptop kernel: [    8.967729] PM: Basic memory bitmaps freed
Feb  2 13:44:47 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Feb  2 13:44:47 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Feb  2 13:44:47 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Feb  2 13:44:47 patricia-laptop kernel: [    0.100591] PM: Registering ACPI NVS region [mem 0x7f577000-0x7f5befff] (294912 bytes)
Feb  2 13:44:47 patricia-laptop kernel: [    1.489810] PM: Checking hibernation image partition UUID=84c2098a-83b5-4a83-a053-8c9277da2941
Feb  2 13:44:47 patricia-laptop kernel: [    1.721220] PM: Hibernation image not present or could not be loaded.
Feb  2 13:44:47 patricia-laptop kernel: [    8.835130] PM: Marking nosave pages: [mem 0x0009f000-0x000fffff]
Feb  2 13:44:47 patricia-laptop kernel: [    8.835142] PM: Basic memory bitmaps created
Feb  2 13:44:47 patricia-laptop kernel: [    9.164258] PM: Basic memory bitmaps freed
Feb  2 14:01:21 patricia-laptop kernel: [ 1018.159796] PM: Marking nosave pages: [mem 0x0009f000-0x000fffff]
Feb  2 14:01:21 patricia-laptop kernel: [ 1018.159817] PM: Basic memory bitmaps created
Feb  2 14:03:13 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Feb  2 14:03:13 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Feb  2 14:03:13 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Feb  2 14:03:13 patricia-laptop kernel: [    0.096585] PM: Registering ACPI NVS region [mem 0x7f577000-0x7f5befff] (294912 bytes)
Feb  2 14:03:13 patricia-laptop kernel: [    1.491516] PM: Checking hibernation image partition UUID=5b29589b-9169-4676-94f4-b4718e39c4fd
Feb  2 14:03:13 patricia-laptop kernel: [    1.703421] PM: Hibernation image not present or could not be loaded.
Feb  2 14:03:13 patricia-laptop kernel: [    3.736477] PM: Marking nosave pages: [mem 0x0009f000-0x000fffff]
Feb  2 14:03:13 patricia-laptop kernel: [    3.736487] PM: Basic memory bitmaps created
Feb  2 14:03:13 patricia-laptop kernel: [    3.761810] PM: Basic memory bitmaps freed
Feb  2 14:09:02 patricia-laptop kernel: [  414.282877] PM: Marking nosave pages: [mem 0x0009f000-0x000fffff]
Feb  2 14:09:02 patricia-laptop kernel: [  414.282898] PM: Basic memory bitmaps created
Feb  2 14:10:47 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Feb  2 14:10:47 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Feb  2 14:10:47 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Feb  2 14:10:47 patricia-laptop kernel: [    0.096588] PM: Registering ACPI NVS region [mem 0x7f577000-0x7f5befff] (294912 bytes)
Feb  2 14:10:47 patricia-laptop kernel: [    1.475737] PM: Checking hibernation image partition UUID=5b29589b-9169-4676-94f4-b4718e39c4fd
Feb  2 14:10:47 patricia-laptop kernel: [    1.704607] PM: Hibernation image not present or could not be loaded.
Feb  2 14:10:47 patricia-laptop kernel: [    3.799809] PM: Marking nosave pages: [mem 0x0009f000-0x000fffff]
Feb  2 14:10:47 patricia-laptop kernel: [    3.799820] PM: Basic memory bitmaps created
Feb  2 14:10:47 patricia-laptop kernel: [    3.825521] PM: Basic memory bitmaps freed
Feb  3 00:04:16 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Feb  3 00:04:16 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Feb  3 00:04:16 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Feb  3 00:04:16 patricia-laptop kernel: [    0.100599] PM: Registering ACPI NVS region [mem 0x7f577000-0x7f5befff] (294912 bytes)
Feb  3 00:04:16 patricia-laptop kernel: [    1.481662] PM: Checking hibernation image partition UUID=5b29589b-9169-4676-94f4-b4718e39c4fd
Feb  3 00:04:16 patricia-laptop kernel: [    1.713021] PM: Hibernation image not present or could not be loaded.
Feb  3 00:04:16 patricia-laptop kernel: [    3.827408] PM: Marking nosave pages: [mem 0x0009f000-0x000fffff]
Feb  3 00:04:16 patricia-laptop kernel: [    3.827419] PM: Basic memory bitmaps created
Feb  3 00:04:16 patricia-laptop kernel: [    3.853303] PM: Basic memory bitmaps freed
Feb  3 12:09:29 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Feb  3 12:09:29 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Feb  3 12:09:29 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Feb  3 12:09:29 patricia-laptop kernel: [    0.096600] PM: Registering ACPI NVS region [mem 0x7f577000-0x7f5befff] (294912 bytes)
Feb  3 12:09:29 patricia-laptop kernel: [    1.485830] PM: Checking hibernation image partition UUID=5b29589b-9169-4676-94f4-b4718e39c4fd
Feb  3 12:09:29 patricia-laptop kernel: [    1.721319] PM: Hibernation image not present or could not be loaded.
Feb  3 12:09:29 patricia-laptop kernel: [    3.791398] PM: Marking nosave pages: [mem 0x0009f000-0x000fffff]
Feb  3 12:09:29 patricia-laptop kernel: [    3.791410] PM: Basic memory bitmaps created
Feb  3 12:09:29 patricia-laptop kernel: [    3.822573] PM: Basic memory bitmaps freed
Feb  3 12:31:35 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Feb  3 12:31:35 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Feb  3 12:31:35 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Feb  3 12:31:35 patricia-laptop kernel: [    0.096600] PM: Registering ACPI NVS region [mem 0x7f577000-0x7f5befff] (294912 bytes)
Feb  3 12:31:35 patricia-laptop kernel: [    1.491583] PM: Checking hibernation image partition UUID=5b29589b-9169-4676-94f4-b4718e39c4fd
Feb  3 12:31:35 patricia-laptop kernel: [    1.716389] PM: Hibernation image not present or could not be loaded.
Feb  3 12:48:02 patricia-laptop kernel: [ 1006.156422] PM: Marking nosave pages: [mem 0x0009f000-0x000fffff]
Feb  3 12:48:02 patricia-laptop kernel: [ 1006.156434] PM: Basic memory bitmaps created
Feb  3 12:50:09 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Feb  3 12:50:09 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Feb  3 12:50:09 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Feb  3 12:50:09 patricia-laptop kernel: [    0.100591] PM: Registering ACPI NVS region [mem 0x7f577000-0x7f5befff] (294912 bytes)
Feb  3 12:50:09 patricia-laptop kernel: [    1.486797] PM: Checking hibernation image partition UUID=5b29589b-9169-4676-94f4-b4718e39c4fd
Feb  3 12:50:09 patricia-laptop kernel: [    1.710673] PM: Hibernation image not present or could not be loaded.
Feb  3 20:18:55 patricia-laptop kernel: [26992.240777] PM: Marking nosave pages: [mem 0x0009f000-0x000fffff]
Feb  3 20:18:55 patricia-laptop kernel: [26992.240789] PM: Basic memory bitmaps created
Feb  3 20:20:54 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Feb  3 20:20:54 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Feb  3 20:20:54 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Feb  3 20:20:54 patricia-laptop kernel: [    0.096596] PM: Registering ACPI NVS region [mem 0x7f577000-0x7f5befff] (294912 bytes)
Feb  3 20:20:54 patricia-laptop kernel: [    1.493792] PM: Checking hibernation image partition UUID=5b29589b-9169-4676-94f4-b4718e39c4fd
Feb  3 20:20:54 patricia-laptop kernel: [    1.717777] PM: Hibernation image not present or could not be loaded.
Feb  4 12:29:29 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Feb  4 12:29:29 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Feb  4 12:29:29 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Feb  4 12:29:29 patricia-laptop kernel: [    0.100602] PM: Registering ACPI NVS region [mem 0x7f577000-0x7f5befff] (294912 bytes)
Feb  4 12:29:29 patricia-laptop kernel: [    1.474779] PM: Checking hibernation image partition UUID=5b29589b-9169-4676-94f4-b4718e39c4fd
Feb  4 12:29:29 patricia-laptop kernel: [    1.710669] PM: Hibernation image not present or could not be loaded.
Feb  4 13:55:22 patricia-laptop kernel: [ 5170.616844] PM: Marking nosave pages: [mem 0x0009f000-0x000fffff]
Feb  4 13:55:22 patricia-laptop kernel: [ 5170.616856] PM: Basic memory bitmaps created
Feb  4 13:57:07 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Feb  4 13:57:07 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Feb  4 13:57:07 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Feb  4 13:57:07 patricia-laptop kernel: [    0.096594] PM: Registering ACPI NVS region [mem 0x7f577000-0x7f5befff] (294912 bytes)
Feb  4 13:57:07 patricia-laptop kernel: [    1.483246] PM: Checking hibernation image partition UUID=5b29589b-9169-4676-94f4-b4718e39c4fd
Feb  4 13:57:07 patricia-laptop kernel: [    1.708017] PM: Hibernation image not present or could not be loaded.
Feb  4 21:26:45 patricia-laptop kernel: [27048.348783] PM: Marking nosave pages: [mem 0x0009f000-0x000fffff]
Feb  4 21:26:45 patricia-laptop kernel: [27048.348795] PM: Basic memory bitmaps created
Feb  4 21:28:28 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Feb  4 21:28:28 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Feb  4 21:28:28 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Feb  4 21:28:28 patricia-laptop kernel: [    0.096594] PM: Registering ACPI NVS region [mem 0x7f577000-0x7f5befff] (294912 bytes)
Feb  4 21:28:28 patricia-laptop kernel: [    1.469827] PM: Checking hibernation image partition UUID=5b29589b-9169-4676-94f4-b4718e39c4fd
Feb  4 21:28:28 patricia-laptop kernel: [    1.698494] PM: Hibernation image not present or could not be loaded.
Feb  4 21:33:13 patricia-laptop kernel: [  352.494532] PM: Marking nosave pages: [mem 0x0009f000-0x000fffff]
Feb  4 21:33:13 patricia-laptop kernel: [  352.494545] PM: Basic memory bitmaps created
Feb  4 21:34:58 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Feb  4 21:34:58 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Feb  4 21:34:58 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Feb  4 21:34:58 patricia-laptop kernel: [    0.100582] PM: Registering ACPI NVS region [mem 0x7f577000-0x7f5befff] (294912 bytes)
Feb  4 21:34:58 patricia-laptop kernel: [    1.475715] PM: Checking hibernation image partition UUID=5b29589b-9169-4676-94f4-b4718e39c4fd
Feb  4 21:34:58 patricia-laptop kernel: [    1.708554] PM: Hibernation image not present or could not be loaded.
Feb  5 09:32:01 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Feb  5 09:32:01 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Feb  5 09:32:01 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Feb  5 09:32:01 patricia-laptop kernel: [    0.104587] PM: Registering ACPI NVS region [mem 0x7f577000-0x7f5befff] (294912 bytes)
Feb  5 09:32:01 patricia-laptop kernel: [    1.489778] PM: Checking hibernation image partition UUID=5b29589b-9169-4676-94f4-b4718e39c4fd
Feb  5 09:32:01 patricia-laptop kernel: [    1.709512] PM: Hibernation image not present or could not be loaded.
Feb  5 13:51:28 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Feb  5 13:51:28 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Feb  5 13:51:28 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Feb  5 13:51:28 patricia-laptop kernel: [    0.096596] PM: Registering ACPI NVS region [mem 0x7f577000-0x7f5befff] (294912 bytes)
Feb  5 13:51:28 patricia-laptop kernel: [    1.319280] PM: Checking hibernation image partition UUID=5b29589b-9169-4676-94f4-b4718e39c4fd
Feb  5 13:51:28 patricia-laptop kernel: [    1.551515] PM: Hibernation image not present or could not be loaded.
Feb  5 13:56:04 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Feb  5 13:56:04 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Feb  5 13:56:04 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Feb  5 13:56:04 patricia-laptop kernel: [    0.100593] PM: Registering ACPI NVS region [mem 0x7f577000-0x7f5befff] (294912 bytes)
Feb  5 13:56:04 patricia-laptop kernel: [    1.487398] PM: Hibernation image not present or could not be loaded.
Feb  5 14:00:10 patricia-laptop kernel: [  264.405312] PM: Marking nosave pages: [mem 0x0009f000-0x000fffff]
Feb  5 14:00:10 patricia-laptop kernel: [  264.405324] PM: Basic memory bitmaps created
Feb  5 14:01:53 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Feb  5 14:01:53 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Feb  5 14:01:53 patricia-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Feb  5 14:01:53 patricia-laptop kernel: [    0.100596] PM: Registering ACPI NVS region [mem 0x7f577000-0x7f5befff] (294912 bytes)
Feb  5 14:01:53 patricia-laptop kernel: [    1.322586] PM: Hibernation image not present or could not be loaded.
herman@patricia-laptop:~$ 

```

It is a tricky one!

---

### Post by Toz on 2013-02-05
> It is a tricky one!
For sure!

Can you post back the contents of  /etc/initramfs-tools/conf.d/resume

and:
```
ls -l /dev/disk/by-uuid
```

---

### Post by Terraman on 2013-02-05
The contents of /etc/initramfs-tools/conf.d/resume:

```
RESUME=/dev/disk/by-uuid/5b29589b-9169-4676-94f4-b4718e39c4fd
```

...and:

```

herman@patricia-laptop:~$ ls -l /dev/disk/by-uuid
total 0
lrwxrwxrwx 1 root root 10 feb  5 14:01 5b29589b-9169-4676-94f4-b4718e39c4fd -> ../../sda6
lrwxrwxrwx 1 root root 10 feb  5 14:01 66050dc2-96e5-4054-90de-8b12e00235d5 -> ../../sda5
lrwxrwxrwx 1 root root 10 feb  5 14:01 9A6839AF68398B51 -> ../../sda1
lrwxrwxrwx 1 root root 10 feb  5 14:01 a408efbc-dbf6-406c-b94b-bcc514058936 -> ../../sda2
lrwxrwxrwx 1 root root 10 feb  5 14:01 E2BED980BED94E23 -> ../../sda3
herman@patricia-laptop:~$
```

---

### Post by Toz on 2013-02-05
Try commenting out the line in your /etc/fstab where you create a tmpfs:
> #tmpfs /tmp tmpfs defaults,noexec,nosuid 0 0

Reboot and try again.

If no luck, run again:
```
sudo update-initramfs -u
```
...reboot and try again.

---

### Post by Terraman on 2013-02-06
> **Toz said:**
> Try commenting out the line in your /etc/fstab where you create a tmpfs:


Reboot and try again.

If no luck, run again:
```
sudo update-initramfs -u
```
...reboot and try again.

Both suggestions have not worked.

---

