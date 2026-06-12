---
title: "USB Modem strange detection"
date: 2013-08-27
forum: General Help
---

### Post by emptycoder on 2013-08-27
I have a WiMax USB Modem which is work on Windows by mounting as CDRom, installing drivers then finally launches GUI where you enter the username and password to connect,  I have searched around and a lot of people said that Ubuntu supports many USB modems and use them under Mobile Broadband Connection.
When I plug the USB nothing happens, until I installed a linux-firmware-nonfree, Ubuntu did detect the USB but in a strange way, it shows as an unplugged wired connection, See image please.

[IMG]https://dl.dropboxusercontent.com/u/39811853/Screenshot.jpg[/IMG]

The other wire connection is a network sharing from another computer, so don't pay attention  to it.
My Question is simple, what to do next? I have no idea what to do now. 
Thanks

---

### Post by sanderj on 2013-08-27
What kind of Ubuntu / interface is that?

Have you clicked on Network Connections and Network Settings; maybe there is something to configure in the USB modem interface, like the country and APN?

If not, I'll give you some hardware command line stuff

---

### Post by emptycoder on 2013-08-27
Thanks for reply sanderj.
This is Gnome 3.4 Shell, just a user interface like Unity and KDE, anyway, I already tried that Network Connections thing, I checked my Mobile Broadband but it didn't detect it any USB modem, So I tried to create a connection manually, here's what happened:
Because Ubuntu didn't detect USB modem, the first dialog shows only a one greyed option (Any Device) then I chose (My country is not listed) which is really not, after that, it asked me for my provider name, I typed the name, with two selectable options
My provider uses GSM technology (GPRS, EDGE, UMTS, HSPA)
My provider uses CDMA technology (1xRTT, EVDO)
I don't know what those two options mean, I'm not an expert, but I tried both of them, it suppose that connection appears on the list when finish the settings but nothing happened, I searched around and I was told that if Ubuntu didn't detect the Modem the Mobile connection won't show.
Another thing that I don't get it, on my Wired section on Network settings, I see two connections, Wired Connection 1 and Wired Connection 2, the number one is an Ethernet Cable, a sharing from other computer, and number 2 is for the USB modem.
So where do we go from here?

---

