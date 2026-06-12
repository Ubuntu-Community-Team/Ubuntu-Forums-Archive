---
title: "Open movie files on Windows Network"
date: 2007-09-24
forum: General Help
---

### Post by icic on 2007-09-24
Hi there!

I am having the problem identical to this unanswered thread: [http://ubuntuforums.org/showthread.php?t=310618](http://ubuntuforums.org/showthread.php?t=310618)

ie I have a number of videos stored on a windows share on my home network, and i would like to play them directly instead of copying them locally

but the problem is that totem won't play them properly, and if i try to associate the files with VLC, it won't "remember" the association and try to use totem to open the file every time.

so i suppose either of these would fix my problem:
1) make it remember the association to open with VLC instead of totem
2) make totem work

thank you very much for your time!

---

### Post by por100pre1 on 2007-09-24
Try grabbing a locally available copy of the required file type. Right-click it and select to open with another application. Use the custom command:

```
wxvlc
```

Then right-click the file again and click Properties. Click the Open with Tab and select VLC.

---

