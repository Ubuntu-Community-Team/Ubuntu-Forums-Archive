---
title: "Urgent!! How do I change the session from terminal?"
date: 2006-11-27
forum: General Help
---

### Post by Nonno Bassotto on 2006-11-27
I've decided to try Beryl, so I installed it, everything went fine and I added beryl-manager to the programs at startup in the session preferences. Then I played a bit now Beryl doesn't draw any window anymore, nor the panel, nor the right-click menu, nothing. ](*,) ](*,) 

So I logged in as another user, since I can't use my main account anymore. I want to remove beryl-manager from the session. How do I do it? Can I edit some text file? Can I edit gconf from the terminal?

EDIT: I removed the file $HOME/.gnome2/session, but this didn't change too much. Now when I log in I see the wallpaper rahter than a white screen...

---

### Post by ynnhoj on 2006-11-27
unfortunately, i don't have a definite answer for you; however, i would suggest firing up yer terminal and poking around in ~/.gconf/ and ~/.config/.  you never know what you might find in there--keep in mind that you may have to dig down another directory or two before you come across the config file you're trying to find.
[size=0](and of course, you want to be looking around in the home directory of your original user, rather than that of your temporary user... just thought i'd clear that up 'cause i used relative paths above..)[/size]

---

### Post by Nonno Bassotto on 2006-11-27
Wonderful: it seems that what I'm looking for is under .config/autostart. Thank you!!!!!!!!!!!!

---

### Post by shin on 2006-11-27
I'd suggest logging in this session that you say is broken. Then ctr+alt+f1 to get to console and then:
```
killall beryl
killall beryl-manager
killall emerald
```

Make sure that it worked by
```
ps x | grep beryl
```

Now go back to X session (ctrl+alt+f7) and run metacity or whatever wm you are using. Open new console (under X) and type there 
```
metacity &
```

Should work.

---

