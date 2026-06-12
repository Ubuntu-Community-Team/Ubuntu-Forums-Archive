---
title: "Evolution Trash folder"
date: 2014-09-15
forum: General Help
---

### Post by aeronutt on 2014-09-15
versions: Ubuntu 14.04, Evolution 3.10.4

The way Evolution handles trash when configured for IMAP has me really confused.  Basically, in my setup, the evolution Trash folder does nothing. Deleting a file simply marks it as deleted, and then I can expunge, but the file never moves to Trash. If I try to set preferences to "Use a Real Folder for Trash", it won't let me select the Evolution Trash folder.  It also won't let me 'hide'  the useless Evolution Trash folder.

Maybe it's something in my configuration, but I've looked through all the preference settings and nothing I change helps. I can of course subscribe to my IMAPs Trash Folder and send trash there, but then I have 2 trash folders showing, one of them useless.

In the end, I'd like 1 trash folder, I'd like my deleted mail to go there (either to IMAP or local), and I'd like that mail to be saved for some fixed time (eg 30 days) or until I empty the trash folder.

Thoughts?

---

### Post by aeronutt on 2014-09-18
Anyone?

---

### Post by aeronutt on 2014-10-07
I finally figured this out.  Once selecting a remote folder for trash, and hitting 'ok', I had to wait a few minutes and it 'linked' the previously unused Trash folder to the remote folder, so now it's only showing one Trash folder. Just had to give the client and server a few minutes to sync.

---

