---
title: "Constraining mouse input to only one process"
date: 2008-03-16
forum: General Help
---

### Post by triplicate on 2008-03-16
Here's my situation. I am trying to play Tribes Vengeance on Wine. Somehow, despite it's garbage ratings on winehq's appdb, it works fine for me. That is, except for one problem. Despite enabling DXGrab inside winecfg, Tribes doesn't want to actually use it. Therefore, I can look around as long as my cursor (whch is still moving behind the maximized window) is inside the constraints of my screen. Once my cursor hits the edge of the workspace behind Tribes, I get stuck, unable to move my field of vision any further in that direction.

I hope I've explained well enough. If not, for clarification purposes, imagine playing a  first person shooter without being able to turn around or look all the way down or up, depending on what your cursor is doing in non-game related processes. Sounds frustrating? It is.

Anyway, My question is whether or not there is either a way to force the wineserver to use DXGrab and stop my cursor from moving on any other screen besides the maximized game AND/OR is there a way to only send input from the mouse to a specific process?

Thanks in advance.

---

### Post by imbjr on 2008-03-16
Type winecfg in a Terminal session and go to the Graphics tab. You should see a "Allow DirectX apps to stop the mouse leaving their window" option. Try that, though I'm unsure how that will relate to DXGrab.

---

### Post by triplicate on 2008-03-16
Been there, done that. That option you speak of is DXGrab in shorthand. I have enabled it, disabled it, you name it. Basically there is nothing in the winecfg GUI that I haven't tried in hopes of fixing this problem. I either need a solution using wine in the command line FORCING DXgrab to work, or an altogether seperate tool to limit mouse input to a specific process.

---

### Post by triplicate on 2008-03-17
Hate to bump, but I've only gotten one reply, and my problem remains unsolved.

---

