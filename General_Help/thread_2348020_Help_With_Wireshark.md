---
title: "Help With Wireshark"
date: 2016-12-30
forum: General Help
---

### Post by shane_faulkinbury2 on 2016-12-30
Can somebody please give me some help with setting up a capture in Wireshark?  Everything unfortunately works on Windows, but I'm unable to get a captures on Ubuntu.  
How to Capture gives me little information, but Network Media seems to be going in the right direction network media specific capture, WLAN.

---

### Post by #&amp;thj^% on 2016-12-30
See if this is useful: [https://www.maketecheasier.com/using-wireshark-ubuntu/](https://www.maketecheasier.com/using-wireshark-ubuntu/)

---

### Post by shane_faulkinbury2 on 2016-12-30
```
[FONT=monospace][COLOR=#c20cb9]**sudo**[/COLOR] [COLOR=#c20cb9]**chmod**[/COLOR] [COLOR=#000000]4711[/COLOR] [COLOR=#000000]**`**[/COLOR][COLOR=#c20cb9]**which**[/COLOR] dumpcap[COLOR=#000000]**`**[/COLOR][/FONT]


```

Sorry, but when I do the above I get the screen shot.

---

### Post by cariboo on 2016-12-30
Try:

```
chmod 4711 /usr/bin/dumpcap
```

---

### Post by shane_faulkinbury2 on 2016-12-30
Thanks a lot guys!  The above command did the trick!

---

