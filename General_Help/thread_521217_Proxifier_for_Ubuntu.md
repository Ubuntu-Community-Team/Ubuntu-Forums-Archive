---
title: "Proxifier for Ubuntu??"
date: 2007-08-09
forum: General Help
---

### Post by veagles on 2007-08-09
I have to access net through a proxy, Is there any proxifier for Ubnuntu??

I use Proxifier in Windows, [www.proxifier.com/index.htm](www.proxifier.com/index.htm)

I have tried proxychains but I couldnt get it to work with firefox or opera.

---

### Post by splintercellguy on 2007-08-09
What kind of proxy are you planning to use?

---

### Post by veagles on 2007-08-09
> **splintercellguy said:**
> What kind of proxy are you planning to use?

HTTP Proxy..

---

### Post by splintercellguy on 2007-08-09
If it's an HTTP proxy why not just tweak GNOME proxy settings or Firefox's proxy settings? Perhaps you have misunderstood my previous question, since I was trying to see if you were using SOCKS 5 or WinGate or something.

---

### Post by veagles on 2007-08-09
> **splintercellguy said:**
> If it's an HTTP proxy why not just tweak GNOME proxy settings or Firefox's proxy settings? Perhaps you have misunderstood my previous question, since I was trying to see if you were using SOCKS 5 or WinGate or something.


I get XML errors or other kinds of errors when i put the http proxy in Firefox in both windows and ubuntu, that's why I use proxifier in windows..

Is there anything similar in Ubuntu?

---

### Post by veagles on 2007-08-09
Or else can someone tell me how to get firefox to work with proxychains..

When I enter proxychains firefox, firefox opens up but doesnt use the proxy,

---

### Post by strabes on 2007-08-09
Just use an environment variable. ```
sudo gedit ~/.bashrc
``` Put the following line at the bottom: ```
export http_proxy=http://proxyurl:portnum
```

Not sure, but you might have to run ```
source ~/.bashrc
```to apply the settings.

---

