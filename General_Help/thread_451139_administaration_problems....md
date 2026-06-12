---
title: "administaration problems..."
date: 2007-05-22
forum: General Help
---

### Post by NiviJah on 2007-05-22
hello, 
i've installed ubuntu (after a hell lot of problems) using to "modprobe piix" command
but now i have some issues:

every time i start ubutu i have to give him the command  again (during boot)
it seems i can't change any system file (not administrator)

how can i fix this?

---

### Post by mitch.c on 2007-05-22
> **NiviJah said:**
> i've installed ubuntu (after a hell lot of problems) using to "modprobe piix" command
but now i have some issues:

every time i start ubutu i have to give him the command  again (during boot)
The simple answer is to add piix to /etc/modules
> **NiviJah said:**
> it seems i can't change any system file (not administrator)
You should be able to use 'sudo' to access and change files using your favorite text editor. For example, when I want to change a file in /etc, I use:
```
$ sudo vim /etc/modules
```
This lets start the vim editor as if I was root and make appropriate changes. If vim is not your cup of tea, try:
```
$ gksudo gedit /etc/modules
```
Take a look at the docs here: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Hope that helps.
-- 
Mitch

---

### Post by NiviJah on 2007-05-22
well i did what you said...
didn't help..
any other ideas?

---

### Post by mitch.c on 2007-05-22
What didn't work... the module won't load at boot? You can't edit a 'system' file as root? If you provide more detail, perhaps I can help.

---

### Post by NiviJah on 2007-05-22
i managed to edit the file.
i put the line "piix" to it and reboot, but it still asks me for the command.
i also tried with
"modprobe piix" and it didn't help..

---

### Post by NiviJah on 2007-05-22
any ideas?

---

### Post by mitch.c on 2007-05-22
Could you describe exactly what happens during and exactly how you are prompted for piix? Do you just modprobe piix when this happens? After you load piix, what is the output of:
```
$ lsmod | grep piix
```

---

### Post by NiviJah on 2007-05-22
i type the command during boot after an error
"ca't access tty......."
i type "modprobe piix"
and the "exit"
after that ubuntu starts normally....

---

### Post by mitch.c on 2007-05-22
Remove piix from /etc/modules and add "piix" to /etc/initramfs-tools/modules, then run:
```
$ sudo update-initramfs -u
```
Does this help?

---

### Post by NiviJah on 2007-05-22
no, didn't help.... :(

---

### Post by mitch.c on 2007-05-22
You may need to add some other modules to /etc/initramfs-tools/modules. I might be able to help you if you post output from:
```
$ lsmod
```
It looks as if this bug [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/106864](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/106864) might be the cause of your problems.

---

### Post by NiviJah on 2007-05-22
this is the output:


lsmod

Module                  Size  Used by

binfmt_misc            12680  1 

rfcomm                 40856  0 

l2cap                  25728  5 rfcomm

bluetooth              55908  4 rfcomm,l2cap

ppdev                  10116  0 

speedstep_lib           6148  0 

cpufreq_stats           7360  0 

cpufreq_userspace       5408  0 

cpufreq_powersave       2688  0 

cpufreq_conservative     8200  0 

cpufreq_ondemand        9228  0 

freq_table              5792  2 cpufreq_stats,cpufreq_ondemand

pcc_acpi               13184  0 

sony_acpi               6284  0 

tc1100_wmi              8068  0 

dev_acpi               12292  0 

ac                      6020  0 

button                  8720  0 

dock                   10268  0 

container               5248  0 

asus_acpi              17308  0 

sbs                    15652  0 

i2c_ec                  5888  1 sbs

video                  16388  0 

backlight               7040  1 asus_acpi

battery                10756  0 

ipv6                  268704  8 

lp                     12452  0 

fuse                   46612  0 

gspca                 607824  0 

snd_intel8x0           34204  1 

snd_ac97_codec         98336  1 snd_intel8x0

parport_pc             36388  1 

parport                36936  3 ppdev,lp,parport_pc

ac97_bus                3200  1 snd_ac97_codec

snd_pcm_oss            44544  0 

snd_mixer_oss          17408  1 snd_pcm_oss

snd_mpu401              9256  0 

snd_mpu401_uart         9472  1 snd_mpu401

snd_pcm                79876  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss

snd_seq_dummy           4740  0 

snd_seq_oss            32896  0 

analog                 12832  0 

sn9c102                90892  0 

snd_seq_midi            9600  0 

snd_rawmidi            25472  2 snd_mpu401_uart,snd_seq_midi

snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi

pcspkr                  4224  0 

gameport               16520  1 analog

