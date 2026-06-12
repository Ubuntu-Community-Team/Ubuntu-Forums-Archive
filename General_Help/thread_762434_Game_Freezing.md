---
title: "Game Freezing"
date: 2008-04-22
forum: General Help
---

### Post by Spatulas on 2008-04-22
Hey,
I'm having an issue with several different games.  All are 3D games, both native and wine.  When running any of them, my computer will periodically lock up for over a minute.  When I restart X, it will get better temporarily, but will start lagging for longer and longer until it will freeze up my entire system for over a minute.  While this is happening, X spikes to full CPU usage.

I am running Kubuntu, have an nVidia card and am using the nvidia drivers.

Any help would be sincerely appreciated.

---

### Post by MoLE on 2008-04-23
hey Spatulas.

The way I'd approach this problem is to exclude a hardware issue first.  This sounds suspiciously like an overheating issue with the card.

Check the BIOS settings - make sure the memory timings etc are sane - may be worth going back to default settings and see if the problem continues.

The next step would be to run the game from the commandline and see what output you're getting - this may provide a clue.  Also X will log it's errors to /var/log/ - have a look at the log and see if there is any info in there that can help us help you.

---

### Post by ibuclaw on 2008-04-23
saving the command line output to a file is a better option to monitor any errors that may occur.

ie: If I were to run sauerbraten.
```
sauerbraten > ~/sauerbraten.log 2>&1
```

So when you are forced to restart X, all data is within that file of what's happening.

Or if you just want to catch the errors:
```
sauerbraten 2>~/sauerbraten.log
```

Regards
Iain

---

### Post by Spatulas on 2008-04-24
Spot on with the overheating diagnosis.  I had turned down my fans to sleep and forgotten to turn them back up again - doing so fixed the problem.

Thanks for the help!

---

