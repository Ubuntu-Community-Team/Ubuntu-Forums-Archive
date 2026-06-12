---
title: "No sound"
date: 2004-10-13
forum: General Help
---

### Post by bpmckie on 2004-10-13
Hi All,
Love the distro, finally got it to install on my Dell 8200 Inspiron Laptop. Works great except it cant find the sound card. I have a intel 82801 internal sound card. When I boot it says alsa cant find a sound card. I am kinda of a newbie at linux, so I was hoping someone could show me how to configure for sound.
Thanks, Brian

---

### Post by triad169 on 2004-10-13
Open up a terminal and try:

```
modprobe snd-intel8x0
```

What output do you get?  If no errors.  then run:

```
sudo /etc/init.d/alsa restart
```

Any errors.  If no try your sound.

Let me know what happens.

Triad

---

### Post by bpmckie on 2004-10-13
Hi,
Thanks for the help. I did what you suggested. I did not get any errors and it stored the alsa settings however when I tried the music player I get and error " /dev/dsp does not exist." Any ideas?
Thanks.

---

### Post by bpmckie on 2004-10-13
Hi Triad,

I just noticed that when I go to try and adjust the volume through volume control, I get and error that states no mixer or devices found. Dont know if that helps.

Brian

---

### Post by triad169 on 2004-10-13
can you open up a terminal and type:

```
lsmod
```

and paste results up here.  

Triad

As a side note Ubuntu should have setup this card automatically for you.  I would post a Bug to them at this url:

