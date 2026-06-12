---
title: "Terminator not loading custom configuration"
date: 2020-09-13
forum: General Help
---

### Post by vtolenti89 on 2020-09-13
I just installed terminator and I have a few questions.
My ~/.config/terminator/config file contains the following:
```
[global_config]
[keybindings]
[profiles]
  [[default]]
    cursor_color = "#aaaaaa"
[layouts]
  [[default]]
    [[[window0]]]
      type = Window
      parent = ""
    [[[child1]]]
      type = Terminal
      parent = window0
      directory = ""
  [[test]]
    [[[child0]]]
      type = Window
      parent = ""
      order = 0
      position = 62:27
      maximised = True
      fullscreen = False
      size = 1858, 1016
      title = outnew
      last_active_term = ef505152-d9aa-4e08-b9f3-edf84fd85261
      last_active_window = True
    [[[child1]]]
      type = HPaned
      parent = child0
      order = 0
      position = 926
      ratio = 0.4997301672962763
    [[[child2]]]
      type = VPaned
      parent = child1
      order = 0
      position = 506
      ratio = 0.5004945598417408
    [[[terminal3]]]
      type = Terminal
      parent = child2
      order = 0
      profile = default
      uuid = 0192c847-4114-450c-b7f2-ddeb3252dddc
      directory = ~/Documents/foo
    [[[terminal4]]]
      type = Terminal
      parent = child2
      order = 1
      profile = default
      uuid = 67e64b69-da37-4012-92ee-7af2ef3905f2
      directory = ~/Documents/foo/frontend
      command = npm start; bash
    [[[terminal5]]]
      type = Terminal
      parent = child1
      order = 1
      profile = default
      uuid = ef505152-d9aa-4e08-b9f3-edf84fd85261
      directory = ~/Documents/foo/backend
      command = npm run dev; bash
[plugins]

```


When I run the following command ```
terminator -m -l test
``` three terminals open, but neither the directories are being loaded nor the custom commands run. 


1. Is there something wrong with this conf file?
2. I noticed sometimes the config file seems to be modified even though I did not changed it. Could that happen under any circumstance? 


Thanks in advance

---

