---
title: "Unable to SSH to my RPi3"
date: 2019-04-16
forum: General Help
---

### Post by ejach2000 on 2019-04-16
Hello, I recently changed my OS on my Raspberry Pi 3 from Raspbian to Ubuntu Mate 18.04 (which was a great decision besides the following problem).
I used Raspbian to host the Transmission BitTorrent client, it worked fine but I have had trouble with file permissions and the download would randomly stop (but this is besides the point).
I installed Transmission right out of the gate after switching to Ubuntu Mate, the installation was clean, no issues. I configured it to what I had on the previous OS, and I can access the Web UI with no issues.
But, I cannot use SSH outside of my Pi. When I attempt to connect to it, the connection it doesn't time out, it just says, 
```
x.x.x.x Connection refused: port 22
```
And when I run ```
sudo systemctl status ssh
``` it mentions something along the lines of:
```
Oct 16 08:59:45 openstack sshd[1214]: error: Could not load host key: /etc/ssh/ssh_host_rsa_key
Oct 16 08:59:45 openstack sshd[1214]: error: Could not load host key: /etc/ssh/ssh_host_dsa_key
Oct 16 08:59:45 openstack sshd[1214]: error: Could not load host key: /etc/ssh/ssh_host_ecdsa_key
```
(I got this directly from [this]("http://ask.xmodulo.com/sshd-error-could-not-load-host-key.html") article, this is nearly identical to the error I got when I look at the status)

I can provide any additional information if necessary.
Thanks!

---

### Post by HermanAB on 2019-04-16
Well, according to the error messages, you need to create the host keys.  Just do so and then restart sshd.

---

### Post by ejach2000 on 2019-04-16
> **HermanAB said:**
> Well, according to the error messages, you need to create the host keys.  Just do so and then restart sshd.  That worked perfectly, thank you for your help!  (Used [this](https://www.cyberciti.biz/faq/howto-regenerate-openssh-host-keys/) guide to create new keys)

---

