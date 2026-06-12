---
title: "systemctl &amp; ufw (not just ufw)"
date: 2018-07-25
forum: General Help
---

### Post by undecidable on 2018-07-25
I have recently moved for 14.04 to 18.04.  One key difference is systemd.

There seem to be some processes I can run either by entering the command name
or running systemd followed by the unit name.
what is the relation between them?

For example, I run:
```
>>sudo ufw enable
Firewall is active and enabled on system startup
>>
>>sudo ufw status
Status: active
```

But if I then do:
```
>>sudo systemctl status ufw
  ufw.service - Uncomplicated firewall
   Loaded: loaded (/lib/systemd/system/ufw.service; enabled; vendor preset: enabled)
   Active: active (exited) since Wed 2018-07-25 09:31:56 HKT; 8h ago
     Docs: man:ufw(8)
  Process: 363 ExecStart=/lib/ufw/ufw-init start quiet (code=exited, status=0/SUCCESS)
 Main PID: 363 (code=exited, status=0/SUCCESS)
```

So if I run the ufw cmd, I can enable/disable the firewall.
But this seems to have no relation to the ufw unit managed by sytemctl.

The same thing applies to (say) openvpn.
eg openvpn can be run & managed in the following 2 independent ways:
```
>>openvpn abc.conf
or
>>systemctl start openvpn@abc
```

What is systemctl actually doing 
with process like ufw where it seems I manage it myself 
with the ufw command?

(in processes where there is a separate daemon, eg vnstat and vnstatd,
I understand systemctl would be managing the daemon.)

---

### Post by #&amp;thj^% on 2018-07-25
> **undecidable said:**
> 
What is systemctl actually doing 
with process like ufw where it seems I manage it myself 
with the ufw command?


When I first got introduced to systemd I felt the same way.:D 
that would be a long drawn out answer here is some food for thought: [https://www.digitalocean.com/community/tutorials/how-to-use-systemctl-to-manage-systemd-services-and-units](https://www.digitalocean.com/community/tutorials/how-to-use-systemctl-to-manage-systemd-services-and-units)

---

### Post by undecidable on 2018-07-25
Thanks 1fallen.  
In fact I have read that, and much more.
I do understand how to use systemctl to manage units etc.

What I don't understand is why there appears to no relation between 
running a command and managing that command's unit by systemctl,
as per the examples above.

---

### Post by steeldriver on 2018-07-25
ufw is a bit special imho - it's not really a "service" in the traditional sense (such as running a listening daemon for example), it's just an interface to the kernel's iptables ruleset

If enabled (as a "service") it just runs once on boot to load the rules into the kernel, and then exits - hence

```

(code=exited, status=0/SUCCESS)

```

---

### Post by undecidable on 2018-07-25
ah, excellent, clear explanation.  Thanks very much steeldriver.

What about openvpn:  do you know the difference between running it as a program
>>openvpn /etc/openvpn/abc.conf
and as a systemctl unit:
>>systemctl start openvpn@abc
?

---

### Post by steeldriver on 2018-07-25
Nope sorry - I know nothing about openvpn

---

### Post by undecidable on 2018-07-25
no problem, I think openvpn is likely a simple case of running as a daemon or non-daemon process.
ufw was the greater mystery.
So I'll close this as solved.

---

