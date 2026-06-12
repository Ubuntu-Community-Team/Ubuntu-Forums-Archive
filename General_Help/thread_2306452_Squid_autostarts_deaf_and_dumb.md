---
title: "Squid autostarts deaf and dumb"
date: 2015-12-15
forum: General Help
---

### Post by ecowan on 2015-12-15
I have a server that runs Squid and Dansguardian to filter web pages. The server shuts down every night and restarts in the morning.

I just rebuilt it, using Wily as the base. But now Squid doesn't autostart properly. Squid is running in the morning, but it doesn't 
respond to any client requests. If I manually "sudo /etc/init.d/squid3 stop" and then ".... start" it works just fine.

Any ideas, anyone? Thanks. - Erny

---

### Post by ian-weisser on 2015-12-15
How, exactly, are you autostarting the service?
Are you starting the service before, for example, the network is available?

---

### Post by ecowan on 2015-12-17
Thanks for your interest.
Squid is started by the script s03squid3 in /et/rc2.d which the squid3 package installed.

If I try to access the web via squid when it was started at boot, /var/log/access.log shows
(time stamp) 27 127.0.0.1 TCP_DENIED/407 4844 GET [http://(url)](http://(url)) HIER_NONE- text/html

- Erny

---

### Post by ecowan on 2016-01-06
I've been thinking about this. Perhaps it is because Squid and Dansguardian are starting in the wrong order. From what I can figure out, it's the RC#.d directories that control the autostart process. Squid and Dansguardian -both have entries s03... in RC2.d, RC3.d, RC4.d and RC5.d. But of course S03dansguardian appears before S03squid. Perhaps if I changed S03dansguardian to S04dansguardian?

I have read /etc/init.d/README and the Debian Policy manual. They talk about using update-rc.d to make changes.

Am I on the right track? It's scary territory, because my system might not be bootable if I get this wrong.

Thanks. - Erny

---

