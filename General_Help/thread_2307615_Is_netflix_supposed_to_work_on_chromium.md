---
title: "Is netflix supposed to work on chromium?"
date: 2015-12-26
forum: General Help
---

### Post by Sotai on 2015-12-26
I have installed chromium-browser and enabled widevine in the plugins. When I try to watch netflix, it won't let me (takes me to the 'netflix system requirements'. When I try to spoof the user agent to be google branded chrome, I get "Error Code: M7121-1321-1005". So does this mean chromium is simply not compatible? If so, then I guess the widevine plugin is just a prop?

---

### Post by Habitual on 2015-12-26
Google Chrome

---

### Post by Vladlenin5000 on 2015-12-26
I should be entirely supported in Google Chrome, not Chromium - [https://insights.ubuntu.com/2014/10/10/watch-netflix-in-ubuntu-today/](https://insights.ubuntu.com/2014/10/10/watch-netflix-in-ubuntu-today/) - although it should also be possible to use Chromium after installing Flash, I guess.

---

### Post by Sotai on 2015-12-26
> **Habitual said:**
> Google Chrome

64-bit-only, after early next year.

---

### Post by Sotai on 2015-12-26
> **Vladlenin5000 said:**
> although it should also be possible to use Chromium after installing Flash, I guess.

Flash has nothing to do with it.

---

### Post by deadflowr on 2015-12-26
> **Sotai said:**
> I have installed chromium-browser and enabled widevine in the plugins. When I try to watch netflix, it won't let me (takes me to the 'netflix system requirements'. When I try to spoof the user agent to be google branded chrome, I get "Error Code: M7121-1321-1005". So does this mean chromium is simply not compatible? If so, then I guess the widevine plugin is just a prop?

Perhaps this will shed some light on it for you:
[https://bugs.launchpad.net/ubuntu/+source/chromium-browser/+bug/1371274](https://bugs.launchpad.net/ubuntu/+source/chromium-browser/+bug/1371274)

My brief read-through of the bug linked, is that where as google-chrome can run widevine without any problems, chromium needs the plugin to be  patched.

Also a good fun read of the chromium bug here:
[https://code.google.com/p/chromium/issues/detail?id=429452](https://code.google.com/p/chromium/issues/detail?id=429452)

---

### Post by Sotai on 2015-12-27
> **deadflowr said:**
> Perhaps this will shed some light on it for you:
[https://bugs.launchpad.net/ubuntu/+source/chromium-browser/+bug/1371274](https://bugs.launchpad.net/ubuntu/+source/chromium-browser/+bug/1371274)

My brief read-through of the bug linked, is that where as google-chrome can run widevine without any problems, chromium needs the plugin to be  patched.

Also a good fun read of the chromium bug here:
[https://code.google.com/p/chromium/issues/detail?id=429452](https://code.google.com/p/chromium/issues/detail?id=429452)

You mean chromium needs to be patched, at least according to that bug report. Shed some light? Unfortunately, it doesn't. Now there are even more questions (although I suspect this is all simply google shenanigans, with the chromium devs as accomplices). I tried the ppa of chromium mentioned there, and it still didn't work, although the error is different. Now netflix says it can't find widevine, despite the fact that the plugin list says it's there, and enabled. So neither the widevine packaged in the mainline ubuntu chromium nor pasting widevine into that ppa chromium works, but the errors are different.

---

### Post by monkeybrain20122 on 2015-12-27
It doesn't work on Chromium, it has to be Chrome

You can use Firefox with pipelight's silverlight plugin [http://pipelight.net/cms/installation.html](http://pipelight.net/cms/installation.html)
and user-agent-overrider addon [https://addons.mozilla.org/en-Us/firefox/addon/user-agent-overrider/](https://addons.mozilla.org/en-Us/firefox/addon/user-agent-overrider/)
Set the user-agent-string to Firefox for windows when you watch Netflix.

---

### Post by Sotai on 2015-12-27
> **monkeybrain20122 said:**
> It doesn't work on Chromium, it has to be Chrome

You can use Firefox with pipelight's silverlight plugin [http://pipelight.net/cms/installation.html](http://pipelight.net/cms/installation.html)
and user-agent-overrider addon [https://addons.mozilla.org/en-Us/firefox/addon/user-agent-overrider/](https://addons.mozilla.org/en-Us/firefox/addon/user-agent-overrider/)
Set the user-agent-string to Firefox for windows when you watch Netflix.

Thanks, but no. If a machine is fast enough for that, it's 64-bit capable.

---

