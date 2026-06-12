---
title: "[SOLVED] nautilus title bar"
date: 2008-01-07
forum: General Help
---

### Post by ideologo on 2008-01-07
For some reason unknown when I open Nautilus the window has no frame no top bar. I can't move away unless I do Alt+tab (if I have other applications open) or closing from the menu  File (Exit). any ideas? Thanks. Needless to say I am a beginner.

---

### Post by drs305 on 2008-01-07
Does this happen every time you open Nautilus? If so, how are you opening it? Do you use any window or desktop managers such as devilspie which may have invoked an 'undecorate' command? 

If it's a single or sporadic occurance, have you tried running
```
killall nautilus
``` 
and then restarting it?

---

### Post by ideologo on 2008-01-08
Yes, it does. I open nautilus just clilcking in any of the bookmarks. No, I do not.
Thanks.

---

### Post by drs305 on 2008-01-08
Have you tried opening synaptic, finding your nautilus-related installations, right-clicking and then marking them all for reinstallation?

---

### Post by ideologo on 2008-01-08
That is a very good idea. However somebodyelse suggested that the xorg files could be corrupted because turning on the computer today there was no way to set the appropriate definition for the monitor who went nuts.

I did the following command:

sudo dpkg-reconfigure xserver-xorg

Thank you for your help!
:guitar:

---

