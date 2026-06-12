---
title: "Proxy exceptions environment variable on the command line"
date: 2008-04-21
forum: General Help
---

### Post by thikrat on 2008-04-21
Hey All,

I have my proxy settings setup via the command line using the usual method.  
```

http_proxy="http://192.168.1.2:3128"
https_proxy="http://192.168.1.2:3128"
ftp_proxy="http://192.168.1.2:3128"

export http_proxy https_proxy ftp_proxy
```

The issue is, I don't want EVERYTHING to go through the proxy.  Right now, in the terminal everything goes through the proxy and I cannot find a way to set proxy exceptions from the command line in the way you would in firefox or in systems settings.  i do not have the option of setting this via a GUI.  I am running a server, with strictly cli/terminal access.  Any help would be greatly appreciated!

---

