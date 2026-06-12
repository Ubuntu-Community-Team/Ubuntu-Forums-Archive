---
title: "Recording issue with ALSA and BeagleBone Black"
date: 2015-05-15
forum: General Help
---

### Post by 012ddd on 2015-05-15
Hello.

I'm trying to record sound from 3 USB microphones using a BeagleBone Black (BBB). All 3 microphones connect to a USB hub, which connects to the single USB port of the BBB.

The issue is ALSA not detecting the microphones when I connect them through the USB hub. The microphones are all working fine - they were all individually tested with the BBB and they all produce accurate recordings using the ALSA drivers. However, when I connect them through the USB hub, they stop being recognized as recording devices by ALSA despite being connected and detected by the BBB (lsusb lists them). I've tried the USB hub with only 1 mic and with all 3 connected, the result is always the same. 

I haven't found much info about this because they simply aren't detected as sound cards, which doesn't seem to be a common issue. Some info I found online seems to be outdated. I tried to change the alsa-base.conf file that configures ALSA (the issue seems to be here) but I couldn't come up with a solution.
I'm also not very experienced with Linux OS and I could be missing something very simple, I would be greatly appreciated if someone could shed a light on this matter.

Some info:
lsusb when connecting the mic directly to the BBB
```

Bus 001 Device 002: ID 1415:2000 Nam Tai E&E Products Ltd. or OmniVision Technologies, Inc. Sony Playstation Eye
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

lsusb when connecting the mics through the USB hub (everything seems to be fine)
```

Bus 001 Device 003: ID 05e3:0610 Genesys Logic, Inc. 4-port hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 1415:2000 Nam Tai E&E Products Ltd. or OmniVision Technologies, Inc. Sony Playstation Eye
Bus 001 Device 005: ID 1415:2000 Nam Tai E&E Products Ltd. or OmniVision Technologies, Inc. Sony Playstation Eye
Bus 001 Device 006: ID 1415:2000 Nam Tai E&E Products Ltd. or OmniVision Technologies, Inc. Sony Playstation Eye

```

Sound cards detected when connecting the mic directly to the BBB
```

 0 [Black          ]: TI_BeagleBone_B - TI BeagleBone Black
                      TI BeagleBone Black
 1 [CameraB409241  ]: USB-Audio - USB Camera-B4.09.24.1
                      OmniVision Technologies, Inc. USB Camera-B4.09.24.1 at usb-musb-hdrc.1.auto-1, 

```

Sound cards detected when connecting the mics through the USB hub (microphones aren't detected)
```

  0 [Black          ]: TI_BeagleBone_B - TI BeagleBone Black
                      TI BeagleBone Black

```

From this point, the microphones are rendered completely useless when connected through the USB hub because they aren't sound cards. It's like they aren't even connected despite being detected by the BBB as USB devices.

This is the detailed information of the microphone. I get excatly this for each microphone and in both situations (connected directly to the BBB or through a USB hub). They are the Playstation Eye camera that can also work as a simple microphone.
```

