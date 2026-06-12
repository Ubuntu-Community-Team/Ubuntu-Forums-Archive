---
title: "Keyboard volume controls wrong sound card"
date: 2006-09-30
forum: General Help
---

### Post by mempf on 2006-09-30
Hi guys.

I have two sound cards: the one that's on my motherboard and an Audigy 4.

I have set the Audigy as my primary sound card in "Sounds". Everything works however the keyboard volume buttons still change the onboard sound card not the Audigy.

How do I change this so my keyboard changes the volume on my Audigy? 

Thanks

---

### Post by Cuppa-Chino on 2006-11-01
Same problem here!

Have Audigy 2 that I want to control but also onboard sound and TV card - with recorder decoder etc.

Seems during install system picked the TV card as primary sound card now I have changed in under System-->Preferences-->Sound but that has not helped with the vol display etc.

Also how do I uninstall the onboard sound card that the system installed during setup.

---

### Post by LxP on 2006-11-01
I've always had the problem where my keyboard volume control only adjusts the *left* speaker and not the right, because my sound card provides a separate channel for each.  In a way, I suppose this is related to your problem.

I came across this GNOME bug report a while ago and it seems to address the issues that I'm having--you may or may not be interested in it too:
[LIST]
[*][http://bugzilla.gnome.org/show_bug.cgi?id=173035](http://bugzilla.gnome.org/show_bug.cgi?id=173035)
[/LIST]

---

### Post by SomeGuy on 2006-11-16
hey
i also have this problem
i have audiy2 and a tv card

for some reason it randomly chooses which to control when i boot up ubuntu then the next time i reboot it may switch to control the ohter card

the link u provided with the pathces in C files

how does one, and by that i mean a n00b like myself, applie these patches

---

### Post by LxP on 2006-11-19
> **SomeGuy said:**
> the link u provided with the pathces in C files
how does one, and by that i mean a n00b like myself, applie these patches

I haven't applied the patches myself, but it would involve downloading a source code package of some sort, merging in the changes with the **patch** utility, compiling and installing.  I personally don't have the confidence to try this, but please do let us know how it goes if you try it out.

---

### Post by nuskooltrials on 2006-11-29
I had this problem as well for an Audigy 2 and found that this worked:

[http://ubuntuforums.org/archive/index.php/t-242996.html]("http://ubuntuforums.org/archive/index.php/t-242996.html")

---

