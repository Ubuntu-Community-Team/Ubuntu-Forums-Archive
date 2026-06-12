---
title: "utorrent and wine problem"
date: 2007-05-01
forum: General Help
---

### Post by JMuffin on 2007-05-01
I've had Ubuntu installed for about a month. I installed wine and got utorrent running, but after restarting my computer last week utorrent will no longer start up. I've tried uninstalling and reinstalling wine and redownloading utorrent, but neither have helped. I have utorrent added to the applications list in wine, but every time I try to open the .exe it tells me there is not a program to handle the file type. I tried opening utorrent from the command line and received the following errors:

err:ole:CoGetClassObject class {304ce942-6e39-40d8-943a-b913c40c9cd4} not registered
err:ole:CoGetClassObject no class object {304ce942-6e39-40d8-943a-b913c40c9cd4} could be created for context 0x1
fixme:listview:LISTVIEW_SetColumnOrderArray iCount 16 lpiArray 0x33ee18
fixme:keyboard:UnregisterHotKey (0x20026,1): stub
err:ole:CoGetClassObject class {304ce942-6e39-40d8-943a-b913c40c9cd4} not registered
err:ole:CoGetClassObject no class object {304ce942-6e39-40d8-943a-b913c40c9cd4} could be created for context 0x1

I have no idea what any of that means, so if anybody could shed some light on it I would greatly appreciate it.

Before last week I had absolutely no problems with utorrent or wine.

---

### Post by zvacet on 2007-05-02
I don´t know if this will help you,but I think you need to delete  .wine folder (home directory>view>show hidden files) and reinstall wine after that.Try to install utorrent again.

[http://ubuntuforums.org/showthread.php?t=191161&highlight=utorrent]("http://ubuntuforums.org/showthread.php?t=191161&highlight=utorrent")

I hope it will work.I know what are you missing.

---

### Post by JMuffin on 2007-05-02
Whatever the problem was, that fixed it. Thanks a bunch! I was going through torrent withdrawal.

---

