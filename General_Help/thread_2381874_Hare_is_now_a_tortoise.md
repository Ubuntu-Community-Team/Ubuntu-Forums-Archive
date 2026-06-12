---
title: "Hare is now a tortoise"
date: 2018-01-06
forum: General Help
---

### Post by Lloydb39 on 2018-01-06
My zippy little homebuilt AMD system, with 16.04, has showed to a crawl. This happened after I tried both Kodi and Plex. Neither worked worth a damn, so I tried to remove all traces of both with Synaptic. Now, doing anything on my computer is like wading through molasses, even after multiple reboots and apt-get updates. System Monitor doesn't seem to indicate anything eating up resources. Can someone tell me a way to get out of this mess?

---

### Post by mikewhatever on 2018-01-06
How about RAM usage?
```
free -m
```

Also, the SM may not show all processes, either select 'Show all', or use top or htop.

---

### Post by Lloydb39 on 2018-01-06
5618 available. Should be good, right?

---

### Post by oldos2er on 2018-01-06
It would help if you show the entire output of free -m. How much RAM? Swap file or partition? If so, what size is it? Have you tried adjusting [swappiness]("https://help.ubuntu.com/community/SwapFaq#What_is_swappiness_and_how_do_I_change_it.3F")?

---

### Post by Lloydb39 on 2018-01-07
>               total        used        free      shared  buff/cache   available
Mem:           7930        1635        3268          61        3025        5893
Swap:          8134           0        8134
I did not know about swappiness, but I'll give it a go.

---

