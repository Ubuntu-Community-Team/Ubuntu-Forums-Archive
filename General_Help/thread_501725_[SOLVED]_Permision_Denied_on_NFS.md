---
title: "[SOLVED] Permision Denied on NFS"
date: 2007-07-15
forum: General Help
---

### Post by NeghVar on 2007-07-15
Ok I have been trying for several hours to get this working and have read at least 5 different guides/tutorials and numerous posts here on the forum with absolutely no success.

I have the exports folder set up to rw access but when I attempt to mount all it comes up with is a permission error. None of these posts or guides solve this as the steps they give do nothing.

On a side note when the server was windows based I didn't have to type 1 single thing, now that I'm trying to get two ubuntu boxes talking to each other the whole thing has hit a brick wall.

---

### Post by Jose Catre-Vandis on 2007-07-15
Probably need more info from you to pinpoint the issue you are having, e.g. how the server machine is set up, and what client you are using, and whether the network and connections are all OK.

Did you follow the guide posted by Malco2001
[http://ubuntuforums.org/showthread.php?t=249889&highlight=nfs+server](http://ubuntuforums.org/showthread.php?t=249889&highlight=nfs+server)

and have a look at my post if using windows clients

[http://ubuntuforums.org/showthread.php?t=310168](http://ubuntuforums.org/showthread.php?t=310168)

from the forums there do appear to be some issues on Fiesty for some users, but I have none. I followed and used maclo's post and learned from it

---

### Post by Mr. C. on 2007-07-15
Show your actual command and output, not your interpretation; too much information is lost in the translation.

MrC

---

### Post by NeghVar on 2007-07-15
Ok, after going through it again I discovered my mistake and have corrected it. I did use the tutorial you posted but by the end of it I was getting so frustrated by the situation that I failed to realise the problem I created when I first started. I was skipping the "media" part of the command and going right onto the individual disks which since they didn't exist in that manner obviously weren't in the exports which led to my permission failure.

So to wrap it up I screwed up, thank you for helping me figure out what went wrong.

---

### Post by Jose Catre-Vandis on 2007-07-17
If at first you don't succeed :)

Glad you got it sorted :)

---

