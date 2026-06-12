---
title: "Disappearing cursor and machine not waking on sleep mode on 16.04"
date: 2016-05-16
forum: General Help
---

### Post by RadioAdi on 2016-05-16
Hi, 

I am experiencing some problems with Lubuntu 16.04. 

a) If I leave my machine for some time so that it goes into sleep mode when I log back in the cursor is not visible. It is still active as I can see object being highlighted as I move over them, I just can't see the cursor. This only happens occasionally, say )20% of the time. 

b) Occasionally when my machine goes into sleep mode it won't wake up again. The screen is blank (black) and tapping on the keyboard or using the track pad or mouse will not wake it up.

The last entry in the history log displays the below which may be relevant with regards to b. 

```
May 15 10:38:47 my_machine systemd-sleep[8281]: Suspending system...
```

I have no idea if these two issues are related, but they are equally frustrating. Anybody know of a fix?

---

### Post by Impavidus on 2016-05-16
a) could be a known bug. Use ctrl+alt+F1 to go to the console and ctrl+alt+F7 to go back and the cursor should reappear. Instead of F1, F2-F6 work too. But as it only happens occasionally, it might be something else. I don't know about b). However, when my laptop is suspended, I have to wake it using the power button.

---

### Post by PaulW2U on 2016-05-16
> **RadioAdi said:**
> a) If I leave my machine for some time so that it goes into sleep mode when I log back in the cursor is not visible. It is still active as I can see object being highlighted as I move over them, I just can't see the cursor. This only happens occasionally, say )20% of the time. 
May be this bug? - [Mouse cursor lost when unlocking with Intel graphics]("https://bugs.launchpad.net/ubuntu/+bug/1568604").

Although yours is the first report that I've seen that says the mouse pointer doesn't disappear **every** time. Do you have Intel graphics?

---

### Post by RadioAdi on 2016-05-17
Thanks guys. 

Yes that bug report does explain the cursor issue (yes I am on Intel), except the issue is intermittent in my case.

---

