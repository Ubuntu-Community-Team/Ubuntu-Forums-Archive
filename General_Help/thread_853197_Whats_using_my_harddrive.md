---
title: "Whats using my harddrive?"
date: 2008-07-08
forum: General Help
---

### Post by gurkburk on 2008-07-08
Im running 8.04 on a laptop (xps m1330). Its got a 7200rpm drive but ive recently started having problems with harddrive activity.
I can hear the drive working constantly at max capacity, and ofcourse the "ide activity" led is going disco as soon as I logon to ubuntu.
My CPU('s.. dualcore) are at around 5-15% perhaps, depending on what I do, still I have bad preformance and response-time even opening the terminal, and these problems started with the drive working so much.

I have a vmware winxp running on the laptop aswell, however ive had that for over a week, and not had this problem, it just started yesterday.

Is there any way to monitor what processes thats sending instructions to the HD? Or, perhaps monitor what files/parts of the discs thats active?

---

### Post by anotherdisciple on 2008-07-08
Check your system monitor or just type "top" in the terminal... I bet it's indexing. I always turn off indexing because I arrange my files in a way that I can remember.

---

### Post by Sef on 2008-07-08
Applications > Accessories > Terminal

then type in ```
top
```

---

### Post by konungursvia on 2008-07-08
It's probably your file system journalling and parking excessively.

---

### Post by anotherdisciple on 2008-07-08
Journaling... hmmm... that's a possibility too. Is there any way to regulate journaling?

---

### Post by HostV on 2008-07-08
I wonder: do you have the same situation once you reinstall your system?

---

