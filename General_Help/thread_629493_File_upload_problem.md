---
title: "File upload problem"
date: 2007-12-02
forum: General Help
---

### Post by cr0bar on 2007-12-02
So anyway, I've searched around quite a bit for a solution to this but to no avail. I tried posting in the absolute beginners section but nada.

When I try uploading a file to, say, megaupload or sendspace no data gets sent, or when uploading an image to tinypic or imageshack the connection just times out. Also when using Bittorrent nothing gets uploaded. I'm presuming it's something in Ubuntu as I never have this problem in Vista, so it's not an ISP issue. I'm not using any firewalls or anything either - this is pretty much a fresh install done last night.

When trying to login to Gmail too via Firefox the connection times out, but when using Thunderbird I can access my account with no problems.

Any ideas?

---

### Post by p_quarles on 2007-12-02
Aside from Gmail and uploads, do you have any problems with other web pages? I.e., slowness, missing images, etc?

I'm guessing you might need to disable ipv6. Before doing that, though, you can run a connectivity test to help verify the problem. Press alt-F1 to open a terminal, and run this:
```
ping -c 5 http://www.google.com
```
This will attempt to send five "pings" to Google. If the connection is working well, you'll get quick responses and "0% packet loss."

---

### Post by cr0bar on 2007-12-02
> **p_quarles said:**
> Aside from Gmail and uploads, do you have any problems with other web pages? I.e., slowness, missing images, etc?

I'm guessing you might need to disable ipv6. Before doing that, though, you can run a connectivity test to help verify the problem. Press alt-F1 to open a terminal, and run this:
```
ping -c 5 http://www.google.com
```
This will attempt to send five "pings" to Google. If the connection is working well, you'll get quick responses and "0% packet loss."

Didn't work with the hostname, got the IP and it worked:

5 packets transmitted, 5 received, 0% packet loss, time 3999ms
rtt min/avg/max/mdev = 51.636/61.834/76.090/9.935 ms

I'm guessing IPv6 needs disabled, then. I have no trouble browsing normal webpages.

---

### Post by p_quarles on 2007-12-02
> **cr0bar said:**
> Didn't work with the hostname, got the IP and it worked:

5 packets transmitted, 5 received, 0% packet loss, time 3999ms
rtt min/avg/max/mdev = 51.636/61.834/76.090/9.935 ms

I'm guessing IPv6 needs disabled, then. I have no trouble browsing normal webpages.
Mm-hmm. If you're able to connect via the IP address but not the domain name, that means it's a DNS problem, and most likely related to the computer attempting to resolve ipv6 domain names. 

This link explains the change that needs to be made:
[http://ubuntu-tutorials.com/2007/11/18/how-to-disable-ipv6-on-ubuntu-710-gutsy-gibbon/](http://ubuntu-tutorials.com/2007/11/18/how-to-disable-ipv6-on-ubuntu-710-gutsy-gibbon/)

To edit that file with a graphical text editor:
```
gksudo gedit /etc/modprobe.d/aliases
```
You'll need to reboot the machine at this point, since this is a change to the kernel itself.

---

