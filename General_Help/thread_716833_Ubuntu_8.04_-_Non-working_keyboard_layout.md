---
title: "Ubuntu 8.04 - Non-working keyboard layout"
date: 2008-03-06
forum: General Help
---

### Post by flegmatyk on 2008-03-06
Hi, I've got a problem with Ubuntu 8.04.

My keyobard layout (Polish) doesn't work, so when I press Alt+Letter, it doesn't give me Polish diacritical letter, but nothing. It worked back in 7.10, in Settings -> Keyboard default layout is set to Polish, in a SCIM Input Method (it's shown in tray) in FrontEnd -> Global Setup -> Keyboard Layout it's set to Polish. I don't know, what am I doing wrong. I'm using Compiz Fusion, and I remember, that some time ago that was a problem with keyboard layouts on Beryl. Thanks in advance.

---

### Post by flegmatyk on 2008-03-06
```
setxkbmap -layout pl
```
seems to work for me, if anybody would like to know the immediate answer. But is it possible to do that in Gnome Keyboard Manager? I guess, that with my method I'd have to run that command every login...

---

