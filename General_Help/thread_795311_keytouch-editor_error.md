---
title: "keytouch-editor error"
date: 2008-05-15
forum: General Help
---

### Post by glacialfury on 2008-05-15
I've installed keytouch and keytouch-editor.  keytouch itself runs fine, except that my keyboard does not appear in the list; per the directions on the community help page, the next appropriate step is to run keytouch-editor, which will allow you to configure the keys manually.

When I run keytouch-editor, it pops up a dialog with the following:

```
No event devices are available in /dev/input/.
```

Click the OK button, dialog closes, program ends.  Anyone have any ideas?

---

### Post by gforster on 2008-05-16
I get the same error. Also, when launched from the menu under System > Preferences, it says: 

Failed to execute child process "/usr/bin/su-to-root" (No such file or directory)

I don't understand enough to be able to deal with either of these problems.

---

### Post by gforster on 2008-05-17
Anyone?  or are we the only two with this problem?

---

### Post by nebajoth on 2008-06-19
You don't have sufficient rights to run keytouch-editor as a normal user.  You need to run the program as root, which has access to things in the /dev hierarchy.

Try this:
```
sudo keytouch-editor
```

---

### Post by kpothi on 2008-12-13
> **nebajoth said:**
> You don't have sufficient rights to run keytouch-editor as a normal user.  You need to run the program as root, which has access to things in the /dev hierarchy.

Try this:
```
sudo keytouch-editor
```

You are right. As a root, I could start it. Thank you! :guitar:

---

