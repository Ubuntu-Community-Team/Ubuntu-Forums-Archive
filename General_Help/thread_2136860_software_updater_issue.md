---
title: "software updater issue"
date: 2013-04-18
forum: General Help
---

### Post by bearbear008 on 2013-04-18
I installed ubuntu 12.10. Usually notification automatically comes to install software updates. This time it didn't . So I clicked software update from dash menu. But when updater checks for updates , it gets always stuck when downloading . Its getting stopped when checking itself , saying , failed to load repositories . What to do? Pls help

---

### Post by uzumakifahim on 2013-04-18
Let's try changing the repository to another one. Maybe there is some problem, when you're trying to connect to the selected repository. To change repository just open **Ubuntu Software Center** and **Edit > Software sources** and select a suitable server (in most cases which is nearer to you).

Hope, this'll help and post the update here.

---

### Post by papibe on 2013-04-18
Hi bearbear008.

Could you open a terminal, run this command and post its results?
```
sudo apt-get update
```
It'll ask you your password to confirm.

Regards.

---

