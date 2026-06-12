---
title: "[SOLVED] Odd, But Harmless Error Message at Startup..."
date: 2008-03-14
forum: General Help
---

### Post by Therion on 2008-03-14
I'm getting the following error message at startup.  I click on "OK" to get past it and everything chugs along just fine, but I'd like to make it go away.  

Error message reads as follows:> **User's $HOME/.dmrc file is being ignored.  This prevents the default session and language from being saved.  File should be owned by user and have 644 permissions.  User's $HOME directory must be owned by user and not be writeable by others.**

What to do?

Thanks in advance...

---

### Post by Rocket2DMn on 2008-03-14
Run:
```
sudo chown *yourusername:yourusername* ~/.dmrc
chmod 644 ~/.dmrc
```

---

### Post by x1a4 on 2008-03-14
```

chown yourUserName:yourDefaultGroupName ~/.dmrc
chmod 644 ~/.dmrc

```

EDIT: Don't you just hate it...you think you're the first to answer a post and when you click 'Submit' somebody beat you to the punch?

---

### Post by Therion on 2008-03-14
I should lashed with a wet noodle, really...  From now on I will google before posting.  

Thanks!!

---

