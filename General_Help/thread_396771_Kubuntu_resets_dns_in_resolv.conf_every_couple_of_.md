---
title: "Kubuntu resets dns in resolv.conf every couple of days"
date: 2007-03-29
forum: General Help
---

### Post by Chryana on 2007-03-29
I wonder if this bug is related to the bug where display power settings reset themselves after reboot. The problem is the following: the content of the file /etc/resolv.conf is a few invalid, or down, dns servers. I get a valid dns server by logging onto my router and copying the dns adresses it displays into Network Settings under the System Settings menu. I check afterwards the file resolv.conf, and it contains the dns I inserted. However, every couple of days, the dns servers I inserted are erased, and replaced with the previous (and invalid) dns servers, always the same ones. This is annoying because it breaks my internet connexion. Any idea what might be causing this? Thank you very much.

---

### Post by qpwoeiruty on 2007-03-29
Have you tried making it read-only?

chmod 222 /etc/resolv.conf

---

### Post by Chryana on 2007-03-29
You mean chmod 444 /etc/resolv.conf? :) No, I admit I did not. I thought about it, though, and I was hoping someone could find a better fix than this little workaround, since now I can't change the settings from the System Settings menu. It is now set like you suggested, and I hope it will work for the time being. Thank you for the reply.

---

### Post by nixclusive on 2007-03-30
Are you using DHCP for obtaining an IP address for you machine from the router? Try editing the file /etc/dhcp3/dhclient.conf and add the line: ```
prepend domain-name-servers <primary>, <secondary>;
``` replace <primary>/<secondary> with the valid IP addresses.

---

### Post by zvacet on 2007-03-30
Did you run** pppoeconf** after inserting nameservers?That should keep your settings.If that failed(after some time)you can try this.Put right nameservers and type
```
sudo /etc/init.d/networking restart
```

P.S.   Try rp-pppoe first.

[http://easylinux.info/wiki/Main_Page]("http://easylinux.info/wiki/Main_Page")
I don´t know wich version do you use but if you are using Edgy replace
Exec=gksudo /opt/rp-pppoe-3.8/go-gui  with Exec=gksudo tkpppoe

---

### Post by qpwoeiruty on 2007-03-30
> **Chryana said:**
> You mean chmod 444 /etc/resolv.conf? :) No, I admit I did not. I thought about it, though, and I was hoping someone could find a better fix than this little workaround, since now I can't change the settings from the System Settings menu. It is now set like you suggested, and I hope it will work for the time being. Thank you for the reply.

Oops, yeah I meant 444. Don't know what I was thinking when I put that down :P

---

### Post by Chryana on 2007-04-02
I tried chmod 444 /etc/resolv.conf and it didn't fix the problem... it comes back after a while. I guess I should have given more details... I indeed use dhcp, and my router takes care of the pppoe connexion. To see what would happen, after fixing resolv.conf once more, I sent 

sudo /etc/init.d/networking restart

It replaced the dns servers in resolv.conf with those displayed by the router, which are valid. I'm wondering if the reason it works for a while and then breaks is that when I reboot it takes it's dns servers from the routers until it decides to use the invalid resolv.conf file. I will leave resolv.conf alone for some more time and see what happens.

---

### Post by Chryana on 2007-04-03
As I expected, the file resolv.conf reset itself again to some invalid values. I really wonder where these dns servers come from. Anyways, I have now edited /etc/dhcp3/dhclient.conf, and added the ip of my router as my dns server. It used to work when I tried it on windows, hopefully it should work now.

---

### Post by Chryana on 2007-04-04
Editing /etc/dhcp3/dhclient.conf didn't work. I just lost my dns servers again. It's easy enough to get them back with /etc/init.d/networking restart, but nevertheless annoying. Did I need to reload or something like that? Or is there something else I could try?

---

### Post by zvacet on 2007-04-04
How your etc/network/interfaces look like.I mean you don´t need to post it here,just look is it everything O.K. there.if i everything O.K.and you still can not solve this problem try the link I posted to you and instructions for changes.When you do all that 

```
cd /opt/rp-pppoe-3.8
```
```
sudo ./go
```

---

