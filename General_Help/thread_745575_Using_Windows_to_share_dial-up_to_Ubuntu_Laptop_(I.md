---
title: "Using Windows to share dial-up to Ubuntu Laptop (I am done Windows part)"
date: 2008-04-04
forum: General Help
---

### Post by s3a on 2008-04-04
I went to:
[http://support.microsoft.com/kb/306126](http://support.microsoft.com/kb/306126)

I've followed similar instructions. Basically, I've got my host part all good.
But now for client part, I need someone to translate that Windows talk into Ubuntu talk for me please. My laptop is connected through a wired router and is running Ubuntu 7.04.

I had tried receiving as DHCP or in ROAMING mode but apparently neither works and then having read that page's client comp part got me thinkig..

Someone please help...I've been at this for several months!

---

### Post by s3a on 2008-04-04
It's the following Windows talk I need converted to Ubuntu tallk:

"On the client computer
To connect to the Internet by using the shared connection, you must confirm the LAN adapter IP configuration, and then configure the client computer. To confirm the LAN adapter IP configuration, follow these steps: 1. Log on to the client computer as Administrator or as Owner. 
2. Click Start, and then click Control Panel. 
3. Click Network and Internet Connections. 
4. Click Network Connections. 
5. Right-click Local Area Connection, and then click Properties. 
6. Click the General tab, click Internet Protocol (TCP/IP) in the This connection uses the following items list, and then click Properties. 
7. In the Internet Protocol (TCP/IP) Properties dialog box, click Obtain an IP address automatically (if it is not already selected), and then click OK.

Note You can also assign a unique static IP address in the range of 192.168.0.2 to 192.168.0.254. For example, you can assign the following static IP address, subnet mask, and default gateway:   IP Address      192.168.0.2
   Subnet mask     255.255.255.0
   Default gateway 192.168.0.1
					
 
8. In the Local Area Connection Properties dialog box, click OK. 
9. Quit Control Panel. 
To view a video about how to confirm the LAN adapter IP configuration, click the Play button () on the following Windows Media Player viewer:



If you have problems viewing this video, click here.  


Note To view this video, you must use Windows Media Player 7.0 or later.

For additional information about how to obtain Windows Media Player version 7.1, click the following article number to view the article in the Microsoft Knowledge Base: 
299321 ([http://support.microsoft.com/kb/299321/](http://support.microsoft.com/kb/299321/)) Description and availability of Windows Media Player 7.1 
To configure the client computer to use the shared Internet connection, follow these steps:1. Click Start, and then click Control Panel. 
2. Click Network and Internet Connections. 
3. Click Internet Options. 
4. In the Internet Properties dialog box, click the Connections tab. 
5. Click the Setup button.

The New Connection Wizard starts. 
6. On the Welcome to the New Connection Wizard page, click Next. 
7. Click Connect to the Internet, and then click Next. 
8. Click Set up my connection manually, and then click Next. 
9. Click Connect using a broadband connection that is always on, and then click Next. 
10. On the Completing the New Connection Wizard page, click Finish. 
11. Quit Control Panel. 
When you now start Microsoft Internet Explorer, the client computer will try to connect to the Internet by using the host computer's shared Internet connection.

To view a video of how to configure the client computer to use the shared Internet connection, click the Play button () on the following Windows Media Player viewer:



If you have problems viewing this video, click here.  


Note To view this video, you must use Windows Media Player 7.0 or later.

For additional information about how to obtain Windows Media Player version 7.1, click the following article number to view the article in the Microsoft Knowledge Base: 
299321 ([http://support.microsoft.com/kb/299321/](http://support.microsoft.com/kb/299321/)) Description and availability of Windows Media Player 7.1 
Back to the top

Troubleshooting
When you turn on Internet Connection Sharing on the host computer, the host computer's LAN adapter is automatically assigned the IP address of 192.168.0.1. Therefore, one of the following situations may occur: &#8226; IP address conflict
Each computer on the LAN must have a unique IP address. If more than one computer has the same IP address, an IP conflict occurs, and one of the network adapters turns off until the conflict is resolved. To resolve this conflict, configure the client computer to automatically obtain an IP address, or assign it a unique IP address. 
&#8226; Loss of network connectivity
If your network is configured with a different IP address range than Internet Connection Sharing uses, you will lose network connectivity with the host computer. To resolve this issue, configure the client computers to automatically obtain an IP address, or assign each client computer a unique IP address in the range of 192.168.0.2 to 192.168.0.254.  



Back to the top

REFERENCES
For additional information about Internet Connection Sharing, click the following article numbers to view the articles in the Microsoft Knowledge Base: 
234815 ([http://support.microsoft.com/kb/234815/](http://support.microsoft.com/kb/234815/)) Description of Internet Connection Sharing 
308552 ([http://support.microsoft.com/kb/308552/](http://support.microsoft.com/kb/308552/)) Description of the Network Setup Wizard in Windows 
308021 ([http://support.microsoft.com/kb/308021/](http://support.microsoft.com/kb/308021/)) Resources for troubleshooting Internet Connection Sharing in Windows XP 
308006 ([http://support.microsoft.com/kb/308006/](http://support.microsoft.com/kb/308006/)) Troubleshooting Internet Connection Sharing in Windows XP 
310563 ([http://support.microsoft.com/kb/310563/](http://support.microsoft.com/kb/310563/)) Description of Internet Connection Sharing in Windows XP"

---

