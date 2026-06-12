---
title: "Android tablet via usb"
date: 2024-04-03
forum: General Help
---

### Post by phatton1 on 2024-04-03
I'm currently using Ubuntu Cinnamon 22.04 and am trying to connect a Lenovo tablet via usb.
When I connect it.... nothing happens. The device starts charging, but doesn't appear as an external device.
No messages on either tablet or on screen.
Can someone point me in the correct direction please.
I know that the usb port(s) are ok , and the tablet is ok, along with it's own port.
TIA

---

### Post by ajgreeny on 2024-04-03
You may need to go to **"Connected devices"** in the tablet's Settings and make the appropriate changes there.

---

### Post by TheFu on 2024-04-03
Some tablets aren't recognized, so you may need to tell Ubuntu about it (or any Linux).  Also, MTP support may not be enabled without installing a few packages first. Then you'll need to ensure any bridge packages are installed to connect the file manager to the underlying MTP tools. That is usually some sort of gvfs-{something} package.

Don't forget to check that the cable being used isn't just a charging cable, but is also a data cable too.  My tablet shipped with a charging only cable, so no data connections worked.  Additionally, I had to enable developer mode in Android to enable some USB connection types before it finally worked.  I ended up using **scrcpy** and **rsync** to get data to/from the tablet when performance is important.  

**When I have more time, I actually use NextCloud between my Nextlcloud server and my Android devices, but this requires running a full NextCloud server to make use of it.  Using Ubuntu snaps can easily install and keep a NextCloud server running. It is nearly a 1-click install that can run on any Linux computer from the largest server to a Raspberry Pi v2.**

The cable issue is extremely common.  When traveling, having a charge-only cable can prevent malware installation over that connection from airport and other USB charging ports.  I need to clearly label my cables once I figure out (again) which cable is which.

---

### Post by sudodus on 2024-04-03
My answer at the following link (describing how to transfer data to an android phone) may be useful also for this case with an android tablet.

[How do I connect my android smartphone to my PC through USB and transfer files?](https://askubuntu.com/questions/1489434/how-do-i-connect-my-android-smartphone-to-my-pc-through-usb-and-transfer-files/1489478#1489478)

---

### Post by phatton1 on 2024-04-04
Thanks ajgreeny, it worked a treat

Thanks also to TheFu and Sudodos for the suggestions

---

### Post by TheFu on 2024-04-04
> **phatton1 said:**
> Thanks ajgreeny, it worked a treat

Thanks also to TheFu and Sudodos for the suggestions

If this is **SOLVED**, please, please, use the _Thread Tools_ button to mark it that way. Help the community out!

---

