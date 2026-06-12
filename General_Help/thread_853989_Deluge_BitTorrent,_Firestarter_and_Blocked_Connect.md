---
title: "Deluge BitTorrent, Firestarter and Blocked Connections"
date: 2008-07-09
forum: General Help
---

### Post by bsriram7 on 2008-07-09
Hi. I downloaded a torrent file and then I ran it in Deluge. It was downloading fine, but the Firestarter icon kept turning red, which is a Blocked connection, right? 

So when I open Firestarter and check the Events tab, there are continuous blocked connections from multiple sources to my IP under the UDP protocol on port 6881 and the service is BitTorrent.

I closed Deluge but Firestarter keeps blocking connections which are still from service: BitTorrent but Deluge is not open or running in the background. I checked the System Monitor. 

I restarted my computer and Firestarter is still blocking connections. What is causing this? And is it something that I should be concerned about? Thank you. I'm on Ubuntu Hardy.

---

### Post by atomkarinca on 2008-07-09
To allow connections from a certain port, open Firestarter, under Policy tab at the bottom right click on the "Allow service" space and select add rule. Name it whatever you want and fill in the port Deluge is using then hit Add. When you hit "Apply Policy" Firestarter should allow the connections from that port.

---

