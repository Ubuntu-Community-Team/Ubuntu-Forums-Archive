---
title: "Script help"
date: 2007-07-12
forum: General Help
---

### Post by herbster on 2007-07-12
I am trying to get conky to close before game starts, then when game exits, start conky again.

```
#!/bin/bash
pkill conky &
export ETSDL_SDL_LIB="libSDL.so"
cd /usr/local/games/enemy-territory/
LD_PRELOAD="/home/bobby/et-sdl-sound.so" ./et.x86 $*
& dual-conky
```

Everything works except the last line, where "dual-conky" is my conky script in /usr/local/bin. If I remove the last line, conky closes, game starts fine, but would like to get conky going again automatically upon game exit.

TIA

---

### Post by yabbadabbadont on 2007-07-12
Try ```
dual-conky &
```

---

### Post by herbster on 2007-07-12
> **yabbadabbadont said:**
> Try ```
dual-conky &
```

You doggone genius, worked like a charm! Thanks so much :)

---

