---
title: "Sharing Files With Other Users On same PC"
date: 2013-01-30
forum: General Help
---

### Post by rbscairns on 2013-01-30
I have a folder "goodstuff" saved in my home>richard>music directory thar I would like other users on my computer to access (read only) so that they can also play the music while logged in.

How can I do this?

**Note:** I am using Ubuntu 12.04 with Gnome Classic

---

### Post by elgordodude on 2013-01-30
With chmod

In a terminal type ```
sudo chmod -R a+r /home/richard/musicdirectory/goodstuff
```

---

