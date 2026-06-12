---
title: "Black dots/lines randomly appear on screen"
date: 2013-05-25
forum: General Help
---

### Post by tyela on 2013-05-25
I have installed Ubuntu 13.04 on a Toshiba Satellite U845-S409 a week ago. Starting yesterday, every once in a while, there is a pattern of short, horizontal black lines that appear over the whole screen, which lasts about a second and then dissapears. Any thoughts on that?

---

### Post by papibe on 2013-05-25
Hi tyela. Welcome to the forum ):P

My first guess would be to check your graphic card and drivers.

Could you open a terminal, run this commands and post the results?
```
lspci -nnk | grep -iA2 vga

xrandr

xvidtune -show

lsmod | grep -iE 'nvidia|intel|fglrx|radeon|nouveau'
```
Regards.

---

### Post by tyela on 2013-05-25
Thanks! Here's what I get:

```
mon@eyvindur:~$ lspci -nnk | grep -iA2 vga
00:02.0 VGA compatible controller [0300]: Intel Corporation 3rd Gen Core processor Graphics Controller [8086:0166] (rev 09)
    Subsystem: Toshiba America Info Systems Device [1179:fba1]
    Kernel driver in use: i915
mon@eyvindur:~$ xrandr
Screen 0: minimum 320 x 200, current 1366 x 768, maximum 32767 x 32767
LVDS1 connected 1366x768+0+0 (normal left inverted right x axis y axis) 310mm x 174mm
   1366x768       60.0*+
   1360x768       59.8     60.0  
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
VGA1 disconnected (normal left inverted right x axis y axis)
HDMI1 disconnected (normal left inverted right x axis y axis)
DP1 disconnected (normal left inverted right x axis y axis)
mon@eyvindur:~$ xvidtune -show
"1366x768"     69.30   1366 1398 1430 1470    768  771  776  786 -hsync -vsync

mon@eyvindur:~$ lsmod | grep -iE 'nvidia|intel|fglrx|radeon|nouveau'
kvm_intel             126842  0 
kvm                   376505  1 kvm_intel
aesni_intel            18156  2 
aes_i586               16995  1 aesni_intel
xts                    12749  1 aesni_intel
lrw                    13057  1 aesni_intel
ablk_helper            13357  1 aesni_intel
snd_hda_intel          38307  3 
snd_hda_codec         117580  3 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel
snd_pcm                80890  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_page_alloc         14230  2 snd_pcm,snd_hda_intel
snd                    56485  16 snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device
```

---

### Post by papibe on 2013-05-25
Thanks.

So far, so good. You have Intel integrated graphics, and you are using the proper driver.

Let's see if there's something on the X log. Could you paste the content of this file?
```
/var/log/Xorg.0.log
```
Please paste it here: [paste.ubuntu.com]("http://paste.ubuntu.com/"), and post back the link to it.

Regards.

---

