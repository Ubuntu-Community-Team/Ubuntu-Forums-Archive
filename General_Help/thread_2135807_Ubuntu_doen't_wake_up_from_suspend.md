---
title: "Ubuntu doen't wake up from suspend"
date: 2013-04-15
forum: General Help
---

### Post by refle on 2013-04-15
Hi I use Ubuntu 12.04 (64bit) on Acer Timeline TG3820.
Sometimes Ubuntu just doesnt wake up from suspend. But not always...
Any issues like that already known?
Thank you!

---

### Post by sp-1070 on 2013-04-15
[http://askubuntu.com/questions/147539/computer-wont-wake-from-suspend](http://askubuntu.com/questions/147539/computer-wont-wake-from-suspend)

This might help

---

### Post by refle on 2013-04-16
Thank you, but actually im not using a nvidia graphic card. 
I have the ATI [COLOR=#333333][FONT=Ubuntu Mono]Mobility Radeon HD 5400 Series and the original driver installed... [/FONT][/COLOR]

---

### Post by sp-1070 on 2013-04-16
[https://help.ubuntu.com/community/AspireTimeline](https://help.ubuntu.com/community/AspireTimeline)

---

### Post by p-dh on 2013-04-16
Before 12.04, I had to turn off USB legacy support in BIOS to get suspend to work. After upgrading to 12.04, I also ended up following the directions from this [post]("http://ubuntuforums.org/showpost.php?p=11905031&postcount=4") to get my (non-Asus) desktop working.
Hope this helps.

Paul :cool:

---

### Post by refle on 2013-05-01
Hi, unfortunately it doesnt seem to help. any other ideas?
i think it must be something with the graphics (although i have installed the proprietary driver)... because when i wake up from suspend the screen turns on to black, than off again, again on to black and then i can log in ... and sometimes it stays just off... this is so strange

---

### Post by refle on 2013-05-12
I think that my computer tries to load the graphics card when i wake it up but it seems not to work very well because:
the screen turns on (black) and then completely off, and again on (black) and completely off.. and not until then, i can load the start screen...
and sometimes it just stays off (the screen) although the cpu is running... any help please!

---

### Post by Toz on 2013-05-12
Are you using the radeon driver? The command will help identify the driver:
```
sudo lspci -vnn | grep -A12 VGA
```

Try suspending manually using the following command and quirks to see if it works:
```
sudo pm-suspend --quirk-s3-bios
```
```
sudo pm-suspend --quirk-s3-mode
```
```
sudo pm-suspend --quirk-s3-bios --quirk-s3-mode
```
```
sudo pm-suspend --quirk-vbe-post
```
```
sudo pm-suspend --quirk-vbestate-restore
```

More information from the pm-suspend man page:
```
man pm-suspend
```

You might also want to have a look at the /var/log/pm-suspend.log file for more information,

---

### Post by refle on 2013-05-12
Hi thank you!


My Graphics:
> 02:00.0 VGA compatible controller [0300]: Advanced Micro Devices [AMD] nee ATI Manhattan [Mobility Radeon HD 5400 Series] [1002:68e0] (prog-if 00 [VGA controller])    Subsystem: Acer Incorporated [ALI] Device [1025:0364]
    Flags: bus master, fast devsel, latency 0, IRQ 46
    Memory at d0000000 (64-bit, prefetchable) [size=256M]
    Memory at cfee0000 (64-bit, non-prefetchable) [size=128K]
    I/O ports at 2000 [size=256]
    [virtual] Expansion ROM at cfe00000 [disabled] [size=128K]
    Capabilities: [50] Power Management version 3
    Capabilities: [58] Express Legacy Endpoint, MSI 00
    Capabilities: [a0] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
    Kernel driver in use: fglrx_pci
    Kernel modules: fglrx, radeon



Here is my pm-suspend.log file - its the one where i couldnt access after waking my notebook up:
> 
Sun May 12 14:52:34 CEST 2013: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:


/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux Refle 3.5.0-28-generic #48~precise1-Ubuntu SMP Wed Apr 24 21:42:24 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
Module                  Size  Used by
ip6table_filter        12816  0 
ip6_tables             27686  1 ip6table_filter
iptable_filter         12811  0 
ip_tables              27474  1 iptable_filter
x_tables               29892  4 ip6table_filter,ip6_tables,iptable_filter,ip_tables
vesafb                 13846  1 
bnep                   18240  2 
rfcomm                 47562  0 
parport_pc             32867  0 
ppdev                  17114  0 
usblp                  18315  0 
arc4                   12530  2 
fglrx                5201123  158 
ath9k                 133095  0 
snd_hda_codec_hdmi     32476  1 
snd_hda_codec_realtek    79855  1 
mac80211              555272  1 ath9k
snd_hda_intel          34063  5 
snd_hda_codec         135141  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
uvcvideo               78117  0 
coretemp               13642  0 
ath9k_common           14054  1 ath9k
videobuf2_core         33025  1 uvcvideo
snd_hwdep              17765  1 snd_hda_codec
ath9k_hw              399752  2 ath9k,ath9k_common
videodev              125126  2 uvcvideo,videobuf2_core
kvm_intel             137888  0 
snd_pcm                97523  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
btusb                  22432  0 
videobuf2_vmalloc      12861  1 uvcvideo
videobuf2_memops       13405  1 videobuf2_vmalloc
kvm                   422160  1 kvm_intel
snd_seq_midi           13325  0 
ath                    24124  3 ath9k,ath9k_common,ath9k_hw
snd_rawmidi            30750  1 snd_seq_midi
snd_seq_midi_event     14900  1 snd_seq_midi
bluetooth             211812  11 bnep,rfcomm,btusb
snd_seq                61931  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14498  3 snd_seq_midi,snd_rawmidi,snd_seq
joydev                 17694  0 
snd                    83674  20 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse               102075  0 
cfg80211              208382  3 ath9k,mac80211,ath
mei                    41410  0 
soundcore              15092  1 snd
snd_page_alloc         18573  2 snd_hda_intel,snd_pcm
microcode              23030  0 
acer_wmi               32845  0 
serio_raw              13216  0 
sparse_keymap          13891  1 acer_wmi
amd_iommu_v2           19228  1 fglrx
intel_ips              18332  0 
wmi                    19257  1 acer_wmi
lpc_ich                17145  0 
mac_hid                13254  0 
video                  19653  1 acer_wmi
lp                     17800  0 
parport                46563  3 parport_pc,ppdev,lp
ahci                   25869  2 
libahci                27338  1 ahci
atl1c                  42092  0 
usb_storage            49288  0 
             total       used       free     shared    buffers     cached
Mem:       3908912    2005248    1903664          0      79176     838812
-/+ buffers/cache:    1087260    2821652
Swap:      3852284          0    3852284


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
stop: Unknown instance: 


/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:


/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:


/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
ATI Catalyst driver detected, not using quirks.


/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0


/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:


/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.

When i suspend it with: 
>> [COLOR=#000000][FONT=Ubuntu Mono]sudo pm-suspend --quirk-s3-mode
[/FONT][/COLOR]it switches the screen off, but the computer stays on - so its the same issue that i sometimes have, when i wake up from suspend...

Any idea?

---

### Post by Toz on 2013-05-12
Can we get a clean debug log file? Try like this:

```
sudo bash
mv /var/log/pm-suspend.log /var/log/pm-suspend.log.BAK
export PM_DEBUG=true
pm-suspend
```

When you recover, post back the log file like this:
```
pastebinit /var/log/pm-suspend.log
```
...and post back the link that is generated.

---

### Post by refle on 2013-05-12
thanks for your reply.
here you go:
[http://paste.ubuntu.com/5658812/](http://paste.ubuntu.com/5658812/)

---

### Post by Toz on 2013-05-12
Nothing abnormal in the log file - as you stated, suspend/resume is working. Did you try all of the quirks from post #8?

Can you also try the following quirks:
```
sudo pm-suspend --quirk-vbemode-restore
```
```
sudo pm-suspend --quirk-reset-brightness
```

EDIT: Can you also post back from syslog:
```
cat /var/log/syslog | grep PM:
```
```
cat /var/log/syslog | grep drm
```

EDIT2:
Does Ctrl+Alt+F1 get you to a visible text console?

---

### Post by refle on 2013-05-13
hi,
sorry pastebinit doesnt work, so here it comes:

> 
May 13 08:25:42 Refle kernel: [ 6457.435030] PM: Syncing filesystems ... done.
May 13 08:25:42 Refle kernel: [ 6457.599114] PM: Preparing system for mem sleep
May 13 08:25:42 Refle kernel: [ 6457.629805] PM: Entering mem sleep
May 13 08:25:42 Refle kernel: [ 6457.809301] PM: suspend of drv:snd_hda_intel dev:0000:00:1b.0 complete after 119.113 msecs
May 13 08:25:42 Refle kernel: [ 6457.809303] PM: suspend of drv:snd_hda_intel dev:0000:02:00.1 complete after 119.346 msecs
May 13 08:25:42 Refle kernel: [ 6457.938674] PM: suspend of drv:fglrx_pci dev:0000:02:00.0 complete after 248.967 msecs
May 13 08:25:42 Refle kernel: [ 6457.938740] PM: suspend of drv:pcieport dev:0000:00:01.0 complete after 248.693 msecs
May 13 08:25:42 Refle kernel: [ 6458.146723] PM: suspend of drv:sd dev:0:0:0:0 complete after 517.435 msecs
May 13 08:25:42 Refle kernel: [ 6458.146800] PM: suspend of drv:scsi dev:target0:0:0 complete after 517.490 msecs
May 13 08:25:42 Refle kernel: [ 6458.146878] PM: suspend of drv:scsi dev:host0 complete after 517.528 msecs
May 13 08:25:42 Refle kernel: [ 6458.147127] PM: suspend of drv: dev:ata1 complete after 517.715 msecs
May 13 08:25:42 Refle kernel: [ 6458.160697] PM: suspend of drv:ahci dev:0000:00:1f.2 complete after 471.273 msecs
May 13 08:25:42 Refle kernel: [ 6458.160757] PM: suspend of drv: dev:pci0000:00 complete after 471.120 msecs
May 13 08:25:42 Refle kernel: [ 6458.160821] PM: suspend of devices complete after 531.845 msecs
May 13 08:25:42 Refle kernel: [ 6458.160823] PM: suspend devices took 0.532 seconds
May 13 08:25:42 Refle kernel: [ 6458.161056] PM: late suspend of devices complete after 0.230 msecs
May 13 08:25:42 Refle kernel: [ 6458.240554] PM: noirq suspend of devices complete after 79.652 msecs
May 13 08:25:42 Refle kernel: [ 6458.500229] PM: Saving platform NVS memory
May 13 08:25:42 Refle kernel: [ 6458.712832] PM: Restoring platform NVS memory
May 13 08:25:42 Refle kernel: [ 6459.508310] PM: noirq resume of devices complete after 0.875 msecs
May 13 08:25:42 Refle kernel: [ 6459.508456] PM: early resume of devices complete after 0.119 msecs
May 13 08:25:42 Refle kernel: [ 6459.686972] PM: resume of drv: dev:ep_00 complete after 178.376 msecs
May 13 08:25:42 Refle kernel: [ 6459.686980] PM: resume of drv:usb dev:2-1.5 complete after 177.737 msecs
May 13 08:25:42 Refle kernel: [ 6459.686986] PM: resume of drv:hub dev:2-1:1.0 complete after 178.447 msecs
May 13 08:25:42 Refle kernel: [ 6459.687002] PM: resume of drv:usb dev:2-1.2 complete after 178.207 msecs
May 13 08:25:42 Refle kernel: [ 6459.687017] PM: resume of drv: dev:ep_81 complete after 178.445 msecs
May 13 08:25:42 Refle kernel: [ 6459.735286] PM: resume of drv:usb dev:2-1.2:1.1 complete after 226.456 msecs
May 13 08:25:42 Refle kernel: [ 6459.735299] PM: resume of drv: dev:ep_00 complete after 226.236 msecs
May 13 08:25:42 Refle kernel: [ 6459.735305] PM: resume of drv: dev:ep_85 complete after 226.391 msecs
May 13 08:25:42 Refle kernel: [ 6459.735316] PM: resume of drv: dev:ep_84 complete after 226.445 msecs
May 13 08:25:42 Refle kernel: [ 6459.735324] PM: resume of drv: dev:ep_03 complete after 226.473 msecs
May 13 08:25:42 Refle kernel: [ 6459.735329] PM: resume of drv:usb-storage dev:2-1.2:1.2 complete after 226.371 msecs
May 13 08:25:42 Refle kernel: [ 6459.735332] PM: resume of drv:usblp dev:2-1.2:1.0 complete after 226.607 msecs
May 13 08:25:42 Refle kernel: [ 6459.735344] PM: resume of drv: dev:ep_08 complete after 226.356 msecs
May 13 08:25:42 Refle kernel: [ 6459.735347] PM: resume of drv: dev:ep_89 complete after 226.313 msecs
May 13 08:25:42 Refle kernel: [ 6459.735350] PM: resume of drv: dev:ep_82 complete after 226.563 msecs
May 13 08:25:42 Refle kernel: [ 6459.735352] PM: resume of drv: dev:ep_01 complete after 226.602 msecs
May 13 08:25:42 Refle kernel: [ 6459.735365] PM: resume of drv:scsi dev:host4 complete after 226.271 msecs
May 13 08:25:42 Refle kernel: [ 6459.735382] PM: resume of drv:scsi_host dev:host4 complete after 226.256 msecs
May 13 08:25:42 Refle kernel: [ 6459.735385] PM: resume of drv:scsi dev:target4:0:0 complete after 226.120 msecs
May 13 08:25:42 Refle kernel: [ 6459.735466] PM: resume of drv:sd dev:4:0:0:0 complete after 226.178 msecs
May 13 08:25:42 Refle kernel: [ 6459.735541] PM: resume of drv:scsi_device dev:4:0:0:0 complete after 226.230 msecs
May 13 08:25:42 Refle kernel: [ 6459.885606] PM: resume of drv: dev:ep_00 complete after 376.663 msecs
May 13 08:25:42 Refle kernel: [ 6459.885638] PM: resume of drv:uvcvideo dev:2-1.5:1.0 complete after 376.763 msecs
May 13 08:25:42 Refle kernel: [ 6459.885641] PM: resume of drv:uvcvideo dev:2-1.5:1.1 complete after 376.716 msecs
May 13 08:25:42 Refle kernel: [ 6459.885665] PM: resume of drv: dev:ep_83 complete after 376.768 msecs
May 13 08:25:42 Refle kernel: [ 6461.076191] PM: resume of drv:scsi dev:host0 complete after 1570.257 msecs
May 13 08:25:42 Refle kernel: [ 6461.076209] PM: resume of drv:scsi_host dev:host0 complete after 1570.268 msecs
May 13 08:25:42 Refle kernel: [ 6461.076217] PM: resume of drv:scsi dev:target0:0:0 complete after 1570.246 msecs
May 13 08:25:42 Refle kernel: [ 6461.076240] PM: resume of drv:sd dev:0:0:0:0 complete after 1570.259 msecs
May 13 08:25:42 Refle kernel: [ 6461.093516] PM: resume of drv:scsi_device dev:0:0:0:0 complete after 1587.546 msecs
May 13 08:25:42 Refle kernel: [ 6463.704811] PM: resume of devices complete after 4204.681 msecs
May 13 08:25:42 Refle kernel: [ 6463.704886] PM: resume devices took 4.204 seconds
May 13 08:25:42 Refle kernel: [ 6463.704939] PM: Finishing wakeup.





> May 12 16:04:44 Refle kernel: [   15.373715] [drm] Initialized drm 1.1.0 20060810May 12 16:04:44 Refle kernel: [   15.668386] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
May 12 16:04:44 Refle kernel: [   15.668387] [drm] Driver supports precise vblank timestamp query.
May 12 16:04:44 Refle kernel: [   16.305396] fbcon: inteldrmfb (fb0) is primary device
May 12 16:04:44 Refle kernel: [   16.305556] fb0: inteldrmfb frame buffer device
May 12 16:04:44 Refle kernel: [   16.305558] drm: registered panic notifier
May 12 16:04:44 Refle kernel: [   16.349620] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0




and i cant access the terminal ...

i also tried all the suspend modes. except the one i mentioned, the modes didnt change anything... the screen turns black-off-black-off and then i get to the login... there must be something strange going on.
would it help if i upload a video of the waking up?

---

### Post by Toz on 2013-05-13
There isn't anything in your log files to help identify a cause. You stated in your original post that sometimes suspend/resume works. How often does it work vs how often does it not work?

Can I get a look at your Xorg.0.log file?
```
pastebinit /var/log/Xorg.0.log
```

And also, after resume, have you tried adjusting your brightness using the brightness function keys? Try both the up and down keys.

---

### Post by refle on 2013-05-13
Thanks for your support.
Here the file: 
[http://paste.ubuntu.com/5661848/](http://paste.ubuntu.com/5661848/)


The resuming doesnt work 1 out of 20 times... however - this 1/20 chance still sucks :(

---

### Post by Toz on 2013-05-13
> **refle said:**
> The resuming doesnt work 1 out of 20 times... however - this 1/20 chance still sucks :(
Are any of these log files from right after an unsuccessful resume? If not, it might be more helpful if we saw all of these log files from right after an unssuccessful resume - I'm just not seeing anything relevant or related.

---

### Post by refle on 2013-06-08
Hi, here log-files after a failed wake-up from suspend: 
[http://paste.ubuntu.com/5744093/](http://paste.ubuntu.com/5744093/)

---

### Post by Toz on 2013-06-08
> **refle said:**
> Hi, here log-files after a failed wake-up from suspend: 
[http://paste.ubuntu.com/5744093/](http://paste.ubuntu.com/5744093/)

Unfortunately, the log file looks fine (in that it suspended and resumed and there were no error messages). I think you are right in your assessment that it is something with the graphics card not re-initializing properly every odd (1/20)th time. I'm not sure what else to suggest. You might want to look at updating the ATi drivers, but since I don't have one, I'm unable to assist or advise on how to do it.

---

### Post by ohellequin on 2013-07-03
hello there,
i am using Ubuntu 13.04 on HP Pavilion g7 and have had this problem since 12.04.

I am not an expert on the Ubuntu Kernel but from my observation I think that when the system wakes up, after suspending, it doesn't activate the main monitor at all.
If you search for LVDS (the main monitor name) in the log file, you can't find it, instead you can find only VGA (the 2nd monitor name).

So I think that a command should be added in the wake up skript, where the activation of the LVDS is included.

If Toz or any other ubuntu developer could prove if i'm wrong or write and if so, finaly fix this problem, that would be great :)

---

### Post by greatsirkain on 2013-07-03
My advent laptop wont wake up unless I press the power button, don't know if this is normal or related to your problems, just thought it was worth mentioning

---

### Post by Toz on 2013-07-03
> **ohellequin said:**
> hello there,
i am using Ubuntu 13.04 on HP Pavilion g7 and have had this problem since 12.04.

I am not an expert on the Ubuntu Kernel but from my observation I think that when the system wakes up, after suspending, it doesn't activate the main monitor at all.
If you search for LVDS (the main monitor name) in the log file, you can't find it, instead you can find only VGA (the 2nd monitor name).

So I think that a command should be added in the wake up skript, where the activation of the LVDS is included.

If Toz or any other ubuntu developer could prove if i'm wrong or write and if so, finaly fix this problem, that would be great :)

What video card do you have and what drivers are you using? This command should help to identify it:
```
sudo lspci -vnn | grep -A15 VGA
```

Also, you can send quirks to the suspend process - some of which might help to revive the monitor. See [here]("http://manpages.ubuntu.com/manpages/precise/man8/pm-action.8.html") for a list of quirks. To try them, you would manually initiate the suspend sequence via:
```
sudo pm-suspend --<quirk_name>
```
...where <quirk_name> is one of the quirks listed in the previous link. Be sure to read the desription of the quirks. Some that you might want to try are:
--quirk-dpms-on
--quirk-s3-bios
--quirk-s3-mode
--quirk-vbe-post
--quirk-vbestate-restore

If you find that works, run it again but this time add ** --store-quirks-as-lkw** to save it as a default quirk for your system.

---

### Post by admrubin on 2013-09-26
Hey,

This worked for me after nothing else did:

      
[http://bernaerts.dyndns.org/linux/74-ubuntu/220-ubuntu-resume-usb-hid](http://bernaerts.dyndns.org/linux/74-ubuntu/220-ubuntu-resume-usb-hid)

Cheers

---

### Post by eva-evapz on 2013-12-05
Hi there,

After reading several posts to fix it, and tried many many proposals that didn't work for me, I finally found a solution.

For me, the issue is on HP Pavilion Dv7 (and other many laptops I noticed), there are 2 annoying issues ; no wake up (resume) from sleep mode, and no shut down properly.
Have to hard reboot...

Ati/Amd graphic card for me (not tested on Nvidia but could work, try it anyway, nothing to lose)

This problem comes from a lake a video quirk database for some pc

Here is what to do for make it work :

- Method with graphical super user mode :

Open Terminal console and type this command :

[COLOR=#0000cd]**sudo nautilus**[/COLOR] - you'll be asked to type your password (it will open your home folder with sudo permission) 

1) From [COLOR=#ff0000]that folder (opened with sudo nautilus)[/COLOR], browse to go and open the directory : system file, usr, lib, pm-utils, [COLOR=#0000ff]sleep.d[/COLOR]
([COLOR=#0000ff]system file/usr/lib/pm-utils/sleep.d[/COLOR])

> then remove/delete the file "98video-quirk-db-handler" that you'll find into that folder

[COLOR=#ff0000](before removing it, drag and drop it to your desktop to keep a copy of it in case this didn't work)[/COLOR]


2) Now, browse and open the directory : /etc/pm/confid.d

> We have to edit a file in this directory

> open and edit a text file on your desktop that you name ADD_PARAMETERS

> type this line into your new text file :

ADD_PARAMETERS="--quirk-s3-mode --quirk-vga-mode-3 --quirk-s3-bios --quirk-radeon-off " (including the quotes)

[NB : [COLOR=#ff0000]if you want to try this with [/COLOR]Nvidia[COLOR=#ff0000] [/COLOR]Card[COLOR=#ff0000] don't add -quirk-radeon-off[/COLOR]]

> Save it on your desktop and close it (don't forget to name the file ADD_PARAMETERS before saving)

> then Drop the text file from desktop into the folder /etc/pm/config.d

([COLOR=#ff0000]verify permissions of the file on "[/COLOR][COLOR=#0000cd]properties - permission menu[/COLOR][COLOR=#ff0000]" it has to be on root "read and write" for all 3 options[/COLOR])

Close the folder

reboot (or close session)

Done ! 

_Note_ : if this didn't work, delete this new created file and replace it by the original one that you have back-up (on your desktop as mentioned before) into the folder [COLOR=#0000FF]system file/usr/lib/pm-utils/sleep.d, [/COLOR]still as root or with [COLOR=#0000cd]sudo nautilus[/COLOR] again.[COLOR=#0000FF][/COLOR]

(Of course you can do all this procedure in a terminal console with root permissions)

It really works perfectly ! wake up from sleep mode and shut down properly !!

That's it.

---

