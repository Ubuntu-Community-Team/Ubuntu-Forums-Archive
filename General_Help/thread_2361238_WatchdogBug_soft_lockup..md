---
title: "Watchdog:Bug: soft lockup."
date: 2017-05-14
forum: General Help
---

### Post by Joao Lacerda on 2017-05-14
Hi Friends!

Can someone give some help on this?

thanks for your time.

[ATTACH=CONFIG]275113[/ATTACH]

---

### Post by TheFu on 2017-05-14
More info please.  these things tend to be HW, SW, and kernel specific.

---

### Post by Impavidus on 2017-05-14
I suggest you dig a bit into the log files. I had a couple of soft lockups the past week, which were caused by [a bug]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1674838"). It was quite obvious when I scanned through /var/log/kern.log.

---

### Post by SlickWilly18 on 2017-05-20
Before you continue, please consider this. I had the same error recently with the inability to shut down without using the REISUB trick. I eventually found the problem. It involves NDISWRAPPER and a bad wireless driver. I bought a known compatible usb wifi dangle and uninstalled the bad driver using   

 ```
sudo ndiswrapper -r net819xp.inf
```

 (net819xp.inf was my bad driver file) I plugged in the new wifi adapter, reset the computer normally, then logged back in to find that the wifi adapter (Panda PAU05 15 bucks  from Amazon) was working without ANY kind of setup or driver installation. (Plug n play) After making the switch to the new wifi adapter, my problem was completely  [SOLVED]. I hope that works for you. I suspect that ndiswrapper is giving many linux users issues with the soft lockup bug, but I've never seen it mentioned, so here it is.

---