Bus 001 Device 002: ID 1415:2000 Nam Tai E&E Products Ltd. or OmniVision Technologies, Inc. Sony Playstation Eye
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x1415 Nam Tai E&E Products Ltd. or OmniVision Technologies, Inc.
  idProduct          0x2000 Sony Playstation Eye
  bcdDevice            2.00
  iManufacturer           1 OmniVision Technologies, Inc.
  iProduct                2 USB Camera-B4.09.24.1
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength          142
    bNumInterfaces          3
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              500mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           3
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      0 
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval              10
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       0
      bNumEndpoints           0
      bInterfaceClass         1 Audio
      bInterfaceSubClass      1 Control Device
      bInterfaceProtocol      0 
      iInterface              0 
      AudioControl Interface Descriptor:
        bLength                 9
        bDescriptorType        36
        bDescriptorSubtype      1 (HEADER)
        bcdADC               1.00
        wTotalLength           42
        bInCollection           1
        baInterfaceNr( 0)       2
      AudioControl Interface Descriptor:
        bLength                12
        bDescriptorType        36
        bDescriptorSubtype      2 (INPUT_TERMINAL)
        bTerminalID             1
        wTerminalType      0x0201 Microphone
        bAssocTerminal          2
        bNrChannels             4
        wChannelConfig     0x0000
        iChannelNames           0 
        iTerminal               0 
      AudioControl Interface Descriptor:
        bLength                 9
        bDescriptorType        36
        bDescriptorSubtype      3 (OUTPUT_TERMINAL)
        bTerminalID             2
        wTerminalType      0x0101 USB Streaming
        bAssocTerminal          1
        bSourceID               3
        iTerminal               0 
      AudioControl Interface Descriptor:
        bLength                12
        bDescriptorType        36
        bDescriptorSubtype      6 (FEATURE_UNIT)
        bUnitID                 3
        bSourceID               1
        bControlSize            1
        bmaControls( 0)      0x00
        bmaControls( 1)      0x02
          Volume Control
        bmaControls( 2)      0x02
          Volume Control
        bmaControls( 3)      0x02
          Volume Control
        bmaControls( 4)      0x02
          Volume Control
        iFeature                0 
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        2
      bAlternateSetting       0
      bNumEndpoints           0
      bInterfaceClass         1 Audio
      bInterfaceSubClass      2 Streaming
      bInterfaceProtocol      0 
      iInterface              0 
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        2
      bAlternateSetting       1
      bNumEndpoints           1
      bInterfaceClass         1 Audio
      bInterfaceSubClass      2 Streaming
      bInterfaceProtocol      0 
      iInterface              0 
      AudioStreaming Interface Descriptor:
        bLength                 7
        bDescriptorType        36
        bDescriptorSubtype      1 (AS_GENERAL)
        bTerminalLink           2
        bDelay                  1 frames
        wFormatTag              1 PCM
      AudioStreaming Interface Descriptor:
        bLength                11
        bDescriptorType        36
        bDescriptorSubtype      2 (FORMAT_TYPE)
        bFormatType             1 (FORMAT_TYPE_I)
        bNrChannels             4
        bSubframeSize           2
        bBitResolution         16
        bSamFreqType            1 Discrete
        tSamFreq[ 0]        16000
      Endpoint Descriptor:
        bLength                 9
        bDescriptorType         5
        bEndpointAddress     0x84  EP 4 IN
        bmAttributes            5
          Transfer Type            Isochronous
          Synch Type               Asynchronous
          Usage Type               Data
        wMaxPacketSize     0x0300  1x 768 bytes
        bInterval               4
        bRefresh                0
        bSynchAddress           0
        AudioControl Endpoint Descriptor:
          bLength                 7
          bDescriptorType        37
          bDescriptorSubtype      1 (EP_GENERAL)
          bmAttributes         0x01
            Sampling Frequency
          bLockDelayUnits         0 Undefined
          wLockDelay              0 Undefined
Device Qualifier (for other device speed):
  bLength                10
  bDescriptorType         6
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  bNumConfigurations      1
Device Status:     0x0000
  (Bus Powered)

```

This is the alsa-base.conf file:
```

# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7
# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe --quiet snd-ioctl32 ; /sbin/modprobe --quiet snd-seq ; : ; }
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi && { /sbin/modprobe --quiet snd-seq-midi ; : ; }
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 && { /sbin/modprobe --quiet snd-emu10k1-synth ; : ; }
# Keep snd-pcsp from beeing loaded as first soundcard
options snd-pcsp index=-2
# Keep snd-usb-audio from beeing loaded as first soundcard
options snd-usb-audio index=-2
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2

```

Any advise would be great, because I'm currently stuck.

---

### Post by QDR06VV9 on 2015-05-15
Hi 012ddd have you tried booting with the mics already pluged in.
This is where I would start.[http://beagleboard.org/latest-images](http://beagleboard.org/latest-images) making sure you have all drivers.
And secondly just a guess here but your alsa-base.conf file: looks odd to me.(That dose not mean it is though.)
> options snd-usb-audio index=-2
Just above #Prevent abnormal drivers from grabbing index 0
I do not think that is needed I would just comment that line out.
If the first suggestion dose not help you could try to change
```
options snd-usb-audio index=-2
``` to 
index=1
Crap I forgot to have you check to see if volume levels are on or not muted.
Through the command "alsamixer" with out the quotes.
Regards

---

### Post by 012ddd on 2015-05-16
I've tried booting with the mics already plugged in, the result is always the same.

I'm almost 100% convinced that is just a matter of changing alsa-base.conf, but I've been unsuccessful so far. I was hoping to find someone who had gone through the same situation, but I'll try your suggestion whenever I can. 

alsamixer is useless because the mics aren't detected by alsa.

---

### Post by QDR06VV9 on 2015-05-16
> **012ddd said:**
> I've tried booting with the mics already plugged in, the result is always the same.

I'm almost 100% convinced that is just a matter of changing alsa-base.conf, but I've been unsuccessful so far. I was hoping to find someone who had gone through the same situation, but I'll try your suggestion whenever I can. 

_**alsamixer is useless because the mics aren't detected by alsa.**_
Yes I knew that but, you would be surprised to see how many times the the volume was muted or the level was set to 0 
I remember when pulseaudio first came into main stay me and alsa became family because it broke my sound(pulseaudio not alsa)
I became very schooled with that alsa-base.conf file.
I really think that the the line above prevent normal drivers from loaded could be removed though.;)
Found this link in a effort to help [http://www.element14.com/community/community/designcenter/single-board-computers/next-gen_beaglebone/blog/2013/05/28/bbb--audio-notes](http://www.element14.com/community/community/designcenter/single-board-computers/next-gen_beaglebone/blog/2013/05/28/bbb--audio-notes)
Kind Regards

---

