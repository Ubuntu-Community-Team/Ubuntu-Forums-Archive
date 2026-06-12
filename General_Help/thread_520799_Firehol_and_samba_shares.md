---
title: "Firehol and samba shares"
date: 2007-08-08
forum: General Help
---

### Post by kspider on 2007-08-08
In feisty, I'd like to be able to use the gnome network browser to browse samba shares.  However, my firehol configuration seems to be preventing this.  With firehol deactivated (no iptables rules) I can browse just fine.

With the following firehol.conf, I can't browse shares, but I can connect to a specific share using gnome's "connect to server" thingy or smb:// in nautilus.

-------firehol.conf---------------------------
version 5
iptables -t filter -I OUTPUT -d 127.0.0.1 -p tcp --dport 3128 -m owner ! --uid-owner dansguardian -j DROP
transparent_squid 8080 "nobody root"

# Accept all client traffic on any interface
 interface any world
	policy drop
	client all accept
	server samba accept
---------------------------------------------------

Is there another port I need to have open to allow an smb broadcast or something?

Thanks - ks

---

### Post by ruibernardo on 2007-08-08
Hi kspider,

I think you should to put "server samba accept" **before** "client all accept".

Also, I can't confirm this, but the line about transparent_proxy should be

transparent_squid 8080 "proxy proxy"

Maybe this helps.

---

### Post by ruibernardo on 2007-08-08
One note: if you don't have a samba server on your Ubuntu, "server samba accept" shouldn't even be necessary.

"client all accept" should be enough.

---

### Post by kspider on 2007-08-09
Thanks - I tried moving the "server samba accept" line and commenting it out.  Neither had an effect.

Does anyone know of a good way to troubleshoot a firewall?  Meaning, how could I compare what necessary packets are getting through with the firewall turned off vs with it turned on?

Thanks - ks

---

### Post by ruibernardo on 2007-08-09
> **kspider said:**
> I tried moving the "server samba accept" line and commenting it out.  Neither had an effect.


I shouldn't have told you to remove that line, but to replace "server" by "client", since it's what you want. 

The following should work:

```
 version 5
iptables -t filter -I OUTPUT -d 127.0.0.1 -p tcp --dport 3128 -m owner ! --uid-owner dansguardian -j DROP
transparent_squid 8080 "proxy proxy"

# Accept all client traffic on any interface
 interface any world
	policy drop
**client samba accept**
client all accept

```

To see the error (log) messages of iptables (the firewall), check the /var/log/messages file. You can do it on the Gnome menu in the "System", "Administration" or opening a terminal and typing "tail -f /var/log/messages". Then try to access your share. If there is any problem, you should see it there.

Check the Squid/Dansguardian messages too.

---

