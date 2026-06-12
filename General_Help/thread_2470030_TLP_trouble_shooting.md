---
title: "TLP trouble shooting"
date: 2021-12-17
forum: General Help
---

### Post by Langstracht on 2021-12-17
Purportedly TLP will allow for starting and ending battery charging for Lenovo Think Pads at user selected levels.  For example start at 40% and cut out at 80%.

But none of my efforts to get this to happen have worked.

Does anyone happen to know how to reveal what the problem(s) is/are?

TIA for assistance.

---

### Post by ajgreeny on 2021-12-17
Have you read the TLP manual from ***man tlp*** in terminal, which seems to answer your question.

I do not have a Thinkpad so can not check this but much of the man output seems to be specifically for Thinkpads only, so it may be some help.
```
setcharge [START_CHARGE STOP_CHARGE] [BAT0|BAT1] (ThinkPads only)
              Set charge thresholds of main (BAT0) or auxiliary (BAT1) battery temporarily.  Values must be between 1 and 100,
              START_CHARGE must not exceed STOP_CHARGE - 4.  Configured thresholds are restored upon next system boot-up. When
              called without arguments, configured thresholds are set.

fullcharge [BAT0|BAT1] (ThinkPads only)
              Set  charge thresholds of main (BAT0) or auxiliary (BAT1) battery to factory presets (96/100) temporarily (caus&#8208;
              ing a full charge).  Configured thresholds are restored upon next system boot-up.

```

---

### Post by grahammechanical on 2021-12-17
There is a TLP web site with documentation and some of it is specific for Ubuntu. You do not tell us what version of Ubuntu you are using but if it is a version with Gnome 40 then there is a conflict between Gnome 40 power profiles and TLP power profiles.

[https://linrunner.de/tlp/installation/ubuntu.html](https://linrunner.de/tlp/installation/ubuntu.html)

Regards

---

### Post by Langstracht on 2021-12-17
Thanks for taking the time to respond.

Yes I consulted the man page.  Perhaps I am missing something but the two scenarios - I don't think ... - pertain to my problem situation.  I don't want a full charge nor to set temporary charging levels.

I DO want to "permanently" change the charging levels to start at 40% and end at 80%.

---

### Post by Langstracht on 2021-12-17
Sorry to say I haven't been able to figure out the Gnome version.  But ubuntu is 18.04.

---

