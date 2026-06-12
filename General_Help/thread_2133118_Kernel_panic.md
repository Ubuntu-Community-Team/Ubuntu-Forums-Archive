---
title: "Kernel panic"
date: 2013-04-07
forum: General Help
---

### Post by mreq on 2013-04-07
So ubuntu crashed on me for the 3rd time in past two months on three Ubuntu 12.04 installs (on the same hw). That's unbearable! Even win7 was more stable [-X.

What could be causing kernel panic? The system is working properly, when all of a sudden the following black screen pops up and the vents start spinning like crazy. I didn't trace any pattern that could lead to this.

---

### Post by dino99 on 2013-04-07
its probably a hardware (chipset or ram) issue; myself have that issue with one of my crappy asus mb, while other hardware systems never have such problem. So let the kernel team knowing about your issue:

> ubuntu-bug linux

[https://wiki.ubuntu.com/Kernel/Debugging](https://wiki.ubuntu.com/Kernel/Debugging)

---

### Post by mörgæs on 2013-04-07
Before posting the bug report you could try running **memtest** for an hour. It shows in the boot menu.

---

### Post by matt_symes on 2013-04-07
Hi

Run the memtest first as suggested above.

You have a tainted kernel with the flags D C O.

[http://tomoyo.sourceforge.jp/cgi-bin/lxr/source/Documentation/oops-tracing.txt](http://tomoyo.sourceforge.jp/cgi-bin/lxr/source/Documentation/oops-tracing.txt)

An panic occurred in read copy update memory update.

What modules do you have loaded ?

```
lsmod
```

Are you using virtualisation ?

Kind regards

---

### Post by mreq on 2013-04-07
I do use virtualization, but no virtual pc was running when the panic occured.

```

petr@sova:~$ lsmod
Module                  Size  Used by
snd_hda_codec_hdmi     32474  1 
snd_hda_codec_realtek   224173  1 
pci_stub               12622  1 
vboxpci                23237  0 
vboxnetadp             25670  0 
vboxnetflt             23478  0 
tpm_infineon           17536  0 
vboxdrv               320211  3 vboxpci,vboxnetadp,vboxnetflt
joydev                 17693  0 
btusb                  18332  0 
rfcomm                 47604  4 
bnep                   18281  2 
parport_pc             32866  0 
bluetooth             180153  11 btusb,rfcomm,bnep
ppdev                  17113  0 
binfmt_misc            17540  1 
arc4                   12529  2 
uvcvideo               72627  0 
videodev               98259  1 uvcvideo
v4l2_compat_ioctl32    17128  1 videodev
qcserial               12822  0 
option                 30161  0 
usb_wwan               20491  2 qcserial,option
usbserial              47077  3 qcserial,option,usb_wwan
snd_hda_intel          33719  6 
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              17764  1 snd_hda_codec
snd_pcm                97275  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61929  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
sony_laptop            45393  0 
tpm_tis                18804  0 
mac_hid                13253  0 
snd                    79041  21 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i915                  477626  3 
drm_kms_helper         46978  1 i915
drm                   241971  4 i915,drm_kms_helper
i2c_algo_bit           13423  1 i915
soundcore              15091  1 snd
psmouse                97485  0 
serio_raw              13211  0 
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
iwlwifi               401140  0 
mac80211              506862  1 iwlwifi
cfg80211              205774  2 iwlwifi,mac80211
rts_pstor             445241  0 
mei                    41616  0 
video                  19651  1 i915
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
usbhid                 47238  0 
hid                    99636  1 usbhid
r8169                  62154  0 

```

---

### Post by mreq on 2013-04-15
Crashed three times yesterday. Haven't had so unstable ubuntu for a whole non-problematic year :confused:

I found out that eventhough using 12.04.2 Xubuntu, I had 3.2** kernel. Tried to upgrade to 3.5*** and see how goes. Am considering clean-intalling 13.04 in 10 days.

---

### Post by gurak2005 on 2013-04-15
Same problem here. Do you use Pidgin im program ???

---

### Post by mreq on 2013-04-15
Nope, I don't.

As for the open apps, what I am running now is prety much my standard (from wmctrl):

```

0x03a00004 -1 xfce4-panel.Xfce4-panel
0x01400003 -1 xfdesktop.Xfdesktop
0x01a0001f -1 Docky.Docky
0x05000054  1 doublecmd.Doublecmd
0x04e00003  0 fogapp.fogapp-b954fff0415dd374cf8162d112a03fb3
0x03c000af  3 Mail.Thunderbird
0x06c00004  0 terminator.Terminator
0x06000003  2 sublime_text.sublime-text-2
0x06000036  1 sublime_text.sublime-text-2
0x06200003  1 evince.Evince
0x07200003  1 evince.Evince
0x07a00008  0 clementine.Clementine
0x07e00004  1 terminator.Terminator
0x05c000ba  3 chromium-browser.Chromium-browser
0x08000003  1 evince.Evince
0x06005076  3 sublime_text.sublime-text-2
0x08800220  3 SmartGit/Hg.SmartGit/Hg
0x08c00003  3 evince.Evince
0x06800004  3 terminator.Terminator

```

---

