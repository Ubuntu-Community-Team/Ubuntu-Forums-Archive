---
title: "How do I add the right click permanently delete option?"
date: 2008-05-04
forum: General Help
---

### Post by 2hot6ft2 on 2008-05-04
Hi. I found this once before and since upgrading to ubuntu 8.04 Hardy with a fresh install, I can't seem to find it again. I want the mouse right click option to permanently delete files bypassing the trash bin.

I am well aware off the hazard of having this option and using it carelessly. I know when I want something gone for good without the double step of moving it to the trash first.

Can anyone either help me find where it was I found it in the first place or tell me how to do it again?


Promise this time I will write it down or print it out.

Thanks in advance.

---

### Post by fjgaude on 2008-05-04
Click on Places/Home Folder... you are now in Nautilus file manager. Click on Edit/Preferences and then on Behavior... there you have options at the bottom of the list.

---

### Post by mc4man on 2008-05-04
In hardy right click delete, whether you can remove confirmation box I'm not sure

---

### Post by mike2357 on 2008-05-04
I think this is what you want:

1.  Open any Nautilus window.  Your home directory will work fine.
2.  Select Edit, then Preferences.
3.  Select the Behavior tab.
4.  You'll see a section titled Trash.

---

### Post by Oldsoldier2003 on 2008-05-04
> **2hot6ft2 said:**
> Hi. I found this once before and since upgrading to ubuntu 8.04 Hardy with a fresh install, I can't seem to find it again. I want the mouse right click option to permanently delete files bypassing the trash bin.

I am well aware off the hazard of having this option and using it carelessly. I know when I want something gone for good without the double step of moving it to the trash first.

Can anyone either help me find where it was I found it in the first place or tell me how to do it again?


Promise this time I will write it down or print it out.

Thanks in advance.

in a terminal:

 ```
gconf-editor
```

then:
Apps>Nautilus>Preferences check the box enable_delete or just do as the above post recommends :)

---

### Post by 2hot6ft2 on 2008-05-06
Cool. Got it. Thanks for the help. I'm not real concerned with the confirmation dialog pop up, now I don't have to keep going to the trash bin and emptying it  every time I delete something that I want gone.
:guitar:

---

