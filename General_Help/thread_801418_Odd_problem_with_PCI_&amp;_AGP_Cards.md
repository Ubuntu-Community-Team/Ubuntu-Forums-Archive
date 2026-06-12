---
title: "Odd problem with PCI &amp; AGP Cards"
date: 2008-05-20
forum: General Help
---

### Post by Het Irv on 2008-05-20
I was recently given a new video card that was better than my old card, so I popped in the new card, and while it works great... I think it broke everything else.

After replacing the card, my wireless and sound cards have stopped working.  I cannot find any problems with my speakers, wireless network, or alsamixer.  If I undo all changes, Wireless will work but sound will not.

Specs:  
Old Video - ATI Radeon 9200 128mb
New Video - Nvidia Geforce FX 5500 256 mb
Wireless  - Linksys WMP54gs (broadcom chipset)
Sound     - Creative SoundBlaster 24-bit  (does not show in lspci)

I have tried replacing my 250w Power Supply with a 350w, but that did not help.

EDIT: PCI cards work better when fully plugged in, so sound works now, but Wireless is still an issue, I can see my home network, but not connect to it.

---

### Post by Het Irv on 2008-05-20
Okay so I found some more information
in /var/log, there is a line that says "Old device 'wlan0' activating, won't change."

Research on that line give one soultion as being to install Wicd.  That doesn't work.

---

### Post by cprofitt on 2008-05-21
I am glad you found the loose card... was that after we talked on IRC?

Can you give me a better description of what happens when you try to connect to your home network? Are you using WEP, WPA or any other security?

---

### Post by Het Irv on 2008-05-22
I this problem has changed so much now...

I reinstalled on one of my drives and everything is in working order.  My only consern is that my wireless is only connecting at very low speeds.... very, very, low.

No security, and it takes a while. (30~45 seconds) after boot for the wireless to actually connect.  It seems like the card is just very slow, I know Internet is fine because I was playing on Xbox Live earlier


Oh yeah, And Gnome Crashes when I click on the shutdown/log off icon at the top.

---

### Post by Het Irv on 2008-06-02
okay I guess I better update this again.

I don't think this is a problem with the cards them selves any more, but the firmware.  More specifically the Nvidia Restricted Drivers.  Everything works fine as long a the Nvidia Drivers have been installed on the system.  I plan to but a temporary Windows Partiton on just to make sure that they will work together and it is the Drivers.

---

