---
title: "Emacs nob question recover-session"
date: 2007-11-18
forum: General Help
---

### Post by underwater on 2007-11-18
Hello,

When I start emacs I get the message 
```

If an Emacs session crashed recently, type Meta-x recover-session RET to recover the files you were editing
```

So I enter the recovery console, and I see two sessions, but I can't seem to really be able to do anything.  The tutorials I've seen online haven't helped, and I really just want that message to go away more than anything.  

Ideas, Suggestions?


Thanks in advance,
Underwater

---

### Post by mali2297 on 2007-11-18
My guess is that you have autosaved files named #filename#. If so, remove them.
An autosave is automatically created as soon as you start changing a file. It is normally deleted when the file is properly saved. If emacs crash though, it can be used to recover the latest changes.

To turn off autosave by default, press **ALT-m** and type
```

customize-variable
auto-save-default

```
Then you should get a customization buffer in which you can toggle the option to autosave. Don't forget to *save for future sessions*.

---

