---
title: "Why won't Ubuntu run on my network?"
date: 2007-04-27
forum: General Help
---

### Post by Zellio on 2007-04-27
I've switched from pppoe to dhcp, nothing.

I've done everything I know to connect linux, nothing.

YET WINDOWS XP, VISTA, MAC OSX... you name, and it can connect to my network... except this.

I'm tired of this. Does it have a PROBLEM with 10 digit codes or soemthing? Do I need to compromise my network and not enter a code AT ALL (in which case, linux will go in the trash) in order for it to run?

---

### Post by zvacet on 2007-04-27
system>administration>network settings>select your modem<properties>choose your type of connection(dhcp or static) and if you are runing feisty leave upper left box uncheked(if you are runing edgy or something else chek that box)>close.In DNS tab replace address you find there with your nameservers>close.

```
sudo pppoeconf
```

If you have USB modem look here 

[https://wiki.ubuntu.com/Home?action=fullsearch&context=180&value=usb+modem&titlesearch=Titles]("https://wiki.ubuntu.com/Home?action=fullsearch&context=180&value=usb+modem&titlesearch=Titles")

After you are done with your modem follow upper guide.

---

### Post by Zellio on 2007-04-27
Page won't load.

pppoe won't work.

---

