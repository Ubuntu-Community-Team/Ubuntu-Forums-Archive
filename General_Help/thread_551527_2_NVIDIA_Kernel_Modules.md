---
title: "2 NVIDIA Kernel Modules"
date: 2007-09-15
forum: General Help
---

### Post by _Phil on 2007-09-15
Hi all

I've got a problem with the Nvidia graphics driver.
After some issues i tried the nvidia 1.0-7184 driver. 
Then i installed the latest, the nvidia 100.14.11.

Now here is my problem:
At startup both kernel modules are loaded. How can i remove the 1.0-7184 module?

I can start X if i type modprobe -r nvidia

Here output of dmesg | grep NVIDIA

> [   13.226155] nvidia: module license 'NVIDIA' taints kernel.
[   13.231563] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-7184  Tue Aug  1 18:38:58 PDT 2006
[   50.203359] NVRM: loading NVIDIA UNIX x86 Kernel Module  100.14.11  Wed Jun 13 18:21:22 PDT 2007

---

### Post by Tobster on 2007-09-15
What I would do is go to Automatix home page  (web page was temporary down at time of writing) and down load the codec from there. 

Automatix offer a lot of attractive software but it is VERY Important that you install each download one at a time.

Thanks

Toby

---

### Post by _Phil on 2007-09-16
I'm talking about the NVIDIA kernel module and not any codecs

---

### Post by nowshining on 2007-09-16
nvidia should of asked and done the uninstallation for u.

did you do the following

download to a directory where you want it


exit all applications

press CTRL + F1

hit enter

input your username

input your password

cd 

to the directory where the download was

and then 

used 

sudo /etc/init.d/gdm stop

insert password

then issued the following command

sudo sh NVIDIA-Linux-x86-100.14.11-pkg1.run

input your password

and followed the on-screen prompts???


edit: then typed

sudo /etc/init.d/gdm start

hit enter

input your password and then hit enter..

---

### Post by _Phil on 2007-09-16
Of course i did it this way. But the new driver didn't uninstall the old one.

I even tried 
```
nvidia-installer -uninstall 
```
which removed the driver for X but not the kernel module

---

### Post by nowshining on 2007-09-16
probably what your looking for is 

```
Open up a terminal
 
type gksudo nautilus
 
filesystem - etc - rc5.d
 
backup and delete nvidia-kernel
 
then go to rcS.d and make sure to backup that one and delete it (i forgot if there is one in there or not)

```

that's from my how to for the fx5200

---

### Post by _Phil on 2007-09-18
Didn't work.. I even suppressed execution of NVIDIA Kernel on Runlevel 2 
by changing
```
sudo mv /etc/rc2.d/S20nvidia-kernel /etc/rc2.d/K20nvidia-kernel
```

I thought the 1.0-7184 module will be loaded in runlevel 2 because of the time in the logfile.

any ideas?

thx
phil

---

### Post by nick_h on 2007-09-18
Did you add "nv" to the disabled modules list in /etc/default/linux-restricted-modules-common?

---

### Post by nowshining on 2007-09-18
"and "nv" disables both the nvidia drivers."

---

### Post by _Phil on 2007-09-18
I'll get home late tonight.
So i'll write you the result late or tomorrow.

---

### Post by _Phil on 2007-09-18
nv add to restricted modules didn't work.

Now i've tried something new.

First

```
sudo nvidia-installer --uninstall
```

then

```
sudo find / -name nvidia
```

and delete every file, that has nvidia in its name.
at least installed the new driver again. -> didn't work, same error as ever.

the funny thing:
```
cat /proc/driver/nvidia/version
```
gives me the 1.0-9639 driver

if I 
```
sudo modprobe -r nvidia
startx
```
which removes the module from the kernel (unfortunatly only temporary)
and then if I check output of
```
cat /proc/driver/nvidia/version
```
it shows the correct module 100.14.11

what the hell is going on? I've never installed 1.0-9639


thx for advices
phil

---

### Post by nowshining on 2007-09-18
in a terminal list all the modules you have at startup and boot

by doing the type

```

lsmod

```

---

### Post by _Phil on 2007-09-19
I'm currently at work.
But i ssh'd to my home machine and did lsmod.

There is 1 nvidia module. I guess if i lsmod after failure of X there would be 2 nvidia modules.
But how to remove the old one??

