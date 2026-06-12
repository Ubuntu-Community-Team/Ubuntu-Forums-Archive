---
title: "direction guidance"
date: 2007-12-09
forum: General Help
---

### Post by davidexe on 2007-12-09
I have just gotten exposed to Linux and Ubuntu. I have gotten our basic server (12 computers) set up in peer-to-peer Windows and will be converting it to domain in a couple weeks. I understand that Ubuntu and Linux can do everything I am going to have to establish over the next 18 months, HOWEVER, there are different approaches.  What I need is some grey haired experience on what is the best path to take to get there.

There are currently 4 small companies (3 to 10 employees each) at 3 main locations plus 2 (home) locations. My setup is the only one running Ubuntu at this time but the others can/will convert.  We will need phone (VOIP), VPN, FTP plus others in the future.

At this time we have an unstable DSL coming into my location. That has a current astrisk based phone system running on it with dedicated phone numbers to that connection. That is being considered to be updated to Comcast (6Mb).  I need an additional connection to run the FTP, VPN, etc. so I can restart it without interrupting the telephone system.

I have ordered a Comcast 6Mb connection which will be installed tomorrow (supposedly).  Now my ignorance starts to show up.

Can I just hook a standard broadband router, with DHCP turned off, to the Comcast and then uplink that to the existing network?  Will it crash the system?  Can I set the Comcast modem at the IP address 192.168.123.2 and then reset the gateways on the existing computers on the network to look at that gateway for all internet traffic while the phone stays on the existing (192.168.123.1) gateway?

I know there are dual wan routers but the two connections do not come into the building at the same location.  If the DSL is updated to Comcast then they would and a dual WAN router would likely be the easiest solution.

There are currently 2 servers running Linux at this location. One running Fedora and mine running Ubuntu.  The Fedora one is currently running the VOIP. We have both running without problem now and can access the different workgroups.

My immediate question was just to shed all internet traffic off the DSL and hold it for the VOIP as the phone conversations are chopping. That is a very temporary condition as it is almost possitive that the DSL will be upgraded in the next month.

Now for my long term question.  Is it best to consider going to individual servers running Ubuntu for each of the various functions (VIOP, FTP, LAN, etc.)?  I currently have 2 servers (a Dell 400SC running the LAN) and a spare 600SC that I am experimenting on.  

The companies do CAD engineering so they will be doing a LOT of data transfer over the VPN once it gets established. That will be slowly integrated over the next 12 months.  The sooner the better.

I have gotten a couple BESFX41 ROUTERS with VPN terminal capability to work with to get the VPN started.  

Any input would be GREATLY appreciated. I want to try and avoid any lengthy and time consuming false starts by going down a general direction that won't work in the end.   I certainly don't mind using some intermediate computers to set up the system and then upgrade to higher end rack servers in the 18 month time period IF the integration of the 4 companies does pan out.  

Sorry for the length of this but wrong input in will definately produce garbage out. You can't help if you don't know what the overall problem is.

So, THANKS in advance for any help and direction you can give.

---

### Post by davidexe on 2007-12-10
anybody out there got any advice?

Thanks

---

