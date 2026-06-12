---
title: "gfuw/firewall -  how is it configured"
date: 2013-11-26
forum: General Help
---

### Post by joverjj on 2013-11-26
it's installed. i don't know if it's working and how to do the correct congiguration. thks

---

### Post by philinux on 2013-11-26
Moved to General Help forum.
These links might help.
[https://help.ubuntu.com/community/Gufw](https://help.ubuntu.com/community/Gufw)

[http://gufw.org/](http://gufw.org/)

---

### Post by fantab on 2013-11-26
> **joverjj said:**
> it's installed. i don't know if it's working and how to do the correct congiguration. thks

GUFW is merely a Graphical front end to UFW. Forget GUFW use UFW, it can be configured with simple command line instructions.

Follow [this guide]("http://blog.bodhizazen.net/linux/firewall-ubuntu-desktops/") for UFW, its very simple with clear instructions. It is all most of the users will need.

Good Luck...

---

### Post by gregz41 on 2013-12-07
Ok question I am just playing with this and learning I have both GUFW UFW  can you run both as one is just the front end or should I uninstall GUFW.......Like I said I'm just playing around with this learning actually :)

---

### Post by gregz41 on 2013-12-07
after thinking about what i just asked is'nt that gfuw just a graphical of the same thing.....I mean UFW is terminal use and GUFW is graphical but are the same thing

---

### Post by fantab on 2013-12-07
> **gregz41 said:**
> after thinking about what i just asked is'nt that gfuw just a graphical of the same thing.....I mean UFW is terminal use and GUFW is graphical but are the same thing

Yes they are the same thing. [UFW]("https://help.ubuntu.com/community/UFW") with a graphical face is GUFW. UFW uses [IPTABLES]("https://help.ubuntu.com/community/IptablesHowTo"), UFW makes IPTABLES configuration easier.

[QUOTE=UFW-Community Ubuntu Documentation]The default firewall configuration tool for Ubuntu is ufw. Developed to ease iptables firewall configuration, ufw provides a user friendly way to create an IPv4 or IPv6 host-based firewall. By default UFW is disabled. 
[Gufw]("https://help.ubuntu.com/community/Gufw") is a GUI that is available as a frontend. [/QUOTE]

Stick with UFW, GUFW is a waste IMO. Or get real and use Iptables. The choice is yours, whatever suits you.

---

### Post by 3rdalbum on 2013-12-07
> **joverjj said:**
> it's installed. i don't know if it's working and how to do the correct congiguration. thks

I'm guessing that you're a regular home user of Ubuntu, not using it for business or a server or anything.

As long as you don't install or enable any server programs (such as VNC, Apache, SSH, FTP servers etc) you don't even need a firewall.

However, since you've already got gUFW you should just block all incoming connections and allow all outgoing.

As noted before on this thread, gUFW is just the face of UFW. You don't need to keep the gUFW program running, the UFW firewall runs constantly in the background.

---

### Post by gregz41 on 2013-12-07
Thanks I will do a little digging into itables :)

---

