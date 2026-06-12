---
title: "Xubuntu 12.04: USB Mouse does not work"
date: 2014-02-21
forum: General Help
---

### Post by jv69 on 2014-02-21
Hello,  I just installed Xubuntu 12.04 on a Dell Optiplex GX620. I was given a Gateway Keyboard and Mouse to use temporary. 
The keyboard works, but no mouse. Searched many web pages on mouse problem. 
I opened a tty (CTRL-ALT F1)  and performed the following:
sudo -update -usbids 
sudo modprobe -r psmouse;
sudo modprobe ehci-hcd  ( ehci-hcd is not installed) 


Then I went to Applications -> Settings, , using F10 and arrow keys on the 
keyboard but there is no mouse configuration options. Currently running updates
to see if something was missed. 

Any help is appreciated.
thanks

---

### Post by jv69 on 2014-02-21
Installed  13.10...   same results

---

### Post by varunendra on 2014-02-22
> **jv69 said:**
> sudo modprobe -r psmouse

That command removes the mouse driver. Did you reload it after that?

What are the outputs of -
```
lsmod
xinput
```

And please use "code" tags for posting command outputs. (please follow the "Using Code Tags" link in my signature if you need to see how)

---

### Post by jv69 on 2014-02-22
Varun,  I did not load it back.
I will try to load it back tonight. Forgot about the code tags. It's been a while.
Thanks
```

sudo modprobe psmouse
xinput

```

---

### Post by jv69 on 2014-02-23
Vanrun. Here is the output from lsmod and xinput:

```

**lsmod output:**

Module                  Size  Used by
dcdbas                 14098  0 
snd_intel8x0           33455  3 
snd_ac97_codec        110213  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80916  2 snd_intel8x0,snd_ac97_codec
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
psmouse                96744  0 
snd_seq_midi_event     14475  1 snd_seq_midi
serio_raw              13027  0 
snd_seq                51592  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    62218  13 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              14635  1 snd
snd_page_alloc         14115  2 snd_intel8x0,snd_pcm
rfcomm                 38139  4 
bnep                   17830  2 
parport_pc             32114  0 
joydev                 17393  0 
bluetooth             158447  10 rfcomm,bnep
ppdev                  12849  0 
i915                  428021  2 
drm_kms_helper         45466  1 i915
drm                   197641  3 i915,drm_kms_helper
mac_hid                13077  0 
i2c_algo_bit           13199  1 i915
video                  19115  1 i915
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
floppy                 60184  0 
usbhid                 41937  0 
hid                    77428  1 usbhid
tg3                   141465  0 


**xinput output:**

â&#381;¡ Virtual core pointer                        id=2    [master pointer  (3)]
Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
Lite-On Technology Corp. USB Multimedia Keyboard    id=9    [slave  pointer  (2)]

 Virtual core keyboard                       id=3    [master keyboard (2)]
 Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
 Power Button                                id=6    [slave  keyboard (3)]
 Power Button                                id=7    [slave  keyboard (3)]
 Lite-On Technology Corp. USB Multimedia Keyboard    id=8    [slave  keyboard (3)]


```

---

### Post by jv69 on 2014-02-23
Varun, I grep dmesg output for usb:

```

[    1.202836] usbcore: registered new interface driver usbfs
[    1.202836] usbcore: registered new interface driver hub
[    1.202836] usbcore: registered new device driver usb
[    2.010261] usbcore: registered new interface driver libusual
[    2.504020] usb 5-2: new low-speed USB device number 2 using uhci_hcd
[    6.336282] input: Lite-On Technology Corp. USB Multimedia Keyboard as /devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2:1.0/input/input2
[    6.337325] generic-usb 0003:04CA:004F.0001: input,hidraw0: USB HID v1.10 Keyboard [Lite-On Technology Corp. USB Multimedia Keyboard] on usb-0000:00:1d.3-2/input0
[    6.360283] input: Lite-On Technology Corp. USB Multimedia Keyboard as /devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2:1.1/input/input3
[    6.360655] generic-usb 0003:04CA:004F.0002: input,hidraw1: USB HID v1.10 Device [Lite-On Technology Corp. USB Multimedia Keyboard] on usb-0000:00:1d.3-2/input1
[    6.360696] usbcore: registered new interface driver usbhid
[    6.360702] usbhid: USB HID core driver


```

---

### Post by jv69 on 2014-02-23
Went to Walmart and bought a $9 Logitech mouse and NOW it works...

---

### Post by varunendra on 2014-02-23
Probably the only option I could suggest anyway, since your xinput output didn't list the mouse at all.

Glad you're not stuck anymore, anyhow. :)

---

### Post by jv69 on 2014-02-24
Varun, thanks for your help. I appreciate it. I learned something new in Linux !

---

