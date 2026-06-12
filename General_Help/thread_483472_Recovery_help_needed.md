---
title: "Recovery help needed"
date: 2007-06-24
forum: General Help
---

### Post by Rodents on 2007-06-24
I installed ubuntu the other day, everythings running smoothly, no problems at all, I turned it off for the night.

booted it up this morning, it was a bit slower, but I logged in like normal and when nautilus tried to load it told me nautilus failed to load, and then it asked me if i wanted to re-start the application, so I tried and it didn't work.. nautilus is dead, but everything else works. I can do somethings but other things nautilus dependant.. don't work

I want to know what might be wrong
and I want to know how I could just re-install nautilus (if possible)
and am curious if it'd be just easier to re-install the entire OS.. again

6.06 lts
hp pavillion n3270 notebook

help is greatly appreciated, I can't find anything anywhere

---

### Post by jpeddicord on 2007-06-25
Hi,

These steps should help you restore Nautilus:
Before you sign in, click on Options, and then Select Session.
Click the Failsafe Terminal option, then sign in. When it asks to make it the default session, just say This Session Only.

Once you are in, type this:
```
mv .nautilus .nautilus.bak
```
Then, type "exit" to return to the login screen. If all went well, you should be able to use Nautilus again.

Jacob

---

