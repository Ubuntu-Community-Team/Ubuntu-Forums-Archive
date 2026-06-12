---
title: "My On Screen Keyboard crashed"
date: 2014-01-05
forum: General Help
---

### Post by rickhunt on 2014-01-05
Unbuntu 12.04 LTS Onscreen Keyboard crashed

Ok, I was playing with the onsceen keyboard preferences, I clicked turn on keyboard scanning (Not even sure what that is) and then the onsceen disappeared. 

Now I can't get it back. 

When I go in to Universal access, and toggle the Onscreen to off and then back on, it appears for a second and then disappears.

I think I just need to turn of the Keyboard scanning that I turned on, but I can't get it to stay open long enough to do that.

Is there a way to do it from the command line, or reset it back to default settings.

I mean I don't really need the Onscreen Keyboard, but I don't like that I messed it up either. :-)

So if anyone knows how to fix this, please let me know.

---

### Post by ajgreeny on 2014-01-05
Is the package that provides this the **matchbox-keyboard**?

If so have a search for a config file, probably hidden, for that and delete it.  It will then make a new version of that file next time you open it.

---

### Post by rickhunt on 2014-01-07
I don't know what package provides it, its under Universal Access...What would the config file be called?

---

