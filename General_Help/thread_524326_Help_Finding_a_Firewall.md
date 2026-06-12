---
title: "Help Finding a Firewall"
date: 2007-08-13
forum: General Help
---

### Post by aaznx on 2007-08-13
I may be picky, but I need a firewall (I can pay if I need to but would prefer not to) that has the following features:

[list]
[*]Traffic Shaping based on type (BitTorrent, Web, VoIP, etc) that isn't just allow/reject, basically let me chose this above or below normal traffic or something
[*]An easy to use interface (no command line)
[/list]

If anyone could help that would be fantastic!

-AaznX

---

### Post by ramjet_1953 on 2007-08-13
OK,

First up, you already have a firewall by default and it is very secure.

It is called [COLOR="Blue"]iptables[/COLOR]

All ports are closed and you are protected.

However, if you need to do any port forwarding, you can download the Firestarter package. It is a graphical front-end for iptables.

[COLOR="Red"]sudo apt-get install firestarter[/COLOR]

There are other GUI front-ends for iptables, like [COLOR="Blue"]GuardDo[/COLOR]g, as well.

Remember to only run the firestarter GUI when you want to make changes. It is not good security practice to have a package that is running in root-mode on your desktop, when connected to the Internet.

Also, if you are working behind an ADSL router, you may also need to set up port forwarding on that as well, as it will also be fire walling your Internet connection.

Regards,
Roger :cool:

---

### Post by eentonig on 2007-08-13
> **ramjet_1953 said:**
> OK,

First up, you already have a firewall by default and it is very secure.

It is called [COLOR="Blue"]iptables[/COLOR]

**All ports are closed and you are protected.**
....

Actually, to start with. Ubuntu's implementation for ip-tables comes with all ports open if I remember correctly. 
The all ports closed statement is correct, but that's because they don't install any server software by default.

I would recommend against firestarter for more advanced FW configuration. You're free to try it off course, but I felt it missed some advanced options. I now use fwbuilder.

---

### Post by aaznx on 2007-08-13
Actually all I really need is a traffic shaper.

I don't want to use the command line, and I don't want to use an overly complex system.

Just be able to say "P2P limited to 128kb/s down 52kb/s up, HTTP 256kb/s down 128kb/s up and it's priority is over P2P, and VoIP takes dominance over everything else!"

---

### Post by frodon on 2007-08-13
Iptables is based on port not on apps type, all you will be able to do will be based on port. I may be wrong but i don't think iptables is designed to handle download/upload rates what it does is advanced packet filtering.
Controlling the download/upload rates is more a software question, it is not related to the firewall (except that on windows some software firewalls offer this as extra feature),

---

### Post by yota on 2007-08-13
You already have a traffic shaping/control command too: it's called tc, but unfortunately I'm not aware of any gui frontend for it.
Anyway there are a couple of premade scripts that you would just have to edit (to configure) and fire, not complicated at all.

One is wondershaper and  it's in the repositories (basic and easy); the other is sabishape and it's available [here]("http://www.sabi.co.uk/") (a bit more complete and configurable)

Hope this helps!

p.s. If you find that 'tc' is missing (I believe it's installed by default, but I'm not sure) it's contained in the "iproute" package.

---

