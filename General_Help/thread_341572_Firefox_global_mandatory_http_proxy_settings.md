---
title: "Firefox global mandatory http proxy settings??"
date: 2007-01-18
forum: General Help
---

### Post by soldonz on 2007-01-18
Hi,

I have a multi-user ubuntu 6.06 server behind a firewall and proxy and I would like to either force all firefox users to use the proxy or at least set it to use the proxy as default. 

I have searched everywhere, just can't find this information somehow (bad luck?)

Can someone tell me how to push the firefox network proxy settings to all users please?

Many thanks,

Peter

---

### Post by peterLinux on 2007-01-18
This may help
[https://addons.mozilla.org/firefox/3896](https://addons.mozilla.org/firefox/3896)

Peter

---

### Post by dcstar on 2007-01-18
> **soldonz said:**
> Hi,

I have a multi-user ubuntu 6.06 server behind a firewall and proxy and I would like to either force all firefox users to use the proxy or at least set it to use the proxy as default. 

I have searched everywhere, just can't find this information somehow (bad luck?)

Can someone tell me how to push the firefox network proxy settings to all users please?

Many thanks,

Peter

I believe these settings are in the user.js file which is in each user's Firefox profile, so you would have to create a script to set those relevant particular variables (using "sed", most likely) when they logged in (or find another way to push it to them).

I just found this which may be of use:
[http://www.mozilla.org/catalog/end-user/customizing/briefprefs.html](http://www.mozilla.org/catalog/end-user/customizing/briefprefs.html)

---

### Post by soldonz on 2007-03-21
Thanks guys, I appreciate the response.

After some more search on the net, I "think" the following solution that I have found may be a bit easier and more suitable.

there is a file /usr/lib/firefox/firefox.conf

add the following line to lock the network setting globally in firefox using autoconfig that's on the server
```

lockPref("network.proxy.autoconfig_url","http://proxy.myserver.com/login.cgi");
lockPref("network.proxy.type",2);

```

or you can set the proxy manually by adding the following lines ([COLOR="Red"]not tested, but it should work just like the one above[/COLOR])

```

lockPref("network.proxy.http","proxy.myserver.com");
lockPref("network.proxy.http_port",3128);
lockPref("network.proxy.type",1);

```

This locks the http settings in firefox only and it does not interfere with anything else that may not want to use http_proxy. (possibly apt-cacher users?)

Regards,

Soldonz

---

