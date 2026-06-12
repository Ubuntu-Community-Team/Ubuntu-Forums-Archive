---
title: "Bash script"
date: 2015-08-18
forum: General Help
---

### Post by Robbyx on 2015-08-18
I am having a lot of trouble with the official way to put Ubuntu 14.04 into hibernate. I find that I can not close down the computer and  the network dies on me. I am trying to find a different way round the hibernate problem. 

 I would like to stick a bash script into the status bar.

"sudo pm-hibernate" is all that I seem to need to close down my computer. Entered into terminal this gives none of the problems.

Am I on the right path with the following ideas?


I found this in an earlier question and have amended it with the code I want.

#include <stdlib.h>

on_button1_clicked            (GtkButton       *button,
                                        gpointer         user_data)
{
  #  system("/home/user/bin/burnit pics");
sudo pm-hibernate
}


Kdocker looks like it might be what I need. The description states: All you need to do is start KDocker and select an application using the mouse and lo! the application gets docked into the system tray. The application can also be made to dissappear from the task bar.

How do I make the bash code appear as an application so that it can be picked up by KDocker? Also how do give the bash script an icon to be used by KDocker?

---

### Post by TheFu on 2015-08-18
If you are trying to write in C, that is not a valid C program.
I doubt you really need C. A shell script can do it.
```

#!/bin/sh
sudo /full/path/to/pm-hibernate
```

pm-hibernate isn't on my systems, so I don't know the path to use.

Then make the file executable and all should be ok - provided sudo -access is already unlocked. Might need to use the GUI version of sudo to get a popup prompt, if needed - I dunno.

---

### Post by Robbyx on 2015-08-18
I have the bash script working but I am struggling to get it into a dock. The file is in my home directory and is called hibernate. 

 I tried alltray but it wants me to click on the window, but which window? Kdocker complains it can not grab the mouse. Any ideas how to proceed?

---

### Post by tgalati4 on 2015-08-19
Let's treat the problem differently.  Install *acpitool* and list the devices that have power during sleep.

Open a terminal:

```
sudo apt-get install acpitool
acpitool -w
```

Leave power to the network card during sleep so it will wake up properly:

```
acpitool -W 5
```

The number you choose is the PCI slot number that your network card hangs off of.

---

### Post by Robbyx on 2015-08-19
I have started with your alt method but the following does not make a lot of sence to me in the context of which slot is the network card

> robins@robins-desktop:~$ acpitool -w
   Device	S-state	  Status   Sysfs node
  ---------------------------------------
  1. PB21	  S4	*disabled
  2. PB22	  S4	*disabled
  3. PB31	  S4	*disabled
  4. PB32	  S4	*disabled
  5. PB33	  S4	*disabled
  6. PB34	  S4	*disabled
  7. SBAZ	  S4	*disabled  pci:0000:00:14.2
  8. PS2K	  S4	*disabled
  9. PS2M	  S4	*disabled
  10. UAR1	  S4	*disabled  pnp:00:07
  11. P0PC	  S4	*disabled  pci:0000:00:14.4
  12. OHC1	  S4	*enabled   pci:0000:00:12.0
  13. EHC1	  S4	*enabled   pci:0000:00:12.2
  14. OHC2	  S4	*enabled   pci:0000:00:13.0
  15. EHC2	  S4	*enabled   pci:0000:00:13.2
  16. OHC3	  S4	*disabled
  17. EHC3	  S4	*disabled
  18. OHC4	  S4	*enabled   pci:0000:00:14.5
  19. XHC0	  S4	*enabled   pci:0000:00:10.0
  20. XHC1	  S4	*enabled   pci:0000:00:10.1
  21. PE20	  S4	*disabled  pci:0000:00:15.0
  22. PE21	  S4	*disabled  pci:0000:00:15.1
  23. PE22	  S4	*disabled  pci:0000:00:15.2
  24. PE23	  S4	*disabled  pci:0000:00:15.3
robins@robins-desktop:~$ 


I had a look in the MB manual (Asrock FM2A88X extreme6+) to see how to invoke s4 sleep. No real guidance on actually invoking sleep.

Is there a shortcut to switch the machine to s4 sleep?

---

### Post by tgalati4 on 2015-08-19
S3 is Standby Sleep (RAM is powered, hard disks spin down, power light flashes slowly, CPU halts, network card is generally powered off).  This mode is usually invoked by hitting the sleep key Fn-F4 perhaps or a dedicated sleep key (1/2 moon, or "Zzz" key).  Hibernate Sleep, S4, can be activated with a special key (sometimes defined in BIOS--like Control-Alt-P), sometimes pushing the power button--also defined behavior is controlled in BIOS.  Through software using pm utilities.  Hibernate stores the RAM in a "snapshot" to your swap partition, then spins down the disk, halts the CPU, and powers down completely.  Including the network card.  Resuming from hibernate takes just about as long as cold boot, since the kernel has to read a 2GB or 4GB file and load it into RAM and that takes a long time with a spinning hard drive.

Your network card is visible with:

```
lspci
```

Write down the PCI slot number and match it up with the *acpitool* discovery.  The number you choose would be 1 to 24 depending on the exact slot that the network card lives in.  "Enable" means it has power while in S4 (hibernate) mode.  "Disable" means that it has no power when in S4 mode.

---

### Post by Robbyx on 2015-08-21
Which one is the pci slot no:
05:00.0 Ethernet controller [0200]: Qualcomm Atheros QCA8171 Gigabit Ethernet [1969:10a1] (rev 10)

