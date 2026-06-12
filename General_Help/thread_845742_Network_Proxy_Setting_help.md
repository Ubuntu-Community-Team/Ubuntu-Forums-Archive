---
title: "Network Proxy Setting help"
date: 2008-06-30
forum: General Help
---

### Post by Eberbachl on 2008-06-30
Please help!

I set up a Ubuntu 8.04 machine on a network with a proxy server present.

I configured System->Preferences->Network Proxy to see the proxy server, but now I have moved the machine to it's final home where it doesn't use a proxy - direct connection to the internet via an ADSL router.

....so - I've changed the Proxy Settings back to Direct Connection, and I can get web browsing and email but it won't forget the proxy configuration for synaptic updates etc!!!

:confused:

Is there a config file hiding somewhere where synaptic stores this proxy information so I can edit and remove it manually?

Many thanks,

Luke.

---

### Post by Eberbachl on 2008-07-01
Bump ;)

Anyone?

---

### Post by dcstar on 2008-07-02
> **Eberbachl said:**
> Please help!

I set up a Ubuntu 8.04 machine on a network with a proxy server present.

I configured System->Preferences->Network Proxy to see the proxy server, but now I have moved the machine to it's final home where it doesn't use a proxy - direct connection to the internet via an ADSL router.

....so - I've changed the Proxy Settings back to Direct Connection, and I can get web browsing and email but it won't forget the proxy configuration for synaptic updates etc!!!

:confused:

Is there a config file hiding somewhere where synaptic stores this proxy information so I can edit and remove it manually?

Many thanks,

Luke.

Synaptic-Settings-Preferences-Network.

---

### Post by Eberbachl on 2008-07-03
Yes, I know where that is. I've changed it, but it still remembers the old proxy settings.

The question is, is there a .conf or similar file containing synaptic's proxy setting somewhere that I can just go and edit?

---

### Post by editrix on 2008-07-03
**If** there is, it's probably in /etc/ There's network files there, and a directory.

Sorry, I don't know any more about it.

---

### Post by Eberbachl on 2008-07-19
Hi Everybody,

Just a follow up post, as I found the fix.

Went out to the machine today, and found the file:

***/etc/apt/apt.conf***

Even though I had removed the proxy server configuration from System->Preferences->Network Proxy, and also from within Synaptic->Settings->Preferences->Network, the file still contained the following line:

```
Acquire::http::Proxy "http://proxyname:8080/";
```

I just removed the line from the file, and everything now works fine.

Come to think of it, that's all the file contained, and my machine (without any proxy configuration) does not contain such a file so I could most likely have just deleted the file.

Anyway, with the file present and the line removed it works fine.

Just thought it might be a useful reference for someone else that might encounter the problem.

:)

---

