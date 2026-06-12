---
title: "Error message when loading firefox"
date: 2008-02-18
forum: General Help
---

### Post by Robbyx on 2008-02-18
The alert is 

TypeError: Components.classes [CID] has no properties.

After this the program opens normally. 

What do I need to change to make the alert go away?

---

### Post by tangibleorange on 2008-02-18
I think this probably has something to do with a faulty Firefox extension.

Tools --> Add-ons or Tools--> Extensions and just keep disabling them until you find the one causing the problem.

Failing that, I think a reinstallation is your best bet :).

---

### Post by strabes on 2008-02-18
Run: ```
firefox -ProfileManager
```Make a new profile, set it as the default, and restart firefox. If the warning disappears then you're good to go.

---

### Post by Robbyx on 2008-02-18
> **tangibleorange said:**
> I think this probably has something to do with a faulty Firefox extension.

Tools --> Add-ons or Tools--> Extensions and just keep disabling them until you find the one causing the problem.

Failing that, I think a reinstallation is your best bet :).

I am going to try running firefox in safemode. Do you know where the program file is located?

I removed and then installed FF. That made no difference. The alert still pops up.

---

### Post by Robbyx on 2008-02-18
> **strabes said:**
> Run: ```
firefox -ProfileManager
```Make a new profile, set it as the default, and restart firefox. If the warning disappears then you're good to go.


I ran the command line and before FF opened the same alert popped up.

Any other ideas that could solve this?

---

### Post by tangibleorange on 2008-02-19
Did you try starting in safemode? Did the alert still pop up?

---

### Post by Robbyx on 2008-02-19
> **tangibleorange said:**
> Did you try starting in safemode? Did the alert still pop up?

No. At present the error message is not jumping up.  I think it is to do with the interaction of Swiftfox. I used it all the time in fiesty, but I am struggling with it in gutsy.  Loads of addons are disabled by Swiftfox. If I stay with FF I can get it to be stable and not have the popup alert. In a way this is a shame because I preferred the speed from Swiftfox.

---

