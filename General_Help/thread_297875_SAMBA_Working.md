---
title: "SAMBA Working"
date: 2006-11-11
forum: General Help
---

### Post by Frihet on 2006-11-11
I finally have SAMBA working from a DHCP Dapper client to a static IP server (Cisco NSLU2). I wanted to put this post up in case others are having a similar problem.

My starting position was that SAMBA connections did not work from my Dapper laptop to the NSLU2 or any Windows box on the network. Under (Gnome) Places, Network Servers, I had a Windows Network Icon, and clicking on it brought up another icon with the correct workgroup name (foo). Clicking on the workgroup icon resulted in an error message -- Sorry, couldn't display all the contents of "Windows Network: foo". I could find no help for this in the discussion group. Deleting the icon did not help anything – it just recreated itself. The properties associated with this icon did not provide the magic my machine required to connect to the NSLU2 (ip address). If I attempted to edit the properties, they “fixed” themselves back to the values that did nothing but make error messages.

So, before resorting to Mandrake (SAMBA works) or FC6, I tried creating a new server. Places, Connect to Server, choose Windows Share, and give ip address in “Server” selection. That's all I did.

A new icon popped up on the Places, Network Servers browser.

Guess what. The new icon worked. I can get to my shares just fine.

The only bad things are:

1.I have a useless workgroup places icon that won't go away and generates confusing error messages when clicked.

2.The new working icon has an ip address for a name. I can't change that. Not good for the wife and kids, but they'll get over that.

I'm learning.

---

