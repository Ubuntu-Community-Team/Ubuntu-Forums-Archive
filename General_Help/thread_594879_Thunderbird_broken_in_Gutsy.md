---
title: "Thunderbird broken in Gutsy"
date: 2007-10-28
forum: General Help
---

### Post by goneskiing on 2007-10-28
When I click on any msg in the Inbox, Thunderbird crashes - no error msg - program just exits.  This is a very serious bug - essentially cannot read any email !

I turned compiz off - still crashes.  Any updates ?  Any workarounds ?

---

### Post by por100pre1 on 2007-10-28
Try creating a new profile:

```
thunderbird -P
```

and move as much settings you can. The profiles should be in ~/.mozilla-thunderbird or in ~/.thunderbird in your user folder.

---

### Post by goneskiing on 2007-10-28
okay Fixed

compreg.dat is the offending file - just delete it (it is under .mozilla-thunderbird then under the funny named folder) - thunderbird will regenerate a new one and keep all the old settings

---

### Post by phansiizwe on 2007-10-31
Thanks goneskiing, that did the trick!!!

How did you figure that out?

---

### Post by phansiizwe on 2007-11-01
OK, too soon, the problem is back... I think I'll try a new profile...

---

### Post by phansiizwe on 2007-11-02
I uninstalled all add-ons (Tools-> Add-Ons) in thunderbird and this seems to have solved the problem.

---

### Post by goneskiing on 2007-12-11
yeah, in my case it was an older version of "Lightening" that caused the problem - uninstalled that and the problem went away.  Been fine ever since.

---

