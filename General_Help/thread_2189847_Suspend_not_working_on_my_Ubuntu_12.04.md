---
title: "Suspend not working on my Ubuntu 12.04"
date: 2013-11-24
forum: General Help
---

### Post by 2xenobii on 2013-11-24
Welcome when trying to turn the state suspend state the screen goes black, and after one second computer returns to the desktop.

My motherboard is Asus P5N-MX
Kernel in my ubuntu is: 3.8.0-33
Nvidia driver is version 304                 
```
/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux Nowy 3.8.0-33-generic #48~precise1-Ubuntu SMP Thu Oct 24 16:31:16 UTC 2013 i686 i686 i386 GNU/Linux
Module                  Size  Used by
bnep                   17852  2 
rfcomm                 38400  0 
bluetooth             211552  10 bnep,rfcomm
nvidia              10287220  40 
arc4                   12509  2 
rt2800usb              22525  0 
binfmt_misc            17292  1 
rt2800lib              61785  1 rt2800usb
crc_ccitt              12627  1 rt2800lib
snd_hda_codec_realtek    65004  1 
rt2x00usb              20099  1 rt2800usb
rt2x00lib              49144  3 rt2800usb,rt2800lib,rt2x00usb
snd_hda_intel          38819  3 
snd_hda_codec         118650  2 snd_hda_codec_realtek,snd_hda_intel
mac80211              541819  3 rt2800lib,rt2x00usb,rt2x00lib
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                85934  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
cfg80211              453919  2 rt2x00lib,mac80211
snd_rawmidi            25157  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51593  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14137  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    57014  15 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12600  1 snd
snd_page_alloc         18398  2 snd_hda_intel,snd_pcm
serio_raw              13031  0 
microcode              18433  0 
i2c_nforce2            12913  0 
ppdev                  12849  0 
asus_atk0110           17742  0 
parport_pc             27612  1 
mac_hid                13077  0 
hwmon_vid              12723  0 
coretemp               13324  0 
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
vesafb                 13540  1 
hid_generic            12484  0 
usbhid                 46125  0 
hid                    87362  2 hid_generic,usbhid
pata_acpi              12886  0 
pata_amd               13761  2 
ahci                   25631  0 
libahci                26336  1 ahci
             total       used       free     shared    buffers     cached
Mem:       1932632     663236    1269396          0      36660     297976
-/+ buffers/cache:     328600    1604032
Swap:      1963004          0    1963004

/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:

/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:

/etc/pm/sleep.d/10_grub-common suspend suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:

/usr/lib/pm-utils/sleep.d/75modules suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:

/usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:

/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:

/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:

/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:

/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
nVidia binary video drive detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Sun Nov 24 17:01:19 CET 2013: performing suspend
Sun Nov 24 17:01:26 CET 2013: Awake.
Sun Nov 24 17:01:26 CET 2013: Running hooks for resume
Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:

/usr/lib/pm-utils/sleep.d/99video resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:

/usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:

/usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron resume suspend:

/usr/lib/pm-utils/sleep.d/95anacron resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:

/usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/90clock resume suspend:

/usr/lib/pm-utils/sleep.d/90clock resume suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/75modules resume suspend:
Reloaded unloaded modules.

/usr/lib/pm-utils/sleep.d/75modules resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend:
Having NetworkManager wake interfaces back up...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common resume suspend:

/etc/pm/sleep.d/10_grub-common resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:

/usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:

/usr/lib/pm-utils/sleep.d/00logging resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.
Sun Nov 24 17:01:27 CET 2013: Finished.
```

---

### Post by Toz on 2013-11-24
Perhaps your network device is waking the system early. Try unloading and reloading during the suspend process.

1. Create the file /etc/pm/config.d/modules:
```
gksudo gedit /etc/pm/config.d/modules
```

2. Copy/paste the following content:
```
SUSPEND_MODULES="rt2800usb"
```

3. Save the file and try again.

If it still doesn't work, try replacing the contents of the file in step #2 with:
```
SUSPEND_MODULES="rt2800usb rt2800lib crc_ccitt rt2x00usb rt2x00lib mac80211 cfg80211"
```
...and trying again.

---