```
lsmod
Module                  Size  Used by
nvidia               7252756  24
binfmt_misc            12680  1
rfcomm                 40856  0
l2cap                  25856  5 rfcomm
bluetooth              55908  4 rfcomm,l2cap
ppdev                  10116  0
speedstep_lib           6148  0
cpufreq_stats           7360  0
cpufreq_conservative     8200  0
cpufreq_ondemand        9228  0
freq_table              5792  2 cpufreq_stats,cpufreq_ondemand
cpufreq_userspace       5408  0
cpufreq_powersave       2688  0
tc1100_wmi              8068  0
sony_acpi               6284  0
pcc_acpi               13184  0
dev_acpi               12292  0
asus_acpi              17308  0
button                  8720  0
dock                   10268  0
sbs                    15652  0
i2c_ec                  6016  1 sbs
battery                10756  0
backlight               7040  1 asus_acpi
ac                      6020  0
video                  16388  0
container               5248  0
nls_utf8                3072  1
ntfs                  107764  1
ipv6                  268960  16
sbp2                   23812  0
lp                     12452  0
fuse                   46612  0
snd_hda_intel          21912  1
snd_hda_codec         205056  1 snd_hda_intel
snd_pcm_oss            44544  0
snd_mixer_oss          17408  1 snd_pcm_oss
snd_pcm                79876  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           4740  0
snd_seq_oss            32896  0
sky2                   43528  0
snd_seq_midi            9600  0
snd_rawmidi            25472  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                52592  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23684  2 snd_pcm,snd_seq
snd_seq_device          9100  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54020  12 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
af_packet              23816  6
soundcore               8672  1 snd
serio_raw               7940  0
snd_page_alloc         10888  2 snd_hda_intel,snd_pcm
iTCO_wdt               11812  0
iTCO_vendor_support     4868  1 iTCO_wdt
parport_pc             36388  1
parport                36936  3 ppdev,lp,parport_pc
intel_agp              26140  1
agpgart                35400  2 nvidia,intel_agp
i2c_core               22656  2 nvidia,i2c_ec
pcspkr                  4224  0
psmouse                38920  0
shpchp                 34324  0
pci_hotplug            32576  1 shpchp
evdev                  11008  3
tsdev                   8768  0
ext3                  133128  6
jbd                    59816  1 ext3
mbcache                 9604  1 ext3
sg                     36252  0
sr_mod                 17060  0
cdrom                  37664  1 sr_mod
sd_mod                 23428  11
generic                 5124  0 [permanent]
usbhid                 26592  0
hid                    27392  1 usbhid
ata_piix               15492  5
ata_generic             9092  0
uhci_hcd               25360  0
floppy                 59524  0
ohci1394               36528  0
ehci_hcd               34188  0
dmfe                   21148  0
ahci                   22020  4
libata                125720  3 ata_piix,ata_generic,ahci
scsi_mod              142348  5 sbp2,sg,sr_mod,sd_mod,libata
ieee1394              299448  2 sbp2,ohci1394
usbcore               134280  4 usbhid,uhci_hcd,ehci_hcd
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
```

---

### Post by nowshining on 2007-09-19
hmmm 

"nvidia               7252756  24"

&

"agpgart                35400  2 nvidia,intel_agp
i2c_core               22656  2 nvidia,i2c_ec"

what Nvidia Card o u use?

---

### Post by nick_h on 2007-09-19
What is the output of dmesg and cat /proc/driver/nvidia/version for this module?

---

### Post by nowshining on 2007-09-19
nick I just remembered a bit ago they announced a new version of the Nvidia drivers they could then install them and see what happens..


.19 i believe - a few posts in the Community Cafe.

---

### Post by _Phil on 2007-09-19
The output of my lsmod was taken as the system was running fine.

i temporarly fixed this problem by unloading the module at runlevel 2

```

sudo echo "#!/bin/sh" > /etc/init.d/S20nvidia-kernel-remove
sudo echo "modprobe -r nvidia" >> /etc/init.d/S20nvidia-kernel-remove
sudo ln -s /etc/init.d/S20nvidia-kernel-remove /etc/rc2.d/S20nvidia-kernel-remove

```

But this can't be the solution.
Does anybody know what modprobe -r  exactly does? I know it removes temporarly any module from the kernel. but how do I remove a module permanently?

cheers
phil

---

### Post by nowshining on 2007-09-19
open up a terminal

type or copy + paste

```

 sudo gedit /etc/default/linux-restricted-modules-common

```

input your password

and follow the directions at the top of the file. :) some wont' remove for me, heack if u'd like to get rid of bluetooth if you don't have it or IPv6 if you don't use it - let me know and i'll direct u to how to do it. EDIT: oh and reboot to finish the job and lsmod to make sure it is gone. :)

---

### Post by _Phil on 2007-09-19
OK will try it if I'm at home.
by the way I have a GeForce FX5900.

The funny thing is I have installed ubuntu many times and never had this issue before.

---

### Post by nowshining on 2007-09-19
lolz, Fx5900 oooh ur the Rich one. :P I just have a lowly 5200. Did you know that you can overlock and or underclock the memory and GPU ?? Nvidia settings has a hidden option called coolbits to do so.

---

### Post by nick_h on 2007-09-19
I suggested /etc/default/linux-restricted-modules-common in an earlier post.  Adding "nv" should prevent the driver from restricted modules being loaded - useful if you have installed a driver downloaded from the nvidia site.

One more thought - the installation of nvidia-glx-new puts a hidden configuration file in /lib/linux-restricted-modules.  The OP might have installed this and still have the file remaining.  (I forget what it is called)

---

### Post by nowshining on 2007-09-20
nick I seem to have the exact same thing on my side once I updated to the .19 version. Wasn't the installer suppose to remove these??

---

### Post by nowshining on 2007-09-20
well adding that did seem to help the slowness a bit and the problems I did have but why the module at .11 tho..

---

### Post by nick_h on 2007-09-20
> Wasn't the installer suppose to remove these??
I think that the nvidia installer removes previous installations first.  It might be worth looking in */var/log/nvidia-installer.log* to check what the installer actually did.

You can also use the installer to uninstall the driver:
```
sudo sh NVIDIA-Linux-x86-x.y.z-pkg1.run --uninstall
```

---

### Post by lubosz on 2007-12-05
> **nick_h said:**
> Did you add "nv" to the disabled modules list in /etc/default/linux-restricted-modules-common?

thanks that solved the problem for me! my x was crashing and i had to un and reinstall the nivida.com beta driver every boot because it conflicted with the ubuntu nvidia module. thanx

---

