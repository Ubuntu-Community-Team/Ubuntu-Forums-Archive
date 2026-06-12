---
title: "Software Updates"
date: 2015-03-05
forum: General Help
---

### Post by jwn-2 on 2015-03-05
Ubuntu 14.04 LTS

I have a Software Update reminder that keeps comming up several times per day, but when I try to install the updates it just says "...fail to download...check your internet connection...". My internet connection is fine (as you can see, I am communicating with you here, and other updates that appears from time to time do install quite fine). How can I get rid of this annoying reminder for updates that does not want to be installed anyway?

---

### Post by Bucky Ball on 2015-03-05
*Thread moved to **General Help**.*

Let's take a closer look. Open a terminal and issue these four commands, one after the other, hitting enter after each:

```
sudo apt-get autoremove
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

Please report any and all errors.

---

### Post by jwn-2 on 2015-03-05
Okay Bucky Ball, I have done that now. There was a lot of output in the terminal, but I did not notice any error messages. Everything seem to have installed okay. I did get a Updater message that I should restart my computer (which I have not done yet). Anything else I should do now, or is the problem now solved?

---

### Post by Bucky Ball on 2015-03-05
Restart your computer and find out if all is well. If not, we'll keep digging.

---

### Post by jwn-2 on 2015-03-05
Okay, I have restarted and I did not get the reminder again (yet), so I suppose it is gone now. I will come back if it does reappear. Thanks Bucky Ball.

---

### Post by Bucky Ball on 2015-03-05
No probs. Give it a little time and if no issues in a few hours, please mark the thread as solved (see the second link in my signature). Good luck. ;)

PS: You can set the updater to only notify once a week (or never) by going to Software Updater (I think that's it in Ubuntu)> Settings in the bottom left corner> Update tab. You'll see the 'Notify me when ...' option down the bottom.

---

### Post by Bucky Ball on 2015-03-05
No probs. Give it a little time and if no issues in a few hours, please mark the thread as solved (see the second link in my signature). Good luck. ;)

PS: You can set the updater to only notify once a week (or never) by going to Software Updater (I think that's it in Ubuntu)> Settings in the bottom left corner> Update tab. You'll see the 'Notify me when ...' option down the bottom.

---