### Post by tyela on 2013-05-25
[http://paste.ubuntu.com/5700944/](http://paste.ubuntu.com/5700944/)

---

### Post by papibe on 2013-05-25
Thanks.

There no graphic error reported on the log.

Let's check the version of your driver. Could you post the output of this command?
```
apt-cache policy xserver-xorg-video-intel
```
Regards.

---

### Post by tyela on 2013-05-25
Alright:

```
xserver-xorg-video-intel:
  Installed: 2:2.21.6-0ubuntu4
  Candidate: 2:2.21.6-0ubuntu4
  Version table:
 *** 2:2.21.6-0ubuntu4 0
        500 http://us.archive.ubuntu.com/ubuntu/ raring/main i386 Packages
        100 /var/lib/dpkg/status
```

---

### Post by papibe on 2013-05-25
It looks like everything is OK.

My only guess (not assuming hardware problems) would be that there's a flaw/bug on the 13.04 driver.

There's only one version upstream you can upgrade to, but it falls into the "experimental/unstable" category.

This would be the instructions to upgrade:
```
sudo add-apt-repository ppa:xorg-edgers/ppa

sudo apt-get update

sudo apt-get upgrade
```
You may need to reboot after that.

Let us know how it goes.
Regards.

---

### Post by tyela on 2013-05-25
Hi papibe,

I upgraded the driver and the problem has not manifested itself since then (it used to be pretty frequent), so I'm going to assume that this is solved for now. I hope I'm not speaking too fast. 

In any case, thanks a lot for the help and for actually explaining what the instructions you're giving me are doing, it's much appreciated!

Cheers.

Alright, it seems that wishful thinking does not work and I have indeed spoken rashly. The problem is still there.

---

### Post by tyela on 2013-05-25
I was typing into terminal and the lines that appeared were now white instead of black. Also, they are more frequent when I do any kind of action. That is, they show up when I click something or give a command, rather than when the computer is idle. But it might be as small as moving the cursor... Not sure that's of any help.

---

### Post by papibe on 2013-05-25
There seems to be 2 1366x768 resolutions available. Are you able to select the other one with different refresh time?

If so, it could be interesting to see if that one is more stable.

Regards.

---

### Post by tyela on 2013-05-26
That's very interesting. I selected the second resolution and it seemed fine. I then switched back to the first one out of curiosity, and I still didn't get the problem since yesterday. Looks good for now. Thanks!

---

### Post by mimozus on 2013-07-18
I'm havnig the same problem.  Flashes of small square black dots appear randomly scattered across the entire screen.

Sony VAIO S Series 15.5" 1920x1080, core i7, Intel HD 4000 Graphics.

I also use an external monitor (hdmi:1920x1080):

Ubuntu 13.04

[~]uname -a
Linux fido 3.8.0-26-generic #38-Ubuntu SMP Mon Jun 17 21:43:33 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

[~]lspci -nnk | grep -iA2 vga
00:02.0 VGA compatible controller [0300]: Intel Corporation 3rd Gen Core processor Graphics Controller [8086:0166] (rev 09)
    Subsystem: Sony Corporation Device [104d:909c]
    Kernel driver in use: i915

[~]xrandr
Screen 0: minimum 320 x 200, current 3840 x 1080, maximum 32767 x 32767
LVDS1 connected 1920x1080+0+0 (normal left inverted right x axis y axis) 345mm x 194mm
   1920x1080      59.9*+   59.9  
   1680x1050      60.0     59.9  
   1600x1024      60.2  
   1400x1050      60.0  
   1280x1024      60.0  
   1440x900       59.9  
   1280x960       60.0  
   1360x768       59.8     60.0  
   1152x864       60.0  
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
VGA1 disconnected (normal left inverted right x axis y axis)
HDMI1 connected 1920x1080+1920+0 (normal left inverted right x axis y axis) 477mm x 268mm
   1920x1080      60.0*+
   1680x1050      59.9  
   1280x1024      75.0     60.0  
   1440x900       59.9  
   1280x960       60.0  
   1024x768       75.1     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   640x480        72.8     75.0     66.7     60.0  
   720x400        70.1  
DP1 disconnected (normal left inverted right x axis y axis)
HDMI2 disconnected (normal left inverted right x axis y axis)
DP2 disconnected (normal left inverted right x axis y axis)

[~]xvidtune -show
"1920x1080"   144.20   1920 1968 2040 2148   1080 1083 1088 1120 -hsync -vsync

[~]lsmod | grep -iE 'nvidia|intel|fglrx|radeon|nouveau'
kvm_intel             132891  0 
kvm                   443165  1 kvm_intel
ghash_clmulni_intel    13259  0 
aesni_intel            55399  1 
aes_x86_64             17255  1 aesni_intel
xts                    12885  1 aesni_intel
lrw                    13257  1 aesni_intel
ablk_helper            13597  1 aesni_intel
cryptd                 20373  3 ghash_clmulni_intel,aesni_intel,ablk_helper
snd_hda_intel          39619  4 
snd_hda_codec         136453  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_pcm                97451  6 snd_usb_audio,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd                    68876  22 snd_hda_codec_realtek,snd_usb_audio,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_usbmidi_lib,snd_hda_codec,snd_hda_intel,snd_seq_device

[~]apt-cache policy xserver-xorg-video-intel
xserver-xorg-video-intel:
  Installed: 2:2.21.6-0ubuntu4
  Candidate: 2:2.21.6-0ubuntu4
  Version table:
 *** 2:2.21.6-0ubuntu4 0
        500 [http://mirrors.arpnetworks.com/Ubuntu/](http://mirrors.arpnetworks.com/Ubuntu/) raring/main amd64 Packages
        100 /var/lib/dpkg/status

---

