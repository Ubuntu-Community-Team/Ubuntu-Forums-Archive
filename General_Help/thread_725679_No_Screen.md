---
title: "No Screen"
date: 2008-03-15
forum: General Help
---

### Post by madara_sama on 2008-03-15
After ubuntu 7.10 installed, I got no loading screen on startup and shutdown. Just after passed the GRuB, my monitor shown text : 
```
starting up...
Loading, please wait...
```
Then I got blank screen with bouncing box which text **"Out of Range"**. This happened on startup, shutdown, or restart. This wasn't happened when I installed Ubuntu 7.04. 
I tried to configure my screen resolution from menu "screen & graphic", and "screen resolution". But I still got the same result. What file, where, and which part do I need to configure? Any clue?

---

### Post by Rocket2DMn on 2008-03-15
The file is xorg.conf, and you can configure it like this: [http://ubuntuforums.org/showthread.php?t=690760](http://ubuntuforums.org/showthread.php?t=690760)
If you need more help after trying that, post:
```
lspci | grep VGA
cat /etc/X11/xorg.conf
```

---

### Post by madara_sama on 2008-03-15
Ok, let me try it first. It's easy to configure by using startup manager, or anything like that. But I want to know manually. Thanks. I will check then.

---