videodev               28160  2 gspca,sn9c102

v4l1_compat            15236  1 videodev

v4l2_common            25216  2 sn9c102,videodev

usblp                  14848  0 

snd_seq                52592  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event

snd_timer              23684  2 snd_pcm,snd_seq

snd_seq_device          9100  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq

usbhid                 26592  0 

hid                    27392  1 usbhid

snd                    54020  14 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_mpu401,snd_mpu401_uart,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device

soundcore               8672  1 snd

snd_page_alloc         10888  2 snd_intel8x0,snd_pcm

iTCO_wdt               11812  0 

iTCO_vendor_support     4868  1 iTCO_wdt

intel_agp              25116  1 

agpgart                35400  1 intel_agp

i2c_core               22784  1 i2c_ec

shpchp                 34324  0 

pci_hotplug            32576  1 shpchp

af_packet              23816  2 

tsdev                   8768  0 

evdev                  11008  4 

ext3                  133128  1 

jbd                    59816  1 ext3

mbcache                 9604  1 ext3

ide_cd                 32672  0 

cdrom                  37664  1 ide_cd

ide_disk               17024  3 

generic                 5124  0 [permanent]

ata_generic             9092  0 

8139too                27648  0 

floppy                 59524  0 

ata_piix               15492  0 

libata                125720  2 ata_generic,ata_piix

scsi_mod              142348  1 libata

8139cp                 25088  0 

mii                     6528  2 8139too,8139cp

ehci_hcd               34188  0 

uhci_hcd               25360  0 

usbcore               134280  7 gspca,sn9c102,usblp,usbhid,ehci_hcd,uhci_hcd

thermal                14856  0 

processor              31048  1 thermal

fan                     5636  0 

fbcon                  42656  0 

tileblit                3584  1 fbcon

font                    9216  1 fbcon

bitblit                 6912  1 fbcon

softcursor              3200  1 bitblit

vesafb                  9220  0 

capability              5896  0 

commoncap               8192  1 capability

piix                   10756  0 [permanent]

---

### Post by mitch.c on 2007-05-22
I found another thread that suggest that udev has not been updated properly. Try:
```
$ sudo apt-get install udev
```
I'm sorry I don't have a definitive answer for you, I'm just following suggestions from other posts.

---

### Post by NiviJah on 2007-05-23
no, didn't help...everything is up to date...
maybe if i tell you what i've done.

i followed does steps (cause i was unable to install ubuntu in any way)

[PHP]UPDATED FIX!!! I removed the old suggestion that I had written and pasted the new fix from the main thread of this problem...... Credit to this goes to
hbjason as these are his exact words. It appears as though it's a combination of some of my suggestions that I found on the internet etc etc.


f you are getting this error (and you have a SATA harddrive); this is the fix:

At the LiveCD initial boot screen:
o Select F6 for more options
o Add the following option to the beginning of the options list:
break=top
o Press enter to start booting
Ubuntu will start booting, but kick you out to a command prompt; at the prompt type these two commands:
modprobe piix
exit

You will now boot into the LiveCD normally.

If you choose to install from the LiveCD, you must make the following modifications (or else your installed system will not be able to boot, just like the LiveCD):
o Make note of the device id of the partitions that were used to install (such as /dev/hda1)
-- if you choose to install the '/boot' mount from a different partition make note of it as well (this would be done from the manual partition selection); just a side note -- if you do this, make sure the boot partition is at least 50MB or the install will error at grub setup
o When the install is complete do not reboot -- stay in the LiveCD
o Open a terminal (Applications->Accessories->Terminal)
o You must now mount the installed partitions by typing the following (assuming the install was to /dev/hda1; otherwise replace '/dev/hda1' with the install partition) commands:

mkdir target
sudo mount /dev/hda1 target

*if you also created a boot partition issue (replace /dev/hda2 with the boot partition) the command:
sudo mount /dev/hda2 target/boot

sudo chroot target

o You will now be in a 'chroot' command prompt for your new ubuntu system (be careful here, you are editing with root access!)
o You must edit the /etc/initramfs-tools/modules file; adding a line with the word: piix
-- you should do this with your favorite unix editor; or simply type the command:
echo piix >> /etc/initramfs-tools/modules
o After modifying the file you must update the system with the command
update-initramfs -u
o When complete, type 'exit' to exit the chroot env; you can now close the Terminal and reset your system.

Now when you boot you will be in your new shinny Ubuntu system![/PHP]


the thing is that the installation went fine but when ubuntu started i failed to complete the rest...
the commands just didn't work....
so i started my pc _witout_ completing the rest of the process



this help?

---

