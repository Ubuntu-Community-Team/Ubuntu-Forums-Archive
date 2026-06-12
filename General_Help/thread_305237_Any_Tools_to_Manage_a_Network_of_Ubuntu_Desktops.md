---
title: "Any Tools to Manage a Network of Ubuntu Desktops?"
date: 2006-11-23
forum: General Help
---

### Post by moufranica on 2006-11-23
Dear Gurus,
I have migrated a couple of computers at my office to Ubuntu Desktop and is also running some services on Ubuntu Server (migrated from RedHat). In the MS Windows world, we had a lot of tools at our hands to manage the desktops. With Ubuntu what kind of tools do we have?

1. Remote Deployment
2. Software Updates Services
3. Software installations [I am aware that I can use Remote Desktop or SSH to do this, but I looking for something more streamlined for multiple desktops]
4. Anything equivalent to SMB [I am not looking for Samba, but something more native to linux].
5. Linux Printing, again I am not looking for clones of MS technology which has some IP concerns, highlighted by the Novell-Microsoft deal.

---

### Post by moufranica on 2006-11-23
I found two things on the web. ZenWorks 7 from Novell, whom I have no intentions of being customer. And Open Country Universal Linux Management Suite. Looks good. But not free. What other options do we have?

---

### Post by temcat on 2006-11-23
AFAIK in the area of management tools Linux is currently behind Windows, so I'm not sure you'll be able to find something ready. But point 4 in your list is there and is called NFS.

---

### Post by adam.tropics on 2006-11-23
There is always[ this...]("https://help.ubuntu.com/community/NetworkManagementTools")I like the look of the second one down, NAV, but have never used it.

---

### Post by speedman on 2006-11-23
> **moufranica said:**
> 1. Remote Deployment

You can remaster the Ubuntu install CD to be customized for your environment.  Or, you can use a tool like mondo (apt-cache show mondo) to deploy your images, or you can use a commercial tool like Acronis to deploy system images stored on the network.  Remastering the Ubuntu CD would be my preferred choice, but each to their own.

> 2. Software Updates Services

apt-cache show dsh

> 3. Software installations I am aware that I can use Remote Desktop or SSH to do this, but I looking for something more streamlined for multiple desktops

As per #2 above.

> 4. Anything equivalent to SMB [I am not looking for Samba, but something more native to linux].

NFS.

> 5. Linux Printing, again I am not looking for clones of MS technology which has some IP concerns, highlighted by the Novell-Microsoft deal.

Configure one box as a CUPS server that can print to the devices you want to share - then enable browsing in /etc/cups/cupsd.conf as per the following example:

Browsing On
BrowseProtocols cups
BrowseAddress 192.168.1.255 #change to suit your network
BrowseAllow All
BrowsePort 631

Once that is done just enable browsing on your Ubuntu client systems from System > Administration > Printing > Global Settings > Detect LAN Printers.

HTH


Regards,

SM

---

### Post by moufranica on 2006-11-25
> **speedman said:**
> You can remaster the Ubuntu install CD to be customized for your environment.  Or, you can use a tool like mondo (apt-cache show mondo) to deploy your images, or you can use a commercial tool like Acronis to deploy system images stored on the network.  Remastering the Ubuntu CD would be my preferred choice, but each to their own.



apt-cache show dsh



As per #2 above.



NFS.



Configure one box as a CUPS server that can print to the devices you want to share - then enable browsing in /etc/cups/cupsd.conf as per the following example:

Browsing On
BrowseProtocols cups
BrowseAddress 192.168.1.255 #change to suit your network
BrowseAllow All
BrowsePort 631

Once that is done just enable browsing on your Ubuntu client systems from System > Administration > Printing > Global Settings > Detect LAN Printers.

HTH


Regards,

SM

Thanks! Sounds very cool. I am going to give it a try. Will inform back when I get them to work properly. Never knew linux had these things. :)

---

### Post by speedman on 2006-11-25
If you have enough systems you might want to look into apt-mirror or apt-proxy, which would give you a local repo for client system updates whereby you can approve what packages you want applied.  Then you can either use cron to have your client systems check in with your local repo, or you could use dsh if you want to do it manually.


Regards,

SM

---

### Post by mcwtlg on 2006-11-25
I have done some Googling but have not found an answer that I can use...

What I need is a Linux version of MS Network Neighborhood to browser Linux boxes.  I have 1 dual boot XP-Linux box and two Linux only boxes on a small home network.  When the XP partition is booted up, I can see all the Linux boxes just fine, but I am having trouble seeing the Linux boxes from a Linux machine when they are the only ones on.  Does such an animal exist?

I know that NFS is a solution, but I was hoping for something a little more newbie-ish if possible.

Tack/Gracias/Thanx/Merci/Abrigado

Mark

---

### Post by moufranica on 2006-11-26
> **mcwtlg said:**
> I have done some Googling but have not found an answer that I can use...

What I need is a Linux version of MS Network Neighborhood to browser Linux boxes.  I have 1 dual boot XP-Linux box and two Linux only boxes on a small home network.  When the XP partition is booted up, I can see all the Linux boxes just fine, but I am having trouble seeing the Linux boxes from a Linux machine when they are the only ones on.  Does such an animal exist?

I know that NFS is a solution, but I was hoping for something a little more newbie-ish if possible.

Tack/Gracias/Thanx/Merci/Abrigado

Mark

I guess right now SaMBa on Linux would be the best choice. You would need to configure some shares on Ubuntu for the "Network Neighborhood" to work. I do wish, much like you that we should be able to use a solution more native to Linux for browsing into other computers. Something as simple as SMB.

---

### Post by moufranica on 2006-11-26
> **speedman said:**
> If you have enough systems you might want to look into apt-mirror or apt-proxy, which would give you a local repo for client system updates whereby you can approve what packages you want applied.  Then you can either use cron to have your client systems check in with your local repo, or you could use dsh if you want to do it manually.


Regards,

SM
I am indeed using apt-proxy. But the apt-get client is not behaving properly, as it keeps on insistently using the http_proxy environment variable, even though it is on the local network and should no be doing so (as I have also configured $ignore_hosts properly).

---

