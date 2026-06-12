---
title: "ssh from outside wont work :("
date: 2007-12-08
forum: General Help
---

### Post by earobinson on 2007-12-08
I have [bell sympatico]("http://www.bell.ca/home/") for my ISP and I want to set up my computer so I can ssh to it from the out side. I have the[ linksys  WRT54G]("http://www.linksys.com/servlet/Satellite?c=L_Product_C2&childpagename=US%2FLayout&cid=1149562300349&pagename=Linksys%2FCommon%2FVisitorWrapper") router with the Firmware Version: v4.21.1  and I have set up a static IP (see screen shot) and set up port forwarding yet I cant ssh into my computer ```
earobinson@MinusOne:~$ ssh 70.52.161.148
ssh: connect to host 70.52.161.148 port 22: Connection refused

```

Any ideas would be great!

Thanks.

Edit: Is bell blocking port 22? How do I get around this?

---

### Post by sg3524 on 2007-12-08
Is ssh running?  

Are you trying to hit it from somewhere other than home (you can't route to that address if you are behind the linsys).?

to see is ssh is running enter 'netstat -ltp' at a console and see if you have a line that has the ssh label in it.

I just tried to get an ssh answer from that address and it timed out.  If there was nothing there I should have gotten a 'no route to host' error message, so something is there.  I just can't tell if its the linksys or your pc.

Gram

---

### Post by earobinson on 2007-12-08
ssh is running I can ssh from inside my lan

---

### Post by sg3524 on 2007-12-08
Just tried again with tcpdump on.  I am sending but not get anything back.

You might be right about being blocked, but that sure would surprise me.

I am a network engineer, but not familiar enough with linksys routers to be much help sorry.  Any chance you have a firewall enabled on top of the NAT?

Gram

---

### Post by geirha on 2007-12-08
According to [this]("http://www.portforward.com/english/routers/port_forwarding/Linksys/WRT54G/SSH.htm") you need to uncheck "Block Anonymous Internet Requests" in the Security tab.

---

### Post by Whiffle on 2007-12-08
I think you've got the static ip address setup in the same range as what the dhcp server uses, which makes things not work.  try something like 192.168.1.151

---

