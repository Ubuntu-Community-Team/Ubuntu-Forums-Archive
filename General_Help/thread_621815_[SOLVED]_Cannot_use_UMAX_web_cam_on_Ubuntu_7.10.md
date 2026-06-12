---
title: "[SOLVED] Cannot use UMAX web cam on Ubuntu 7.10"
date: 2007-11-24
forum: General Help
---

### Post by PmDematagoda on 2007-11-24
I just tried using my UMAX AstraPix PC 210 but it simply does not work:(, I tried to use it through Skype and yet it would only give a green output without the hint of a picture and when I tried using the web cam using Camorama Webcam Viewer it simply told me that it could not connect to the video device and told me to check the connection but the connection was good. 

I would really appreciate any help received.

---

### Post by hikaricore on 2007-11-24
After plugging the device in, you should probably check the output of:

> dmesg

From a terminal.  This will show you if the device is being recognized.  Posting the output here may allow someone to point you in the right direction as well.
You may also want to do an internet (google, yahoo, whatever) search of something like:

*"UMAX AstraPix PC 210" Linux*

To see if there are any sollutions elsewhere, or anyone saying if this device functions under Linux in the first place.

Be aware that there are thousands of different devices like webcams in existence and they may not all be supported correctly yet due to the manufacturers not providing proper data for drivers to be written.

Hope this helps,

--Aaron

---

### Post by PmDematagoda on 2007-11-24
Thanks for the reply hikaricore, here is what I get for the USB web camera from dmesg:-
```

[ 2476.806917] usb 1-1: new full speed USB device using uhci_hcd and address 5
[ 2476.969573] usb 1-1: configuration #1 chosen from 1 choice
[ 2477.301694] Linux video capture interface: v2.00
[ 2477.438213] sn9c102: V4L2 driver for SN9C1xx PC Camera Controllers v1:1.44
[ 2477.441211] usb 1-1: SN9C103 PC Camera Controller detected (vid:pid 0x0C45:0x608F)
[ 2477.543609] usb 1-1: OV7630 image sensor detected
[ 2477.687165] usb 1-1: Initialization succeeded
[ 2477.687323] usb 1-1: V4L2 device registered as /dev/video0
[ 2477.687328] usb 1-1: Optional device control through 'sysfs' interface disabled
[ 2477.687601] usbcore: registered new interface driver sn9c102
[ 2477.692560] usbcore: registered new interface driver snd-usb-audio
[ 2520.161757] compat_ioctl32: v4l2 ioctl VIDIOC_S_PARM, dir=rw (0xc0cc5616)
[ 2520.161894] ioctl32(skype:7245): Unknown cmd fd(18) cmd(c0cc5616){t:'V';sz:204} arg(f41b9e50) on /dev/video0
[ 2520.178282] compat_ioctl32: v4l2 ioctl VIDIOC_S_PARM, dir=rw (0xc0cc5616)
[ 2520.178503] ioctl32(skype:7245): Unknown cmd fd(18) cmd(c0cc5616){t:'V';sz:204} arg(f41b9e20) on /dev/video0
[ 2812.796141] usb 1-1: Device /dev/video0 is busy...
[ 3060.683761] usb 1-1: USB disconnect, address 5
[ 3060.683985] usb 1-1: Disconnecting SN9C1xx PC Camera...
[ 3060.683990] usb 1-1: V4L2 device /dev/video0 deregistered
[ 3071.511584] usb 1-2: new full speed USB device using uhci_hcd and address 6
[ 3081.651958] usb 1-2: configuration #1 chosen from 1 choice
[ 3334.312826] hub 1-0:1.0: port 2 disabled by hub (EMI?), re-enabling...
[ 3334.312835] usb 1-2: USB disconnect, address 6
[ 3340.277568] usb 1-1: new full speed USB device using uhci_hcd and address 8
[ 3340.447892] usb 1-1: configuration #1 chosen from 1 choice
[ 3340.452763] usb 1-1: SN9C103 PC Camera Controller detected (vid:pid 0x0C45:0x608F)
[ 3340.551412] usb 1-1: OV7630 image sensor detected
[ 3340.689975] usb 1-1: Initialization succeeded
[ 3340.690022] usb 1-1: V4L2 device registered as /dev/video0
[ 3340.690030] usb 1-1: Optional device control through 'sysfs' interface disabled

```

And I did try googling any instructions on how to get this web cam to work, even searched for any Linux drivers for it on the UMAX website, but to no avail:(.

---

### Post by hikaricore on 2007-11-24
> **PmDematagoda said:**
> Thanks for the reply hikaricore, here is what I get for the USB web camera from dmesg:-
```

[ 2476.806917] usb 1-1: new full speed USB device using uhci_hcd and address 5
[ 2476.969573] usb 1-1: configuration #1 chosen from 1 choice
[ 2477.301694] Linux video capture interface: v2.00
[ 2477.438213] sn9c102: V4L2 driver for SN9C1xx PC Camera Controllers v1:1.44
[ 2477.441211] usb 1-1: SN9C103 PC Camera Controller detected (vid:pid 0x0C45:0x608F)
[ 2477.543609] usb 1-1: OV7630 image sensor detected
[ 2477.687165] usb 1-1: Initialization succeeded
[ 2477.687323] usb 1-1: V4L2 device registered as /dev/video0
[ 2477.687328] usb 1-1: Optional device control through 'sysfs' interface disabled
[ 2477.687601] usbcore: registered new interface driver sn9c102
[ 2477.692560] usbcore: registered new interface driver snd-usb-audio
[ 2520.161757] compat_ioctl32: v4l2 ioctl VIDIOC_S_PARM, dir=rw (0xc0cc5616)
[ 2520.161894] ioctl32(skype:7245): Unknown cmd fd(18) cmd(c0cc5616){t:'V';sz:204} arg(f41b9e50) on /dev/video0
[ 2520.178282] compat_ioctl32: v4l2 ioctl VIDIOC_S_PARM, dir=rw (0xc0cc5616)
[ 2520.178503] ioctl32(skype:7245): Unknown cmd fd(18) cmd(c0cc5616){t:'V';sz:204} arg(f41b9e20) on /dev/video0
[ 2812.796141] usb 1-1: Device /dev/video0 is busy...
[ 3060.683761] usb 1-1: USB disconnect, address 5
[ 3060.683985] usb 1-1: Disconnecting SN9C1xx PC Camera...
[ 3060.683990] usb 1-1: V4L2 device /dev/video0 deregistered
[ 3071.511584] usb 1-2: new full speed USB device using uhci_hcd and address 6
[ 3081.651958] usb 1-2: configuration #1 chosen from 1 choice
[ 3334.312826] hub 1-0:1.0: port 2 disabled by hub (EMI?), re-enabling...
[ 3334.312835] usb 1-2: USB disconnect, address 6
[ 3340.277568] usb 1-1: new full speed USB device using uhci_hcd and address 8
[ 3340.447892] usb 1-1: configuration #1 chosen from 1 choice
[B][ 3340.452763] usb 1-1: SN9C103 PC Camera Controller detected (vid:pid 0x0C45:0x608F)
[ 3340.551412] usb 1-1: OV7630 image sensor detected
[ 3340.689975] usb 1-1: Initialization succeeded
[ 3340.690022] usb 1-1: V4L2 device registered as _/dev/video0_[/B]
[ 3340.690030] usb 1-1: Optional device control through 'sysfs' interface disabled

```

And I did try googling any instructions on how to get this web cam to work, even searched for any Linux drivers for it on the UMAX website, but to no avail:(.

Well it definately is being recognized as per the section I've bolded and underlined.
It's being mounted at /dev/video0 so I can't imagine why it isn't working.  O.o

I've only ever used a webcam twice and it just worked, hopefully someone else can give you some pointers.

---

### Post by PmDematagoda on 2007-11-28
I still haven't managed to solve my problem, does anyone have anyway of solving this please?

---

### Post by loell on 2007-11-28
so its been recognized, can you

```
lsmod | grep videodev
```

let us see what driver it uses.

---

### Post by PmDematagoda on 2007-11-28
Here is the output I got:-
```

videodev               31360  1 sn9c102
v4l1_compat            15364  1 videodev
v4l2_common            21888  3 sn9c102,compat_ioctl32,videodev

```

---

### Post by loell on 2007-11-28
it uses the sonix based webcam driver.

searching a bit, I think this webcam is a no go :(

---

### Post by PmDematagoda on 2007-11-28
> **loell said:**
> it uses the sonix based webcam driver.

searching a bit, I think this webcam is a no go :(

That is what I thought so too when I searched around for it but I decided to have some hope that maybe now a fix has been made for this issue, it seems there has not been a fix made for this issue as of now. No matter, I will most likely purchase a new webcam, the UMAX one was getting too old anyway.

Could anyone suggest a good webcam that would work with Linux/Ubuntu out of the box?

---

### Post by loell on 2007-11-28
yeah,
 you can print [this]("http://mxhaard.free.fr/spca5xx.html") before buying a webcam.

and since you mentioned skype, you can then cross reference this [https://wiki.ubuntu.com/SkypeWebCams]("https://wiki.ubuntu.com/SkypeWebCams")

---

### Post by PmDematagoda on 2007-11-28
> **loell said:**
> yeah,
 you can print [this]("http://mxhaard.free.fr/spca5xx.html") before buying a webcam.

and since you mentioned skype, you can then cross reference this [https://wiki.ubuntu.com/SkypeWebCams]("https://wiki.ubuntu.com/SkypeWebCams")

Thanks for the links loell, they are really helpful:).

---

### Post by Koppie on 2007-12-02
Wait a sec.  I have the same problem.  My webcam worked fine under Feisty, even when I upgraded Feisty to the Gutsy beta.  But when Gutsy final came out, I wiped my partition and reinstalled, and since then the webcam has green video.  Looks like there have been problems in the past with the sn9c102 driver in various linux kernels, especially 2.6.5.  I guess those problems were fixed but now they're back.

But what does "no go" mean?  Has sn9c102 support been deprecated in 2.6.22?  If so, why can my computer see the camera and even recognizes the correct driver?  I tried a bunch of fixes from various places and restarted my system and tried different programs and it didn't help.

I just don't understand why Gutsy wouldn't support it if Feisty did.  Do I really need to give up on this and get a new webcam?

---

### Post by loell on 2007-12-03
the sonix webcam driver or sn9c102 , has been there since 2004 i guess , if it worked for you in fiesty and flawlessly, I think you should report this to launchpad, so you can use it in time  for hardy :)

---

### Post by RavanH on 2007-12-03
Similar problem here :( (except I do not even get a green screen, just nothing)

After connecting my webcam to a USB port, dmesg reports:
```
[ 1712.368017] usb 1-2: new full speed USB device using ohci_hcd and address 4
[ 1712.472811] usb 1-2: configuration #1 chosen from 1 choice
[ 1712.475711] usb 1-2: SN9C120 PC Camera Controller detected (vid:pid 0x0C45:0x613C)
[ 1712.516198] usb 1-2: HV7131R image sensor detected
[ 1712.998992] usb 1-2: Initialization succeeded
[ 1712.999026] usb 1-2: V4L2 device registered as /dev/video0
[ 1712.999030] usb 1-2: Optional device control through 'sysfs' interface disabled
[ 1713.002480] usbcore: registered new interface driver gspca
[ 1713.002671] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/gspcav1/gspca_core.c: gspca driver 01.00.12 registered
```

Then after trying camorama (and getting the "check connection" error) dmesg has a new line:
```
[ 1784.400771] usb 1-2: usb_submit_urb() failed, error -28
```

I noticed a permission issue on /dev/video0 so (as suggested on another thread) I added my username to the video group ```
sudo gpasswd -a MY_USERNAME video
``` but that did not change much, only the permission error in dov4l...

Anyone any ideas? 

Oh, and why is this thread marked [SOLVED] if that solution is nothing more then "buy a new device" !?! Please un-mark it again.

---

### Post by loell on 2007-12-03
> **RavanH said:**
> 
Oh, and why is this thread marked [SOLVED] if that solution is nothing more then "buy a new device" !?! Please un-mark it again.

it is the OP's prerogative, I would recommend you to make another thread.

---

### Post by manoynmonic on 2008-03-30
This works.  Poor picture quality, but works on my machine with UMAX PC210.

[http://nixbit.com/cat/multimedia/graphics/sn-webcam/](http://nixbit.com/cat/multimedia/graphics/sn-webcam/)

---

### Post by rickyrockrat on 2008-05-28
The -28 problem is because you have another USB device plugged into the same hub (by hub, I mean motherboard hub). Even plugging in another hub will cause this issue.  I also removed my bluetooth driver since I don't have any bluetooth devices.

-28 is a "no space left on device" and in this case it means not enough bandwidth.

Cheers.

---

