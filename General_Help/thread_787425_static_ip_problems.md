---
title: "static ip problems"
date: 2008-05-08
forum: General Help
---

### Post by notatoad on 2008-05-08
i followed the instructions here: [http://howtoforge.com/perfect_setup_ubuntu_6.06_p3](http://howtoforge.com/perfect_setup_ubuntu_6.06_p3) to set up a static ip on my nas box running 7.10 to make a /etc/network/interfaces looking like this: 
```
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address 192.168.1.3
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.1.255
        gateway 192.168.1.2
```

my router (with the internet plugged into it) is at 192.168.1.2, my dhcp server (running dd-wrt) is at 192.168.1.1
now trying to ssh into it gives me a "connection refused" error.  any ideas what went wrong?

---

### Post by hariprs on 2008-05-08
Can you able to ping and telnet?

---

### Post by Iowan on 2008-05-08
The problem you're describing seems more like a SSH setup issue than an IP problem.

I'm trying to find what/where I had to change in my SSH setup to allow connections.

I remember copying data into an **authorized_keys2** file - but I still use passwords.

---

### Post by notatoad on 2008-05-08
i've been connecting to it for a year over ssh through a dhcp-assigned ip address.  i'm pretty sure it's not an ssh problem.

it was saying no "route to IP" before i rebooted, now i have plugged a graphics card in and it looks like the problem may be that it's getting stuck fscking on boot rather than a network configuration problem.

---

