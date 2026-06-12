---
title: "X Error: BadDevice, invalid or uninitialized input device 168"
date: 2006-10-19
forum: General Help
---

### Post by hayati on 2006-10-19
i know that similar (perharps exactly the same) messages could come to forum before. The question is;
When I run a gui program from the terminal, i get the following errors, but the program seems to run fine.
```
X Error: BadDevice, invalid or uninitialized input device 168
Major opcode: 148
Minor opcode: 3
Resource id: 0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
Major opcode: 148
Minor opcode: 3
Resource id: 0x0
Failed to open device
```

there is solutions to make these messages disappeared.(xorg.conf wacom device entries) But i thing still something is going wrong. Because;

commenting-out mentioned lines stops error messages. but i wonder if anyone noticed that a KNotify window is trying to appear in menu bar, but it never appears. it's like when a program is loading before its window appears. Cursor changes to 'wait cursor' and window's caption in the taskbar appears but KNotify's window never appears. This means that something wrong is happening, but system is simply ignores errors or cannot process them. I had this problem within a kdevelop qt project(also other gui applications causes same problem when they're called from console). Even after commenting-out mentioned lines KNotify window is about to appear. But after a couple of seconds everything gets normal. So i thing the solution stops the error messages, but the problem still exists.

---

