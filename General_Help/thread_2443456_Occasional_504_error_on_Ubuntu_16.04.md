---
title: "Occasional 504 error on Ubuntu 16.04"
date: 2020-05-15
forum: General Help
---

### Post by danielpwong on 2020-05-15
[FONT=&amp]We are trying to move an application from on-prem to Azure. It runs on Tomcat 4 and was Ubuntu 14.04 on-prem and is 16.04 in Azure. We get it running in Azure on a standalone VM, but when we put an Azure Application Gateway in front of it, we start getting occasional 504 errors. We aren't able to see any pattern in the frequency or timing of them. We used TCPDump to trace the packet to the VM, but it doesn't ever show up on the Tomcat logs, nor does it get picked up by the garbage collector.
 
Additionally, we have deployed it on an AKS cluster and didn't get the error.
[/FONT]

---

### Post by TheFu on 2020-05-16
No clue about the MSFT infrastructure issues. Sorry.
Why bother with 16.04?  Free support ends in less than a year for that release. It really isn't worth the effort.
Tomcat 4 has been EOL for a long, long time. [http://tomcat.apache.org/security-4.html](http://tomcat.apache.org/security-4.html)  Stuff should be on Tomcat v9 at this point.

Someone needs to ensure, in writing, that management understands the risks and accepts the risks for when it gets hacked.

For troubleshooting, I'd draw a diagram and start tracing how far any request gets in the network architecture.  BTW, it is almost never the network and usually falls back onto the software configuration or expectations of the software team.  Once had a few hundred servers stop working every 24 hours. Seems the security team had implemented a close firewall rule every day for connections that weren't active (transferring data).  The application would make a CORBA connection then assume it was open forever. When the firewall closed every 24 hours, restarting the app was needed. Since the restart happened across hundreds of servers, it seemed like a cascade failure as each would fail, in turn.  The developers put in an auto-reconnection function and the firewall team was happy. Took about 6 months to get that change created, tested, and deployed. All in the name of better security inside our LAN in a special subnet that only our equipment could access.  The clients were spread out over our region and used cellular data, but all the devices were placed onto a dedicated LAN by the cell provider to extend parts of our corporate subnet out to those devices.  That was really frustrating when devices would get stolen - no internet access at all for the thieves.

---

