---
title: "[SOLVED] Messed lock screen up"
date: 2007-08-10
forum: General Help
---

### Post by nvteighen on 2007-08-10
OK, this is something weird and I'll try to explain it the best I can:

1. I wanted to try assigning a "face" to my account and see how they look in the lock screen (not login screen)
2. So, I went to System --> Preferences --> About me, and changed the image.
3. I did Ctrl+Alt+L to lock the screen and there it was the image I put.
4. I didn't like it, so I went back to "About me", and chose "No image".
5. Again, I locked the screen with Ctrl+Alt+L to see everything was fine, but...
6. Now there sits the default image you see when not having a "face" assigned to your account.

I have included a screenshot of my lockscreen; what I want to do is to get rid of that image at the top. I've searched gconf, in my home folder, etc. without any result... Can someone help me please?

This issue is almost irrelevant, just only a bit annoying... So, if you have to help someone with a more serious problem, help that other person first... This can wait a bit.

Thank you!

---

### Post by sisco311 on 2007-08-10
```
rm ~/.face
```

---

### Post by nvteighen on 2007-08-10
> **sisco311 said:**
> ```
rm ~/.face
```

It worked. Thank you very much!

---

