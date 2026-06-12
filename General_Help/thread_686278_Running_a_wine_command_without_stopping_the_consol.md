---
title: "Running a wine command without stopping the console"
date: 2008-02-03
forum: General Help
---

### Post by Statix0 on 2008-02-03
What I'm trying to do is do another command a second or two after I launch a wine program in my .sh script.

I want:
do stuff here
wine Start.exe
do something here, after Start.exe launches, but while it is still running

The problem is that once Start.exe is running the script waits until it closes before executing the next command. I'm looking for a way to get by this.

---

### Post by osx424242 on 2008-02-03
add a '&' after the command, e.g.:
wine Start.exe &

alternatively, with the focus on the terminal window from which you ran wine, press ^z (hold down control then press the 'z' key), then type 'bg' (for 'BackGround') (without the ' characters, of course).

---

