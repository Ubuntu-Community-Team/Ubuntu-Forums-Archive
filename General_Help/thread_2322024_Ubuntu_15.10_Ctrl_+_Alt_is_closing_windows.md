---
title: "Ubuntu 15.10 Ctrl + Alt is closing windows"
date: 2016-04-25
forum: General Help
---

### Post by kane5 on 2016-04-25
Hello everyone, so I have been having this issue where Ctrl + Alt is closing any windows/programs that I am currently in. I have not modified any shortcuts or anything related to them that I can think of. I first noticed this when I tried to open a terminal using ctrl + alt + T. This will open a terminal but will also close any open program. I appreciate any suggestions! Thanks

---

### Post by kane5 on 2016-05-03
Anyone have any ideas?

---

### Post by kane5 on 2016-05-10
Cant seem to find anyone with my issue

---

### Post by kane5 on 2016-05-26
Can anyone help me out? I have tried changing/adding shortcuts but nothing is fixing the issue.

---

### Post by QDR06VV9 on 2016-05-26
Not sure if you have looked at your short-cuts to see if Alt+F4 still shows Closes window. Maybe it got changed some how??
Just trying to get the ball rolling for you.

---

### Post by kane5 on 2016-06-13
I have tried everything I could think of with shortcuts. No shortcuts were changed, and no custom shortcuts were created either. I never modified anything involving shortcuts since I installed ubuntu. Anyone else have any ideas on what the problem could be?

---

### Post by kane5 on 2016-07-20
Anyone have any other suggestions?

---

### Post by QDR06VV9 on 2016-07-20
This behaviour also can happen with unity --replace.

One possible solution is to check in whether commands are enabled in CompizConfig Settings Manager you may need to install it with 
```
sudo apt-get install compizconfig-settings-manager.

```
Look for an option called 'Commands', in the 'General' category. In my case this was un-checked. I suspect these settings may have been used when restarting Unity/Compiz.

---

