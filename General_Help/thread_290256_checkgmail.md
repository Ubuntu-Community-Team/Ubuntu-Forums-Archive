---
title: "checkgmail"
date: 2006-11-01
forum: General Help
---

### Post by devils3cups on 2006-11-01
I have Ubuntu set up so that it runs checkgmail on startup and it starts up perfectly fine. The problem is, is that it loads before i auto connect to my network so checkgmail always shows that its not connected to gmail. Once im connected if I close checkgmail and open a new one, or just open a new one it works perfectly. Is there a way so that i can have checkgmail only start once  im connected to my network? Is there anyway to write a script like that because it could also fix other problems in the future?

---

### Post by 23meg on 2006-11-01
You can try delaying it a bit, say, four seconds. Try a greater value if that fails.

Put the following in a script,```
sleep 4
checkgmail
```make it executable and have it run at startup.

---

### Post by devils3cups on 2006-11-01
I was thinking that but i couldnt find the name of the feature sleep. Im sure that will work but is there anyway to check if i am specifically connected to my network?

---

### Post by 23meg on 2006-11-01
You could ping your gateway or another reliable host (here it's Google)
```

ping -c 1 www.google.com
if [ $? = 0 ]
then
checkgmail
fi

```There definitely is a more elegant way but this should do.

---

### Post by devils3cups on 2006-11-01
nice nice im liking the more specificity :D

---

### Post by fragos on 2006-11-02
Try installing Gnome mail notification.  It handles gmail and integrates nicely.

---

