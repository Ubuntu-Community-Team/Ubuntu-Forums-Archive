---
title: "LUbuntu Leave/Shutdown, Leave/Reboot etc question"
date: 2020-11-09
forum: General Help
---

### Post by David_Partridge on 2020-11-09
When I login to my Lubuntu 20.04.1 system using X2Go, when I end the session using Leave/Logout I get logged out as expected.

If I select Leave/Shutdown I get logged out, but the system doesn't actually shutdown, and similarly for the other actions (Reboot etc.).

I'm guessing this is some sort of configuration issue - so how do I configure this so I can take those actions.

Thanks
David

---

### Post by TheFu on 2020-11-09
On MS-Windows, over an RDP session, the shutdown option isn't available. Could it be that LUbuntu is following that lead?
If you want to shutdown the system, you can definitely open a terminal and run
```
sudo shutdown now
```
or if you want to wait 1 minute:
```
sudo shutdown
```

This assumes the current userid is in the sudo group.

---

### Post by David_Partridge on 2020-11-09
Yes, of course I can use sudo, but that's messy as it leaves the session hanging until the shutdown/reboot or whatever has finished.  When I used XDMCP it "just worked", but now LUbuntu has change to LXQt, I can't use that anymore.

D.

---

### Post by TheFu on 2020-11-09
> **David_Partridge said:**
> Yes, of course I can use sudo, but that's messy as it leaves the session hanging until the shutdown/reboot or whatever has finished.  When I used XDMCP it "just worked", but now LUbuntu has change to LXQt, I can't use that anymore.

D.

I tested this yesterday for another thread here and didn't find any hanging sessions, just the window was left open until the timeout. Since I knew the VM was shutdown, I just closed/minimized that window.  Wouldn't be hard to assign a accel-key to do both the shutdown and minimize the window.  Wayland is breaking some things as other things are improving.  If your desktop runs inside a VM and your client is on the same LAN, then you can use SPICE which is freaky fast, but for over-the-internet GUI desktops, x2go is still probably the best option.  I've not figured out how to use SPICE to a desktop running directly on hardware.

---