lspci -t shows the following enabled 

  +-14.3
           +-14.4-[01]--
           +-14.5
           +-15.0-[02]--
           +-15.1-[03]----00.0
           +-15.2-[04]----00.0
           +-15.3-[05]----00.0

---

### Post by tgalati4 on 2015-08-21
For you it looks like slot 24.

Try:

```
sudo acpitool -W 24
acpitool
```

Put your machine into hibernation.  Then check the network lights on the router and on the back of the PC's network jack.  They should be flashing.  No lights means no power to the network card.

---

### Post by Robbyx on 2015-08-22
I put the computer into hibernation but when  I rebooted, although it came up with the state before the hibernation, the network connection was permanently off and the os would not close down without turning off the power.

---

### Post by tgalati4 on 2015-08-23
You might need to add your network module to the following file:  /etc/default/acpi-support

Put it in the whitelist so it gets reloaded when coming out of hibernation.

What network module are you running?

```
lsmod
```

---

### Post by Robbyx on 2015-08-23
```
Module                  Size  Used by
usblp                  22901  0 
pci_stub               12622  1 
vboxpci                23273  0 
vboxnetadp             25670  0 
vboxnetflt             27880  0 
vboxdrv               438241  3 vboxnetadp,vboxnetflt,vboxpci
uvcvideo               81073  0 
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
videobuf2_core         59104  1 uvcvideo
v4l2_common            15681  1 videobuf2_core
snd_usb_audio         161790  1 
videodev              153793  3 uvcvideo,v4l2_common,videobuf2_core
media                  21903  2 uvcvideo,videodev
snd_usbmidi_lib        29828  1 snd_usb_audio
rfcomm                 69509  12 
bnep                   19624  2 
binfmt_misc            17468  1 
joydev                 17393  0 
nls_iso8859_1          12713  3 
fglrx               12457916  201 
uas                    27255  0 
usb_storage            66545  8 uas
hid_generic            12559  0 
usbhid                 52616  1 
hid                   110426  2 hid_generic,usbhid
btusb                  32497  0 
bluetooth             446409  22 bnep,btusb,rfcomm
6lowpan_iphc           18702  1 bluetooth
snd_hda_codec_realtek    77561  1 
snd_hda_codec_generic    69011  1 snd_hda_codec_realtek
snd_hda_codec_hdmi     47548  1 
snd_hda_intel          30469  5 
kvm_amd                60328  0 
kvm                   452096  1 kvm_amd
snd_hda_controller     30228  1 snd_hda_intel
snd_hda_codec         139719  5 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_intel,snd_hda_controller
crct10dif_pclmul       14307  0 
snd_hwdep              17698  2 snd_usb_audio,snd_hda_codec
crc32_pclmul           13133  0 
ghash_clmulni_intel    13230  0 
aesni_intel           152552  1 
snd_pcm               104112  5 snd_usb_audio,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_controller
aes_x86_64             17131  1 aesni_intel
lrw                    13286  1 aesni_intel
gf128mul               14951  1 lrw
snd_seq_midi           13564  0 
glue_helper            13990  1 aesni_intel
ablk_helper            13597  1 aesni_intel
snd_seq_midi_event     14899  1 snd_seq_midi
cryptd                 20359  3 ghash_clmulni_intel,aesni_intel,ablk_helper
snd_rawmidi            30876  2 snd_usbmidi_lib,snd_seq_midi
serio_raw              13483  0 
snd_seq                63074  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
k10temp                13144  0 
edac_core              56549  0 
edac_mce_amd           22578  0 
snd_timer              29562  2 snd_pcm,snd_seq
snd                    79468  25 snd_hda_codec_realtek,snd_usb_audio,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_usbmidi_lib,snd_hda_codec,snd_hda_intel,snd_seq_device
shpchp                 37047  0 
i2c_piix4              22166  0 
soundcore              15047  2 snd,snd_hda_codec
amd_iommu_v2           18916  1 fglrx
parport_pc             32741  0 
ppdev                  17671  0 
video                  20128  0 
mac_hid                13227  0 
lp                     17759  0 
parport                42348  3 lp,ppdev,parport_pc
pata_acpi              13053  0 
psmouse               106767  0 
alx                    36817  0 
mdio                   13561  1 alx
ahci                   34142  0 
pata_atiixp            13279  5 
libahci                32424  1 ahci
```

---

### Post by Robbyx on 2015-08-29
> **tgalati4 said:**
> You might need to add your network module to the following file:  /etc/default/acpi-support

Put it in the whitelist so it gets reloaded when coming out of hibernation.

What network module are you running?

```
lsmod
```

Could you please look at the printout of lsmod and advise me which network module I am running.

---

### Post by tgalati4 on 2015-08-29
*alx* and *mdio* are the two modules loaded to drive your gigabit network card.  Put one or both in the /etc/default/acpi-support file and reboot.

> # Add modules to this list to leave them in the kernel over suspend/resume
MODULES_WHITELIST="alx"

or

> # Add modules to this list to leave them in the kernel over suspend/resume
MODULES_WHITELIST="alx, mdio"

---

### Post by Robbyx on 2015-08-29
I put through the adjustment to the whitelist of acpi-support. It does not seem to have made any difference. 

Upon rebooting after suspending the wired network connection  is showing it is not connected.

On a normal closedown  following a suspend restart, there is an error that shows the close down stops at the  modem manager.
The keyboard stops working at some stage and I had to do REISUB.

Power off even via the c/L does not close down unless there is a hard reboot.

R

---

