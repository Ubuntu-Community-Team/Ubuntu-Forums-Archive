---
title: "[Lubuntu 19.10] Keep getting &quot;No such file or directory&quot; when starting some programs"
date: 2020-04-14
forum: General Help
---

### Post by ytterbious on 2020-04-14
I've been having the same problem when trying to run two unrelated   programs, Dropbox and Unified Remote (a cloud storage program, and a   wifi-connected input device from my phone, respectively).



Dropbox autostarts when I log in, but I always get this error:
```
/home/$USER/https:/www.dropbox.com/cli_link_nonce?nonce=69f442fe27d071b7e55c9a1209ee2545: No such file or directory
```

Any later attempt to kill/restart the program ends up loading the   process into memory, but the gui window never shows up. Guess it just   gives up ha.

And THEN, just today I saw that when I tried to start Unified Remote,   launching it from the .desktop file never loads, but it shows up as   being loaded in memory too.

When I try to load Unified Remote from its executable from /opt, I get this error message 
```
/home/$USER/http:/localhost:9510/web: No such file or directory
```

Relevant console output from the executable is:
```

Unified Remote Server (3.6.0.745)
Copyright (c) 2010-2015 Unified Intents AB.  All rights reserved.

starting server...
tcp interface could not start (check log)
udp interface could not start (check log)
bluetooth interface could not start (check log)
http interface could not start (check log)
discovery interface could not start (check log)

*** Access Manager ***
http://192.168.1.167:9510/web
ready (waiting for connection or debug command)
enter 'help' to see a list of available commands
enter 'exit' to terminate server
> stopping server...
exiting...

```

***After some fiddling:***
Okay, so I seem to have partially fixed the Dropbox issue by disabling  my VPN (though it still throws that error occasionally, and I don't know  what was happening there - anyone who has an idea, let me know). For  whatever reason Unified Remote (urserver) is still producing the same  behaviour, so perhaps they're not related? I'm totally in the dark, let  me know what you guys think.

---

