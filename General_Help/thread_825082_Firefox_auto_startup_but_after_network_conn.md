---
title: "Firefox auto startup but after network conn"
date: 2008-06-10
forum: General Help
---

### Post by shreko on 2008-06-10
I have a following problem. Firefox auto starts on startup, but it starts up before wifi connects and gives up showing "unable to connect". After 15-20 sec when wifi connects, if I refresh ff everything is OK, but I need this to be without user intervention, because FF page is a web page with an input box and user scans a barcode on a reader attached, no keyboard, no mouse.
I have  the same setting that works perfectly with wired conn. but not with wifi. Is there anything that can be done?

Thanks

Shreko

---

### Post by Happy_Man on 2008-06-10
Assuming you're using the Sessions manager in GNOME, you can add a delay to the command so that firefox starts up x number of seconds after login. A sample command looks like:

```
sleep 20 && firefox &
```

Where "20" is the number of seconds to wait. You can change that to whatever you want. Hope this helps!

---

