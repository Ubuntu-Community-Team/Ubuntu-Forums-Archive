---
title: "vim problem in gutsy"
date: 2007-11-05
forum: General Help
---

### Post by bmgz on 2007-11-05
I normally use vim as an IDE by using a vertical split screen with the file explorer on the left and the file editing done in the right pane. However, I can't get this to work in gutsy. 

When I press shift-P in the file explorer to open the file in the right-hand window, I get an error:

[COLOR="Red"]Error detected while processing function <SNR>25_NetPrevWinOpen..<SNR>25_NetBrow
seChgDir:
line    5:
(NetBrowseChgDir) b:netrw_curdir doesn't exist!
Press ENTER or type command to continue[/COLOR]

Is this a bug or is it just me? Is there a way to fix this? I need to do some work rather urgently!

---

### Post by pylon42 on 2007-11-05
Hrmm... here's what I get:

```
Error detected while processing function <SNR>18_NetPrevWinOpen..<SNR>18_NetBrowseChgDir:
line   87:
E121: Undefined variable: w:netrw_liststyle
E15: Invalid expression: w:netrw_liststyle == s:TREELIST && exists("w:netrw_treedict")
```

---

