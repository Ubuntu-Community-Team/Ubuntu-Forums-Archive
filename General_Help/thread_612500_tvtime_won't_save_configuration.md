---
title: "tvtime won't save configuration"
date: 2007-11-14
forum: General Help
---

### Post by Ripfox on 2007-11-14
When I exit TvTime all my settings dissapear, anyone have this problem? It's like picture settings like brightness ect...

---

### Post by Ouchy on 2007-11-14
I had this problem. After running tvtime in terminal, it looked like I didn't have access to the tvtime configuration files located at ~/.tvtime.

I ended up changing group ownership of the folder from root to my username, and then it started to work.

---

### Post by Ripfox on 2007-11-14
Yep this was the problem! Thanks, I just did sudo chown -R username:username ~/.tvtime and now it works! :)

---

