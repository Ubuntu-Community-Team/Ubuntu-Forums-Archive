---
title: "Firefox Locking Up with Specific Localhost Connection"
date: 2022-04-16
forum: General Help
---

### Post by Quarkrad on 2022-04-16
I trying to use Plex Server internally only (family video streamed to tv) - no need for external tv/films.   I can log into plex server via [www.plex.tv](www.plex.tv) through firefox without any problem but when I try via localhost:32400/web/index.html firefox locks up.  Brave and Vivaldi browsers do not have any problem using the same address. I have taken away all my extensions and firejail so firefox is running natively.

---

### Post by Quarkrad on 2022-04-16
If I start firefox in safe mode the address works

---

### Post by #&amp;thj^% on 2022-04-16
have  a look at the logs: "/var/lib/plexmediaserver/Library/Application Support/Plex Media Server/Logs"
also I remember having to set  network.dns.disableIPv6 was already set to true however once I set this to false localhost:32400 worked.
It's a thing with firefox.
Good Luck

---

### Post by Quarkrad on 2022-04-16
All the log files are empty.  I also made the change to false (it was already on false) and firefox still locks up - it doesn't seem to matter whether the setting is true or false.  Interesting - Brave browser, on launching localhost:32400/web/index.html immediately changes this address to:

```
https://app.plex.tv/auth/#!?clientID=7v68c02b3axou8jjp14lrodi&context%5Bdevice%5D%5Bproduct%5D=Plex%20Web&context%5Bdevice%5D%5Bversion%5D=4.76.1&context%5Bdevice%5D%5Bplatform%5D=Chrome&context%5Bdevice%5D%5BplatformVersion%5D=100.0&context%5Bdevice%5D%5Bdevice%5D=Linux&context%5Bdevice%5D%5Bmodel%5D=bundled&context%5Bdevice%5D%5BscreenResolution%5D=1918x895%2C1920x1080&context%5Bdevice%5D%5Blayout%5D=desktop&context%5Bdevice%5D%5Bprotocol%5D=http-loopback&forwardUrl=http%3A%2F%2Flocalhost%3A32400%2Fweb%2Findex.html%23%21%2Flogin%3FpinID%3D2009469155&code=yq20ynuwrrzm7sfqbyuualwnc&language=en-GB
```

I assume firefox should also make this change but it locks up before it gets to that page.

---

### Post by #&amp;thj^% on 2022-04-16
> **Quarkrad said:**
> 
I assume firefox should also make this change but it locks up before it gets to that page.
Yep mine does. (Screenshot)
I would now head to Mozilla for support.
First have a look at this thread: [https://support.mozilla.org/en-US/questions/1011967](https://support.mozilla.org/en-US/questions/1011967)

---

