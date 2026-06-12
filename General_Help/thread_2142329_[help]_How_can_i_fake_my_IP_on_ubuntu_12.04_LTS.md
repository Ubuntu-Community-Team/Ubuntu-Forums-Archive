---
title: "[help] How can i fake my IP on ubuntu 12.04 LTS"
date: 2013-05-05
forum: General Help
---

### Post by loftyboyt on 2013-05-05
Somebody help me. I want to fake my ip address to browers somes website. Cause that webs blog my ip. i found how to changes my ip but nothings found. 
If you know please show me how i can. Thanks you so much!

---

### Post by Mopar1973Man on 2013-05-05
Most people use a proxy server and change the proxy setting within Firefox (or what ever your using).

Another good site to try.
[http://www.hidemyass.com/](http://www.hidemyass.com/)

---

### Post by 3rdalbum on 2013-05-05
If you don't trust that website, you should not visit it. Every website logs IP addresses. You can't just "fake" an IP address because then the data you want to receive would go to the wrong place.

You could try a VPN or SSH tunnel.

---

### Post by loftyboyt on 2013-05-05
:) Thanks you! 
did you know the soft could be run in ubuntu?. Cause when i used that proxy... my browers is very slow cause  so many ad run same time.

---

### Post by loftyboyt on 2013-05-05
> **3rdalbum said:**
> If you don't trust that website, you should not visit it. Every website logs IP addresses. You can't just "fake" an IP address because then the data you want to receive would go to the wrong place.

You could try a VPN or SSH tunnel.

can i find VPN and SSH tunnel form where? Can you give me some tutorial. :( i'm newbei in ubuntu. i don't know why my ip is bloked by administrator. and form my country i can;t browers some website thus i have to changes my ip to come there.
p/s: sorry if my english's so poor, of couse if you don't understand what i wrote.

---

### Post by sammiev on 2013-05-05
I use [Witopia]("https://www.witopia.net/support/") for a VPN.

I also use bind9 for my DNS.

[PHP]sudo apt-get install bind9[/PHP]

Set your DNS 127.0.0.1 in your browser.

[PHP]sudo /etc/init.d/bind9 restart[/PHP]

---

