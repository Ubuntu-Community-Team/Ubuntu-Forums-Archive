---
title: "scanner"
date: 2020-02-25
forum: General Help
---

### Post by oldbob2 on 2020-02-25
Hi folks,

I'm using Ubuntu 18.04.4 LTS and have just installed my printer/scanner drivers via the Software Manager, it's an Epsom AIO WF-3520. 

Can anyone tell me why I have to disable the ufw firewall to use the scanner? The printer works fine with the ufw enabled.

I also had this 'quirk' when I was using Mint Cinnamon, is it a common problem/quirk? It's no biggie as it's a simple process in Terminal to disable the ufw, I just wondered if there's a workaround.

---

### Post by rbmorse on 2020-02-25
Maybe the scanner front-end is calling home to check for updates when it is started?   Is that a configurable option in its setup?

---

### Post by SeijiSensei on 2020-02-25
If you're using it over the network, it appears that EPSON uses TCP port 1865 to send data to the computer, and UDP port 2968 for network discovery.  Add UFW rules to allow traffic to and from these ports.

[https://epson.com/faq/SPT_C11CD16201~faq-0000525-shared?faq_cat=faq-8796127635532](https://epson.com/faq/SPT_C11CD16201~faq-0000525-shared?faq_cat=faq-8796127635532)

Or alternatively add rules to whitelist the printer's IP address.

---

### Post by oldbob2 on 2020-02-26
> **rbmorse said:**
> Maybe the scanner front-end is calling home to check for updates when it is started?   Is that a configurable option in its setup?

Not that I'm aware of, there's nothing to indicate this in the printers settings, but as I said, its no problem to disable the firewall, scan what I need then re-enabling it again.

---

### Post by oldbob2 on 2020-02-26
> **SeijiSensei said:**
> If you're using it over the network, it appears that EPSON uses TCP port 1865 to send data to the computer, and UDP port 2968 for network discovery.  Add UFW rules to allow traffic to and from these ports.

[https://epson.com/faq/SPT_C11CD16201~faq-0000525-shared?faq_cat=faq-8796127635532](https://epson.com/faq/SPT_C11CD16201~faq-0000525-shared?faq_cat=faq-8796127635532)

Or alternatively add rules to whitelist the printer's IP address.

I tried both suggestions and still no go, never mind, its not as if the scanner gets much usage anyway. I can live with turning the firewall on and off when it's needed ;).

Thanks for taking the time to look this up for me, I appreciate then help.

---