### Post by dave35 on 2013-11-24
I had a similar problem after a fresh install, after googling I tried this and suspend started working. Run the commands as root ...

$nano /etc/default/grub

# Original line ..
# GRUB_CMDLINE_LINUX="acpi=off noapic nolapic edd=on nodmraid nomodeset"
# Changed to ..
GRUB_CMDLINE_LINUX="noapic nolapic edd=on nodmraid nomodeset"
$update-grub

I also saw something where the Video card driver could also prevent the computer going into suspend. I use the proprietary one if that makes a difference I don't know ...

---

### Post by Toz on 2013-11-24
A couple of things to keep in mind with this post:

> **dave35 said:**
> I had a similar problem after a fresh install, after googling I tried this and suspend started working. Run the commands as root ...

$nano /etc/default/grub

# Original line ..
# GRUB_CMDLINE_LINUX="acpi=off noapic nolapic edd=on nodmraid nomodeset"
# Changed to ..
GRUB_CMDLINE_LINUX="noapic nolapic edd=on nodmraid nomodeset"
$update-grub
The default GRUB_CMDLINE_LINUX entry is:
> GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
@dave35, you have a number of different entries listed there that may be potentially disruptive to the OP. See [here]("http://askubuntu.com/questions/186296/what-are-the-f6-options-during-installation") for a more detailed description of the items. Of particular concern would be "nodmraid" (if you are using a raid setup) and "nomodeset" (which may lead to video issues).
> I also saw something where the Video card driver could also prevent the computer going into suspend. I use the proprietary one if that makes a difference I don't know ...
OP is already using the proprietary nvidia driver. From the module listing from the suspend log:
> nvidia              10287220  40 

---

### Post by 2xenobii on 2013-11-25
@Toz I added these modules what you said and nothing has changed
Put the log again :
> /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.
Mon Nov 25 22:21:15 CET 2013: Finished.
Initial commandline parameters: 
Mon Nov 25 22:24:55 CET 2013: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux Nowy 3.8.0-33-generic #48~precise1-Ubuntu SMP Thu Oct 24 16:31:16 UTC 2013 i686 i686 i386 GNU/Linux
Module                  Size  Used by
rt2800usb              22525  0 
rt2800lib              61785  1 rt2800usb
crc_ccitt              12627  1 rt2800lib
rt2x00usb              20099  1 rt2800usb
rt2x00lib              49144  3 rt2800usb,rt2800lib,rt2x00usb
mac80211              541819  3 rt2800lib,rt2x00usb,rt2x00lib
cfg80211              453919  2 rt2x00lib,mac80211
nls_iso8859_1          12617  1 
usb_storage            48053  1 
bnep                   17852  2 
rfcomm                 38400  0 
bluetooth             211552  10 bnep,rfcomm
nvidia              10287220  40 
arc4                   12509  2 
binfmt_misc            17292  1 
snd_hda_codec_realtek    65004  1 
snd_hda_intel          38819  3 
snd_hda_codec         118650  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                85934  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25157  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51593  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14137  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    57014  15 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12600  1 snd
snd_page_alloc         18398  2 snd_hda_intel,snd_pcm
microcode              18433  0 
serio_raw              13031  0 
ppdev                  12849  0 
asus_atk0110           17742  0 
i2c_nforce2            12913  0 
parport_pc             27612  1 
mac_hid                13077  0 
hwmon_vid              12723  0 
coretemp               13324  0 
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
vesafb                 13540  1 
hid_generic            12484  0 
usbhid                 46125  0 
hid                    87362  2 hid_generic,usbhid
pata_acpi              12886  0 
ahci                   25631  0 
libahci                26336  1 ahci
pata_amd               13761  2 
             total       used       free     shared    buffers     cached
Mem:       1932632    1007128     925504          0      85712     551644
-/+ buffers/cache:     369772    1562860
Swap:      1963004          0    1963004

/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:

/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:

/etc/pm/sleep.d/10_grub-common suspend suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:
Unloading kernel module rt2800usb...Done.
Unloading kernel module rt2800lib...Done.
Unloading kernel module crc_ccitt...Done.
Unloading kernel module rt2x00usb...Done.
Unloading kernel module rt2x00lib...Done.
Unloading kernel module mac80211...Done.
Unloading kernel module cfg80211...Done.

