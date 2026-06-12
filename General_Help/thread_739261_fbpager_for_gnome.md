---
title: "fbpager for gnome?"
date: 2008-03-29
forum: General Help
---

### Post by bigblop on 2008-03-29
I have tried to install fluxbox and fbpager to make fbpager run in gnome (Ubuntu 7.10) but nothing happens when I type fbpager from a shell.

I have made a file in ~/.fluxbox/fbpager containing:

fbpager.alpha: 255
fbpager.x: 0
fbpager.y: 0
fbpager.workspace.width: 64
fbpager.workspace.height: 64
fbpager.workspacesPerRow: 6400
fbpager.followDrag: false
fbpager.followMove: false
fbpager.changeWorkspaceButton: 11
fbpager.raiseWindowButton: 2
fbpager.lowerWindowButton: 3
fbpager.closeWindowButton: 3 3 1
fbpager.exitButton: 1 3 3
fbpager.nextWorkspaceButton: 4
fbpager.prevWorkspaceButton: 5
fbpager.moveInWorkspaceButton: 1
fbpager.dragToWorkspaceButton: 2
fbpager.align: LeftToRight
fbpager.color: white
fbpager.windowColor: white
fbpager.focusedWindowColor: white
fbpager.windowBorderColor: black
fbpager.backgroundColor: darkgray
fbpager.currentBackgroundColor: lightgray
fbpager.multiClickTime: 250
fbpager.icons: false
fbpager.windowBorderWidth: 1

How do I start fbpager in gnome?

---

### Post by kiccioni on 2008-06-14
think there's no way yet to make fbpager work under gnome...:(

---

### Post by urukrama on 2008-06-14
If fbpager doesn't work, you could try a different pager. I recommend netwmpager. You can download the source code [here]("http://ftp.osuosl.org/pub/gentoo/distfiles/netwmpager-1.11.tar.bz2").

---

