---
title: "redirect spotify app to VPN"
date: 2017-12-01
forum: General Help
---

### Post by zeronoid on 2017-12-01
Hi,

How can i redirect Spotify linux app to a VPN (only spotify app not all the system) because it not available in my area?

---

### Post by Kirk Schnable on 2017-12-02
Don't really use Spotify but I thought I'd chip in here since this thread is pretty quiet.

VPN's function based on the routing table.  If you can determine the IP address ranges used by all Spotify services, you could add a static route on your system to route them via the VPN tunnel.  I'm not sure where you'd get that information though as I doubt Spotify has it publicly documented what their IP ranges are across their network.

You might have better luck with a proxy as opposed to a VPN.  I doubt Spotify supports proxy settings in their application because they don't really want their geo restrictions bypassed.  That said, you might be able to use Socksify to proxy it to a Socks proxy.  [https://linux.die.net/man/1/socksify](https://linux.die.net/man/1/socksify)

---

### Post by zeronoid on 2017-12-03
ok thanks

---

