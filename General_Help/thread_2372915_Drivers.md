---
title: "Drivers"
date: 2017-09-30
forum: General Help
---

### Post by ra.abbasi on 2017-09-30
Hi all,

I've recently installed Ubuntu 16.04 x64 on my HP laptop. How should I know if all the drivers are installed correctly, especially the graphics driver?

---

### Post by HermanAB on 2017-09-30
Simple.  Does it work?

You can play video and see what happens.  If it plays smoothly and doesn't stutter, then you are OK.

You can also list the running modules with lsmod to see what is installed.

---

### Post by ra.abbasi on 2017-10-01
what is "[COLOR=#000000]lsmod" please?
I'm new on Ubuntu. [/COLOR]

---

### Post by slickymaster on 2017-10-01
From the Linux man pages> DESCRIPTION
       lsmod is a trivial program which nicely formats the contents of the /proc/modules, showing what kernel modules are currently loaded.
All you have to do is to open a terminal window (Ctrl+A+T) and enter the following```
lsmod
```Afterwards just copy/past the output you get into thread [using code tags]("https://ubuntuforums.org/showthread.php?t=2171721&p=12776168&viewfull=1#post12776168") for the effect.

---

### Post by HermanAB on 2017-10-01
On Linux, device drivers (and other things) are called modules.  You can list all loaded modules with the command lsmod:
```

$ lsmod
Module                  Size  Used by
ccm                    17773  0 
rfcomm                 69461  2 
fuse                   91492  3 
ip6t_rpfilter          12546  1 
ip6t_REJECT            12625  2 
...

```

---

### Post by gordintoronto on 2017-10-01
Drivers is one of the biggest differences between Windows and Linux. In most cases, Linux "just works" and you don't have to worry about drivers.

For video, it's possible that there is an "additional driver" which was not automatically installed. Unfortunately, I run Xubuntu 17.04, so I don't know how to check for an Additional Driver in Ubuntu 16.04.

---

### Post by ra.abbasi on 2017-10-03
I did:

```
abbasi@abbasi-HP:~$ lsmod
Module                  Size  Used by
ccm                    20480  2
binfmt_misc            20480  1
nls_iso8859_1          16384  1
hp_wmi                 16384  0
sparse_keymap          16384  1 hp_wmi
intel_rapl             20480  0
x86_pkg_temp_thermal    16384  0
intel_powerclamp       16384  0
coretemp               16384  0
snd_hda_codec_hdmi     49152  1
kvm                   593920  0
snd_hda_codec_realtek    90112  1
snd_hda_codec_generic    73728  1 snd_hda_codec_realtek
irqbypass              16384  1 kvm
snd_hda_intel          36864  3
snd_hda_codec         126976  4 snd_hda_intel,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec_realtek
snd_hda_core           81920  5 snd_hda_intel,snd_hda_codec,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec_realtek
snd_hwdep              16384  1 snd_hda_codec
crct10dif_pclmul       16384  0
crc32_pclmul           16384  0
ghash_clmulni_intel    16384  0
snd_pcm               102400  4 snd_hda_intel,snd_hda_codec,snd_hda_core,snd_hda_codec_hdmi
cryptd                 24576  1 ghash_clmulni_intel
intel_cstate           20480  0
intel_rapl_perf        16384  0
snd_seq_midi           16384  0
snd_seq_midi_event     16384  1 snd_seq_midi
arc4                   16384  2
snd_rawmidi            32768  1 snd_seq_midi
uvcvideo               90112  0
rt2800pci              16384  0
videobuf2_vmalloc      16384  1 uvcvideo
rt2800mmio             16384  1 rt2800pci
videobuf2_memops       16384  1 videobuf2_vmalloc
rt2800lib              94208  2 rt2800mmio,rt2800pci
rt2x00pci              16384  1 rt2800pci
rt2x00mmio             16384  2 rt2800mmio,rt2800pci
videobuf2_v4l2         24576  1 uvcvideo
videobuf2_core         40960  2 uvcvideo,videobuf2_v4l2
videodev              172032  3 uvcvideo,videobuf2_core,videobuf2_v4l2
media                  40960  2 uvcvideo,videodev
rt2x00lib              53248  5 rt2800lib,rt2x00pci,rt2800mmio,rt2x00mmio,rt2800pci
snd_seq                65536  2 snd_seq_midi_event,snd_seq_midi
joydev                 20480  0
input_leds             16384  0
serio_raw              16384  0
mac80211              782336  3 rt2800lib,rt2x00pci,rt2x00lib
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              32768  2 snd_seq,snd_pcm
cfg80211              602112  2 rt2x00lib,mac80211
rtsx_pci_ms            20480  0
lpc_ich                24576  0
memstick               16384  1 rtsx_pci_ms
eeprom_93cx6           16384  1 rt2800pci
snd                    77824  17 snd_hda_intel,snd_hwdep,snd_seq,snd_hda_codec,snd_timer,snd_rawmidi,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_seq_device,snd_hda_codec_realtek,snd_pcm
shpchp                 36864  0
soundcore              16384  1 snd
mei_me                 40960  0
mei                   102400  1 mei_me
mac_hid                16384  0
hp_wireless            16384  0
parport_pc             32768  0
ppdev                  20480  0
lp                     20480  0
parport                49152  3 lp,parport_pc,ppdev
autofs4                40960  2
rtsx_pci_sdmmc         24576  0
i915                 1449984  88
i2c_algo_bit           16384  1 i915
drm_kms_helper        151552  1 i915
psmouse               139264  0
ahci                   36864  3
libahci                32768  1 ahci
syscopyarea            16384  1 drm_kms_helper
r8169                  81920  0
sysfillrect            16384  1 drm_kms_helper
sysimgblt              16384  1 drm_kms_helper
mii                    16384  1 r8169
fb_sys_fops            16384  1 drm_kms_helper
drm                   352256  5 i915,drm_kms_helper
rtsx_pci               57344  2 rtsx_pci_sdmmc,rtsx_pci_ms
wmi                    16384  1 hp_wmi
video                  40960  1 i915
fjes                   77824  0
abbasi@abbasi-HP:~$ 
```

I use an HP 250 laptop. Ubuntu is terribly slow at times. Especially the Firefox browser and Ubuntu Software program.
The system stops, firefox stops repeatedly and it took about 30 minutes and a few rebooting until I could send this post. (I eidtted it on my Windows machine)
I tried to install Chrome but faced an error.
Chrome is really great on my Windows machine.

---

### Post by gordintoronto on 2017-10-03
What are the specs of your HP laptop? (processor, memory, hard drive space, video).  The HP 250 is a large family of computers, from low-end to high-end.

You might be better off with Lubuntu, Ubuntu Mate or Xubuntu.

---

### Post by ra.abbasi on 2017-10-04
Here is the machine's specs:

---

### Post by mastablasta on 2017-10-04
the GPU has drivers in the kernel. is there enough ram (2Gb or more)?

i would suggest you try chromium (in the repositories). Firefox is giving me issues on Kubuntu 64bit, though it works perfectly on the PC with 32bit OS.

Ubuntu should run fine and smooth on this device. perhaps something else is wrong a setting or something!? have you even considered using a different version such as Xubuntu or Kubuntu? maybe just live session to make sure all works well.

---

### Post by ra.abbasi on 2017-10-07
The RAM is 4GB.
Chromium is rather better but it faces DNS errors at times.
I need to set Google's DNS addresses manually to the network settings of it.

Now based on the specs above and the output of the *lsmod* command, doesn't my Ubuntu lack any driver?

---

