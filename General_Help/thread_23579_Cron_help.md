---
title: "Cron help?"
date: 2005-04-02
forum: General Help
---

### Post by Nequeo on 2005-04-02
I'm afraid this one has me stumped...

I have the following in my crontab:


```

0 2 * * * /home/sger/apps/azureus/azureus
0 9 * * * killall java

```

All I want to do is start Azureus at 2:00am and kill it off at 9:00am (I'd welcome any suggestions about a more elegant way to do this, as well). 

These jobs are running, I see them in my logs. But Azureus never appears. I can launch Azureus with that script from both the launcher and the command line. But for some reason it won't work in cron or at. The killall java bit certainly works. 

For what it's worth I'm running Hoary AMD64 version... But I suspect that's unrelated. I'm sure I just need to slightly modify the command to get the script running through cron, but I'm stumped if I know how.

Any help would be appreciated.

Thanks!

---

### Post by negatory on 2005-04-03
There's a plugin for Azureus that allows you to schedule downloads, you can get it [here](http://azureus.sourceforge.net/plugin_details.php?plugin=SpeedScheduler).

Have you started it as root and running your X session as a normal user?If that happens than you may have no permissions to run azureus on that X session.
If you did a new crontab for your user (the one running X) I guess it would be ok.
Hope it helped!

Pedro Carrico

---

### Post by alastair on 2005-04-03
Cron has a different environment than the usual, so it might just be that Java can't be found, for instance. You could look into that - there should be output/error mailed to you as well. You can set PATH up in the crontab.

See : man 5 crontab

---

### Post by Nequeo on 2005-04-03
Thanks...

I figured it was something simple like that. I'll RTFM and see if i can get it working with cron. And then once I've beaten the cron, I'll prolly switch over to the plugin.

Cheers,

---

