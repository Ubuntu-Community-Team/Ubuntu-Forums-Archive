---
title: "How do i change the dhcp in Kubuntu?"
date: 2005-10-28
forum: General Help
---

### Post by derek19 on 2005-10-28
I know with mandriva you can set your dhcp name when you configure the lan connection. But since Kubuntu does it for you, where can i go change it so its that dhcp name wherever i go?


Thanks.

---

### Post by MarcDM on 2005-10-28
Haven't used Kubuntu, but on Ubuntu and Debian, to set a dhcp name, you edit the file /etc/dhcp3/dhclient.conf
and add a line like 
send host-name "blah.foo.com";

or are we talking about something else here?

---

### Post by derek19 on 2005-10-28
When i log onto my works network, it gives this:

dhcp-1711-129.dhcp.xxxxxxx.com

I don't want it to say dhcp-1711-129. When i logon a network, i would like it to say something i choose. Like linuxbuntu.dhcp.xxxxxxxxx.com. 

Anyone know where i can go to set it to default to what i choose?

---

### Post by derek19 on 2005-10-31
I changed the host name to what i want but still the network is assiging its own host name. 

Anyone help with this?

---

### Post by danron on 2005-11-02
Probably the DHCP server is configured to not allow you to set your own host. Run a tcpdump and pipe the result to dhcpdump (google for it) and you can see if dhclient really sends the host-name. If it does and the server still returns another host-name there's nothing you can do on the client side.

---

### Post by derek19 on 2005-11-04
[QUOTE=danron]Probably the DHCP server is configured to not allow you to set your own host. Run a tcpdump and pipe the result to dhcpdump (google for it) and you can see if dhclient really sends the host-name. If it does and the server still returns another host-name there's nothing you can do on the client side.[/QUOTE]

I'm able to change the dhcp name with mandriva. So that means i should be able to with any linux software correct?

---

