---
title: "Connection timed out HTTPS in Squid"
date: 2016-05-15
forum: General Help
---

### Post by javier50 on 2016-05-15
[COLOR=#000000][FONT=Verdana]Hi everyone. [/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]Please you can help with the following: [/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]Using squid 3.1.23, the client browse pages HTTP without problems (eg [www.cnn.com]("http://www.cnn.com")) but in HTTPS (example: [www.google.com]("http://www.google.com")) is in "waiting for google.com..." for 5min, and then displays the next screen: [/FONT][/COLOR]

> [B][SIZE=2]The following error was encountered while trying to retrieve the URL: [http://www.google.com/](http://www.google.com/)

    Connection to 2607:f8b0:4007:802::2004 failed. 

The system returned: (110) Connection timed out 

The remote host or network may be down. Please try the request again.[/SIZE][/B]



[COLOR=#000000][FONT=Verdana]Any suggestions? [/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]Thank you.[/FONT][/COLOR]

---

### Post by SeijiSensei on 2016-05-16
[http://wiki.squid-cache.org/Features/SslBump](http://wiki.squid-cache.org/Features/SslBump)

---

### Post by javier50 on 2016-05-16
> **SeijiSensei said:**
> [http://wiki.squid-cache.org/Features/SslBump](http://wiki.squid-cache.org/Features/SslBump)

Thanks for your reply.


I installed a "self sing" in the server, but the problem continues. What really catches my attention is that it is only in some HTTPS pages, give examples: Google or yahoo does not work, however, some banks (eg, bankofamerica**[B])**[/B] work without problems which are HTTPS.


Specific: When going into [www.google.com]("http://www.google.com") (for example) the browser show "waiting for google.com ..." for about 4min and then displays the following:

```

[COLOR=#073763][FONT=verdana]*The following error was encountered while trying to retrieve the URL:[http://www.google.com/](http://www.google.com/)*[/FONT][/COLOR][INDENT]***Connection to 2607:f8b0:4007:802::2004 failed.***
[/INDENT]
[COLOR=#073763][FONT=verdana]*The system returned: (110) Connection timed out*[/FONT][/COLOR]
[COLOR=#073763][FONT=verdana]*The remote host or network may be down. Please try the request again.*[/FONT][/COLOR]

```

Thanks for your opinion.

---

