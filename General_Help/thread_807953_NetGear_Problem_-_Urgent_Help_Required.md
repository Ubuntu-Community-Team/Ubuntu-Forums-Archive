---
title: "NetGear Problem - Urgent Help Required"
date: 2008-05-26
forum: General Help
---

### Post by GCoffee on 2008-05-26
Hello All,

I am having a problem with my NetGear Wireless network, and quite frankly, I have had enough.

The internet simply conks out, The wireless displays fine, the pc downstairs has connection problems to - the one which is connected to the router.. The laptop however is fine - and it isn't connected to the router and has a inbuilt wireless device.

So I'm guessing it is  my wireless adpater which is the problem. It's a usb one. WG111v2. I have tried everything from changing the usb port it is in to throwing it across the room - to no avail.

Please Help!
GCoffee.

---

### Post by GCoffee on 2008-05-26
bump - all suggestions welcome!

---

### Post by prshah on 2008-05-29
> **GCoffee said:**
> 
The internet simply conks out, 

So I'm guessing it is  my wireless adpater which is the problem. It's a usb one. WG111v2. 

There is a known problem with the Windows 98 driver of this particular adapter. If you are using ndiswrapper (and I'm pretty sure you are), make sure you have not used it with the Windows 98 version of the Windows drivers. Get the XP drivers and use ndiswrapper with that.

If you are already using the XP drivers then I don't have a clue. Do you have a dual boot to check if the adapter works fine in XP?

---

### Post by WRDN on 2008-05-29
Im using the same adapter, and since 8.04 was released, it seems to work fine.

As prshah said, you can use the ndiswrapper tool and install the Windows 98 driver. Sometimes it will work straight away, you may have to blacklist the other driver though.

[Guide]("http://ubuntuforums.org/showthread.php?t=212365")
[Another Guide]("http://wawob.blogspot.com/2007/02/install-netgear-wg111v2-usb-device-on.html")

---

### Post by prshah on 2008-05-29
> **WRDN said:**
> 
As prshah said, you can use the ndiswrapper tool and install the Windows 98 driver. 

Err.. I said _not_ to use the Windows 98 driver. There is a known bug in it that exactly produces the OP's problem.

---

### Post by WRDN on 2008-05-29
> **prshah said:**
> Err.. I said _not_ to use the Windows 98 driver. There is a known bug in it that exactly produces the OP's problem.

Ah sorry, I misread your post.
Ive used the Windows 98 driver before, and its worked fine for me.

---

