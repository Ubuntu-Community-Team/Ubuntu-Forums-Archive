---
title: "ERROR after running update manager."
date: 2008-06-18
forum: General Help
---

### Post by gdmlsk on 2008-06-18
I encounter this error after running update manager in tandem with manual flash update.

My computer lags for flash video and games. I tried to remove the flash plugin from mozilla through synaptic but the error below popped up.
[IMG]http://img441.imageshack.us/img441/432/screenshotsynapticbi9.png[/IMG]

Please help.

GREETING message:
VERY new to Ubuntu, Linux. I had given up using XP and donated it. Windows XP began to get too repetitive, or maybe it wasn't versatile--who knows?. So here I am, installing Linux for the first time and using it. And this definitely won't be the last time I will use it. :)

---

### Post by cdtech on 2008-06-18
Add the following line to /etc/apt/apt.conf.d/70debconf:
```
APT::Cache-Limit "16777216";
```

Hope that helps.....

[B]P.S.
Or you could probably just use the command sudo apt-get clean maybe.[/B]

---

### Post by gdmlsk on 2008-06-20
It's still showing the same dialog box. The error is not leaving.

And another problem I have is with my flash video only displaying frame by frame, VERY slow. I tested this on flash games too and the same thing happened. Is there a way to work around this problem?

---

