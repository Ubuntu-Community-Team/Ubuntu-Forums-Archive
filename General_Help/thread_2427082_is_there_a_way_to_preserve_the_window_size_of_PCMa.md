---
title: "is there a way to preserve the window size of PCManFM?"
date: 2019-09-17
forum: General Help
---

### Post by ardouronerous on 2019-09-17
I'm running Lubuntu 18.04.

I have a preferred window size for PCManFM and I'd like to preserve it because sometimes I would accidentally change the window size with my mouse clicks, and I'd like know if there's a way to perverse the size, like after I close PCManFM, it would revert back to my preferred window height and width. Is there a way to do this, thanks.

---

### Post by TheFu on 2019-09-19
All proper X/Windows client programs should support the -geometry command line switch.  Something like this:
```
-geometry 80x25+760+355 
```
or
```
--geometry 80x25+760+355 
```
to control both the size and screen placement for the window. Caja works with the 2nd example.

I don't know about PCManFM.

---

