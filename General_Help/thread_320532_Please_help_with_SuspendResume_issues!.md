---
title: "Please help with Suspend/Resume issues!"
date: 2006-12-17
forum: General Help
---

### Post by twitchku on 2006-12-17
I'm having a few problems with suspend/resume.
I can't seem to be able to get anything from gnome-screensaver-command inside a suspend/resume script. I have a script that will essentiall do:

ssdump
```
echo "screensaver: `gnome-screensaver-command -q`" >> ~/screen
```

which, after resuming from suspend, will yield in ~/screensaver: "screensaver: " even if the command is run as userx (owner of home and current screensaver user) user with:

```
sudo -H -u userx ssdump
```

If i manually run either ssdump or that sudo command from a terminal, it will say: "screensaver: The screensaver is inactive"

Anyone know what i could be doing wrong?

---

