---
title: "pxe boot tftp time out with ubuntu 14.04 server"
date: 2014-11-10
forum: General Help
---

### Post by Tony_Lillie on 2014-11-10
Going to do this quick and dirty because my brain is toast. 12 hours in and I still have no solution. Am trying to PXE boot using tftp-hpa and get a tftp time out error. I've looked at all the pertinent config files and read dozens of posts and how-to's to no avail. 

Mostly I followed this : [https://help.ubuntu.com/community/DisklessUbuntuHowto](https://help.ubuntu.com/community/DisklessUbuntuHowto)  and this: [http://programsketches.org/?p=4](http://programsketches.org/?p=4)  and filled in the gaps with dozens of other posts and sites etc...

The server and the client are identical machines, and the server is doing both DHCP and TFTP. DHCP seems to be working because the client picks up the static IP and other DHCP network info just fine, but then it times out during TFTP. I've disabled UFW, and confirmed that TFTP is definitely running as a daemon service and listening on port 69. I'm at a loss...

Can someone please help me troubleshoot this? I don't know where to look to find the cause of the problem, other than the various config files that I tweaked repeatedly along the way.

Not sure if this helps, but TFTP was not even listening on port 69 until I added the --listen command to the options in the /etc/default/tftpd-hpa file. I thought I had nailed it when it finally showed evidence of listening, but no. I'm just mentioning it because sometimes the bread crumbs are the best clues.

I've also tweaked the tftp_address from 0.0.0.0:69 to 192.168.2.2:69 and seen no effect. It wasn't clear to me which was better if any.

In the /etc/dhcp/dhcpd.conf I've tweaked the filename from "/pxelinux.0" to "pxelinux.0" back and forth more than once because it appears differently in various posts and I haven't figured out which way is truly correct, though I think the first option is probably right.

I'm going to shut-up now and pray for some help.

Anyone??

---

### Post by vinayak4 on 2015-04-12
I have also facing the same issue. Can you help me with the solution which you applied?

---

