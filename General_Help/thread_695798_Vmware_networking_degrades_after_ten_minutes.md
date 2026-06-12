---
title: "Vmware networking degrades after ten minutes"
date: 2008-02-13
forum: General Help
---

### Post by speacock on 2008-02-13
I'm running Ubuntu 6.06, and VMware server 1.0.4.
The problem. 
1) Start vmware server.
2) Start a virtual machine that has XP on it. 
3) Use IE and browse the internet, or start FTP to do a download.
4) After 10 minutes the communication in the IE window, or the FTP stops. IE gives page not found messages, FTP just quits carrying on the conversation. 
5) DNS is still resolving, you can ping stuff and get a response, do a trace route and get a response, but no http or ftp traffic seems to happen. 

I've tried this with both NAT and bridged networking, the same experience. 
If I reboot the VM, then I get another 10 minutes (note it really seems to be exactly 10 minutes according to the system clock). 
If I suspend the VM, then come back in and resume the VM, the http and the ftp will not work. 

I can connect to an FTP site after the 10 minutes, but it will not transfer anything (no download, upload or even a directory listing).

Thanks, 

Steve

---

### Post by Trail on 2008-02-14
I don't really have any ideas, but did you virus-scan the XP? Maybe try the windows log for a hint.

---

### Post by speacock on 2008-02-15
Thanks Trail. Good idea. I should have thought of that. 
So I scanned it. No Viruses, 

The sytem log shows that the "Computer Browser" dies about 8 minutes after boot up. Some Googling shows this is due to the Windows Firewall being diabled. So I enable the firewall, and reboot the VM and after 10 minutes the "Computer Browser" has not died, but IE and FTP will not talk to any sites. 

So then I got another bright idea. I started tomcat on the Guest OS (my Ubuntu machine) and then I opened IE on the guest. I entered the IP address of my host (as returned in ipconfig /all on the XP guest) and I get my webpages. 

I noticed that vmnet8 network device shows a number of RX errors. If I use the browser and try and hit a site, this number increases by 2 or 3. If I ping, then this number does not increase. Is there any place I can look and find the errors generated on vmnet8 (which is the NAT network for vm's). I took a quick look at /var/log and didn't see any log files that looked related, nor any entries in syslog that seemed related. 

Thanks, 

Steve

---

