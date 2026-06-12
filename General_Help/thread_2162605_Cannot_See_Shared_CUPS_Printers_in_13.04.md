---
title: "Cannot See Shared CUPS Printers in 13.04"
date: 2013-07-15
forum: General Help
---

### Post by BeardoTheDwarf on 2013-07-15
Problem: in Ubuntu 13.04, in my CUPS configuration screen, the option "Show printers shared by other systems" is missing. We have something like 10 shared printers in the office, all being shared through our cups server. Up until 13.04, doing

**$ sudo system-config-printer**

with the "Show printers shared by other systems" option activated has always populated the window with all the CUPS printers on the network.

In 13.04, the option doesn't exist and no printers are visible by default (although the CUPS server is reachable and I can connect to printers by URI):

I've just replicated this on my own machine with a fresh virtual-machine install of Ubuntu 13.04.

This issue is consistent across both the GUI-tool (system-config-printer) and the http tool (localhost:631/admin), so I'm guessing it's CUPS.

12.10 machine (working) cups version: 1.6.1
13.04 machine cups version: 1.6.3


_**[[Attempts to Fix:]]**_

I thought it might be related to this issue: [http://ubuntuforums.org/showthread.php?t=2145419](http://ubuntuforums.org/showthread.php?t=2145419) -- but apparently not.

In /etc/cups/cups-browsed.conf :
    1. add 'cups' to BrowseRemoteProtocols line
    (BrowseRemoteProtocols dnssd cups)
    2. Add "BrowseLocalProtocols cups"

Anyone have an idea? We can't roll out Ubuntu 13.04 to our client machines while printing has to be configured on a per-user, per-printer basis.

Thanks!

---

### Post by BeardoTheDwarf on 2013-07-16
Some Images, to clarify: (note that I get the exact same options in the CUPS web interface -- localhost:631)

Image: No Option (Ubuntu 13.04):

[IMG]http://postimg.org/image/xqjmlrjrh/[/IMG]
edit: image here: [http://postimg.org/image/6tzndg0y5/](http://postimg.org/image/6tzndg0y5/)


#######################

Ubuntu 12.10:

[IMG]http://postimg.org/image/xqjmlrjrh/[/IMG]

edit: image WITH option: [http://postimg.org/image/osr3j1rd9/](http://postimg.org/image/osr3j1rd9/)

---

### Post by pqwoerituytrueiwoq on 2013-07-16
So you are saying the issue is The GUI on the Client systems is not showing the printer without telling it a ip address at the very least correct?
On my desktop i am running xubuntu 13.04, my printer is shared via this system
my virtualbox xubuntu 13.10 when i click "Add" in system-config-printer and expand the Network Printer tree i see my printer
same on my 13.04 laptop
however on 13.10 even with no printers configured it shows up when i try to print (out of ink so i can't actually print)
edit:
xubuntu 13.10 found my printer on the network and configured without any user input

---

### Post by BeardoTheDwarf on 2013-07-17
Hi, thanks for the reply.

I just edited the post above -- it looks like my image links weren't being displayed. In the linked pictures, you can now see the "Show printers shared by other systems" option that's missing in 13.04.

I just tried doing system-config-printer --> "add" button --> expand "Network Printer", and nothing is autoconfigured. I'd have to manually connect to all 10 CUPS printers with their ipp:// .

When I try to print in Libreoffice, I don't see any networked printers that I haven't manually added (via specifying ipp URI).

Any ideas?

---

### Post by pqwoerituytrueiwoq on 2013-07-17
Does this not happen on your system? [http://www.yourupload.com/watch/4hl062](http://www.yourupload.com/watch/4hl062)
If it does not show up use find printer (right below where my printer appeared)
if i do that i get 2 options 
[[img]http://www.zimagez.com/miniature/screenshot-07172013-112344am.php[/img]](http://www.zimagez.com/zimage/screenshot-07172013-112344am.php)

---

### Post by BeardoTheDwarf on 2013-07-18
Thanks so much for your continued help, and for taking all this time!

On my system, network printers do not autopopulate like they do in your video, nor do I see any options when I click on "find printer." :-(. I don't even see the network printers I've added via "ipp://" -- I only see those on the first screen (the main Printer Config screen).

Strange, no? I'm reproducing this on both 
1. client machines that have been upgraded via dist-upgrade, and 
2. fresh installs of 'vanilla' Ubuntu 13.04.

Any other ideas about where I should look for clues?

Thanks again for all your effort.

---

### Post by BeardoTheDwarf on 2013-07-19
Should I post this in a different forum? Maybe "general" isn't the right place for it?

---

### Post by Neil Smith on 2013-08-02
I'm having the same problem. My /etc/cups/cups-browsed file contains:

```
BrowseRemoteProtocols dnssd cups
BrowseLocalProtocols dnssd cups
BrowseProtocols dnssd cups
BrowseAllow 192.168.2.0/255.255.255.0
BrowsePoll cups15.domain.tld
Browsing On
```

My Cups 1.5 server sees its own printers, and the ones connected to the Cups 1.6 machine. The Cups 1.6 machine only sees the printers connected locally to it. As that latter machine is my desktop, I'd like it to see the remote printers.

If anyone has any ideas of how to fix this, I'd love to hear them!

---

