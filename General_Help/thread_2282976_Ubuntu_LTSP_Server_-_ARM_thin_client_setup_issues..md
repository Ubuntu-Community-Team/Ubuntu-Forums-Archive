---
title: "Ubuntu LTSP Server - ARM thin client setup issues."
date: 2015-06-18
forum: General Help
---

### Post by krish2487 on 2015-06-18
[COLOR=#000000]Hello, Let me give a brief introduction before I get to the actual problem.[/COLOR]
[COLOR=#000000]We are a ubuntu shop with the exception of our SAP ERP server which runs on windows 2012 R2 and Terminal Server running windows server 2008 R2.[/COLOR]
[COLOR=#000000]All in all about 40 clients.[/COLOR]

[COLOR=#000000]We are very happy with the setup. However, in an effort to go green with power consumption we are trying to migrate to a thin client setup. [/COLOR]
[COLOR=#000000]We wanted to scrap out existing PCs and get proper thin clients that can be fit to the monitors. [/COLOR]

[COLOR=#000000]I have successfully setup a test LTSP server (ubuntu 14.04) and client using virtualbox on my laptop. It boots and I am able to login to the server from the client.[/COLOR]
[COLOR=#000000]The network is setup correctly on VirtualBox (bridged mode) and no DHCP server issues etc. So far so good.[/COLOR]

[COLOR=#000000]We are trying to evaluate a thin client from QHMPL - Model QHM6056 for booting into the LTSP server.[/COLOR]
[COLOR=#000000]This is where I hit a brick wall. The thin client runs windows embedded and I cant get it to PXE boot. I am not that good with windows, having given up on windows a decade back.[/COLOR]
[COLOR=#000000]The thin client itself is a generic rebranded ARM thinclient based on CLG7700. The client itself boots into windows CE embedded. There is an option of working as a "thin client" but it does not see the DHCP server and boot into ubuntu LTSP.[/COLOR]

[COLOR=#000000]Has anyone else faced a similar situation? I will be extremely grateful to anyone who can help me with this.[/COLOR]

[COLOR=#000000]What I am looking for is help with either [/COLOR]
[COLOR=#000000]1. network booting a thin client[/COLOR]
[COLOR=#000000]2. Setup the thin client to access a ltsp server post booting into the embedded windows.[/COLOR]

[COLOR=#000000]Thanks in advance.

PS: Yes it is a duplicate in server subforums. The server forums seem to be a little sparse in terms of views, hence the repost. Maybe someone already faced such an issue and can help me out with this.

Yes, I know it is also possible to use xrdp to connect to ubuntu LTSP from a win ce thin client and I have done so. I would like to use epoptes for centralized management and administration. The xrdp sessions do not show in epoptes. Hence my predicament. [/COLOR]

---

### Post by ventrical on 2015-06-18
> **krish2487 said:**
> [COLOR=#000000]Hello, Let me give a brief introduction before I get to the actual problem.[/COLOR]
[COLOR=#000000]We are a ubuntu shop with the exception of our SAP ERP server which runs on windows 2012 R2 and Terminal Server running windows server 2008 R2.[/COLOR]
[COLOR=#000000]All in all about 40 clients.[/COLOR]

[COLOR=#000000]We are very happy with the setup. However, in an effort to go green with power consumption we are trying to migrate to a thin client setup. [/COLOR]
[COLOR=#000000]We wanted to scrap out existing PCs and get proper thin clients that can be fit to the monitors. [/COLOR]

[COLOR=#000000]I have successfully setup a test LTSP server (ubuntu 14.04) and client using virtualbox on my laptop. It boots and I am able to login to the server from the client.[/COLOR]
[COLOR=#000000]The network is setup correctly on VirtualBox (bridged mode) and no DHCP server issues etc. So far so good.[/COLOR]

[COLOR=#000000]We are trying to evaluate a thin client from QHMPL - Model QHM6056 for booting into the LTSP server.[/COLOR]
[COLOR=#000000]This is where I hit a brick wall. The thin client runs windows embedded and I cant get it to PXE boot. I am not that good with windows, having given up on windows a decade back.[/COLOR]
[COLOR=#000000]The thin client itself is a generic rebranded ARM thinclient based on CLG7700. The client itself boots into windows CE embedded. There is an option of working as a "thin client" but it does not see the DHCP server and boot into ubuntu LTSP.[/COLOR]

[COLOR=#000000]Has anyone else faced a similar situation? I will be extremely grateful to anyone who can help me with this.[/COLOR]

[COLOR=#000000]What I am looking for is help with either [/COLOR]
[COLOR=#000000]1. network booting a thin client[/COLOR]
[COLOR=#000000]2. Setup the thin client to access a ltsp server post booting into the embedded windows.[/COLOR]

[COLOR=#000000]Thanks in advance.

PS: Yes it is a duplicate in server subforums. The server forums seem to be a little sparse in terms of views, hence the repost. Maybe someone already faced such an issue and can help me out with this.

Yes, I know it is also possible to use xrdp to connect to ubuntu LTSP from a win ce thin client and I have done so. I would like to use epoptes for centralized management and administration. The xrdp sessions do not show in epoptes. Hence my predicament. [/COLOR]


 I tired to set up a HP TC using TCOS from the Software center and it was a miserable failure. I still may try again. The error I get is ftp server error (after setup and startup) and then permission denied. I did watch a video on youtube (don't have the link off hand) where they are demonstrating how easy it is to set up a tc. It shows a teacher setting up her network but she is using the  Edubuntu flavour!! That leads me to only another question (sorry - do not have an answer) - my question being, does Edubuntu have a custom software package for thin clients that other ubuntus do not?

*note* I am aware that HP has a total free software package to work with Windows but I do not want to use windows or VM. I want  a mainline set up from desktop/server to TC using only ubuntu .

Regards..

---

### Post by ventrical on 2015-06-18
I have the HP TPC-W004-TC. If I find that link , i'll post it.

---

