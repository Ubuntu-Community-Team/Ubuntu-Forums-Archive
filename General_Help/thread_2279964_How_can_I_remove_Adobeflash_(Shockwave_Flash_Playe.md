---
title: "How can I remove Adobeflash (Shockwave Flash Player)?"
date: 2015-05-27
forum: General Help
---

### Post by mikodo on 2015-05-27
Thanks to monkeybrain20122's advice in this [Ubuntu Forum Thread]("http://ubuntuforums.org/showthread.php?t=2278445"), I really enjoy using Smtube and Smplayer, for for watching YouTube. I don't watch much, but it works for all the stuff I have tried, so far.

That got me thinking of removing Adobe Flash (Shockwave Flash Player). Rant about inherent vulnerability possibilities.

So, if I remove the flashplugin-installer package, what do I do next, to remove the Adobe Flash Player plugin, that was downloaded from the Adobe web site?

Thanks.

---

### Post by monkeybrain20122 on 2015-05-27
If you purge the package the folder /usr/lib/flashplugin-installer should be removed along with it. libflashplayer.so is in it.

BTW Since you have removed flash you may like this [https://addons.mozilla.org/en-US/firefox/addon/watch-with-mpv/?src=cb-dl-created](https://addons.mozilla.org/en-US/firefox/addon/watch-with-mpv/?src=cb-dl-created)

---

### Post by mikodo on 2015-05-27
> **monkeybrain20122 said:**
> If you purge the package the folder /usr/lib/flashplugin-installer should be removed along with it. libflashplayer.so is in it.

BTW Since you have removed flash you may like this [https://addons.mozilla.org/en-US/firefox/addon/watch-with-mpv/?src=cb-dl-created](https://addons.mozilla.org/en-US/firefox/addon/watch-with-mpv/?src=cb-dl-created)

Thanks, again.  :)

Edit. I thought I should include the command I used, for anyone reading this solved thread.

```
sudo apt-get remove --purge flashplugin-installer
```

---

