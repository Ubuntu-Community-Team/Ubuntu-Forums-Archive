---
title: "automatically save screenshots upon pressing PrintScreen key without prompting"
date: 2017-11-02
forum: General Help
---

### Post by msvcp71 on 2017-11-02
Every time i want to screenshot something, i press PrintScreen key and it always prompts me where to save, but when the prompt window appears it freezes some fullscreen applications and wine applications, any way to make it automatically save without prompting when i press PrintScreen? 
i use the default screenshot software that came with ubuntu 16.04 lts
[IMG]https://i.imgur.com/NCU2jyT.png[/IMG]
wanting to remove this annoying message

---

### Post by vasa1 on 2017-11-02
```
gnome-screenshot -wp -f /home/vasa1/Dropbox/Screenshots/"GS$(date +%Y%m%d%H%M%S)".png
```captures the active window without any prompting.

Read *man gnome-screenshot* for more.

---

