---
title: "Put a shortcut for a program used by Wine on the Taskbar"
date: 2014-07-16
forum: General Help
---

### Post by mattw1 on 2014-07-16
I am trying to put a shortcut for a Windows program loaded by Wine on the Task Bar so that it can be launched from there.  I have attached a screenshot to show the shortcut I am talking about and have opened it's properties so that you can see relevant info.  Is there a way to do this that is relatively simple?

[ATTACH=CONFIG]254781[/ATTACH]

---

### Post by Dennis N on 2014-07-16
Since you have a Desktop shortcut showing in your image, there is probably an entry for the program in the Lubuntu main menu. To add a launcher to the bottom panel, follow the procedure in post #3 of this thread: 

[http://ubuntuforums.org/showthread.php?t=2234295](http://ubuntuforums.org/showthread.php?t=2234295)

see paragraph beginning "If you want a launcher on a panel..."

---

### Post by mattw1 on 2014-07-16
thx for the response.  Unfortunatley, no, there isn't one in the main menu.  When I installed program with Wine nothing came up in the main menu.

---

### Post by linux_dream on 2014-07-16
Since you already have the .desktop file, what I'd do is to move that file to /usr/share/applications.  If this doesn't work, open the .desktop file with leafpad or any other text editor and post here what it contains.

---

### Post by Dennis N on 2014-07-17
The attachment shows you have a file IrfanView.desktop on your Desktop (and in your Desktop folder). Usually, if you have a shortcut on the Desktop like this, it came from right-clicking on the Main Menu entry and choosing "Add to Desktop". So I am wondering how it got there. Did the Wine installer put it there but not in /usr/share/applications or ~/.local/share/applications?

At any rate, linux_dream is right. If you copy IrfanView.desktop from ~/Desktop to ~/.local/share/applications OR /usr/share/applications, it should then appear in the Main menu under the category specified in the .desktop file (graphics?). Then, once there, you can use the procedure linked to in post #2 to add a launcher.

---

### Post by mattw1 on 2014-07-17
Thanks.  Suggestion worked.  Much appreciated.  btw, yes Dennis N, the wine installer put the icon on my desktop but not in the main menu.  Go figure.

---

