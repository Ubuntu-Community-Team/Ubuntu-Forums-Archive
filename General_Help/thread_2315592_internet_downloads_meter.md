---
title: "internet downloads meter"
date: 2016-02-29
forum: General Help
---

### Post by zandu on 2016-02-29
Is there a good download meter for Ubuntu  ?

---

### Post by X-RED_Tech on 2016-03-01
What's a download meter?

---

### Post by slickymaster on 2016-03-01
There's [BitMeter]("http://codebox.org.uk/pages/bitmeteros/downloads"). It's a web based internet bandwidth and data transfer monitor.

---

### Post by bswarm2 on 2016-03-01
There's always conky. Here's a snippet of my conkyrc network stats...
```
Up Speed: ${upspeed eth0}/s
Up Total: ${totalup eth0}b
Down Speed: ${downspeed eth0}/s
Down Total: ${totaldown eth0}b
${downspeedgraph eth0 22}
```

---

### Post by X-RED_Tech on 2016-03-01
I've installed BitMeter as suggested by slickymaster but couldn't make it work no matter what. Plus, after rebooting, a crash error appeared. Uninstalled.

---

### Post by slickymaster on 2016-03-01
> **X-RED_Tech said:**
> I've installed BitMeter as suggested by slickymaster but couldn't make it work no matter what. Plus, after rebooting, a crash error appeared. Uninstalled.
After installation you can access the BitMeter OS web interface using your web-browser```
http://localhost:2605
```BitMeter OS runs in the background, on a local web server on port 2605.

---

### Post by howefield on 2016-03-01
> **X-RED_Tech said:**
> I've installed BitMeter as suggested by slickymaster but couldn't make it work no matter what. Plus, after rebooting, a crash error appeared. Uninstalled.

I've just tried the 0.8 (experimental version) - worked fine. Uninstalled and tried the stable 0.7.6 again fine. What error did you get ?

An alternative nice, simple and easy network traffic monitor is vnstat. It's a command line tool but very easy to use.

Quite simple and low resources. It is in the repository so very easy to get up and running.

---

### Post by Habitual on 2016-03-01
vnstat here.

---

### Post by X-RED_Tech on 2016-03-02
```
[COLOR=#000000][FONT=Ubuntu Mono]http://localhost:2605[/FONT][/COLOR]
```

Yes, I've figured out the above but it gave some "unable to connect" error in the webpage and then crash errors on restart. 
It doesn't matter, it was just an experiment. I wouldn't be using it and already uninstalled.

---

