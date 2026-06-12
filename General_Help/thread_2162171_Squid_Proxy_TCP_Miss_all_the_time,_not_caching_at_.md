---
title: "Squid Proxy TCP_Miss all the time, not caching at all"
date: 2013-07-13
forum: General Help
---

### Post by jcyin on 2013-07-13
[LEFT][COLOR=#333333][FONT=UbuntuRegular]I've installed Squid Proxy [/FONT][/COLOR][COLOR=#333333][FONT=UbuntuRegular]on Ubuntu for a forward proxy via[/FONT][/COLOR][COLOR=#333333][FONT=UbuntuRegular] [/FONT][/COLOR]```
[COLOR=#333333][FONT=UbuntuRegular]sudo apt-get install squid[/FONT][/COLOR]
```[COLOR=#333333][FONT=UbuntuRegular] [/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]I've not modified any of the default settings in squid.conf apart from [/FONT][/COLOR]```
[COLOR=#333333][FONT=UbuntuRegular]http_access deny all[/FONT][/COLOR]
```[COLOR=#333333][FONT=UbuntuRegular] to [/FONT][/COLOR]```
[COLOR=#333333][FONT=UbuntuRegular]http_access allow all[/FONT][/COLOR]
```
[COLOR=#333333][FONT=UbuntuRegular]Now I've used this command [/FONT][/COLOR]```
[COLOR=#333333][FONT=UbuntuRegular]# tail -f /var/log/squid3/access.log[/FONT][/COLOR]
```[COLOR=#333333][FONT=UbuntuRegular] to monitor the squid access logs in real time and I see that despite numerous different types of websites, static and dynamic, lots of images and static files, the results are still always the same.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]Lots of TCP_Miss and barely two or three TCP_Hits I've also checked the size of Squid's spool and it's only 4.0K
So I know now that Squid is not caching anything. Is there anyone able to help me out there with this? I've read almost every single article from google when searching for "Squid TCP_Miss" and "Squid not caching" but none of those worked for me.
Thanks


[/FONT][/COLOR][/LEFT]

---

### Post by gimmerealroot on 2013-07-18
What does running the following command on the server produce:

squidclient -h 127.0.0.1 -p 3128 [http://www.foxnews.com](http://www.foxnews.com)

dig yahoo.com

---

