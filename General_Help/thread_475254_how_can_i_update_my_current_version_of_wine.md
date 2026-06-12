---
title: "how can i update my current version of wine"
date: 2007-06-15
forum: General Help
---

### Post by kdarkentity on 2007-06-15
i want to just update my version of wine rather than reinstalling it completely

---

### Post by Brucevdk on 2007-06-17
I'm not entirely sure what you mean but you can add the official Wine repository as described at [the WineHQ website]("http://www.winehq.org/site/download-deb"). For your convenience here is the entire procedure (execute these lines from the terminal):
```

wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -
sudo wget http://wine.budgetdedicated.com/apt/sources.list.d/feisty.list -O /etc/apt/sources.list.d/winehq.list
sudo apt-get update

```

If you're using an older version of Wine the update manager icon should pop up in the notification area and you should be able to update Wine to the latest available version.

---

### Post by kdarkentity on 2007-06-17
alright thanks but ive already figured it out

---

