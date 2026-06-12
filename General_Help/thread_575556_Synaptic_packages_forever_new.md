---
title: "Synaptic: packages forever new?"
date: 2007-10-14
forum: General Help
---

### Post by wolfger on 2007-10-14
This has been bothering me for a while now, so I figure I'll ask this vast pool of wisdom:
Do packages *ever* stop being "New in repository" in Synaptic Package Manager? I find it rather annoying to have "new" packages every time I update, only to run down the list and find nothing's changed.

---

### Post by erginemr on 2007-10-15
That also bothered me for some time, and I thought something was seriously wrong in Synaptic. Happened especially after I changed the repository addresses. 

But eventually (I believe after one week of staying on charts), it stopped reporting them as new. How about yours? I'd suggest you to wait for at least one week...

---

### Post by wolfger on 2007-10-15
Seems like it's been longer than a week, but it may just be my impatience. I'll wait another week and see what happens.

---

### Post by erginemr on 2007-10-23
So... Any change?

---

### Post by wolfger on 2007-10-23
Nope. Everything that was there prior to my initial post is still "new".

---

### Post by erginemr on 2007-10-25
Oh, well!... 

I think I have found something in aptitude that is worth a try. When use type "aptitude" from the console and nothing else, you end up with a text-mode but graphical menu of "aptitude" that lists all installed and available programs, allows you to install / temove them and what not.

The thing that drew my attention is a setting in the menu. When you press "Ctrl+T", you access aptitude's mein menu above. From under Options -> Misc., there is a setting there that says "Forget which packages are new.." and disables the reporting of new packages. Let us try that one and see if it makes any difference. Press "q" to leave the graphical interface and fall back to the console.

For the changes to apply, you need to update the packages by issuing "sudo aptitude update" from the console. And run "synaptic" to see if it helps...

---

### Post by erginemr on 2007-10-25
Speaking of the graphical features of "aptitude", there is another setting I'd like to mention that comes in handy: From "Ctrl+T" -> Main Menu -> Options -> Dependency Handling (the mouse also works), disable the line that says: "Install Recommended Packages automatically"

I have noticed its effect when I tried to install tvtime with "sudo aptitude install tvtime" and the system tried to install a myriad of packages summing up to ~44 MB.

On the other hand, when I disable the automated installation of recommended packages, the same command above installs only one or two packages with ~1.8 MB.

I do not know whether those "recommended" packages do a significant job or not, but I did not observe any significant performance impact between the two. 

This "aptitude" thingy definitely deserves a time investment to learn, they have even stuffed a little game (mine sweeper) inside.

---

