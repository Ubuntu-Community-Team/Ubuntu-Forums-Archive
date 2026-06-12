---
title: "need help with ufw - can't ping local machines..."
date: 2024-05-08
forum: General Help
---

### Post by pacho415 on 2024-05-08
hi guys, 
i set up these ufw rules and they look correct to me but I can't ping any other device on the same network...

[FONT=lucida console]# set firewall rules[/FONT]
[FONT=lucida console]echo "Setting firewall rules..."[/FONT]
[FONT=lucida console]# all[/FONT]
[FONT=lucida console]sudo ufw default deny incoming[/FONT]
[FONT=lucida console]sudo ufw default deny outgoing[/FONT]
[FONT=lucida console]# local[/FONT]
[FONT=lucida console]sudo ufw allow from 192.168.178.0/24[/FONT]
[FONT=lucida console]sudo ufw allow to 192.168.178.0/24[/FONT]
[FONT=lucida console]# ssh[/FONT]
[FONT=lucida console]sudo ufw allow ssh[/FONT]
[FONT=lucida console]# transmission[/FONT]
[FONT=lucida console]sudo ufw allow in 51413/tcp[/FONT]
[FONT=lucida console]sudo ufw allow out 51413/tcp[/FONT]
[FONT=lucida console]# wireguard[/FONT]
[FONT=lucida console]sudo ufw allow in on wg0[/FONT]
[FONT=lucida console]sudo ufw allow out on wg0[/FONT]
[FONT=lucida console]
[/FONT]
[FONT=lucida console]# apply firewall rules[/FONT]
[FONT=lucida console]echo "Applying firewall rules..."[/FONT]
[FONT=lucida console]sudo ufw enable[/FONT]

what am I missing?

---

### Post by aljames2 on 2024-05-09
It would help when you post to show commands, code, & outputs within code tags.

By default, ufw denies incoming, allows outgoing, and denys routing.  Even with deny incoming it doesn't block ping by default, you have to go out of your way to block ping. Other things are probably causing this, likely your network.

I think before anyone can help you, you should tell more about your network.  What is this host (i.e. a VM, hypervisor host, container, or a single bare metal OS)?  If this is a VM, then which hypervisor are you using?  Do you have a bridge set up for your VMs to communicate on the network?  If not, then you may be running on the default hypervisor network which I think is NAT for KVM, which would inhibit communication between hosts on the network.

If this machine is not exposed to the internet, perhaps you could  temporarily disable your firewall and then try ping.  If ping still  doesnt' work, then you know it's likely your network.  Remember to enable it again after this quick test.

If ping does work when the firwall is brought down, and then breaks again when the firewall is enabled, then it could be your firewall, or, whatever you are doing with Wireguard on your network such as dropping ping packets to quiet down requests on your LAN.

You could try checking the result of this simple command to have a look at your firewall rules which you have set. Sometimes you can have extra rules set that you did by accident or through various trial & error along the way:

```
sudo ufw status
```

---

