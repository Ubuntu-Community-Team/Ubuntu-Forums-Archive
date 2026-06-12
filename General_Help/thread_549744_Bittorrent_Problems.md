---
title: "Bittorrent Problems"
date: 2007-09-13
forum: General Help
---

### Post by fattom23 on 2007-09-13
I'm having huge problems with all of my bittorrent applications.  I've tried the default bt client, azureus, bittornado, and even the WOW updater.  All of these applications give either extremely low download speeds (1-2 kB per second) or stop altogether.  I have used firestarter to open ports 6881-6999 and the recommended ports for the Blizzard Downloader, but it hasn't helped at all.  What kinds of things should I be looking at, as bittorrent works just fine under windows on the same box.  Any help you could give would be appreciated, although I've tried enough applications to assume that changing the client is not going to help at all.  Anyway, thanks for taking the time to read this and at least trying to help.  Peace.

---

### Post by chewearn on 2007-09-13
Do you have a hardware router between your computer and the internet (have you set-up port forwarding in your router) ?

---

### Post by Chilongola on 2007-09-13
Ktorrent or Deluge.  I personally find Deluge much better. With a 128 connection presently downloading at  15 kib/s

---

### Post by felker2 on 2007-09-13
Are you behind a NAT device (ADSL modem, router, etc)? If so, have you done the port forwarding in that NAT device to your Linux system? Have you checked the IP adress you're forwarding to is indeed the IP adress of your Ubuntu system?
BTW: I myself use UPnP to let the port forwarding happen automagically. If you want to do it manually, there is info on [http://portforward.com/routers.htm]("http://portforward.com/routers.htm")

When downloading with Azureus, do you see green happy faces? Do you see "NAT OK" in the bottom bar of Azureus?

In Azureus, what does Tool -> NAT / Firewall test -> Test tell you? And is the port number you're seeing there the same has you have opened up in your firewall Firestarter?

---

### Post by fattom23 on 2007-09-13
I am not behind a hardware router and I have opened the correct port in firestarter.  I keep thinking that it has to have something to do with the fact that I'm using bittorrent.  Thanks for the help so far, and I just want to stress that it runs slowly no matter what client I use, and that I have normal speeds when downloading with http and ftp.  Also, bittorrent runs fine under windows, so I know it's not my ISP throttling my speeds.  Thanks, and any suggestions would be greatly appreciated.

---

### Post by felker2 on 2007-09-13
> **fattom23 said:**
>  Thanks, and any suggestions would be greatly appreciated.

I gave you a few suggestions to check (see above: azureus' faces, azureus' self-check), so I guess you will follow-up to that?

---

### Post by fattom23 on 2007-09-13
Sorry I forgot to respond to those suggestions.  I do get the green dot for NAT OK and my faces typically vary between read and green, even for the same torrent.  I would think that it was a poorly seeded torrent, but I had one last night that had 114 seeds and was still going about as slow as dirt.  Anyway, thanks a lot for the helpful suggestions.

---

