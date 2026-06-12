---
title: "Can I save a document directly into a folder?"
date: 2020-07-19
forum: General Help
---

### Post by alaudacorax on 2020-07-19
I keep my documents in a quite deeply nested system of sub-directories and sub-sub-directories and so on, all inside my Dropbox folder.

I'm in a directory, right-click to create a new document, Ctrl+s ... and the dialogue box defaults to /home folder and I have to navigate all the way back to the folder I started from before I can save. This is often ten or more clicks of the mouse away.

Is there any way to make Files save new documents directly into the folder I created them from?

This seems to me such an obvious procedure that I can't believe that there isn't an option for doing it; but I'm damned if I can find it, or any mention of it online (not with DuckDuckGo, anyway). Or am I missing something obvious. Anyone help?

Forgot to mention, I'm using the latest LibreOffice Writer on the standard Ubuntu 20.04.

---

### Post by dragonfly41 on 2020-07-19
To manage such workflows I use a twin-panel file manager. If you go into Synaptic Package Manager and search "File Manager" or "multi-panel" or "twin-panel" you will find several to experiment with.

4pane
tuxcmd
mc
krusader

I settled on Krusader for my workflows.
You can build up history of bookmarks, frequent url's, and define various useractions.

---

### Post by Dennis N on 2020-07-19
Use bookmark(s) in the file chooser to select the save location of a newly created document. Then you can get to that bookmarked directory in one click. Also, in LibreOffice, you can change the default location from ~/Documents to something else with Tools > Options > LibreOffice > Paths

---

### Post by mIk3_08 on 2020-07-19
To add the current folder to the bookmark list, press Ctrl+D or use the command Bookmarks.  Add Bookmark.
To remove or rearrange bookmarks in a different order use the Bookmarks - Edit Bookmarks command.

---

### Post by alaudacorax on 2020-07-19
Thanks for the suggestions, everybody. I shall look into that lot. The concept of bookmarks in the file manager is new to me, but now I know which way to look.

---

### Post by alaudacorax on 2020-07-19
Hah! I'm torn between laughing at myself and doing a really epic, concussive face-palm. I worked out how to do the quick saves using bookmarks. Thanks again for that. I then realised that all the sub-folders I'll need to bookmark this month *have exactly the same name*, '2020.07' :oops::oops::oops:. Lack of foresight, there ...

---

### Post by ajgreeny on 2020-07-19
You can probably rename the bookmarks by right clicking on them; I can in Xubuntu but I'm not certain about other DE versions, so try that before you delete the bookmarks.

---

### Post by alaudacorax on 2020-07-19
Yes, thanks ajgreeny, all sorted now. Another thing I've discovered only in the last few hours---after some three years with Ubuntu---is that you can rename a file with F2. I really must learn to read the instructions ...

---