[http://bugzilla.ubuntu.com/](http://bugzilla.ubuntu.com/)

---

### Post by bpmckie on 2004-10-13
Hi,
Here is the rsult of lsmod.
Module                  Size  Used by
nls_cp437               5696  0
isofs                  36632  0
udf                    91812  0
acpi                    5996  0
proc_intf               3776  0
cpufreq_powersave       1728  0
cpufreq_userspace       5240  2
freq_table              4196  1 acpi
ipv6                  256996  8
orinoco_cs              9160  1
orinoco                42892  1 orinoco_cs
hermes                  8480  2 orinoco_cs,orinoco
ds                     18436  7 orinoco_cs
button                  6584  0
ac                      4812  0
battery                 9388  0
af_packet              22088  4
ohci1394               34884  0
ieee1394              108408  1 ohci1394
yenta_socket           20992  1
pcmcia_core            68404  3 orinoco_cs,ds,yenta_socket
3c59x                  38728  0
snd_intel8x0m          19656  0
snd_intel8x0           35468  0
snd_ac97_codec         67844  2 snd_intel8x0m,snd_intel8x0
snd_pcm_oss            52968  0
snd_mixer_oss          19456  1 snd_pcm_oss
snd_pcm                95140  3 snd_intel8x0m,snd_intel8x0,snd_pcm_oss
snd_timer              24900  1 snd_pcm
snd_page_alloc         11432  3 snd_intel8x0m,snd_intel8x0,snd_pcm
gameport                4608  1 snd_intel8x0
snd_mpu401_uart         7776  1 snd_intel8x0
snd_rawmidi            24704  1 snd_mpu401_uart
snd_seq_device          8040  1 snd_rawmidi
snd                    55300  10 snd_intel8x0m,snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_mpu401_uart,snd_rawmidi,snd_seq_device
soundcore              10112  1 snd
hw_random               5364  0
usblp                  12832  0
uhci_hcd               31952  0
usbcore               115684  4 usblp,uhci_hcd
pci_hotplug            33680  0
intel_agp              22112  1
agpgart                33640  2 intel_agp
floppy                 59156  0
rtc                    12536  0
pcspkr                  3592  0
md                     48552  0
dm_mod                 57308  1
capability              4520  0
commoncap               7072  1 capability
nvidia               4821300  14
parport_pc             34752  1
lp                     10724  0
parport                40712  2 parport_pc,lp
ide_cd                 41572  0
cdrom                  39392  1 ide_cd
evdev                   9440  0
tsdev                   7232  0
mousedev               10220  1
psmouse                19720  0
reiserfs              240880  2
ext2                   69960  0
ext3                  123880  0
jbd                    60824  1 ext3
mbcache                 9092  2 ext2,ext3
ide_generic             1408  0
ide_disk               18752  5
piix                   13088  1
ide_core              136120  4 ide_cd,ide_generic,ide_disk,piix
unix                   28080  765
fan                     3980  0
thermal                12976  0
processor              17392  2 acpi,thermal
font                    8352  0
vesafb                  6560  0
cfbcopyarea             3712  1 vesafb
cfbimgblt               3072  1 vesafb
cfbfillrect             3616  1 vesafb
Thanks,Brian

---

### Post by triad169 on 2004-10-14
From your lsmod it does appear all your sound modules are loading for your sound card.  Try this at the terminal and let me know results.

```

amixer set Master 60 unmute
amixer set PCM 60 unmute

```

If no error try sound.  If error post results.  Also post results of

```
lspci
```

Triad

---

### Post by bpmckie on 2004-10-14
Hi,
Those didnt seem to work. Using the mixer commands I recieved the same error message. "amixer: Mixer attach default error: No such device.

Here is the output of the lspci:
bpmckie@ubuntu:~ $ lspci
0000:00:00.0 Host bridge: Intel Corp. 82845 845 (Brookdale) Chipset Host Bridge (rev 04)
0000:00:01.0 PCI bridge: Intel Corp. 82845 845 (Brookdale) Chipset AGP Bridge (rev 04)
0000:00:1d.0 USB Controller: Intel Corp. 82801CA/CAM USB (Hub #1) (rev 02)
0000:00:1d.2 USB Controller: Intel Corp. 82801CA/CAM USB (Hub #3) (rev 02)
0000:00:1e.0 PCI bridge: Intel Corp. 82801BAM/CAM PCI Bridge (rev 42)
0000:00:1f.0 ISA bridge: Intel Corp. 82801CAM ISA Bridge (LPC) (rev 02)
0000:00:1f.1 IDE interface: Intel Corp. 82801CAM IDE U100 (rev 02)
0000:00:1f.5 Multimedia audio controller: Intel Corp. 82801CA/CAM AC'97 Audio Controller (rev 02)
0000:00:1f.6 Modem: Intel Corp. 82801CA/CAM AC'97 Modem Controller (rev 02)
0000:01:00.0 VGA compatible controller: nVidia Corporation NV11 [GeForce2 Go] (rev b2)
0000:02:00.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 78)
0000:02:01.0 CardBus bridge: Texas Instruments PCI4451 PC card Cardbus Controller
0000:02:01.1 CardBus bridge: Texas Instruments PCI4451 PC card Cardbus Controller
0000:02:01.2 FireWire (IEEE 1394): Texas Instruments PCI4451 IEEE-1394 Controller
0000:02:03.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 01)
bpmckie@ubuntu:~ $

Thanks again for all your help.
Brian

---

### Post by triad169 on 2004-10-14
Aftyer doing some research I have come to the conclusion that it's a kernel issue either related to acpi or that your soundcard  IRQ is conflicting with another device (usually the Printer Port on Dell Laptops).

Lets try disabling acpi for pci.  You can do this by passing a kernel command at boot-up.  

Restart Your Computer.
When Grub Screen Appears.  Select your Ubuntu System.  The hit the *e* key

This will bring up a way to customize boot options for that selected kernel (Grub gives good on screen directions on what to do).  No go down and select the line that has the kernel parameters on it.  Mine looks like this:

```
kernel          /boot/vmlinuz-2.6.8.1-3-386 root=/dev/hda1 ro quiet splash
```

add *pci=noacpi * so line should look like this:

```
kernel          /boot/vmlinuz-2.6.8.1-3-386 root=/dev/hda1 pci=noacpi ro quiet splash
```

Now boot up.  Check if your sound works.  pass the amixer commands from above to the terminal. etc. If it does you will need to enter this entry permenantly to menu.1st.  just open terminal and type:

```
nano -w /boot/grub/menu.lst
```

and change line to match above.  save changes and reboot.

Triad

---

### Post by bpmckie on 2004-10-14
Cool!!!!

Thank you so much. That did the trick. Edited the grub menu and rebooted and voila, Sound. :D 

Thanks again
Brian

---

### Post by butters on 2004-10-20
I'm having the same problem...

Why do I have to disable ACPI?  I have used tens of different kernels based on 2.6.8.1 and 2.6.9_rc[1,2,3,4] with no problems with ACPI routing IRQs for the PCI bus controller.  The problem is that the kernel is assigning the RAMDISK driver IRQ 7, and then when the Intel ICH requests an IRQ, it tries to get IRQ 7 and fails.  

I'm sorry, this is definitely a bug in ubuntu's kernel patchset.

---

### Post by triad169 on 2004-10-20
[quote=triad169]can you open up a terminal and type:

```
lsmod
```

and paste results up here.  

Triad

As a side note Ubuntu should have setup this card automatically for you.  I would post a Bug to them at this url:

[http://bugzilla.ubuntu.com/](http://bugzilla.ubuntu.com/)[/quote]

This was suggested in earlier in this thread.  Yes it is a bug and shouldnt have been a problem.  and it isnt Totally native to Ubuntu because I found fix in Gentoo Forums.  There seems to be a specific set of variables that are required for this to happen usually involving conflicting IRQs and weather you have device compiled into kernel or as module will effect.  Or if you use Alsa with OSS emulation, etc. Do a seach on Google and you will see what I mean with the 2.6.8.1 kernel.  

Triad

---

### Post by abaete on 2004-10-20
Hi! Same problem. This is lspci

0000:00:00.0 Host bridge: VIA Technologies, Inc. VT82C598 [Apollo MVP3] (rev 04)
0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT82C598/694x [Apollo MVP3/Pro133x AGP]
0000:00:07.0 ISA bridge: VIA Technologies, Inc. VT82C586/A/B PCI-to-ISA [Apollo VP] (rev 47)
0000:00:07.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
0000:00:07.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 02)
0000:00:07.3 PCI bridge: VIA Technologies, Inc. VT82C586B ACPI (rev 10)
0000:00:08.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
0000:00:09.0 VGA compatible controller: Silicon Integrated Systems [SiS] 86C326 5598/6326 (rev 0b)
0000:00:0a.0 Modem: PCTel Inc HSP MicroModem 56 (rev 02)


and this is LSMOD

Module                  Size  Used by
isofs                  33976  0
af_packet              20872  2
pppoe                  13632  2
pppox                   3848  1 pppoe
ppp_generic            27668  6 pppoe,pppox
slhc                    7040  1 ppp_generic
proc_intf               3968  0
cpufreq_powersave       2048  0
cpufreq_userspace       5336  0
freq_table              4356  0
ipv6                  230020  10
8139cp                 19072  0
8139too                23936  0
mii                     4864  2 8139cp,8139too
crc32                   4608  2 8139cp,8139too
usblp                  12032  0
uhci_hcd               29328  0
usbcore               104292  4 usblp,uhci_hcd
pci_hotplug            30640  0
via_agp                 8832  1
agpgart                31784  1 via_agp
ns558                   5760  0
gameport                4736  1 ns558
floppy                 54996  0
pcspkr                  3816  0
rtc                    12216  0
md                     44744  0
dm_mod                 51068  1
capability              4872  0
commoncap               7168  1 capability
parport_pc             32064  1
lp                     10436  0
parport                37320  2 parport_pc,lp
evdev                   9088  0
tsdev                   7168  0
ide_cd                 38276  0
cdrom                  35872  1 ide_cd
mousedev               10124  1
psmouse                17800  0
reiserfs              207600  1
ide_generic             1664  0
ide_disk               16768  4
via82cxxx              13084  1
ide_core              125272  4 ide_cd,ide_generic,ide_disk,via82cxxx
unix                   25904  716
font                    8576  0
vesafb                  6688  0
cfbcopyarea             3968  1 vesafb
cfbimgblt               3200  1 vesafb
cfbfillrect             3712  1 vesafb


Hope u can help.

---

### Post by K6-III on 2004-10-21
Go the terminal.

Type "alsamixer" without the "".

Use that to manually raise your volume.  Worked for me...

---

### Post by butters on 2004-10-21
Triad - My fellow Gentoo user, what do I need to configure different in my kernel to get a reasonable kernel (such as 2.6.9-ck1) to work with Ubuntu?  I know Ubuntu uses an initrd for booting, do I just enable ramdisk and initrd support and point it to the same initrd image that it uses now?  Is there a make target for the initrd image (make &amp;&amp; make modules_install &amp;&amp; make initrd)?

Just browsed the config file left in the /boot directory.  Seems as if the ramdisk and initrd support options are part of the parallel IDE drivers like you mentioned before.  This kernel is so huge coming from Gentoo.  I've got to roll my own here.  Just need to figure out the whole initrd thing.

---

### Post by abaete on 2004-10-21
Hi,

the alsamixer doens't work. Sound card is not detected. When I click sound properties (on the speaker icon in meni bar), it says no sound mixer was found.......

Despite of this problem, I really loved the distro!!!

---

### Post by butters on 2004-10-21
Fixed the problem the right way (but you're not gunna like it):

This is not a problem with Ubuntu per se.  It is a problem with the default kernel configuration.  Both ALSA and OSS are enabled, all as modules, and this conflict with IRQ requests from the BLK_DEV_RAM module.  Basically, if you've got the wrong hardware, this kernel is not gunna give you much love.  I followed the following steps:

download linux-2.6.9 source tree from kernel.org
extract linux in /usr/src
ln -s linux-2.6.9 linux
download patch-2.6.9-ck1 from [http://members.optusnet.com.au/ckolivas/kernel/](http://members.optusnet.com.au/ckolivas/kernel/)
save in /usr/src/patches
in /usr/src/linux, execute
bzcat ../patches/patch-2.6.9-ck1.bz2 | patch -p1
make mrproper
make defconfig
make menuconfig
&lt;configure kernel, suck it down&gt;
I disabled ramdisk and initrd, because I don't like them
make &amp;&amp; make modules_install
cp arch/i386/boot/bzImage /boot/custom-2.6.9-ck1
nano -w /boot/grub/menu.lst
copy current boot section, removing the initrd line and replaing the kernel image to point to /custom-2.6.9-ck1
If you have two network interfaces, such as a wireless chipset, you may need to edit /etc/network/interfaces since eth0 and eth1 are flipped
also remove any modules no longer in your kernel from /etc/modules
reboot

oila!! with a REAL kernel, your sound and wireless chipsets will work as advertised, and your computer will rock a little more.

---

### Post by erpaco on 2004-10-27
Hello, I have the same problem with a card VIA VT8233A. Me does not this function:
```
kernel          /boot/vmlinuz-2.6.8.1-3-386 root=/dev/hda1 pci=noacpi ro quiet splash
``` 

My lspci:
```

0000:00:00.0 Host bridge: VIA Technologies, Inc. VT8366/A/7 [Apollo KT266/A/333]
0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT8366/A/7 [Apollo KT266/A/333 AGP]
0000:00:0b.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
0000:00:0c.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
0000:00:11.0 ISA bridge: VIA Technologies, Inc. VT8233A ISA Bridge
0000:00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
0000:00:11.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 23)
0000:00:11.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 23)
0000:00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 40)
0000:01:00.0 VGA compatible controller: nVidia Corporation NV11 [GeForce2 MX/MX 400] (rev b2)

```

my lsmod
```

Module                  Size  Used by
proc_intf               3968  0
freq_table              4356  0
cpufreq_userspace       5336  0
cpufreq_powersave       2048  0
button                  6936  0
ac                      5132  0
battery                 9740  0
ipv6                  230020  8
snd_via82xx            26660  3
snd_ac97_codec         59268  1 snd_via82xx
snd_pcm_oss            48168  0
snd_mixer_oss          16640  3 snd_pcm_oss
snd_pcm                85540  2 snd_via82xx,snd_pcm_oss
snd_timer              23172  1 snd_pcm
snd_page_alloc         11144  2 snd_via82xx,snd_pcm
snd_mpu401_uart         7296  1 snd_via82xx
snd_rawmidi            23232  1 snd_mpu401_uart
snd_seq_device          7944  1 snd_rawmidi
snd                    50660  11 snd_via82xx,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_mpu401_uart,snd_rawmidi,snd_seq_device
soundcore               9824  3 snd
uhci_hcd               29328  0
usbcore               104292  3 uhci_hcd
via_ircc               20368  0
irda                  167360  1 via_ircc
crc_ccitt               2432  1 irda
8139too                23936  0
8139cp                 19072  0
mii                     4864  2 8139too,8139cp
crc32                   4608  2 8139too,8139cp
pci_hotplug            30640  0
via_agp                 8832  1
agpgart                31784  1 via_agp
analog                 10784  0
gameport                4736  2 snd_via82xx,analog
floppy                 54996  0
pcspkr                  3816  0
rtc                    12216  0
md                     44744  0
dm_mod                 51068  1
capability              4872  0
commoncap               7168  1 capability
parport_pc             32064  1
lp                     10436  0
parport                37320  2 parport_pc,lp
ide_cd                 38276  0
tsdev                   7168  0
cdrom                  35872  1 ide_cd
evdev                   9088  0
mousedev               10124  1
psmouse                17800  0
ext3                  109544  1
jbd                    54552  1 ext3
ide_generic             1664  0
via82cxxx              13084  1
ide_disk               16768  4
ide_core              125272  4 ide_cd,ide_generic,via82cxxx,ide_disk
unix                   25904  686
fan                     4236  0
thermal                13200  0
processor              17712  1 thermal
font                    8576  0
vesafb                  6688  0
cfbcopyarea             3968  1 vesafb
cfbimgblt               3200  1 vesafb
cfbfillrect             3712  1 vesafb

```


Thanks by the aid and to forgive my english.

---

### Post by theBlackDragon on 2004-10-28
[QUOTE=triad169]Aftyer doing some research I have come to the conclusion that it's a kernel issue either related to acpi or that your soundcard  IRQ is conflicting with another device (usually the Printer Port on Dell Laptops).

Lets try disabling acpi for pci.  You can do this by passing a kernel command at boot-up.  

Restart Your Computer.
When Grub Screen Appears.  Select your Ubuntu System.  The hit the *e* key

This will bring up a way to customize boot options for that selected kernel (Grub gives good on screen directions on what to do).  No go down and select the line that has the kernel parameters on it.  Mine looks like this:

```
kernel          /boot/vmlinuz-2.6.8.1-3-386 root=/dev/hda1 ro quiet splash
```

add *pci=noacpi * so line should look like this:

```
kernel          /boot/vmlinuz-2.6.8.1-3-386 root=/dev/hda1 pci=noacpi ro quiet splash
```

Now boot up.  Check if your sound works.  pass the amixer commands from above to the terminal. etc. If it does you will need to enter this entry permenantly to menu.1st.  just open terminal and type:

```
nano -w /boot/grub/menu.lst
```

and change line to match above.  save changes and reboot.

Triad[/QUOTE]


I tried the above and now Ubuntu hands on "Starting PCMCIA services..." :(

Any ideas?

---

### Post by FSWolf on 2007-10-20
hi im having the same problem as the rest of these people i have a sound card 
it didnt !!
i just started u p one day after install and no sound. 

any way 
im running a dell dimention 4100 desk top 
i did lsmod

heres what i got
binfmt_misc            12680  1 
rfcomm                 40856  0 
l2cap                  25856  5 rfcomm
bluetooth              55908  4 rfcomm,l2cap
ppdev                  10116  0 
speedstep_lib           6148  0 
cpufreq_stats           7360  0 
cpufreq_powersave       2688  0 
cpufreq_ondemand        9228  0 
freq_table              5792  2 cpufreq_stats,cpufreq_ondemand
cpufreq_userspace       5408  0 
cpufreq_conservative     8200  0 
sony_acpi               6284  0 
tc1100_wmi              8068  0 
pcc_acpi               13184  0 
dev_acpi               12292  0 
video                  16388  0 
button                  8720  0 
sbs                    15652  0 
ac                      6020  0 
i2c_ec                  6016  1 sbs
asus_acpi              17308  0 
battery                10756  0 
ipt_TCPMSS              4992  1 
xt_tcpmss               3200  1 
xt_tcpudp               4224  1 
container               5248  0 
iptable_mangle          3712  1 
ip_tables              13796  1 iptable_mangle
x_tables               16388  4 ipt_TCPMSS,xt_tcpmss,xt_tcpudp,ip_tables
dock                   10268  0 
backlight               7040  1 asus_acpi
pppoe                  15424  2 
pppox                   4488  1 pppoe
ppp_generic            29076  6 pppoe,pppox
slhc                    7680  1 ppp_generic
ipv6                  268960  12 
lp                     12452  0 
fuse                   46612  0 
snd_emu10k1_synth       8192  0 
snd_emux_synth         35456  1 snd_emu10k1_synth
snd_seq_virmidi         7936  1 snd_emux_synth
snd_seq_midi_emul       7680  1 snd_emux_synth
snd_emu10k1           121248  1 snd_emu10k1_synth
snd_ac97_codec         98464  1 snd_emu10k1
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44544  0 
snd_mixer_oss          17408  1 snd_pcm_oss
snd_pcm                79876  3 snd_emu10k1,snd_ac97_codec,snd_pcm_oss
snd_page_alloc         10888  2 snd_emu10k1,snd_pcm
snd_util_mem            5760  2 snd_emux_synth,snd_emu10k1
snd_hwdep               9988  2 snd_emux_synth,snd_emu10k1
snd_seq_dummy           4740  0 
snd_seq_oss            32896  0 
snd_seq_midi            9600  0 
snd_rawmidi            25472  3 snd_seq_virmidi,snd_emu10k1,snd_seq_midi
snd_seq_midi_event      8448  3 snd_seq_virmidi,snd_seq_oss,snd_seq_midi
snd_seq                52592  9 snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
nvidia               4713780  22 
snd_timer              23684  3 snd_emu10k1,snd_pcm,snd_seq
snd_seq_device          9100  8 snd_emu10k1_synth,snd_emux_synth,snd_emu10k1,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
i2c_core               22656  2 i2c_ec,nvidia
emu10k1_gp              4736  0 
snd                    54020  13 snd_emux_synth,snd_seq_virmidi,snd_emu10k1,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8672  1 snd
parport_pc             36388  1 
parport                36936  3 ppdev,lp,parport_pc
gameport               16520  2 emu10k1_gp
pcspkr                  4224  0 
psmouse                38920  0 
serio_raw               7940  0 
intel_agp              26140  1 
agpgart                35400  2 nvidia,intel_agp
iTCO_wdt               11812  0 
iTCO_vendor_support     4868  1 iTCO_wdt
shpchp                 34324  0 
pci_hotplug            32576  1 shpchp
af_packet              23816  4 
tsdev                   8768  0 
evdev                  11008  3 
ext3                  133128  1 
jbd                    59816  1 ext3
mbcache                 9604  1 ext3
sg                     36252  0 
sr_mod                 17060  0 
cdrom                  37664  1 sr_mod
sd_mod                 23428  3 
floppy                 59524  0 
uhci_hcd               25360  0 
usbcore               134280  2 uhci_hcd
tulip                  53536  0 
ata_piix               15492  2 
ata_generic             9092  0 
libata                125720  2 ata_piix,ata_generic
scsi_mod              142348  4 sg,sr_mod,sd_mod,libata
generic                 5124  0 [permanent]
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

can some one please help :(

---

