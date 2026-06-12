---
title: "VPN restart script when ping fails (or tun0 isn't present if someone knows how?)"
date: 2017-08-10
forum: General Help
---

### Post by derekcentrico on 2017-08-10
Howdy all.  I finally was able to get all data for the user VPN to pipe through the VPN whilst the rest of my data uses my WAN.  Only issues now is that every 48-36 hours the VPN drops and doesn't reconnect even with persistent variables enabled.

Basically, I don't know how to detect if tun0 is no longer there to reset the connection so I figured ping is a good way as well.

I'm missing something here because ping gives an error.

```
#!/bin/bash
x=`sudo -H -u vpn bash -c ping -c1 google.com 2>&1 | grep unknown`
if [ ! "$x" = "" ]; then
        echo "TUN0 down!! Attempting to restart."
        service openvpn@openvpn.service restart
fi

```

Ping gives me a usage result vs the actual ping result when I run the above command.  If I use the ping portion of the string solo in terminal it works fine...

Any thoughts on how to get this script to work -or- to detect tun0 is not present and to restart the service would be great.

Thanks all!

---

