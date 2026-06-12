---
title: "remove personal internet access vpn (pia)"
date: 2015-08-08
forum: General Help
---

### Post by jgw on 2015-08-08
I recently learned that my usenet server subscription also includes a vpn for the same price.  I have been using PIA and its gotten strange.  What I want to do is to simply remove pia from my system and move the other, which I have been paying for (I have not paying attention).  I can use the "sudo apt-get remove <program name here>" but am not sure that will do the job so I thought I would ask to make sure.

I actually did the apt-get remove thing.  It said it did the job.  I check for pia folder and files and found a pile of them.  I then went to the network manager, clicked on vpn and there were all the pia vpn locations.  I clicked on the one I used and pia is now running yet again (no icon but it is still running and connected).  I find this one a bit odd.

Thank you................

---

### Post by QDR06VV9 on 2015-08-08
> **jgw said:**
> I recently learned that my usenet server subscription also includes a vpn for the same price.  I have been using PIA and its gotten strange.  What I want to do is to simply remove pia from my system and move the other, which I have been paying for (I have not paying attention).  I can use the "sudo apt-get remove <program name here>" but am not sure that will do the job so I thought I would ask to make sure.

Thank you................
I am not sure how you installed pia, but if it was .deb then you would issue the command you mentioned.
to set up Usenet VPN see this [https://www.usenetserver.com/vpn/#setup](https://www.usenetserver.com/vpn/#setup)
Looks pretty straight forward.
Regards

---

### Post by jgw on 2015-08-08
Thank you for the reply.  

Yep, it does look pretty simple.  I am not sure, however, how its going to interact with the pia stuff.  For instance, in the setup they want one to goto the vpn tab in networks/configure and add.  The problem is that the pia vpn is sitting there and it doesn't seem eager to add another.  When you press add you are gifted with adding ethernet (strange because that is already there) and VPN is used up with pia.  This, obviously, confuses me.  I can disconnect pia but it remains.  (kinda pernicious) 

I think part of the problem is that pia and linux are not a real happy mix and the linux part is, by their own definition (using beta), not ready for prime time.  I keep thinking that the way to get rid of pia is to simply delete every file I can find but I have no idea what that will even do.  I have asked pia howto delete their program and got an answer and did that but it continues to remain.

---

### Post by QDR06VV9 on 2015-08-08
For now you could just edit your network connections pertaining to the PIA specific configs
If you went with openvpn option it should follow their specific instructions and protocol.
Regards

---

### Post by jgw on 2015-08-09
I think what I am going to do is to simply remove any and all references to pia, folders and files, reboot my machine and see what happens.  Should be interesting.  I really don't want to install another vpn when I already have another installed and, apparently, functional.

thank you for the reply!

---

### Post by jgw on 2015-08-09
I have now deleted every folder and file I could find throughout my system that involved pia (as super user)  That made absolutely no difference.  I then went to vpn and all the pia sites remained.  I then choose the one I had been using and, I am, yet again, using the vpn network.  I am at a complete loss and have no idea if getting rid of pia is even possible.  I have not closed my account with them as I need the vpn and this continues to be a mess I am, obviously, not competent to deal with.  

Thank you...................

---

### Post by QDR06VV9 on 2015-08-10
Can you also access the Usernet VPN?
After looking at all the posts about trying to unistall PIA, makes me happy i went with another choice.
Keep after them(PIA) until you are satisfied. You are a paying customer you should be handled as such.
As buckyball puts it "Don't just ware it make some noise"
Kind Regards

---

### Post by jgw on 2015-08-12
Have yet to install the usenet server vpn.  There have been problems.  The first one is that there is a problem with the installation instructions in that they do not accurately reflect what ubuntu does.  I think the pptp installation failed because my machine is not setup for ptp so I started checking and it seems generally accepted that I should be doing the open vpn thing.  I then tried to install that one and have run into some problems but I have reported same and I should have an answer today so I can proceed.

---

### Post by QDR06VV9 on 2015-08-12
Sometimes they forget or even assume that you already have installed "openvpn && network-manager-openvpn && network-manager-openvpn-gnome"
 Just a heads-up
 I am currently using IPVanish, with the openvpn software.
Please keep us updated if you would.
 Kind Regards

---

### Post by pfrandsen on 2016-08-02
Seems like you just have to run this command:

rm -rf ~/.pia_manager/

[https://helpdesk.privateinternetaccess.com/hc/en-us/articles/219660167-Uninstalling-the-Linux-Beta-Client](https://helpdesk.privateinternetaccess.com/hc/en-us/articles/219660167-Uninstalling-the-Linux-Beta-Client)

---

