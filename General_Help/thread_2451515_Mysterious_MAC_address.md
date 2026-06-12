---
title: "Mysterious MAC address"
date: 2020-10-05
forum: General Help
---

### Post by Geoff_Lane on 2020-10-05
Folks,

When at home and using wifi analyzer on my mobile, every so often when I view the Access Point list a mystery MAC address appears.  It has a question mark where the AP name normally is.  It is on the same channel as my network plus signal strength similar to my AP.

What is odd, the MAC 52:dc:e7:dd:70:f5 shows following message;  No vendor for this MAC: 52:dc:e7:dd:70:f5. This MAC can be transmitted when a device is not associated with an access point. In this case, it can be considered randomized.

The message is puzzling, the message mentions randomized but is always the same.  

Anyone able to throw any light on this?

Geoff

---

### Post by scorp123 on 2020-10-05
> **Geoff_Lane said:**
>  The message is puzzling, the message mentions randomized but is always the same. 

Could be a VM? Softwares such as VMware, VirtualBox, KVM etc. will randomly create a MAC address for their VM's, and that made-up MAC address usually won't correspond to any official MAC range that's assigned to the various hardware manufacturers. Once the VM is configured the MAC usually stays the same afterwards. 

Or someone has manually changed their MAC address on their laptop (e.g. for privacy reasons?) and is (accidentally?) trying to connect with your network?

Also: Do you have lots of neighbours around you? I sometimes also get random MAC addresses trying to connect to my WLAN network.... those are usually mobile phones, tablets and other devices from the neighbouring apartments, briefly trying to auto-connect (which they can't) and then going away again. Also there's the main road right underneath one side of the house where I live. So sometimes I also get brief connection attempts from the devices of the people sitting in their cars while they drive by my house...

If you have lots and lots of neighbours around you and each of them is running their own WiFi network it might be worth checking out which frequency band they are all using, and then setting your network to a different frequency, so their WiFi doesn't get into the way of your's. The less crowded a WiFi frequency band is the better your WiFi performance will be.

---

### Post by Geoff_Lane on 2020-10-06
> **scorp123 said:**
> Could be a VM? Softwares such as VMware, VirtualBox, KVM etc. will randomly create a MAC address for their VM's, and that made-up MAC address usually won't correspond to any official MAC range that's assigned to the various hardware manufacturers. Once the VM is configured the MAC usually stays the same afterwards. 

Or someone has manually changed their MAC address on their laptop (e.g. for privacy reasons?) and is (accidentally?) trying to connect with your network?

Also: Do you have lots of neighbours around you? 

If you have lots and lots of neighbours around you and each of them is running their own WiFi network it might be worth checking out which frequency band they are all using, and then setting your network to a different frequency, so their WiFi doesn't get into the way of your's. The less crowded a WiFi frequency band is the better your WiFi performance will be.

Thank you for prompt reply.

I ran VirtualMachine under Windows10 but seldom actually log on to Windows.  Don't run it on Linux as BIOS doesn't allow virtualisation even though 64 bit machine :mad:

My two closest neighbours do give out strong WiFi signals but both on different channel to me.  I do keep an eye on channels as the wifi auto channel function not brilliant so I set channels manually myself.

The MAC address randomly appears then disappears but as mentioned, always my channel.

Geoff

---

