---
title: "iptables slowly"
date: 2008-05-25
forum: General Help
---

### Post by flokky on 2008-05-25
I'm having two little problems with iptables:
First problem: when I want to output the content of the firewall and enter [PHP]iptables -L -vx[/PHP]
The output is shown on my screen, but very slowly. This command used to take less than a second five years ago, now it's taking 20 seconds to complete! 
I've checked in other SSH session, my server isn't doing anything special.

Second problem: I'm using iptables to know how many bytes were uploaded and downloaded by my users. This always went OK. I'm using the IP-address combined with the MAC. At the moment I'm seeing the netbios name instead of the IP. 

I would like to see this:[PHP] pkts      bytes target     prot opt in     out     source               destination
      25     1712 RETURN     all  --  any    any     **192.168.0.106**          anywhere            MAC 00:0F:B0:CA:D4:1B[/PHP]

But I'm seeing this:
[PHP] pkts      bytes target     prot opt in     out     source               destination
      25     1712 RETURN     all  --  any    any     **lpt60.local**          anywhere            MAC 00:0F:B0:CA:D4:1B[/PHP]

Thanks for helping out

---

### Post by HalPomeranz on 2008-05-25
By default, iptables will do name service lookups on IP addresses in the output.  I suspect that something in your configuration has changed recently that makes your name service lookups take longer-- perhaps they're timing out.

Anyway, you can turn off name service lookups by adding the -n option:

```
iptables -L -vxn
```

---

### Post by flokky on 2008-06-03
HalPomeranz: Thank you so much for that solution! I wouldn't have found this without you.

---

