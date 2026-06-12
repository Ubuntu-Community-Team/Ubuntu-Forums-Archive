---
title: "Ubuntu Server w/ XPe clients"
date: 2013-06-27
forum: General Help
---

### Post by SelfSupport on 2013-06-27
I am considering repurposing 10 Wyse S90's (512mb RAM, 512mb Flash) with XPe for a specific but limited use.

We have a board that meets monthly and the intent is to move away from reams of printed documents and replace them with LCD's and keyboards. I'm considering Ubuntu 12.04 LTSP as the primary server with the XP TC's attached. It would be a standalone server/network dedicated to the board for their meetings. Some board members carry various netbooks, smartphones, etc. however, considering the variety of OS's involved and not really wanting to establish support issues on non company equipment not to mention client sw installation etc. I would like to consider the TC's which would remain attached to the 19" monitors instead. 

One goal is to mitigate licensing costs so open source server and office apps are on the menu here which brings me to two questions. The applications 

1. TC's are Windows XP embedded and would need to access applications such as OpenOffice on the server, Firefox (internet use), PDF reader, an audio program and perhaps a video app such as VLC. Would it be better to run WINE and install the open source Windows apps on the server or would it be better to run VMWare and install Windows for the clients to talk to (licensing issue here)?
2. Once RDP is established from the TC's to LTSP, can the apps be Linux based and run without virtualization or emulation?

Keep in mind that the principle objective is to run the apps on the server, not the TC's due to hardware limitations.

If Wine is the suggested way to go, do apps have to be installed for each instance of a client like they do with VM?

Responses and suggestions are appreciated.

---

