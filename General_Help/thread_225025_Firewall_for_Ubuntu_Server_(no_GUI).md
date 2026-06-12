---
title: "Firewall for Ubuntu Server (no GUI)"
date: 2006-07-28
forum: General Help
---

### Post by ProjectGod on 2006-07-28
hiya
is there a shell based utility to manipulate IP tables like firestarter or perhaps more granular than that to use on an ubuntu server? (without x window sys)

i would like to have this filtering out traffic and wish to open up ports for ssh etc.

many thanks.

---

### Post by hanzomon4 on 2006-07-28
Yes Their is [LINK]("http://www.ubuntuforums.org/showthread.php?t=159661&highlight=iptables")

---

### Post by ProjectGod on 2006-07-28
lol!  edit IP tables using the... ahem... iptables utility. 

very self explanatory! thankyou. :D

---

### Post by linuxbz on 2006-07-28
I really like firehol. I have used it in school and home situations.

[http://firehol.sourceforge.net/](http://firehol.sourceforge.net/)

apt-get install firehol

---

### Post by ProjectGod on 2006-07-28
firehol? hmmm does that require the x window sys? or is it nice like aptitude. :)

---

### Post by linuxbz on 2006-07-29
Firehol does not require a GUI. You just edit a text file in /etc/firehol. When you restart the firewall, it checks the configuration ... if there is a configuration error, it keeps the old iptables firewall.  If no error, it starts the new firewall.

It is much easier than writing iptables rules from scratch, but allows you to add them directly if you want to.  A simple firewall is easy, and a very complex one is possible.  Just the right combination for me.

It comes with a text-based configuration wizard that will try to examine your present Internet connections and listening services, and generate a commented configuration file from that.  After installation, it is "/usr/sbin/firehol-wizard".

You can also do "man firehol", and you can find documentation in "/usr/share/doc/firehol".  All is about as friendly as you can make what is a tricky, technical subject.

It also helps you learn about iptables, so you know what you are doing, instead of the typical GUI that hides all that from you.

Anyway, I like it a lot.

---

### Post by hanzomon4 on 2006-07-29
I'll have to try this Firehol

---

### Post by ProjectGod on 2006-07-30
cool. i'll give it a go too. :)

---

### Post by m83 on 2006-07-30
[Shorewall]("http://www.shorewall.net/") is the best firewall I have ever seen. You can do everything you want with it. It even supports traffic shaping.

---

