---
title: "Strange Firefox bookmarks"
date: 2007-05-29
forum: General Help
---

### Post by Philipek on 2007-05-29
Hello! I changed over from openSUSE and installed Feisty. Great installation, beats the crap out staring of at an inoperative screen for three hours! Anyway, here's my problem: Previously I had my /home mounted on a separate partition and kept the mount point during the Ubuntu installation. Anyway, after installation everything seems to be hunky-dory and where it should be (so far) except for one thing. I can't make new bookmarks in Firefox if I try to create them in the bookmarks folder. I click ADD but nothing happens. However, if I put them in a sub folder I have no problems... Well, I've searched through many forums and it beats me. Probably something ridiculously simple, but I damned if figure it out. Any suggestions?

---

### Post by vtel57 on 2007-05-29
You say that /home partition was from your SuSE installation? If so, you'll probably have to check ownership/permissions of all the data on that partition. You can change ownership at the command line by typing this:

```
 $ sudo chown -R <your user name here> /home/<your user name here>
```

Wherever I use < and >, don't type them. They're just there to signify that you need to "fill in the blank" with whatever is requested. In the case above, your user account name.

This will change ownership to your user account, as it should be. Even though you may have used the same user name in the /home when it was SuSE, you'll still have to chown it in Ubuntu.

Luck!

---

