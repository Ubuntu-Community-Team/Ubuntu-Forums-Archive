---
title: "Right arrow key is broken"
date: 2006-09-06
forum: General Help
---

### Post by Grog140 on 2006-09-06
Ok, this is pretty wierd. I can't use my right arrow key while ogged in.

At the login screen it works fine but once I glog in the key does absolutley nothing.

I was playing around with keyboard shortcuts today but I know 100% for sure that I did not assign anything to my right arrow key.

Could anyone help? Thanks.

---

### Post by Grog140 on 2006-09-11
I finally found the answer but I need to use this command every time I log in in order to get a functional right arrow key:

```
xmodmap -e "keycode 102 = Right" 
```

How can I make this a permanent effect?

---

### Post by Grog140 on 2006-09-28
This is really starting to bug me, so I have to bump it... :(

---

