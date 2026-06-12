---
title: "supertux config"
date: 2008-06-18
forum: General Help
---

### Post by lgdadmdc on 2008-06-18
I just installed supertux2 and I don't have a config file in the hidden folder in my home folder. can someone please post a config file that I can copy and paste? I love this game.

---

### Post by acreech on 2010-03-21
> **lgdadmdc said:**
> I just installed supertux2 and I don't have a config file in the hidden folder in my home folder. can someone please post a config file that I can copy and paste? I love this game.

For anyone who maybe trying to make this game run. This is the Supertux2 config file. Just save it as ~/.supertux2/config

```
(supertux-config
  (show_fps #f)
  (console #f)
  (locale "")
  (video
    (fullscreen #t)
    (video "auto")
    (vsync #t)
    (width 800)
    (height 600)
    (aspect_ratio -1)
  )
  (audio
    (sound_enabled #t)
    (music_enabled #t)
  )
  (control
    (keymap
      (map
        (key 13)
        (control "menu-select")
      )
      (map
        (key 19)
        (control "pause-menu")
      )
      (map
        (key 27)
        (control "pause-menu")
      )
      (map
        (key 32)
        (control "jump")
      )
      (map
        (key 94)
        (control "console")
      )
      (map
        (key 112)
        (control "pause-menu")
      )
      (map
        (key 127)
        (control "peek-left")
      )
      (map
        (key 271)
        (control "menu-select")
      )
      (map
        (key 273)
        (control "up")
      )
      (map
        (key 274)
        (control "down")
      )
      (map
        (key 275)
        (control "right")
      )
      (map
        (key 276)
        (control "left")
      )
      (map
        (key 279)
        (control "peek-right")
      )
      (map
        (key 306)
        (control "action")
      )
      (map
        (key 308)
        (control "action")
      )
    )
    (joystick
      (dead-zone 1000)
      (jump-with-up #f)
      (map
        (button 0)
        (control "jump")
      )
      (map
        (button 1)
        (control "action")
      )
      (map
        (axis -2)
        (control "up")
      )
      (map
        (axis -1)
        (control "left")
      )
      (map
        (axis 1)
        (control "right")
      )
      (map
        (axis 2)
        (control "down")
      )
    )
  )
)
```

---

