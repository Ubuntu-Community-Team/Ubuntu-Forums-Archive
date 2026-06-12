---
title: "Thunderbird crash at startup - Ubuntu 12.04"
date: 2015-09-07
forum: General Help
---

### Post by candtalan on 2015-09-07
I am running Ubuntu 12.04 on a desktop pc, fully updated, and immediately following a number of updates presumably including thunderbird, (after a 10 day holiday away) I find Thunderbird crashed soon when using. It now crashes on thunderbird startup - that is, the screen shades dark, and although the tbird window is resizable I can do nothing in tbird. Looking at system monitor processes, it shows that thunderbird is using 100% CPU (on one core whatever. There are 4 cores in this pc)  No error message is shown. It has to be closed via tbird launcher icon: Quit, Force quit. When I run:
(terminal)  thunderbird -safe-mode
however, tbird crashes as before.
I have tried a number of actions, all failed, except it seems ok having copied pasted the .thunderbird folder into another Partition (same machine) which is running Ubuntu 14.04 - in this OS I was careful to first update fully but NOT include thunderbird in the accepted updates.
I would be grateful for some help here
tia

---

### Post by howefield on 2015-09-07
Given that you have a copy of the .thunderbird folder elsewhere on your machine have you tried deleting or renaming the original ~/.thunderbird folder to force it to start from scratch?

---

### Post by candtalan on 2015-09-07
TY
That was similar to my action into 14.04, which seemed to work, although I am unclear of the steps to take and their significance.
1)Delete tbird ./thunderbird
2) start existing installed empty tbird
3) dismiss new account requests
4) close tbird
5) paste in the original ./thunderbird

step 5 is what I am unclear about. Is this as I describe?

tia

---

### Post by howefield on 2015-09-07
If you are saying that thunderbird starts correctly with a new profile, it confirms the issue lies in your profile rather than thunderbird itself. When Thunderbird starts after an update it usually checks and validates your extensions and add-ons, perhaps it had an issue with one of them ? The one that caused me an issue recently was "lightening" although it correctly offered to update the extension and all was well.

I'd expect you to have issue reoccur if you simply paste in the old profile folder, is it too onerous to recreate your account ?

---

### Post by candtalan on 2015-09-07
ty
I will test again the paste of same old profile first

---

### Post by candtalan on 2015-09-07
yes, with an empty start (old profile renamed temporarily) then replace the profile with the old one, yes it crashes.
My account is quite complex, so it would be worth some effort to retain the basics.....
tia

---

