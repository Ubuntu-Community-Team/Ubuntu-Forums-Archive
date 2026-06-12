---
title: "Switching Proxy in KDE"
date: 2007-09-03
forum: General Help
---

### Post by karl_kashofer on 2007-09-03
Hi !

I use my computer at home (static ip, direct connection to internet) and at work (dynamic ip, have to use webproxy).
I would like to set up a shell script which switches these two environments for kde, but also for console (apt).

I know i can use profiles in the network settings, but i'd rather do it with shell scripts.
So:
I can figure out how to ping a server, check if it responds and then switch the network connection accordingly. I guess I could then set KDE to use http_proxy variable for proxy setup, but how do I get KDE to re-read the settings ?

Is there some other way to set the proxy used by kde from a shell script ?
Or is there a simpler solution to my problem ?

Thanks,
karl

---

### Post by strabes on 2007-09-03
If you're storing the environment variable http_proxy in the ~/.bashrc file (which I do when I'm at my university) then you can just use the command ```
source ~/.bashrc
``` to reload the settings instantly.

---

