---
title: "firefox downloads slow"
date: 2006-10-24
forum: General Help
---

### Post by strattonbrazil on 2006-10-24
Hey,

For quite a while when I try to download something on Firefox, it takes several seconds for it to start.  Like I'll click on the OK box and it will just sit there for several seconds.  

If I use Opera or even wget, the file starts immediately.  And in Firefox, once it starts, it goes fine, but it's just really annoying to hit OK, and then having to wait five or six seconds to go back to what I was doing.  Especially annoying when I have several files to download.  

Has anyone dealt with this problem?

---

### Post by funkyade on 2006-10-24
This may help:

1. In the address bar enter **about:config**
2. look for an entry called **network.dns.disableIPv6**
3. double click on it to toggle it's state to **true**
4. look for an entry called **network.http.pipelining**
5. double click again to set it to **true**
6. look for an entry named **network.http.pipelining.maxrequests**
7. double click again and set the value to 8 (or more)

in addition to this try installing the FlashGot extension using the extension manager - you will need to have curl installed as well ```
sudo aptitude install curl
```

also make sure you have the latest version of firefox, or try Flock ([http://flock.com/)](http://flock.com/)), which is basically firefox, but with a load of web2 stuff added to it - it is also faster imho.

hope this helps a little.

---

### Post by strattonbrazil on 2006-10-24
That did it.  Thanks a lot.  It was ridiculous to wait so long for it to finish.  It was like it was frozen for a few seconds.  I think it was the pipelining.  Thanks so much.

---

### Post by codeslicer on 2007-04-29
Also, for faster loading of web pages, you can try changing your DNS settings to use opendns. Go to:
[http://wwww.opendns.com]("http://wwww.opendns.com") It also stops phishing. (No I don't work there)

---

