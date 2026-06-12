---
title: "How do I switch from Dolphin to Konqueror in Gutsy?"
date: 2007-10-28
forum: General Help
---

### Post by ibohren on 2007-10-28
I recently upgraded from Feisty to Gutsy (Kubuntu) and I'm finding that I don't really care for Dolphin. I've started getting this strange message whenever I close a window:

"ERROR-DOLPHIN

Unable to save bookmarks in /home/ibohren/.kde/share/apps/d3lphin/bookmarks.xml. Reported error was: Permission denied. This error message will only be shown once. The cause of the error needs to be fixed as quickly as possible, which is most likely a full hard drive."

I don't even understand this message. My hard drive is not even close to being full and I haven't done anything out of the ordinary in terms of settings changes.

Can anyone tell me how to switch back to having Konqueror as my default file manager. I can't seem to find an option in the system settings. 

Thanks a lot

---

### Post by aos101 on 2007-10-28
I haven't done it, but I did read how some people have done it in the Kubuntu Gutsy comments:
> Alt-F2, run "kcontrol". Go to KDE Components -> File Associations, select inode/directory, move konqueror to the top of the list, click "Apply". That's it, Dolphin is konquered.
[https://wiki.kubuntu.org/KubuntuGutsyComments](https://wiki.kubuntu.org/KubuntuGutsyComments)

Also in the comments is someone else who (I think) got the same error as you with Dolphin:
> if I open Dolphin, and then I close it, an error occurs: "Impossibile salvare i segnalibri in /home/vale/.kde/share/apps/d3lphin/bookmarks.xml. L'errore riportato è: Permesso negato. Questo messaggio di errore sarà mostrato una volta soltanto. La causa dell'errore deve essere risolta al più presto; quasi sicuramente il disco rigido è pieno.". I runned "sudo chown USER : USER /home/USER/.kde/share/apps/d3lphin/bookmarks.xml", and now it works!
It sounds there like the file owner could be wrong, so you might want to check that file is owned by yourself.

---

### Post by raul_ on 2007-10-28
It happens when you "sudo dolphin"

---

### Post by ibohren on 2007-10-28
That did the trick. Thanks a ton guys!

---

### Post by MickS on 2007-10-28
Thanks for that, Dolphin was bugging me.

Mick

---

### Post by Mahstah on 2007-10-28
This worked for me too. However, I had to run the script slightly differently than described above. The : USER part messed up the command. The one that worked for me was "sudo chown USER /home/USER/.kde/share/apps/d3lphin/bookmarks.xml" where USER was replaced by my username.

This happened after I had chosen the "Open as root" option in Dolphin to access a folder that was restricted. After that window was closed new windows returned the error when closed.

---