/usr/lib/pm-utils/sleep.d/75modules suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:

/usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:

/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
stop: Unknown instance: 

/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:

/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:

/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
nVidia binary video drive detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Mon Nov 25 22:24:56 CET 2013: performing suspend
Mon Nov 25 22:25:04 CET 2013: Awake.
Mon Nov 25 22:25:04 CET 2013: Running hooks for resume
Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:

/usr/lib/pm-utils/sleep.d/99video resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:

/usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:

/usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron resume suspend:

/usr/lib/pm-utils/sleep.d/95anacron resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:

/usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/90clock resume suspend:

/usr/lib/pm-utils/sleep.d/90clock resume suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/75modules resume suspend:
Reloaded unloaded modules.

/usr/lib/pm-utils/sleep.d/75modules resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend:
Having NetworkManager wake interfaces back up...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common resume suspend:

/etc/pm/sleep.d/10_grub-common resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:

/usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:

/usr/lib/pm-utils/sleep.d/00logging resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.
Mon Nov 25 22:25:05 CET 2013: Finished.

---

### Post by Toz on 2013-11-25
Something is waking your system early - looks like its not the network card. Feel free to remove the file you created.

What devices are enabled to wakeup the system?
```
cat /proc/acpi/wakeup
```

---

### Post by 2xenobii on 2013-11-26
cat /proc/acpi/wakeup
> kaczka2@Nowy:~$ cat /proc/acpi/wakeup
Device    S-state      Status   Sysfs node
HUB0      S5    *disabled  pci:0000:00:0a.0
XVR0      S5    *disabled  pci:0000:00:0b.0
XVR1      S5    *disabled  pci:0000:00:0c.0
XVR2      S5    *disabled  pci:0000:00:0d.0
UAR1      S5    *disabled  pnp:00:07
PS2K      S4    *enabled   pnp:00:09
USB0      S4    *enabled   pci:0000:00:04.0
USB2      S4    *enabled   pci:0000:00:04.1
AZAD      S5    *disabled  pci:0000:00:09.0
MMAC      S5    *disabled
kaczka2@Nowy:~$ 


---

### Post by Toz on 2013-11-26
Perhaps the USB devices are waking the system early. Try these commands:
```
 
echo "USB0" | sudo tee /proc/acpi/wakeup
echo "USB2" | sudo tee /proc/acpi/wakeup
```
...enter your password when prompted.

Then post back the results of:
```
cat /proc/acpi/wakeup
```
...again to confirm that those devices are disabled as wakeup devices and try suspending again.

---

### Post by 2xenobii on 2013-11-27
It works! The computer passed to the standby. Will I have to turn off the USB device if it's permanent ?
cat /proc/acpi/wakeup
> kaczka2@Nowy:~$ cat /proc/acpi/wakeup
Device    S-state      Status   Sysfs node
HUB0      S5    *disabled  pci:0000:00:0a.0
XVR0      S5    *disabled  pci:0000:00:0b.0
XVR1      S5    *disabled  pci:0000:00:0c.0
XVR2      S5    *disabled  pci:0000:00:0d.0
UAR1      S5    *disabled  pnp:00:07
PS2K      S4    *enabled   pnp:00:09
USB0      S4    *disabled  pci:0000:00:04.0
USB2      S4    *disabled  pci:0000:00:04.1
AZAD      S5    *disabled  pci:0000:00:09.0
MMAC      S5    *disabled
kaczka2@Nowy:~$ 


---

### Post by 2xenobii on 2013-11-27
Unfortunately, after a system restart, the devices
> USB0 S4 *enabled pci:0000:00:04.0
USB2 S4 *enabled pci:0000:00:04.1
are enabled

---

### Post by Toz on 2013-11-27
With root privlidges add the lines:
```

echo "USB0" > /proc/acpi/wakeup
echo "USB2" > /proc/acpi/wakeup
```
...to your **/etc/rc.local** file _above_ the *exit 0* command, like this:

```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

echo "USB0" > /proc/acpi/wakeup
echo "USB2" > /proc/acpi/wakeup

exit 0
```

This script will run on boot and will disable those devices from wakeing up the system.

---

### Post by 2xenobii on 2013-11-27
Thanks for your help everything works

---

