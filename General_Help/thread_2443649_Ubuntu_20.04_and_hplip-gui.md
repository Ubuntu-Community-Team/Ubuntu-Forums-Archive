---
title: "Ubuntu 20.04 and hplip-gui"
date: 2020-05-18
forum: General Help
---

### Post by jimbuntu1968 on 2020-05-18
Hi all,

I wonder if anyone can help me with an issue I am having with my HP Envy 5020 printer. The printer can be connected either wirelessly or via USB and it gets installed automatically by Ubuntu.
The problem is when I install the hplip-gui package and run the HPLIP Toolbox. This allows me to then see more detail about the printer such as ink levels. 
When I run the setup it asks what type of connection do I want to use, 1, USB 2, Network/Ethernet/Wireless network (direct connection or JetDirect) 3, Wireless/802.11(requires a temporary USB connection and is only available for select devices)
Previously I have selected option 3, clicked next at which point it lists my printer and then I click next, it then asks for wi-fi details etc and then completes, tells me to remove the USB cable and go to hp-setup 192.168.0.13 to finalise installation after which I can see the ink levels and scan directly from the HPLIP Toolbox.
Since installing a fresh copy of 20.04 when I run the setup up I get the choose connection option, plug in the USB lead and click next, it lists my printer on the next screen but when I highlight it and click next I get a communication error, an I/O error occurred Please check the USB connection to your printer and try again. (Device I/O error)
I can confirm the USB cable is OK, which would make sense as it detects the printer over USB, but to be sure I have tried the cable in a different PC and printer. I have also tried another cable.
I have also tried running a live USB of 20.04 as my actual install is the minimal version so I wondered if that was the issue, same thing. I have tried a live USB with Kubuntu 20.04 and the same thing. I then tried with a live USB of 18.04 and the printer installed perfectly!
Can anyone shed any light on this please, whether it's the hplip-gui package causing the problem or some other packages that haven't been included in the 20.04 ISO?

Thanks

James

---

