---
title: "[SOLVED] Brother printer on printserver"
date: 2007-11-08
forum: General Help
---

### Post by Go_Bucks on 2007-11-08
My wife has a Brother MFC-7820N multifunction printer attached to a Linksys MPSM-54G printserver. I have followed instructions in numerous places on here for how to set up a print server and have tried numerous protocols. On both of our computers (running Gutsy) I can get an initial connection to the printer using http: or ipp: and can print a test page successfully. Each time I get a test page I cheer, as theoretically that means my set-up works. Afterward, however, I am NEVER able to print from any program I try... I just get numerous pages of gibberish out of the printer. Any ideas?

I know the printer will work directly connected, the problem is that the fax line is on the opposite side of the room from the desks (the printer sits on a large shelf) and reconfiguring the layout of the room is not an option.

---

### Post by civic_si on 2007-11-08
I am running an older brother mfc 9600 on a HP Jet Direct print server and everything works fine. I just point mine to the ip address of the jet direct with the printer drivers and it works. in the gui under the printers this is how my url is socket://192.168.1.11:9100 the port should probably be the same.

---

### Post by Go_Bucks on 2007-11-08
Thanks, but that URI didn't work (and I did replace yours with the ip address of my print server).

---

### Post by Go_Bucks on 2007-11-08
bump

---

### Post by dcstar on 2007-11-08
> **Go_Bucks said:**
> My wife has a Brother MFC-7820N multifunction printer attached to a Linksys MPSM-54G printserver.
..........

I don't really understand why a printer with built-in networking is connected to an external print server (unless it is used as a Wireless LAN bridge.......)

You should either connect the printer to the bridge using it's network connection and use the 7820N setup, or treat it as a non-networked printer (MFC-7820 drivers, assuming you have that option) if it is connected via USB to the print server.

---

### Post by Go_Bucks on 2007-11-08
> **dcstar said:**
> I don't really understand why a printer with built-in networking is connected to an external print server (unless it is used as a Wireless LAN bridge.......)

You should either connect the printer to the bridge using it's network connection and use the 7820N setup, or treat it as a non-networked printer (MFC-7820 drivers, assuming you have that option) if it is connected via USB to the print server.

It is my wife's printer... I didn't even know there was a network interface on it until you said that and low and behold... I am working on getting that set up now. Thanks!

---

