---
title: "HelpDesk:: REVERSE Remote Desktop"
date: 2008-04-05
forum: General Help
---

### Post by JGJones on 2008-04-05
REVERSE Remote Desktop:

Some background...

I support Windows users simply by asking them to run a small VNC server that would just automatically connecto to my PC where I am running a *listening* vncviewer.

I create this tool using [UltraVNC's SC (SingleClick)]("http://www.uvnc.com/addons/singleclick.html")

From the site: 

[INDENT]UltraVNC SC (SingleClick)

What is SC?

UltraVNC SC is a mini (166k) UltraVNC Server that can be customized and preconfigured for download by a Customer. UltraVNC SC does not require installation and does not make use of the registry. The customer only have to download the little executable and Click to make a connection. The connection is initiated by the server, to allow easy access thru customers firewall.[/INDENT]

This tool have been a major lifesaver many times - especially as i support many roaming clients - and have been used even if they are in Starbuck's or whatever - it bypass the firewall since it is their PC that is calling out - many place's firewall usually allow all outbound connections.

This means I never need to explain to client how to do things like "start SSH" or whatever (not that they have it on Windows!)

However recently my brother have gotten an Ubuntu laptop from Dell as I said I would not support Windows (I know my brother...within a month, the laptop would be crawling with viruses and all that). However I do not want have to explain to him how to setup SSH, open ports in a router etc (he use his laptop via wifi hotzones and will be getting 3G broadband).

Furthermore, my father is also thinking about installing Ubuntu too. And finally in my company, I have rolled out Ubuntu for external client access on older machines which could pass onto staff computers by request etc.

My problem is...

Is there an alternative to UltraVNC SC for Linux that I can use? Ideally I'll just want them to just get an application from me which they can then just run as a server and connect to my computer via a listening viewer. I've looked high and low and I've not had any success in how to do this.

This is my main issue - I really do need some way of doing this with Ubuntu without asking staff/clients/family/friends to go and open ports in firewall etc etc. This would be a valuable addition to doing helpdesk with Ubuntu users.

(this became an pressing issue when in a mailing list where I am a senior member - Deaf-LUG - some user gave up with Ubuntu because sometime explaining thing by text doesn't work too well where English isn't native language (ie they prefer sign language) and they are happy with the use of remote desktop but this does need to be as above).

Thanks in advance.
__________________
JGJones

---

### Post by williamts99 on 2008-04-27
Basically you can have them install x11vnc server and create a link with the following command:
x11vnc -connect myip.homeip.net:5500


On your system you would use: vncviewer -listen

Best Regards,
Williamts99

---

### Post by krunge on 2008-04-28
> **JGJones said:**
> REVERSE Remote Desktop:

I support Windows users simply by asking them to run a small VNC server that would just automatically connecto to my PC where I am running a *listening* vncviewer.

I create this tool using [UltraVNC's SC (SingleClick)]("http://www.uvnc.com/addons/singleclick.html")


There are some ideas for single click operation on Unix here:

[http://www.karlrunge.com/x11vnc/#faq-singleclick]("http://www.karlrunge.com/x11vnc/#faq-singleclick")

[http://www.karlrunge.com/x11vnc/single-click.html]("http://www.karlrunge.com/x11vnc/single-click.html")

---

