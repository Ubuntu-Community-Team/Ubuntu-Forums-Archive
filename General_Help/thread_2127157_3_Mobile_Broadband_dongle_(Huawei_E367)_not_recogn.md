---
title: "3 Mobile Broadband dongle (Huawei E367) not recognised"
date: 2013-03-19
forum: General Help
---

### Post by Jameela on 2013-03-19
I am a new user with Ubuntu 12.04 

When I try to connect my 3 Mobile internet dongle (Huawei E367) into the USB port, nothing happens!  ...No connection wizard comes up.

Looking in the Wired Network menu (top right of screen) it does not even list "Mobile Internet", so I cannot enable it if it is just not there!

Can anybody suggest what is wrong?

Thanks

---

### Post by 3rdalbum on 2013-03-19
When you plug in a mobile broadband dongle, it will appear as though nothing has happened. You need to go to the network manager (the one you mention as the "wired network menu") and go to Edit Connections...

Click on the Mobile Broadband tab and click the Add button. Follow the prompts to set up your connection. When that's done, you should be able to use the Network Manager menu to connect.

---

### Post by Jameela on 2013-03-19
Thanks but I've already tried that and it was not successful

In the "Wired Connections" drop-down menu, selecting "Edit Connections", it has a tab for Mobile Broadband.

I clicked "Add" and went through the dialogue screens.

On the Editing 3 Internet page, there are 3 tabs:

IPv4 Settings  /  Mobile Broadband  /  PPP Settings

Under Mobile Broadband, it displays the number as     *99#      (but I did not enter this)

The Username and Password are blank because this is for Pay-as-you-go mobile broadband

Is this correct?

However, even though there is this entry on "Edit Connections", there is nothing displaying on first "Wired Network" drop-down menu.  ...I thought it should have the option "Enable Mobile Broadband" next to "Enable Networking"  but it doesn't.

Any suggestions?

Thanks.

---

### Post by 3rdalbum on 2013-03-19
The name you gave to the connection should appear in the Network Manager menu.

---

### Post by Jameela on 2013-03-20
> **3rdalbum said:**
> The name you gave to the connection should appear in the Network Manager menu.

**The problemm is now solved!**

Searching Google, I came accross this post on another forum:   [http://www.webmasterworld.com/linux/4342878.htm](http://www.webmasterworld.com/linux/4342878.htm)

Following the thread down, a contributer named  **dstiles**  wrote the following:

**************************************************************[INDENT][FONT=verdana][SIZE=2][COLOR=#000000]ALRIGHT! 
 
Poking  partially at random, changing things to what I thought they should be  after reading a few more web sites (this time with brain engaged!)... 
 
In Network Connections --> Mobile Broadband select the new modem (3 Internet 1) (install a new one if not already done). 
 
On the IPv4 Settings tab: 
 Automatic (PPP) 
 Connect Automatically: (tick) 
 Available to all users: (your choice - I ticked it) 
 Routes: (none) 
 
Mobile Broadband tab: 
 Number: *99# (that's star 99 hash) 
 Username: three 
 password: three 
 APN: 3internet (remember this is three.co.uk network) 
 Network: (empty) 
 PIN: 0000 
 
PPP Settings tab: 
 Configure Methods: EAP and PAP (only) 
 Point to point encryption: (not ticked) 
 Allow BSD: (ticked) 
 Allow Deflate: (ticked) 
 Use TCP header: (ticked) 
 Echo: (not ticked) 
 
When I saved that lot - Bingo! 
 
The only real changes I made from previous attempts were: 
 *99# (previously tried 99# and before that the product Identifier 074...) 
 Removed all Methods except EAP and PAP (previosly only removed CHAP). 
 
For interest, from Connection Info: 
 Interface: GSM (ttyUSB0) - (that's zero not o) 
 Hardware Address: (nothing) 
 Driver: option1 
 Speed: unknown (dongle is showing blue so lower range - cyan is higher) 
 Security: unknown 
 IP Address: 94.196.nnn.nnn 
 Broadcast address: (same as IP) 
 Subnet Mask: 255.255.255.255 
 Primary DNS: 217.171.nnn.n 
 Secondary DNS: (same as primary) 
 
Network rDNS shows as Hutchison H3G UK (in my case 94.196/15) 
 
For  some of the testing I had my Etho0 LAN cable plugged in and connected  to the internet. Both Etho0 and 3Internet1 showed connected (no idea at  this point which would actually do the work). 
 
When I  disconnected Mobile in Network Connections the dongle's light went back  to flashing blue (3 network detected but not connected).  
[/COLOR][/SIZE][/FONT][/INDENT]
[FONT=verdana][SIZE=2][COLOR=#000000]
**********************************************************

I followed these instructions exactly, and 3 Mobile Internet worked on Ubuntu[/COLOR][/SIZE][/FONT]: Just Tick "Enable Mobile Broadband" in the Wired Networks drop-down menu (which is now an option) and click on "3 internet 1" to start it. Then, after a few seconds wait, the computer connects to the internet via the dongle, but without the familiar blue "3Connect"  window.  It just connects automatically, and there is a very tiny sigal-strenth icon dispayed at the top right of the screen.

Credits be to **dstiles**

Thanks

---

