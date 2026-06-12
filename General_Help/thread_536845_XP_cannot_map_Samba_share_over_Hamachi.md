---
title: "XP cannot map Samba share over Hamachi"
date: 2007-08-28
forum: General Help
---

### Post by Ambis on 2007-08-28
- I have a box running Ubuntu 7.04.
- At eth1 it is connected directly to a Vista box.
- Eth2 is connected to my ADSL router (NAT)
- XP box way over the Interweb, also behind another router (NAT)

- Samba has bind interfaces only set to true, and interfaces are eth1 and ham0 (no need for eth0)
- Samba share works great directly trough eth1 (crossover cable) with Vista, so Samba is fine
- Hamachi works with Ubuntu, XP and Vista all ok (all ping eachothers, SSH etc works trought Hamachi, connection is P2P between all)
- Iptables has no rules
- Ubuntu's router doesn't need (to my knowledge) other forwards (for this) other than for Hamachi UDP traffic, which is set and working

The problem is: When I try to access the samba share trough hamachi with the XP box (way over the Interweb), using \\5.x.x.x\myusername, it asks for username and password. I provide those associated with my Samba share, and when I click OK it just asks it again.

Is there any way to get a samba share working trough Hamachi on any Windows machine with a working Hamachi? Did some research about this, and lots of topics described the same problem but all were without any definitive answer.

And yes, I could use WinSCP, and I infact do use it, but I cant play mp3:s trough it etc. This would be more than useful if I'd get it to work.

Please, help.

---

### Post by will71110 on 2007-08-28
I dont use Hamachi but I have goten openVPN to work running on my Ubuntu box. (usign webmin to modify it)

To get it to work I had to add iptables.  Basically turned my box into a NAT for my internal network.  This might not help but here is what I added into the iptables

iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
iptables -A FORWARD -i eth0 -o ppp0 -m state RELATED,ESTABLISHED -j ACCEPT
iptables -A FORWARD -i ppp0 -o eth -j ACCEPT

Of course you'd have to taylor this to your settings.

---

### Post by Ambis on 2007-08-28
Thanks, those look like valid iptables rules to me, but for the second one it says 

Bad argument `RELATED,ESTABLISHED'
Try `iptables -h' or 'iptables --help' for more information.

I have no idea what's wrong with that.

My version is

# iptables -A FORWARD -i eth0 -o ham0 -m state RELATED,ESTABLISHED -j ACCEPT

Should the input be the internet connected eth or hamachi?

---

### Post by will71110 on 2007-08-28
Oops....sorry I was freetyping that.

It's

iptables -A FORWARD -i eth0 -o ppp0 -m state --state RELATED,ESTABLISHED -j ACCEPT

---

### Post by will71110 on 2007-08-28
Re-read your post...here is how it goes

iptables -A FORWARD -i eth0 (Internal Network) -o ham0 (VPNed network)

And I forgot too you need to tell your box to forward traffic

echo 1 > /proc/sys/net/ipv4/ip_forward

EDIT:  Dont forget you need the last part 

iptables -A FORWARD -i ham0 -o eth0 -j ACCEPT

to return the traffic to the VPN

Be aware that this will delete if you restart the computer.  I'd suggest writing a script and putting a link it in your rc.local file

Oh and if you are having problem with the iptables you can 
iptables --flush

and start over

---

### Post by Ambis on 2007-08-28
Cheers, I'll try that.

I'd just like to know what that "echo 1 > /proc/sys/net/ipv4/ip_forward" bit does? If this doesn't work out, do I need to take that away or... what?

---

### Post by will71110 on 2007-08-28
It tells your box that you will use port Forwarding which if your iptables are empty, port forwarding will not happen.

---

### Post by Ambis on 2007-08-28
Oh man!

That actually seems to work right :) I'm not 100% sure since I'm now at the Vista box in the same LAN as the Ubuntu, but I did manage to map the samba share with \\5.x.x.x\usr. I guess it should make no difference where the other hamachi machine is since the connections always come from ham0.

Now I just need to find out how to import those rules at startup.

---

### Post by will71110 on 2007-08-28
I'll post instructions on how to do that later tonight...Heading home from work :)

---

### Post by Ambis on 2007-08-28
Oh crap, false alarm.

Since I had the same share already mapped, it seemed to work. When I copied a file to the hamachi share, I saw it using the gigalan (eth1) route and not the hamachi.

When I disconnected them all and rebooted Vista, now it doesn't want to map the share anymore. So, back to the drawing board. Maybe I'll just stick to the WinSCP then.

---

### Post by will71110 on 2007-08-28
Can you ping your internal network when you VPN using the stuff I told you?

---

### Post by Ambis on 2007-08-28
> **will71110 said:**
> Can you ping your internal network when you VPN using the stuff I told you?

What I did, was I moved my Vista to the Bridge connection in my ADSL router, so instead of having the Hamachi route inside the NAT, it now runs trough the NAT IP, not a local IP. Just to make sure there is no LAN confusion, since the point is to make this work *outside* the LAN. No need for encryption when there is a network cable with computers at both ends (eth1).

Both computers still ping each others fine (through Hamachi of course), but the sharing doesn't work.

Edit: Also the crossover gigalan cable is not connected ATM to reduce any additional weird behaviour.

---

### Post by will71110 on 2007-08-28
You might need to NAT to both ethernet ports but it'd be eaiser if you had a switch off eth0 and hooked both computers to the switch.

If you NAT from eth0 to ham0 you also have to NAT eth0 to eth1 and NAT eth1 to ham0. To much of a hassel. (this can cause issues too particually with port addressing).

---

### Post by will71110 on 2007-08-28
You might need to NAT to both ethernet ports but it'd be eaiser if you had a switch off eth0 and hooked both computers to the switch.

If you NAT from eth0 to ham0 you also have to NAT eth0 to eth1 and NAT eth1 to ham0. To much of a hassel. (this can cause issues too particually with port addressing).

EDIT: or did I mis read your post?

---

### Post by will71110 on 2007-08-29
This might be just an access issue then?  Can you see the drive(s)?  Another option would be FTP.  

I had a couple of smbfs issues before that I have ironed out so if it is an access issue I might be able to help you out there.

---

