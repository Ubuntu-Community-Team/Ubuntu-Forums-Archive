---
title: "[SOLVED] Update manager says 17 updates available but.."
date: 2008-03-27
forum: General Help
---

### Post by Sweet Spot on 2008-03-27
For the past month or so, the update manager has been showing the same available updates (Fiesty) but when I click to install the updates, it simply checks for updates again, and that's it. On occasion there will be additional updates added to the current 17 which don't do diddley, and they will install just fine, so I'm really baffled about this behavior. 

I'm assuming that I'll only see updates which apply to Fiesty because that's what I'm using, and not updates for Gutsy, right ? I'd really like to know what's up and why this is happening, and please not just a quick terminal fix like sudo apt update & upgrade /whatever, because that won't enable me to learn from what's happening. Thanks. 

doug

---

### Post by forrestcupp on 2008-03-27
Can you post a screen shot of your update manager so we can see exactly what it says?

---

### Post by Sweet Spot on 2008-03-27
Sure, no problem. It doesn't say anything though. When I click to update, it just re checks for updates, and that's it. And I'm left with what was there before.

---

### Post by forrestcupp on 2008-03-27
That's weird.  Try manually installing them from a terminal to see what happens.
```
sudo apt-get update
sudo apt-get install audacity bzip2 evolution evolution-common
```
and add whatever else not shown that is in the list and won't go away.

---

### Post by danbuter on 2008-03-27
Even easier:
sudo aptitude update
sudo aptitude upgrade

---

### Post by dcstar on 2008-03-27
> **Sweet Spot said:**
> Sure, no problem. It doesn't say anything though. When I click to update, it just re checks for updates, and that's it. And I'm left with what was there before.

Check Synaptic-Settings-Preferences-Distribution and make sure that you have the top option selected.

---

### Post by Sweet Spot on 2008-03-28
> **dcstar said:**
> Check Synaptic-Settings-Preferences-Distribution and make sure that you have the top option selected.



Diddy ! That seems to have done the trick, sir ! Though I'm still left with wondering why ?  I had that particular one set for "Feisty", so in essense shouldn't that mean it would only check for packages available FOR Feisty ? 

Setting it for "newest" or "latest", what packages are those really intended for, and if Gutsy etc.. I hope that won't create any other problems ?

Anyway, thanks a bunch ! 

Doug

---

### Post by dcstar on 2008-03-28
> **Sweet Spot said:**
> Diddy ! That seems to have done the trick, sir ! Though I'm still left with wondering why ?  I had that particular one set for "Feisty", so in essense shouldn't that mean it would only check for packages available FOR Feisty ? 

Setting it for "newest" or "latest", what packages are those really intended for, and if Gutsy etc.. I hope that won't create any other problems ?

Anyway, thanks a bunch ! 

Doug

It comes down to selecting an individual repository rather than the latest version from any of your repositories.

(And read my footer for marking this thread as solved).

---

### Post by Sweet Spot on 2008-03-29
Cool, cool. Done.

---

