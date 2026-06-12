---
title: "Powering on an external USB drive remotely"
date: 2018-10-17
forum: General Help
---

### Post by bomberb17 on 2018-10-17
I have an external USB hard drive on my Ubuntu 18.04 LTS. I am remotely  managing the system with Teamviewer (I have ssh access as well). I want  to remotely power down my hard drive and then power it on again when I  need it. I powered it down using the button in "Disks". However this way it  disappears and I can't find a way to power it back on. I tried running udevadm trigger but it didn't come up. Only way I've found to power it up again is by rebooting. So is there a way to power it back on remotely?

---

### Post by TheFu on 2018-10-18
Just a thought ... if you put the USB device on a "clapper" power controller, then remote in and play the sound of hands clapping twice it will power on the USB power and startup the disk?
[https://www.youtube.com/watch?v=Ny8-G8EoWOw](https://www.youtube.com/watch?v=Ny8-G8EoWOw)

There might be other methods that can be controlled using IoT stuff, but I'm not a fan of allowing internet access to IoT devices. Too many security risks.

---

### Post by bomberb17 on 2018-10-18
> **bomberb17 said:**
> I want  to _**remotely**_ power down my hard drive and then power it on again when I  need it. 

????
How are you supposed to clap remotely?
Hope I get some real help.

---

### Post by TheFu on 2018-10-18
> **bomberb17 said:**
> ????
How are you supposed to clap remotely?
Hope I get some real help.

Play an audio file.  I'm 100% positive that this works.  I use it all the time over ssh with **cmus**.

I was being 100% serious about the solution.

---

### Post by bomberb17 on 2018-10-18
Ok so this is in a work environment, I cannot leave the speakers on and clap loudly every so on. Also using a smart plug could do the same without clapping etc.
I am not looking at such solutions. I want to do this in a clean way using SSH and/or teamviewer (and without rebooting).

---

### Post by TheFu on 2018-10-18
If the USB device is powering down, I don't know any method beside a physical action either with the power or USB plug to bring it back. Sorry. Some devices just require a power cycle to come back online.

BTW, I have a cheap 4-disk array that works similarly.  Once powered off, NOTHING can bring it back short of physically pushing a logical button. The button isn't a normal on/off with different switch positions. It is a toggle and at boot from a power-loss, always in the off position.  The clapper didn't work.  But for other external disk devices I don't have this issue and my more expensive disk arrays definitely do not.

Just brainstorming here, but have you looked at how hibernation/standby wake code works?  Perhaps that could be used for this device?

Maybe someone else will be able to help.

---

### Post by bomberb17 on 2018-10-18
Rebooting the PC powers on the disk again. During the reboot process there must be some sort of "USB scan" command that powers it on again. 
I am looking for that command. I tried ```
udevadm trigger
``` which is supposed to do something like this (although I've seen this work for older ubuntu versions) but it had no effect.

---

### Post by TheFu on 2018-10-19
I should have asked this sooner ...
* did the disk power on/off the way you intended with 16.04?
* if you power it off using hdparm, not "gnome-disks", can you power it back up using hdparm?  Instead of completely powering down, what about letting the disk spin down?```

       -B     Get/set Advanced Power Management feature, if the drive supports
              it.  A  low  value  means aggressive power management and a high
              value means better performance.  Possible  settings  range  from
              values  1  through  127 (which permit spin-down), and values 128
              through 254 (which do not permit spin-down).  The highest degree
              of  power  management  is  attained with a setting of 1, and the
              highest I/O performance with a setting of 254.  A value  of  255
              tells  hdparm to disable Advanced Power Management altogether on
              the drive (not all drives support disabling it, but most do).
       --idle-immediate
              Issue  an  ATA  IDLE_IMMEDIATE  command, to put the drive into a
              lower power state.  Usually the device remains spun-up.

```
Check out the -s and -S options.  Might be worth putting some into the hdparm.conf file.
There are specific commands for specific models of drives too.  

Back to some other thoughts ... 

Is the disk only powered via USB or is there an external power supply?  Does the device has a power switch/button with 2 positions?

Is there a vendor and model for the disk, enclosure, that might help someone be more helpful?  Different controllers will have different capabilities and behaviors.

Manually mounted and umount the disk could might leave things in a different way than letting the system automatic GVFS mount handle it. Plus, gvfs is slow for transfers when compared to real mounts.

Not that it will help you, but I decided long ago that leaving spinning disks spinning was better for the disks life than powering them up and down.  Everyone needs to decide if this is a good idea or not based on their specific use-case.

---

### Post by bomberb17 on 2018-10-20
I powered it down through the "Disks" utility. (there is a power button on the top of the disk window".
I am using 18.04, not 16.04. I am not on-site to try the hdparm option, but I will try it on Monday. Letting it spin down without actually powering off the entire disk sounds a reasonable idea.
About the other thoughts/questions:
It is a 3.5" disk powered through external power supply (its on [this]("https://www.amazon.com/ORICO-External-Docking-Station-Support/dp/B012V5MSGK/ref=sr_1_7?s=electronics&ie=UTF8&qid=1540047057&sr=1-7&keywords=orico+external+hard+drive+docking+station") docking station)
Unmounting the disk does not seem to have any effect on its power state, it stays spinning.
I know that spin-ups degrade a disk's life (in a similar manner to working hours). However in my case I would only need to use the drive maybe once or twice per month, there is no point for letting the drive spinning for all that time.

---

### Post by sp40140 on 2018-10-20
Out of curiosity, why do you need to / want to power off the drive?

---

### Post by QIII on 2018-10-20
I believe the user's last sentence in his post above yours goes a long way towards explaining the "why".

In any case, let's concentrate on the "how" here rather than the "why".

Thanks.

---

### Post by bomberb17 on 2018-10-21
> **QIII said:**
> I believe the user's last sentence in his post above yours goes a long way towards explaining the "why".

In any case, let's concentrate on the "how" here rather than the "why".

Thanks.

+1 Thanks

---

### Post by sp40140 on 2018-10-21
I know someone who uses raspberry pi zero to manage few light/fan fixtures in his home.
May be that is something you can look into. Pi zero costs $5. Just an idea.

---

### Post by bomberb17 on 2018-10-21
As I said in my previous message
> **bomberb17 said:**
> ... 
Also using a smart  plug could do the same without clapping etc.
I am not looking at such solutions. I want to do this in a clean way  using SSH and/or teamviewer (and without rebooting).

---

### Post by HermanAB on 2018-10-22
For a reliable solution, put a relay in the computer:
[https://numato.com/product/2-channel-usb-solid-state-relay-module](https://numato.com/product/2-channel-usb-solid-state-relay-module)

You can also look at the list of device drivers with lsmod, then unload and reload the USB driver with rmmod and modprobe.  That would be equivalent to rebooting the machine.

---

### Post by bomberb17 on 2018-10-23
Ok I tried hdparm, but it seems my external HD dock does not support it
```
~$ sudo hdparm -B 1 /dev/sdb

/dev/sdb:
 setting Advanced Power Management level to 0x01 (1)
 APM_level    = not supported
~$ sudo hdparm -S 1 /dev/sdb

/dev/sdb:
 setting standby to 1 (5 seconds)
SG_IO: bad/missing sense data, sb[]:  70 00 05 00 00 00 00 0a 00 00 00 00 20 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
```





> **HermanAB said:**
> For a reliable solution, put a relay in the computer:
[https://numato.com/product/2-channel-usb-solid-state-relay-module](https://numato.com/product/2-channel-usb-solid-state-relay-module)

You can also look at the list of device drivers with lsmod, then unload and reload the USB driver with rmmod and modprobe.  That would be equivalent to rebooting the machine.

As I said in my previous replies, I don't want such an "external" solution (no smart plugs, clapping plugs, relays etc).
Regarding lsmod, here is my output, but I can't tell which one is the USB driver... Can you help? Is it maybe the last one?

```
$ lsmod
Module                  Size  Used by
snd_hda_codec_hdmi     49152  1
intel_rapl             20480  0
x86_pkg_temp_thermal    16384  0
snd_hda_codec_realtek   106496  1
intel_powerclamp       16384  0
snd_hda_codec_generic    73728  1 snd_hda_codec_realtek
coretemp               16384  0
snd_hda_intel          40960  6
snd_hda_codec         126976  4 snd_hda_intel,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec_realtek
snd_hda_core           81920  5 snd_hda_intel,snd_hda_codec,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec_realtek
kvm_intel             212992  0
kvm                   598016  1 kvm_intel
irqbypass              16384  1 kvm
crct10dif_pclmul       16384  0
crc32_pclmul           16384  0
snd_hwdep              20480  1 snd_hda_codec
ghash_clmulni_intel    16384  0
pcbc                   16384  0
snd_pcm                98304  4 snd_hda_intel,snd_hda_codec,snd_hda_core,snd_hda_codec_hdmi
aesni_intel           188416  0
dcdbas                 16384  0
aes_x86_64             20480  1 aesni_intel
input_leds             16384  0
crypto_simd            16384  1 aesni_intel
glue_helper            16384  1 aesni_intel
snd_seq_midi           16384  0
snd_seq_midi_event     16384  1 snd_seq_midi
snd_rawmidi            32768  1 snd_seq_midi
snd_seq                65536  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              32768  2 snd_seq,snd_pcm
cryptd                 24576  3 crypto_simd,ghash_clmulni_intel,aesni_intel
intel_cstate           20480  0
dell_wmi               16384  0
intel_rapl_perf        16384  0
snd                    81920  23 snd_hda_intel,snd_hwdep,snd_seq,snd_hda_codec,snd_timer,snd_rawmidi,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_seq_device,snd_hda_codec_realtek,snd_pcm
sparse_keymap          16384  1 dell_wmi
dell_smbios_wmi        16384  0
dell_smbios            16384  2 dell_wmi,dell_smbios_wmi
serio_raw              16384  0
mei_me                 40960  0
mac_hid                16384  0
soundcore              16384  1 snd
wmi_bmof               16384  0
dell_wmi_descriptor    16384  2 dell_wmi,dell_smbios_wmi
shpchp                 36864  0
mei                    90112  1 mei_me
acpi_pad              180224  0
sch_fq_codel           20480  2
parport_pc             36864  0
ppdev                  20480  0
lp                     20480  0
parport                49152  3 lp,parport_pc,ppdev
ip_tables              28672  0
x_tables               40960  1 ip_tables
autofs4                40960  2
hid_generic            16384  0
usbhid                 49152  2
hid                   118784  2 hid_generic,usbhid
i915                 1617920  24
i2c_algo_bit           16384  1 i915
drm_kms_helper        172032  1 i915
syscopyarea            16384  1 drm_kms_helper
e1000e                249856  0
sysfillrect            16384  1 drm_kms_helper
sysimgblt              16384  1 drm_kms_helper
fb_sys_fops            16384  1 drm_kms_helper
ptp                    20480  1 e1000e
psmouse               147456  0
drm                   401408  16 i915,drm_kms_helper
ahci                   36864  1
pps_core               20480  1 ptp
libahci                32768  1 ahci
wmi                    24576  4 dell_wmi,wmi_bmof,dell_wmi_descriptor,dell_smbios_wmi
video                  45056  2 dell_wmi,i915
uas                    24576  0
usb_storage            69632  1 uas

```

---

### Post by HermanAB on 2018-10-24
Yup, looks like this one: usb_storage            69632  1 uas

So, I would try something like this:
# rmmod usb_storage; sleep 5; modprobe usb_storage

and see what happens.  

It may work - or not - since it only resets the host device driver and doesn't reset the disk drive itself, since it remains powered up.  Maybe you are lucky!

---

### Post by bomberb17 on 2018-10-25
Hmm I did
```
$ sudo rmmod usb_storage
rmmod: ERROR: Module usb_storage is in use by: uas
```

So I did rmmod uas first then usb_storage, then waited and ran modprobe again. They appeared again in lsmod, but the disk does not spin up..

---

### Post by HermanAB on 2018-10-25
Then, I guess your only solution is a solid state relay to cycle power on the device.

---

### Post by bomberb17 on 2018-10-25
Still there must be away somehow it can be done. Relays/swtiches or physically unplugging and replugging the HDD USB dock are "physical" solutions.
A "non-physical" solution (i.e. without some external action, I don't know if this is the correct term for it!) is rebooting. There must be a way to "simulate" a reboot for this purpose..

---

### Post by HermanAB on 2018-10-26
As usual, 'it depends'.  Some things, once turned off, cannot be turned on again with a software command, since the microcontroller isn't running anymore. Those type of things will only restart with a power cycle reboot.

---

### Post by bomberb17 on 2018-10-26
But is a reboot considered a power cycle? Essentially the computer is remained powered on during the reboot process, it just reloads the OS. On the the other hand, the moment the BIOS screen pops up, the disk spins again and the fans work at full speed for a brief moment. I don't know, you may be right and this can only be done with a ('soft'?) power cycle..

---

### Post by him610 on 2018-10-27
You might consider one of those IOT wall plugs that can be powered on/off through the LAN or from your smart phone. Here is one here => [https://www.amazon.com/WeMo-Switch-Smart-Works-Alexa/dp/B00BB2MMNE]("https://www.amazon.com/WeMo-Switch-Smart-Works-Alexa/dp/B00BB2MMNE")

---

