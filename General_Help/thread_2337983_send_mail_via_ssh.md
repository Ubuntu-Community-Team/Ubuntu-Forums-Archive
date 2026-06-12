---
title: "send mail via ssh"
date: 2016-09-23
forum: General Help
---

### Post by marchello_lippi2 on 2016-09-23
Hi all, 

My ISP blocks 25 port, so I would like to send mail via ssh on my vps. 
How do I create ssh tunnel properly or is there any mail utility that knows how to send message through ssh? 
Thanks ahead.

---

### Post by marchello_lippi2 on 2016-09-23
Ok, I figured out how to do it manually.

> 
ssh -nNT -L 9000:myvps:25 myuser@myvps

sendemail -f [EMAIL="me@example.com"]me@example.com[/EMAIL] -t [EMAIL="me@example.com"]me@example.com[/EMAIL] -u subject -m "test console" -s 127.0.0.1:9000


What I'd like also to do is to figure out how to set my monit to send notification via ssh. 
If someone has idea please share.

---

### Post by marchello_lippi2 on 2016-09-23
Added below code to crontab, so it should recreate ssh tunnel if it was broken.

> 
0 * * * * ssh -nNT -L 9000:myvps:25 myuser@myvps > /dev/null


also added 127.0.0.1:9000 as my smtp settings into monit config file. 
It works well for now. 

I think cron should alert me about error if the tunnel exists when trying to recreate it. Will see and will think how to ommit error (if any).

---

### Post by SeijiSensei on 2016-09-23
You might want to consider setting up a full-time tunnel with OpenVPN.  Take a look at [http://openvpn.net/static.html](http://openvpn.net/static.html).

---

### Post by marchello_lippi2 on 2016-09-23
I'd love to set up a full-time tunnel with OpenVPN, but it seems impossible at my vps, can't set tun device etc. But thanks for suggestion.

---

### Post by SeijiSensei on 2016-09-24
My only experience with virtual servers is at Linode where you have a complete Linux distribution.

It may be that you just need to [create the tun device]("https://www.kernel.org/doc/Documentation/networking/tuntap.txt") with mknod like this:
```

mkdir -p /dev/net
mknod /dev/net/tun c 10 200

```
You need to run these as root, of course.

If that doesn't work then it's likely your provider hasn't included support for the tun module in the kernel.

---

