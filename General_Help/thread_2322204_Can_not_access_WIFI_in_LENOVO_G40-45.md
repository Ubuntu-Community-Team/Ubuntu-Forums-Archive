---
title: "Can not access WIFI in LENOVO G40-45"
date: 2016-04-26
forum: General Help
---

### Post by bediwatta on 2016-04-26
Hi all,
I am a new Ubuntu user and installed Ubuntu 16 on my laptop Lenovo G40-45.
But I can not connect to my WIFI. I followed many posts on web to do the job.
but I am still unable to do.
Can anyone guide me. Great help
Thanks
Bediwatta:confused:

---

### Post by UbuntuAddict99 on 2016-04-26
Hello bediwatta,

And first of WELCOME to Ubuntu.
Now when you say you are unable to connect to your WI-FI, do you mean actual connecting through the settings? or there is NO WI-FI connections visible and it only has a Ethernet connection? because i have a similar issue with my Acer E5 laptop. Where every so often after a few updates my WI-FI NIC is turned off (disabled) and only my Ethernet is working so i have to re-install the Linux version of my NIC's driver to get my wireless connections working again.

So if you could elaborate the issue a bit more that would be better for us your fellow Ubuntuers to help you. And also there has been ALOT, of bugs with 16.04 LTS so far.

Happy Linuxing.

"Linux Ubuntu The Final Frontier!"
                                             -UbuntuAddict99

---

### Post by bediwatta on 2016-04-26
No WIFI connections visible in the network list.
Only when plugged in by Ethernet cable internet works.
but I need to connect to internet by WIFI

---

### Post by UbuntuAddict99 on 2016-04-27
Then all you need to do is to look up the model of your Wireless card or NIC. And search for the Linux drivers for it and install them.

Happy Linuxing.

P.S. This article should be able to help you find your WI-FI's NIC on Linux Ubuntu URL [http://www.cyberciti.biz/faq/linux-list-network-cards-command/](http://www.cyberciti.biz/faq/linux-list-network-cards-command/)

"Linux Ubuntu The Final Frontier!"
                                              _UbuntuAddict99

---

### Post by bediwatta on 2016-04-27
Thank you very much...This worked....:D

---

### Post by UbuntuAddict99 on 2016-04-27
You are very welcome Bediwatta,

And i hope you are enjoying Linux Ubuntu.

Happy Linuxing.

P.S. Keep those drivers around, because in my case. Anyway every so often it disables but i re-install it in a minuets time and i have WI-FI again.

"Linux Ubuntu The Finale Frontier!"
                                              -UbuntuAddict99

---

### Post by jeremy31 on 2016-04-27
This thread is lacking a lot of details

bediwatta can you post the result of ```
lspci -nnk | grep -iA2 net
```

Along with what you did to solve the issue?

---

