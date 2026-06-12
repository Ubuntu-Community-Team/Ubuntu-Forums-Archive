---
title: "apache2 question."
date: 2013-11-05
forum: General Help
---

### Post by linuxsudoer on 2013-11-05
I'm setting up my first apache2 web server. I am using ubuntu 12.04lts. (not server edition). I am not sure how to make the website visible to public. On my local network it works great. I figured next step would be change the ports.conf to my ip have it Listen 80. Whenever I type my ip in though it brings my router up. According to [http://canyouseeme.org](http://canyouseeme.org) my ports are open.  Where should I look next? I been through the router options everything looks to be in order. any help hits tricks or links I can read up on will be appreciated. meanwhile I shall continue my searching and troubleshooting the best I can.

Thanks in advance!

---

### Post by linuxsudoer on 2013-11-05
Update, I had the option to remote manage my router on obviously. I turned this off and then it blocks port 80 from the router xD... I found a new headache to work around.

---

### Post by linuxsudoer on 2013-11-06
so im thinking I have configred ports.conf incorrectly. I am getting this error now when I restart apache2

>  ... waiting .apache2: Could not reliably determine the server's fully qualified domain name, 
using 127.0.1.1 for ServerName

---

### Post by Lars Noodén on 2013-11-06
It's just a warning.  It cannot find a hostname in DNS associated with the ip number the web server is using.  You can set ServerName explicitly to get past that.

---

