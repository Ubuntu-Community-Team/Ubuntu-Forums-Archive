---
title: "Cannot Access SAMBA Shares Off Local Network"
date: 2012-11-23
forum: General Help
---

### Post by jpv41193 on 2012-11-23
I'm having a very interesting problem with Lubuntu...

I set up a couple of Samba shares on an old desktop. It sits in my dorm room at school and I use it for just storing/sharing files. I'm able to connect to it perfectly fine while on campus. My SSH works, I can connect by the normal means from both Mac and PC.

Now, while I've been on vacation and am off the local network, I cannot connect to my server in Windows (by Run > \\HOSTNAME), nor can I connect to it on my Mac (Go > Connect to Server: HOSTNAME). The weird part is I can still connect to it via SSH and I can ping it, both with the hostname.

I had Windows try diagnosing the connection for me as a long shot and found that my server wasn't responding to requests over Port 445. So, "duh", I thought. I allowed port 139 in the firewall but not 445. So I added the allow rule to the firewall and still, nothing - even after rebooting the entire server.

So my question is, what on earth have I done wrong? I works perfectly fine while I'm on campus, but hasn't worked at all off campus. The really confusing part is that I can still SSH into it.

---

### Post by jpv41193 on 2012-11-25
I'm back on campus now and have verified that I can still access the server as normal. The problem is with it connecting off the local network only.

---

### Post by personalpc on 2012-11-25
Looks like your campus has a firewall that you don't have access to. By default most LAN's allow all internal traffic letting you access any machine connected to the campus. They also have very restricted rules when it comes to incoming traffic from an outside network. Your best bet is to do a nmap scan on the IP address you get from whatismyip.com when you are at campus. Whatever open ports nmap finds use in your samba conf in /etc/samba/smb.conf if you have any questions let me know

P.S. I would not advise generating too much traffic on your campus network because you most likely have signed a contract of use when they gave you access. This can result in expulsion of the student if you fall out of its guidelines. Example: network map scanning the firewall will get you into serious trouble if caught....

---

