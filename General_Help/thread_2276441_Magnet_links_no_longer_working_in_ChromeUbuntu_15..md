---
title: "Magnet links no longer working in Chrome/Ubuntu 15.04"
date: 2015-05-02
forum: General Help
---

### Post by EssG on 2015-05-02
Wondering if anyone else is experiencing this issue: I click on a magnet link in chrome, and Deluge (the associated program) will start up, but no torrent will be added. I never had to configure this in previous versions of Ubuntu. Any help would be appreciated.

---

### Post by axerun on 2015-05-02
There is a bug somewhere.. :-)

[https://bugzilla.gnome.org/show_bug.cgi?id=748600](https://bugzilla.gnome.org/show_bug.cgi?id=748600)

Rune

---

### Post by kikoff on 2015-07-20
Have anyone found a fix yet? Getting pretty desperate for a solution.

---

### Post by howefield on 2015-07-20
Yep, chrome not opening magnet link sure is a pretty dire situation, rofl. :)

Thought this was fixed, can you give me a suitable link to try.. by suitable I mean legitimate and above board.

---

### Post by carlo-becchi-web on 2015-09-13
Hi howefield.
As it is today, the problem is still there.
Please try:

[http://www.openoffice.org/distribution/p2p/magnet.html](http://www.openoffice.org/distribution/p2p/magnet.html)

---

### Post by monkeybrain20122 on 2015-09-13
> **carlo-becchi-web said:**
> Hi howefield.
As it is today, the problem is still there.
Please try:

[http://www.openoffice.org/distribution/p2p/magnet.html](http://www.openoffice.org/distribution/p2p/magnet.html)

Qbittorrent opened as expected but complained that magnet link not recognised. But the same happens in FF, so maybe it is your link.

---

### Post by cdysthe on 2015-10-02
> **monkeybrain20122 said:**
> Qbittorrent opened as expected but complained that magnet link not recognised. But the same happens in FF, so maybe it is your link.

Hi,

This is still a problem. Anyone found a solution?

---

### Post by cariboo on 2015-10-02
> **monkeybrain20122 said:**
> Qbittorrent opened as expected but complained that magnet link not recognised. But the same happens in FF, so maybe it is your link.

I get the same thing in Chromium, Qbittorrent opens, but there is no link, I'd suggest there may be something wrong with the link on the OpenOffice page, as I have no problem with magnetic links on other sites.

---

### Post by howefield on 2015-10-02
> **cariboo said:**
> I get the same thing in Chromium, Qbittorrent opens, but there is no link, I'd suggest there may be something wrong with the link on the OpenOffice page, as I have no problem with magnetic links on other sites.

+1

Seems to be working here (Chromium 45.0.2454.85 and Transmission 2.84 (14307)), just trying some random magnet links.

Only issue is torrent options window comes up blank, however the link is added to download window once the "Open" button is selected.

A possible workaround is to right click and copy the magnet link and open the url with your torrent client.

---

### Post by kikoff on 2015-10-06
Still have the problem. Same in every browser, torrent client etc.

I find the .torrent or magnet link. Try to open it in transmission or qbittorrent, even popcorntime. It finds the .torrent file, opens it. But can't connect to tracker. Here is my log from qbittorrent if that helps.

06/10/2015 14:24:54 - UPnP/NAT-PMP: Port mapping failure, message: could not map port using UPnP: no router found
06/10/2015 14:24:54 - UPnP/NAT-PMP: Port mapping failure, message: could not map port using UPnP: no router found
06/10/2015 14:22:18 - qBittorrent is successfully listening on interface :: port: TCP/3808
06/10/2015 14:22:18 - qBittorrent is successfully listening on interface 0.0.0.0 port: TCP/3808
06/10/2015 14:22:17 - '/home/kikoff/.local/share/data/qBittorrent/BT_backup/5dcd101a75d4ea015656cace713054bf8063f362.torrent' resumed. (fast resume)
06/10/2015 14:22:17 - Options were saved successfully.
06/10/2015 14:22:17 - Embedded Tracker [OFF]
06/10/2015 14:22:17 - Encryption support [ON]
06/10/2015 14:22:17 - Local Peer Discovery support [ON]
06/10/2015 14:22:17 - PeX support [ON]
06/10/2015 14:22:17 - DHT support [ON], port: UDP/3808
06/10/2015 14:22:17 - Anonymous mode [OFF]
06/10/2015 14:22:17 - HTTP user agent is qBittorrent v3.1.8
06/10/2015 14:22:17 - UPnP / NAT-PMP support [ON]
06/10/2015 14:22:17 - qBittorrent is trying to listen on any interface port: TCP/3808
06/10/2015 14:22:17 - Peer ID: -qB3180-

---

