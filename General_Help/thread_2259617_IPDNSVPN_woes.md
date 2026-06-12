---
title: "IP/DNS/VPN woes"
date: 2015-01-05
forum: General Help
---

### Post by drfox on 2015-01-05
I use NeoRouter for my VPN. Several days ago, my backup server (Ubuntu Server 3.13.0-43, 64-bit) stopped being attached to my VPN.
The nrtap has disappeared, and when I try to start neorouter, it just fails.
This must be related: when I try to ping neorouter.com, it hangs with the message "PING neorouter.com (72.167.40.31) 56(84) bytes of data" and ultimately fails at 3999ms
I use Uverse as my ISP at home and Comcast at work and have 2 Xubuntu laptops (one at each location)
My Xubuntu laptop(s) can ping neorouter, and I can navigate to the neorouter.com website with Firefox, but when I click on "Dashboard", it hangs. Clicking on [https://72.167.40.3/Dashboard/Login.aspx](https://72.167.40.3/Dashboard/Login.aspx) works after I authorize a security exception in Firefox, but [https://secure.neorouter.com/dashboard/](https://secure.neorouter.com/dashboard/) does not work even though they resolve to the same thing. Oh, one more thing...I needed to add Uverse and Google DNS servers in my Network Connections even though I'm using DHCP.
My wife uses Windows 7 behind the same Uverse modem-router, and she has no issues with the neorouter website, at work the Windows PCs all work fine, and everything was working on the Ubuntu Server until some time last week, so it would appear that it's a Ubuntu problem. 
Does anybody have any suggestions for troubleshooting?

---

### Post by sandyd on 2015-01-05
> **drfox said:**
> I use NeoRouter for my VPN. Several days ago, my backup server (Ubuntu Server 3.13.0-43, 64-bit) stopped being attached to my VPN.
The nrtap has disappeared, and when I try to start neorouter, it just fails.
This must be related: when I try to ping neorouter.com, it hangs with the message "PING neorouter.com (72.167.40.31) 56(84) bytes of data" and ultimately fails at 3999ms
I use Uverse as my ISP at home and Comcast at work and have 2 Xubuntu laptops (one at each location)
My Xubuntu laptop(s) can ping neorouter, and I can navigate to the neorouter.com website with Firefox, but when I click on "Dashboard", it hangs. Clicking on [https://72.167.40.3/Dashboard/Login.aspx](https://72.167.40.3/Dashboard/Login.aspx) works after I authorize a security exception in Firefox, but [https://secure.neorouter.com/dashboard/](https://secure.neorouter.com/dashboard/) does not work even though they resolve to the same thing. Oh, one more thing...I needed to add Uverse and Google DNS servers in my Network Connections even though I'm using DHCP.
My wife uses Windows 7 behind the same Uverse modem-router, and she has no issues with the neorouter website, at work the Windows PCs all work fine, and everything was working on the Ubuntu Server until some time last week, so it would appear that it's a Ubuntu problem. 
Does anybody have any suggestions for troubleshooting?

Try doing a mtr to neorouter.com from the backup server, and compare it with a mtr from the xubuntu laptop in the same location. Are there any differences? Does the backup server mtr manage to reach neorouter.com?

---

### Post by drfox on 2015-01-08
Thanks for the suggestion. I wound up adding a gui to the server and was able to see the problem.

---

