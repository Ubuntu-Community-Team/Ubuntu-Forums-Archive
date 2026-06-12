---
title: "Upgraded to 12.04 then problem with firefox"
date: 2013-05-10
forum: General Help
---

### Post by rapattack1 on 2013-05-10
Hi I am on a friends computer and she accidentally upgraded to 12.04. For got what she had before. Anyway when she clicks on firefox there is an applet that says 'Could not initialize the application's security component. The most likely cause is problems with files in your application's profile directory. Please check that this directory has no read/write restrictions and your hard disk is not full or close to full. It is recommended that you exit the application and fix the problem. If you continue to use this session, you might see incorrect application behaviour when accessing security features.'
and we are not able to get on the net. 
I installed chrome and we go on the net fine plus imported the bookmarks and history. I am not that proficient to understand much about profiles but am aware of them.

---

### Post by PowerBarry43 on 2013-05-10
Hi

Try running:

```
sudo chown -R $USER:$USER ~/.mozilla
```

Hope this helps!

Barry

---

### Post by rapattack1 on 2013-05-15
Oops so sorry been so busy...will try this when i get time to go to her place again and when i remember. Thanks

---

