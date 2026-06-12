---
title: "Trouble with lightsquid config"
date: 2012-12-28
forum: General Help
---

### Post by awil on 2012-12-28
I don't have a lot of experience with linux. I am running Ubuntu 12.04 precise in VMware. It is a transparent proxy setup with traffic coming from a pfsense box. I have squid proxy server running and producing log files. Squid3 is doing its job perfectly. I installed perl, apache, and lightsquid for the lightsquid install.

I get the apache test "It works " message in the browser (chrome, IE, & firefox). I ran the check-setup.pl and lightparser.pl without any issues. When I access the server locally through loop back address or remotely 192.168.#.#/lightsquid I get the message below




[COLOR=DarkGreen]**Forbidden**

 You don't have permission to access /lightsquid/ on this server.
  Apache/2.2.22 (Ubuntu) Server at 192.168.5.197 Port 80
[/COLOR]




www-data user has access to the entire folder /var/www/lightsquid. I think I may have the wrong permissions somewhere. Can anyone give me some suggestions, please?

Thank You

---

### Post by awil on 2012-12-28
Can anyone let me know if they successfully installed lightsquid on Ubuntu 12.04? If you have did you follow the instructions exactly the way they are on [http://lightsquid.sourceforge.net/Installs.html](http://lightsquid.sourceforge.net/Installs.html) or was it entirely different. Any help would be greatly appreciated.

---

### Post by awil on 2013-01-08
I gave up trying to get lightsquid to work. I found out there are many different log analyzers out there. Sarg worked perfectly:p . I was viewing charts and graphs in the matter of minutes without tons of configuration.

---

