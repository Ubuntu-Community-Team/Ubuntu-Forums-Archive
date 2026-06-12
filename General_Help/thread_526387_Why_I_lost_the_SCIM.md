---
title: "Why I lost the SCIM?"
date: 2007-08-14
forum: General Help
---

### Post by ela04cz on 2007-08-14
Hi guys, just encountered a small problem, lost my scim input method. My system is xubuntu 7.04, the scim was pre-installed and worked finely. This morning when I turned on the machine, I couldn´t find it in the system try any more. I opened the SCIM input setup panel, and checked the ¨trigger¨ hotkey, it is ctrl+space like it use to be. But now I hit the ctrl+space, nothing comes up. I removed the package and reinstalled it, doesn´t work, then I remove the config file of scim and the package, then install, still doesn´t work. Any ideas?

---

### Post by Blutack on 2007-08-14
You might want to shift this to a different thread, SCIM ain't really beginners forum stuff and you'd probably have more luck elsewhere.  Of course, I'm going to be instantly proved wrong when you get six posts with the answer, in which case I take credit.

---

### Post by ela04cz on 2007-08-16
no one has ever encountered this?

---

### Post by henzo on 2007-08-16
I have the same problem and posted it on another forum but don't get an answer too. So I will follow this item. It has always been a good program under Ubuntu.

---

### Post by frodon on 2007-08-16
Duplicate threads merged.

---

### Post by clubsoda on 2007-08-16
On the SCIM toolbar, did you try clicking on "English/Keyboard" and selecting the input method?

I had a similar problem, re-installed various things, but in the end I think I just needed to press control-j to fix it!

Possibly the language-pack upgrades broke SCIM's settings.

---

### Post by matrix11 on 2007-08-17
I got it working using the information in this link: [https://help.ubuntu.com/community/Japanese_Input_and_Fonts_in_Ubuntu_7.04](https://help.ubuntu.com/community/Japanese_Input_and_Fonts_in_Ubuntu_7.04)

I just created the file /etc/X11/Xsession.d/74custom-scim_startup with the following lines:
```
export XMODIFIERS="@im=SCIM"
export GTK_IM_MODULE="scim"
export XIM_PROGRAM="scim -d"
export QT_IM_MODULE="scim"
```

Then just logged back in, and SCIM is working (responds to the scim input keys like it used to) :biggrin:

---

### Post by ela04cz on 2007-08-18
Problem solved! :guitar:  Thank you so much Matrix11 !!

---

### Post by henzo on 2007-08-19
promlem has been solved in this way. many thanks

---

