---
title: "Bluetooth blueman stops before bluetooth dongle adapter initialised"
date: 2021-02-21
forum: General Help
---

### Post by Handssolow on 2021-02-21
Like many I'm having a problem with bluetooth when running Ubuntu 20.04. I'm using the same Cambridge CSR 4.0 USB dongle that I previoulsly used until recently with 16.04, though it took me a while back then to get it working. I want to use a Bose bluetooth speaker to play music via a bluetooth link, not transfer files etc. I've been on this a week or more. Somehow 20.04 doesn't recognise that I have a bluetooth adapter connected, though lsusb does.

If I attempt to start the bluetooth gui nothing happens, I assume because no it hasn't found a bluetooth adaptor.

Over the past couple of weeks I've twice booted up to see on my desktop the dialogue windows for the BT adapter (I then choose visible), and the larger BT manager window were I've the option to search, pair and connect etc. The first time nothing much happened however, this afternoon it appeared again, and using it was able to connect to my bluetooth speaker and play music. Reboots and I'm back to having no bluetooth again.

It's as if blueman doesn't wait, if it doesn't immediatelly find a BT dongle it dies.

Is there a way to prevent this happening? I thinking it's a dbus-1 issue pulling the plug. "You have no BT dongle then I will close down this bt option to save power".

So for me this isn't a kernel issue, I'm now on 5.8.4. It's not a BT dongle driver issue. Not a bios issue or a GRUB issue, otherwise it wouldn't have worked a few hours ago, albeit once. It could be a Gnome issue and/or a bluez issue and the setting for the bluetooth manager or a dbus time out.

One observation, on the time BT worked, after I initially logged in with my password it took slightly longer for my desktop to appear, I started to think I'd make a mistake entering my password, I hadn't, when the desktop appeared there was bluetooth manager or is it blueman?

Any suggestions?

---

### Post by Handssolow on 2021-02-24
My EkoBuy CSR 4.0 USB bluetooth dongle was working previously under 16.04, although that took me a while. With 16.04's EOL approaching in April 2021, in December 2020 I ended up on 20.04 Ubuntu with Mate desktop. On my GA-FXA990-UD5 based destop PC the USB 2 and USB 3 headers are each individually connected to two sockets on a front panel. I'd been playng around with bios patching to be able to boot from a NVMe SSD PCI adapter, and exploring Manjaro on another PC and I think somewhere along the way I must have unplugged the USB bluetooth dongle. I can't explain the following findings.

I found that if the BT USB dongle was plugged into a USB 3 socket it showed up in lsusb, but bluetooth didn't work, blueman-manager stopped, the bluetooth applet didn't work, no bt icon appeared on the top toolbar. No bt adapter was found. Swapping the dongle to a USB 2 socket and it was invisible to lsusb.

I discovered yesterday though that if I plug the bt dongle into a USB 2 socket and then booted up from cold, bluetooth was fully working as expected.

The same is the case if I boot from a live DVD of Ubuntu Mate, OK plugged into USB 2 not in USB 3. There's nothing on any of the three BT USB dongles' instruction leaflets that I now have, that refers to which USB socket version they work with.

Bottom line, you having a problem with bluetooth? Check what happening if you cold boot with the BT dongle in a USB 2 socket.

---

