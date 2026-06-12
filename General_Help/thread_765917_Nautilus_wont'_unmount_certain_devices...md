---
title: "Nautilus wont' unmount certain devices.."
date: 2008-04-24
forum: General Help
---

### Post by Sweet Spot on 2008-04-24
I just bought a Sansa View the other day, and it initially worked just fine. In order to get Ubuntu/Linux to see it as a MSC device, you have to put it in lock position, hold left on the D pad and plug in the usb cable. At that point, Nautilus opens, and shows the contents of the DAP, and allows drag and drop transfers.  Yesterday, this worked fine, and right clicking on the Sansa drive then selecting unmount, would work flawlessly. It would simply unmount, and then I'd get a message saying not to unplug until data was finished being written to the device. 

So it would do it's thing, then say ok to disconnect. Today, I get a message saying "Can Not Unmount Volume. Can not unmount the volume Sansa View"  Details: can not remove directory"  So I hit ok, and get an exclamation point pop up. 

This has happened also with my Sony W810i Phone, when it didnt' used to. I don't know if this behavior is due to some miscommunication error, or what ?  I have no other choice but to disconnect the DAP. So. disconnected, the dap's database is refreshing anyway, and the files and folders are there, but I can't help but think that this behavior is still abnormal because it wasn't this way yesterday. And I'd rather be told that data is being written to the device and then to disconnect, rather than carelessly do so.

Any ideas about this ?

doug

---

### Post by natrixgli on 2008-04-24
Do you have any nautilus windows displaying contents of the device at the time? Or what about the terminal? 

What happens if you try to unmount it using 'sudo umount /dev/sdxx' (where xx=the appropriate letter/partition number for your device)

-n8

---

### Post by Sweet Spot on 2008-04-25
> **natrixgli said:**
> Do you have any nautilus windows displaying contents of the device at the time? Or what about the terminal? 

What happens if you try to unmount it using 'sudo umount /dev/sdxx' (where xx=the appropriate letter/partition number for your device)

-n8

For question #1, perhaps this is possible. Should I direct the view to a different folder before trying to unmount first ?  For the second question... There is no letter or partition number. It's simply listed as SANSA VIEW (as shown, I'm not shouting). I tried it with that, but says it can't find it. 

Doug

---

### Post by Sweet Spot on 2008-04-25
Incidentally, when I reopen Nautilus, I can see the Sansa View on the right side where the devices are, and can once again mount that volume. But now, it seems that when I unmount... Wait !

This is so weeeeird... 

I was playing around with Nautilus, going from the DAP's directory, to other ones, trying to mount and unmount while in it, and out of it. Then all of a sudden, I unmounted and was told to safely disconnect ! This is really erratic behavior !

---

