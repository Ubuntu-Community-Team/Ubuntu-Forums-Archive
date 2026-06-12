---
title: "Need help with PPTP PTY failed error"
date: 2015-04-17
forum: General Help
---

### Post by Azdour on 2015-04-17
Hi,

It's been along time since I've needed to post anything requesting help on these forums as everything up till now has worked great :)

I've installed pptpd many times previously on Ubuntu 10.04 and made a handy guide to help me set them up and I never had a problem.

Now I am trying to set up pptpd on Xubuntu 14.04 and I'm getting an error when trying to VPN in externally.

I can connect while on the internal network (using both Xubuntu and Windows 7 machines) so that shows pptp is running, I have port forwarded 1723 to the machine and a port scan website that I usually use reports the port is open.

The error I get when trying to connect externally is:

Apr 15 20:41:21 test-server pptpd[2788]: CTRL: Client xxx.xxx.xx.xxx control connection started
Apr 15 20:41:21 test-server pptpd[2788]: CTRL: Starting call (launching pppd, opening GRE)
Apr 15 20:41:21 test-server pppd[2789]: Plugin /usr/lib/pptpd/pptpd-logwtmp.so loaded.
Apr 15 20:41:51 test-server pptpd[2788]: GRE: read(fd=6,buffer=b77b7480,len=8196) from PTY failed: status = -1 error = Input/output error, usually caused by unexpected termination of pppd, check option syntax and pppd logs
Apr 15 20:41:51 test-server pptpd[2788]: CTRL: PTY read or GRE write failed (pty,gre)=(6,7)
Apr 15 20:41:51 test-server pptpd[2788]: CTRL: Reaping child PPP[2789]
Apr 15 20:41:51 test-server pptpd[2788]: CTRL: Client xxx.xxx.xx.xxx control connection finished

Any help would be greatly appreciated.

---

### Post by dino99 on 2015-04-17
all is written: error = Input/output error, usually caused by unexpected termination of pppd, check option syntax and pppd logs

so glance at the manpage & pppd logs ;)

the most recent thread found when gloogling around 'ubuntu pppd pty vpn'  [https://wiki.archlinux.org/index.php/PPTP_VPN_client_setup_with_pptpclient](https://wiki.archlinux.org/index.php/PPTP_VPN_client_setup_with_pptpclient)
and an answer that might help: [http://askubuntu.com/questions/269399/failed-to-connect-to-pptp-vpn-server-on-ubuntu](http://askubuntu.com/questions/269399/failed-to-connect-to-pptp-vpn-server-on-ubuntu)

---

### Post by Azdour on 2015-04-17
As soon as I saw the error in the syslog log I did my googling :)

pptp does not have its own log - it just seems to use syslog.

The second link does not give me any clues about my issue.  I have googled the error message before coming here and while I see several results with the same error they where never solved or no one bothered putting the answer.

I have used exactly the same steps as setting up on the old Ubuntu 10.04, I've double checked it.

The VPN works when I am on the same internal network so that tells me it is up and running fine.  The only difference for the external computer is that it has to go through a router that port forwards to the pptp server.  Its a BT infinity hub (where previously when it worked on 10.04 it was a netgear router). 

The external computer when it tries to connect to the VPN is getting through otherwise we would not have it's IP in the log, its just the GRE fails.

---

