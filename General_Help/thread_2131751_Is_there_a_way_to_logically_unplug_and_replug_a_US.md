---
title: "Is there a way to logically unplug and replug a USB device to achieve the same result"
date: 2013-04-02
forum: General Help
---

### Post by KillerKelvUK on 2013-04-02
Hi, not sure whether what I'm seeking here has an appropriate equivalent in linux...

I have a USB DVB-S2 adapter, have the firmware files in /lib/firmware.  I'm periodically seeing issues that look like the device isn't responding properly and when I've unplugged and replugged the USB cable the issue is reset and I'm back to normal.  I'm still debugging and am new'ish to linux so am wondering whether there is a more appropriate way to do what I'm doing or whether a physical disconnection/reconnection is the only method?

I realise any DVB issues are more specialised that this group is intended for so I'll save those and post where appropriate so I guess I'm looking for a generic command set that would work for a variety of usb connected device types?

Thanks all,

K

---

### Post by Bashing-om on 2013-04-02
KillerKelvUK; Hi !

When ready to disconnect the usb devices do you "safely remove drive" them. Either from the file manager or from the terminal ?

In order not to produce file errors, the devices MUST be unmounted; linux uses a cache for file operations, this cache is not written to disk until the device is "unmounted".

Terminal method I use:
```
ls /media  ##gives the device identifier(s) ->8023-774f
sudo umount /media/8023-774f
```[INDENT=2]
hope this helps

[/INDENT]

---

### Post by Paqman on 2013-04-02
> **Bashing-om said:**
> 
When ready to disconnect the usb devices do you "safely remove drive" them. Either from the file manager or from the terminal ?


DVB is a digital video standard, so the OP isn't talking about a storage device here. I doubt a TV tuner would be mounted in /media would it?

---

### Post by Bashing-om on 2013-04-02
oopps -- that is jumping to a erroronious conclusion !

Good you are reading ..

---

### Post by KillerKelvUK on 2013-04-03
Hi both, thanks for the interest...my devices are, to the best of my knowledge, only present in the /dev tree.  I believe they are /dev/dvb/adapator0/...

---

### Post by KillerKelvUK on 2013-04-03
Okay so have been reading more on this subject and I've not yet worked up the courage to start playing round...partly because I can't get my dvb device connected inside a VirtualBox so am doing this all on production.

Is the solution I'm looking for to simply unload the firmware from the device?  I've had to ensure the correct .fw files are located within /lib/firmware and when the device is connected the dmesg output shows that it needs to load said .fw file to enable it.  Is there a way for me to force unload and reload the firmware...is this modprobe?

---

### Post by btindie on 2013-04-03
It's easy enough to remove the device with [this]("http://www.linuxmantra.com/2011/03/remove-usb-device-from-command-line.html"), but it doesn't appear to be possible to rescan the usb bus to detect it again.
```
echo 1 | sudo tee /sys/bus/usb/devices/usb1/remove
```
which would be the preferred way as it only affects a single device.

Where as the [below]("http://abunchofbaloney.blogspot.co.uk/2012/11/reset-usb-ports-in-ubuntu-1210.html") works fine but it causes everything on the bus to first be removed.```
echo "00:1a.0" | sudo tee /sys/bus/pci/drivers/ehci_hcd/unbind
echo "00:1a.0" | sudo tee /sys/bus/pci/drivers/ehci_hcd/bind
```
'ehci_hcd' is the driver for the usb hub, it may be ohci or xhci depending on your hardware.

The other method involves building a small C [application]("http://gconfig.blogspot.co.uk/2012/07/how-to-reset-usb-device-in-linux.html") which may be the best method.

---

### Post by KillerKelvUK on 2013-04-03
@btindie, thank you I'll give the C application a try, appreciate the help.

K

---

### Post by KillerKelvUK on 2013-04-03
@btindia, kudos...the c application did exactly what I needed it to.  No more pot-holing under the desk to unplug/replug my dvb box :-)

---

