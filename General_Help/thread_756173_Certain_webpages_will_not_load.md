---
title: "Certain webpages will not load"
date: 2008-04-15
forum: General Help
---

### Post by psychofish25 on 2008-04-15
For most websites, such as youtube and wikipedia, everything runs normal. However, for other sites such as Google, Yahoo, and Facebook, they will not load and I get an error. I have tried all search engines and none of them seem to work, yet most other websites do. Is this a known problem? How can I fix it?

---

### Post by Sam Lars on 2008-04-15
What web browser and what version are you using, and what error do you get?

---

### Post by psychofish25 on 2008-04-15
It occurs on all browsers but only on this particular computer. The only error I get is that it's unable to connect, as if I don't have internet hooked up.

---

### Post by Sam Lars on 2008-04-15
Does this appear immediately or after a timeout?
Is there anything different or special about its connection?

---

### Post by psychofish25 on 2008-04-15
It appears as if it's trying to connect and just can't. It's a normal connection, I just can't point out anything different.

---

### Post by Sam Lars on 2008-04-15
Can you ping any of the sites from a terminal?
```
ping site.com
```

---

### Post by psychofish25 on 2008-04-16
Well i was saying its my pc for reference, its actually my friends running XP and its as if the internet wont go to those sites, the ping returns nothing.

---

### Post by prshah on 2008-04-16
> **psychofish25 said:**
> Well i was saying its my pc for reference, its actually my friends running XP and its as if the internet wont go to those sites, the ping returns nothing.
 
If this is a Windows machine, maybe this is the wrong forum for this post; that being said:

Click Start->Run, then type in "eventvwr.msc", press enter. In the log viewer that opens up, go the the "System" section, and look for any events with ID 4226.

Please post back results here.

---

