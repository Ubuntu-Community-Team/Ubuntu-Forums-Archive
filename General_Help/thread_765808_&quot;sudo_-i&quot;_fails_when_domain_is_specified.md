---
title: "&quot;sudo -i&quot; fails when domain is specified in 8.04"
date: 2008-04-24
forum: General Help
---

### Post by a2u on 2008-04-24
If I specify the domain name in System->Administration->Network->General->Domain Name, this control panel seems to add the domain name after hostnames that you enter in System->Administration->Network->Hosts.

For example, adding the hostname tetsuo leads to this in /etc/hosts:

192.168.x.x    tetsuo[COLOR="Blue"].domain.name[/COLOR]

Then, when you try to do a "sudo -i", the sudo command fails, complaining that tetsuo (without the domain name) is unknown.

The only way to fix this seems to be to manually edit /etc/hosts and adding another alias like this:

192.168.x.x    tetsuo.domain.name    [COLOR="Blue"]tetsuo[/COLOR]

I'm wondering if the Network control panel can be fixed so it won't arbitrarily add the domain name to hostnames in /etc/hosts.  It seems to do this everytime you save the network configuration, throwing away whatever manual edits you've made.

Regards,

Albertus (a2u)

---

### Post by bodhi.zazen on 2008-04-24
Not exactly sure what you are doing, but if you are changing your hostname you need to edit both 

/etc/hostname and /etc/hosts 

you hostname needs to be the same in those two files.

Other then that, if you are not changing your hostname, IMO best add host names (manually) in /etc/hosts as you are.

---

### Post by mainspecht on 2008-04-30
Succes!!
Thank you

---

