---
title: "Where is Edgy kernel-686?"
date: 2006-10-27
forum: General Help
---

### Post by erikcw on 2006-10-27
Hi all,

I just finished upgrading to Edgy, and the first thing I'm missing is the 686smb kernel for 2.6.17.  I can't seem to find it in apt.  Has it (2.6.17-10-686) not been released yet?

Thanks!
Erik

---

### Post by galileon on 2006-10-27
use the -generic one, its got smp included

---

### Post by bionnaki on 2006-10-27
sudo aptitutde install linux-686

---

### Post by mega on 2006-10-27
generic one wont even boot for me :(

---

### Post by galileon on 2006-10-27
what errors does it give? 

when grub appears, press e to edit the line, and try to remove the quiet and splash options from the kernel parameters, this will make the bootup verbose, and post any error it gives...

---

### Post by mega on 2006-10-27
here's the error

I did see this error fly past during the upgrade from dapper, something about it not being there durring a copy

[IMG]http://freddy.geekopolis.com/gallery2/d/4821-2/DSC_1167.JPG[/IMG]

---

### Post by galileon on 2006-10-27
hmmmm...could you check if the root file system specified in /boot/grub/menu.lst is the correct one? its of the form 

kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/hdaX, where X is the partition number..

besides, it should be the same as in the entry(-386) which works for you...

---

### Post by mega on 2006-10-27
they are all the same

I would guess that the generic kernel does not have my sata drivers in it

---

### Post by galileon on 2006-10-27
maybe you could try to rebuild the initrd for it then....


determine which module is needed for your sata, from lsmod in the working kernel

then sudo gedit /etc/initramfs-tools/modules,

add the module in the list, 

then  mkinitramfs 2.6.17-10-generic -o initrd-2.6.17-10-generic

copy the file initrd-2.6.17-10-generic to your /boot,

edit grub and make sure theres a line for 
initrd          /boot/initrd.img-2.6.17-10-generic

that might work...

---

### Post by mega on 2006-10-27
Module                  Size  Used by
nls_utf8                2304  1 
nls_cp437               6016  1 
vfat                   13440  1 
fat                    54556  1 vfat
binfmt_misc            11784  1 
rfcomm                 38936  0 
hidp                   32000  2 
l2cap                  23300  10 rfcomm,hidp
bluetooth              48996  5 rfcomm,hidp,l2cap
speedstep_lib           4868  0 
cpufreq_userspace       4372  0 
cpufreq_stats           5892  0 
freq_table              4996  1 cpufreq_stats
cpufreq_powersave       2048  0 
cpufreq_ondemand        6944  0 
cpufreq_conservative     7200  0 
video                  16644  0 
tc1100_wmi              7428  0 
sbs                    15776  0 
sony_acpi               5516  0 
pcc_acpi               13184  0 
i2c_ec                  5376  1 sbs
hotkey                 10660  0 
dev_acpi               11140  0 
button                  7056  0 
battery                10756  0 
container               4736  0 
ac                      5892  0 
asus_acpi              16792  0 
dm_mod                 60088  3 
md_mod                 78740  0 
parport_pc             36132  0 
lp                     11972  0 
parport                37320  2 parport_pc,lp
ipv6                  257632  8 
af_packet              21768  2 
tsdev                   8256  0 
usbhid                 42464  0 
sg                     35356  0 
nvidia               4713396  32 
usb_storage            73408  1 
libusual               15632  1 usb_storage
e100                   36484  0 
mii                     6016  1 e100
usblp                  14336  0 
snd_hda_intel          18580  1 
snd_hda_codec         163712  1 snd_hda_intel
snd_pcm_oss            46080  0 
snd_mixer_oss          18560  1 snd_pcm_oss
snd_pcm                80520  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_timer              23172  1 snd_pcm
i2c_core               22288  2 i2c_ec,nvidia
psmouse                40072  0 
serio_raw               7300  0 
evdev                  10496  1 
rtc                    12596  0 
pcspkr                  3072  0 
hw_random               6168  0 
shpchp                 40856  0 
pci_hotplug            31284  1 shpchp
snd                    55428  8 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
intel_agp              25116  1 
agpgart                33456  2 nvidia,intel_agp
soundcore               9952  1 snd
snd_page_alloc         10504  2 snd_hda_intel,snd_pcm
ext3                  138632  1 
jbd                    55700  1 ext3
ehci_hcd               32520  0 
uhci_hcd               23176  0 
usbcore               130304  7 usbhid,usb_storage,libusual,usblp,ehci_hcd,uhci_hcd
ide_generic             1536  0 
sd_mod                 21648  5 
ahci                   19076  4 
libata                 73228  1 ahci
scsi_mod              141320  5 sg,usb_storage,sd_mod,ahci,libata
piix                   10628  1 
generic                 4868  0 
thermal                14600  0 
processor              26028  1 thermal
fan                     5124  0 
fbcon                  40480  0 
tileblit                2944  1 fbcon
font                    8448  1 fbcon
bitblit                 6272  1 fbcon
softcursor              2432  1 bitblit
vesafb                  8348  0 
capability              5000  0 
commoncap               7808  1 capability


I'm guessing it's generic?

---

### Post by galileon on 2006-10-27
hmmm..sorry, i can't figure out which one it might be...could you post the result of lspci please? it would tell us about your chipset, then maybe we can google for the driver (thus knowing which module is the right one...)

---

### Post by mega on 2006-10-27
mega@mainpc:/var/log$ lspci
00:00.0 Host bridge: Intel Corporation 945G/GZ/P/PL Express Memory Controller Hub
00:01.0 PCI bridge: Intel Corporation 945G/GZ/P/PL Express PCI Express Root Port
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.4 PCI bridge: Intel Corporation 82801GR/GH/GHM (ICH7 Family) PCI Express Port 5 (rev 01)
00:1c.5 PCI bridge: Intel Corporation 82801GR/GH/GHM (ICH7 Family) PCI Express Port 6 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 SATA controller: Intel Corporation 82801GR/GH (ICH7 Family) Serial ATA Storage Controller AHCI (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation Unknown device 01df (rev a1)
05:08.0 Ethernet controller: Intel Corporation 82801G (ICH7 Family) LAN Controller (rev 01)

---

### Post by mega on 2006-10-27
this thread details how to fix

[http://ubuntuforums.org/showthread.php?t=282956](http://ubuntuforums.org/showthread.php?t=282956)

now I just have to figure out how to reorder grub's menu so generic starts by default

---

### Post by galileon on 2006-10-27
aaah, easy one,

sudo gedit /boot/grub/menu.lst

look for the line:

default 0

change the zero to whichever number your generic kernel is...(count from nought)

---

