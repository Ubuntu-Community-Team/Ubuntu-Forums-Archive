---
title: "chrome size and position don't stick"
date: 2024-06-14
forum: General Help
---

### Post by marcw on 2024-06-14
After one of the last couple of chrome updates, maybe 5 days ago or so, my chrome browser doesn't stay sized or positioned after I close and open it a few times.  It always want to grow a bit until after 3-4 openings it becomes maximized.  And it always seems to want to start at the top of the screen instead of where I last placed it.  Both of these behaviors are new from about 5 days ago.  Not sure it's a chrome issue or something else but it is sure annoying. 

Any ideas or solutions?

running 20.04.5 LTS with latest updates.
Current chrome version is 126.0.6478.61 (Official Build) (64-bit)

---

### Post by TheFu on 2024-06-15
Tell the program where you want it to start and how large the window should be in the CLI options at startup.  I did this for years with Chromium, before it became available only as a snap under Ubuntu.  No I use Brave-Browser, but the same options work.  
```

#!/bin/bash 

firejail --private /opt/brave.com/brave/brave-browser \
   --window-position="97,0" \
   --window-size="1683,1153"  "$@"  &
```

Just pick the location and size you want, put it into a script and change all the ways you start the program to use that script instead.

I've never used Google-Chrome.  That doesn't make any sense to me, but to each their own.

Also, you can remove the **firejail --private** part if you don't want it.  I prefer not to allow chromium-based browsers any access to write to any storage.

---

### Post by marcw on 2024-06-15
Thanks.  I now recall those settings, or something similar, in my Firefox days.  But I found something easier since I'm not doing a lot of CLI or scripting stuff any more.  I went into the Chrome settings and under Appearance I just enabled "Use system title bar and borders".  I gained an unwanted title bar but I can live with that.  At least Chrome now stays where I put it and stays the same size.

---

