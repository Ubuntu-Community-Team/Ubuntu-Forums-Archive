---
title: "Checkgmail issue (since Feisty?)"
date: 2007-04-21
forum: General Help
---

### Post by bootsbradford on 2007-04-21
I've been using Checkgmail very happily for a few months on Edgy. 

I upgraded to Feisty just over a week ago now and I think there's been a problem ever since. I'm still notified of new mail but when I click on the icon, I cannot carry out the actions that I should be able to (e.g. opening a single email, archiving, deleting etc. without going into gmail itself.)

Has anyone else had this problem? Any ideas how to fix?

---

### Post by wampirek on 2007-04-24
> **bootsbradford said:**
> I've been using Checkgmail very happily for a few months on Edgy. 

I upgraded to Feisty just over a week ago now and I think there's been a problem ever since. I'm still notified of new mail but when I click on the icon, I cannot carry out the actions that I should be able to (e.g. opening a single email, archiving, deleting etc. without going into gmail itself.)

Has anyone else had this problem? Any ideas how to fix?

I've got the same problem, but only when I have Desktop Effects enabled. 
Try to turn Desktop Effects off - it should help.

---

### Post by bootsbradford on 2007-04-24
Yes, the same works for me, just a shame that you can't have Desktop Effects AND checkgmail working together!

---

### Post by ciscosurfer on 2007-04-24
> **bootsbradford said:**
> Yes, the same works for me, just a shame that you can't have Desktop Effects AND checkgmail working together!And this comes straight from the developers page on sourceforge for checkgmail:
[INDENT]_CheckGmail and XGL/Compiz_ 		
Sorry, but these two don't seem to like each other very much (CheckGmail still works, but you won't be able to use a lot of the nifty features). I don't have a system running XGL and can't bugfix this one myself, but from what I can tell the issue lies with incompatibilities in the Gtk2-perl modules (and more specifically the signal_connect methods) rather than my own code. Please stop reporting this issue!! At the moment there's nothing I can do about it, and anyone experiencing this problem would be better off reporting it to the Gtk2-perl developers. Thanks! :)
[/INDENT]Gimme a break! (pun intended)

---

### Post by stevieb on 2007-05-19
i think checkgmail is now fixed; take a look [here]("http://checkgmail.sourceforge.net/")

i've tried it, and it seems to work...
-steve

---

### Post by bootsbradford on 2007-05-20
Thanks for this. Unfortunately, I have had to temporarily abandon Ubuntu with as a result of random freezing that many people are suffering from. Hopefully this too will get fixed too and I can return to Ubuntu and Checkgmail!

---

### Post by mustang on 2007-05-28
> **stevieb said:**
> i think checkgmail is now fixed; take a look [here]("http://checkgmail.sourceforge.net/")

i've tried it, and it seems to work...
-steve

Thanks for notifying us. It works perfectly on my side.

---

