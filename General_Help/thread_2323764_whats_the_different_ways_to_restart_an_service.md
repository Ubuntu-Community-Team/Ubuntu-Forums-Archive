---
title: "whats the different ways to restart an service?"
date: 2016-05-08
forum: General Help
---

### Post by weiqi3 on 2016-05-08
I know there are two ways to restart dhcp server, like "[COLOR=#333333][FONT=UbuntuMono]sudo service isc-dhcp-server restart[/FONT][/COLOR]" and "sudo /etc/init.d/isc-dhcp-server restart". I want to know whats the difference between this two ways. And Why when I configure my dhcp server, I always failed in using [COLOR=#333333][FONT=UbuntuMono]sudo service isc-dhcp-server restart. But [/FONT][/COLOR][FONT=UbuntuMono, courier, monospace][COLOR=#333333]succeed in using [/COLOR][/FONT]sudo /etc/init.d/isc-dhcp-server restart?

---

### Post by Bucky Ball on 2016-05-08
Welcome. All I can say is that the second command states specifically the correct path to the service you are trying to restart, the other doesn't. It's missing the path.

For instance, try putting yourself in the correct folder:

```
cd  /etc/init.d/
```

Then:

```
sudo service isc-dhcp-server restart
```

---

### Post by nerdtron on 2016-05-08
> **weiqi3 said:**
> I know there are two ways to restart dhcp server, like "[COLOR=#333333][FONT=UbuntuMono]sudo service isc-dhcp-server restart[/FONT][/COLOR]" and "sudo /etc/init.d/isc-dhcp-server restart". I want to know whats the difference between this two ways. And Why when I configure my dhcp server, I always failed in using [COLOR=#333333][FONT=UbuntuMono]sudo service isc-dhcp-server restart. But [/FONT][/COLOR][FONT=UbuntuMono][COLOR=#333333]succeed in using [/COLOR][/FONT]sudo /etc/init.d/isc-dhcp-server restart?


Is isc-dhcp-server a custom program? Also, on the newer ubuntu 16.04, we use systemd to stop/start services now since the "init" way is the old (legacy) way.

---

### Post by weiqi3 on 2016-05-08
> **nerdtron said:**
> Is isc-dhcp-server a custom program? Also, on the newer ubuntu 16.04, we use systemd to stop/start services now since the "init" way is the old (legacy) way.
[COLOR=#000000]Hi, [/COLOR]
[COLOR=#000000]Can you explain more about the difference between "init" and "systemd"? Thank you so much.[/COLOR]

---

### Post by nerdtron on 2016-05-08
Here's the long story which is easier to read for beginners (including history): [http://www.linuxjournal.com/content/initializing-and-managing-services-linux-past-present-and-future](http://www.linuxjournal.com/content/initializing-and-managing-services-linux-past-present-and-future)

But the most notable is that using old init, services are started "one at a time" or sequentially during bootup. And all processes are being called by the init program. Systemd on the other hand can launch simultaneous processes during bootup (means faster bootup). I'm just scratching the surface here. systemd can do a lot more like manage the start/stop of services including possible scheduling like how cron does things.

---

