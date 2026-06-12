---
title: "External HD on USB 3 via PCIe not auto loading at startup"
date: 2015-06-29
forum: General Help
---

### Post by Robbyx on 2015-06-29
My MB and CPU predate USB 3. 

There comes a point in the startup of the operating system that it stops because it can find the external HD's listed in the fstab. At that point I pull out the power to the hd and replace it. Ubuntu recognises the drive and loads it. Here is the output from dmseg -n 35 at the  halt point . It was obtained via the manual drive load option. There are a few error messages. Can you please suggest what I can do to clear them?


[   24.562320] input: HDA Intel Line Out Front as /devices/pci0000:00/0000:00:1b.0/sound/card0/input12
[   24.562409] input: HDA Intel Line Out Surround as /devices/pci0000:00/0000:00:1b.0/sound/card0/input13
[   24.563405] input: HDA Intel Line Out CLFE as /devices/pci0000:00/0000:00:1b.0/sound/card0/input14
[   24.563584] input: HDA Intel Line Out Side as /devices/pci0000:00/0000:00:1b.0/sound/card0/input15
[   24.626578] ACPI Warning: SystemIO range 0x00000428-0x0000042f conflicts with OpRegion 0x0000042c-0x0000042d (\GP2C) (20140424/utaddress-258)
[   24.626585] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   24.626639] lpc_ich: Resource conflict(s) found affecting gpio_ich
[   24.644166] WARNING! power/level is deprecated; use power/control instead
[   24.679707] nvidia: module license 'NVIDIA' taints kernel.
[   24.679711] Disabling lock debugging due to kernel taint
[   24.731814] nvidia: module verification failed: signature and/or  required key missing - tainting kernel
[   24.738615] scsi 11:0:0:0: Direct-Access     SanDisk  Cruzer Switch    1.26 PQ: 0 ANSI: 5
[   24.777909] sd 11:0:0:0: Attached scsi generic sg4 type 0
[   24.778553] sd 11:0:0:0: [sdd] 125031680 512-byte logical blocks: (64.0 GB/59.6 GiB)
[   24.780194] sd 11:0:0:0: [sdd] Write Protect is off
[   24.780198] sd 11:0:0:0: [sdd] Mode Sense: 43 00 00 00
[   24.781226] sd 11:0:0:0: [sdd] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[   24.795140]  sdd: sdd1 sdd2
[   24.800544] sd 11:0:0:0: [sdd] Attached SCSI removable disk
[   24.804369] media: Linux media interface: v0.10
[   24.815686] Linux video capture interface: v2.00
[   24.828955] cdc_acm 1-3.1.1:1.1: This device cannot do calls on its own. It is not a modem.
[   24.829058] cdc_acm 1-3.1.1:1.1: ttyACM0: USB ACM device
[   24.832986] usbcore: registered new interface driver cdc_acm
[   24.832988] cdc_acm: USB Abstract Control Model driver for USB modems and ISDN adapters
[   24.851734] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=none
[   24.858894] [drm] Initialized nvidia-drm 0.0.0 20140818 for 0000:01:00.0 on minor 0
[   24.858905] NVRM: loading NVIDIA UNIX x86 Kernel Module  304.125  Mon Dec  1 19:55:52 PST 2014
[   25.109825] gpio_ich: GPIO from 195 to 255 on gpio_ich
[   25.155638] usb 1-3.3: Warning! Unlikely big volume range (=3072), cval->res is probably wrong.
[   25.155642] usb 1-3.3: [5] FU [Mic Capture Volume] ch = 1, val = 4608/7680/1
[   25.156172] usbcore: registered new interface driver snd-usb-audio
[   25.157033] uvcvideo: Found UVC 1.00 device <unnamed> (046d:0990)
[   25.172801] input: UVC Camera (046d:0990) as /devices/pci0000:00/0000:00:1a.7/usb1/1-3/1-3.3/1-3.3:1.0/input/input16
[   25.172971] usbcore: registered new interface driver uvcvideo
[   25.172973] USB Video Class driver (1.1.1)
[   25.754387] usblp 1-3.4:1.0: usblp2: USB Bidirectional printer dev 8 if 0 alt 0 proto 2 vid 0x04F9 pid 0x01B7
[   25.754441] usbcore: registered new interface driver usblp
[   42.249803] init: mountall main process (217) terminated with status 2
[   42.292168] init: plymouth-upstart-bridge main process ended, respawning

---

### Post by v3.xx on 2015-06-29
I haven't used it in a while, think it still works.

["pysdm" ]("http://www.howtogeek.com/60817/how-to-auto-mount-partitions-at-linux-startup-the-easy-way/")

---

### Post by Robbyx on 2015-06-29
I am having trouble finding it. Not in synaptic. This gives me the oportunity to ask if you think it will deal with my problem because fstab is calling the correct drive and setting it up only after I remove the power from the HD and reapply it. Does that indicate  an fstab problem.

There were other problems in the dmseg output. Were there any that you can  comment on? 

R

---

### Post by v3.xx on 2015-06-29
I'm not much at dmseg, but I wonder if dkms would help with the kernel and your driver.  Do you have dkms installed?

And your right, pysdm is gone.  How sad, it just made fstab so simple.

Have you plugged your drive in the back of your computer?

---

### Post by Robbyx on 2015-06-29
> **v3.xx said:**
> I'm not much at dmseg, but I wonder if dkms would help with the kernel and your driver.  Do you have dkms installed?

And your right, pysdm is gone.  How sad, it just made fstab so simple.

Have you plugged your drive in the back of your computer?

I have dkms installed.

yes, but what that means is that it is in a pcie socket.

I have this set up for 7 years and I decided that  I should change the motherboard, cpu and memory. I have been having some other problems and I thought it was time for a change. Hopefully those problems will disappear with the new equipment.

Do you know if I have to do a new install when switching from intel 386 to an amd A10-7800. If I do I assume there is only disadvantages in switching from 32 to 64 as the big disadvantage of 32 is covered in Ubuntu so that more than 4gb can be accessed (despite what is suggested on the download page for gnome). 

R

---

