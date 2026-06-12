---
title: "Ctrl+alt+T sometimes have to do it four times"
date: 2013-12-23
forum: General Help
---

### Post by rocky-oceans on 2013-12-23
To open a terminal I use the shortcut ctrl+alt+t. However, sometimes I have to press that combination several times for it to work. Is there a solution to this? Before, on the same hardware, I've not had a problem with this. Note that I'm using Ubuntu 13.10.

---

### Post by raja.genupula on 2013-12-23
seems to be some what complicated issue. use keylogger to check whether your keys are recording or not by using some keylogger software. search software center for that.

---

### Post by stinkeye on 2013-12-23
keymon will help you determine if the key presses are being registered.
```
sudo apt-get install keymon
```

---

### Post by rocky-oceans on 2013-12-23
> **stinkeye said:**
> keymon will help you determine if the key presses are being registered.
```
sudo apt-get install keymon
```

I installed it an the keys are indeed being registered. Any other ideas for debugging?

Has anyone else seen this behavior?

---

### Post by stinkeye on 2013-12-23
May be a focus issue.
Used to see this when I had conky on the desktop.
I would have to click on the desktop first or have at least one window open for shortcut keys to work.
When shortcuts wouldn't work the global menu would still be showing the last closed app instead of returning to "Ubuntu Desktop".

---

### Post by rocky-oceans on 2013-12-24
thanks for the replies. I guess I'll have to live with it.

---

### Post by stinkeye on 2013-12-24
> **rocky-oceans said:**
> thanks for the replies. I guess I'll have to live with it.

Do you have anything running on the desktop?
What worked for me was to give the conky window no focus in ccsm.

---

