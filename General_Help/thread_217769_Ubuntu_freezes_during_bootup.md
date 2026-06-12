---
title: "Ubuntu freezes during bootup"
date: 2006-07-17
forum: General Help
---

### Post by cloucas on 2006-07-17
I had a friend install Ubuntu and latest Dapper packages, and configured ppp modem connection on my A22p IBM Thinkpad.  The system worked fine for a few days and then it stopped booting.

It freezes while displaying "IPv6 over IPv4 tunneling driver"

I don't know what to do...Is there a way I can boot, by excluding certain features like the networking part?  I don't have a network at home, although had the laptop connected onto a network while I installed Ubuntu.

Any help?  I am new to Linux, and there seems to be no way of bypassing this point to get my machine to start.

Thanks in advance

Chris

---

### Post by Rui Pais on 2006-07-17
HI, maybe disabling ipv6...
if you dont't knoew how, just do:

```
sudo gedit /etc/modprobe.d/bad_list
```
and add
> alias net-pf-10 off

Now reboot and IPv6 sould be turn off on your system.

Hope that helps

---

### Post by cloucas on 2006-07-17
Thanks for your response!

The problem is I cannot get the computer to boot so as to give the commands you mention.

How do I go get it to boot?


Thanks a lot!

Chris

---

### Post by cloucas on 2006-07-18
I have managed to start it up by pressing CTRL-C while trying to configure network iterfaces.  I then configured it the way you said.

The PC works fine now.  Thanks a lot.

Chris

---

