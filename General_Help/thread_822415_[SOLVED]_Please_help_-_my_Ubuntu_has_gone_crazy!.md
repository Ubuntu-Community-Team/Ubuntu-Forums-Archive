---
title: "[SOLVED] Please help - my Ubuntu has gone crazy!"
date: 2008-06-08
forum: General Help
---

### Post by FoxTheCave on 2008-06-08
Alright, here's what happened.

I was installing updates for my Ubuntu, about 100 megs of updates, just like it told me to. Then, halfway through installing the downloaded updates - my laptop just froze. It crashed. I had no choice but to turn it off and then on. 

Now, my Ubuntu has gone crazy. For some reason, the toolbars at the bottom that allow me to access 'Places' and 'System' and 'Applications' have just gone. Theres just black space there. Additionally, all my files now have however much space they take up written below their icon.

Additionally, I can not download any updates, or I asssume install anything. It says something about a corruption.

Has anyone else experienced this? Can someone please help me?

Many thanks in advance!

---

### Post by tom66 on 2008-06-08
Well, make sure you definitely can't install something, try reinstalling gnome-desktop or ubuntu-desktop. 

I have seen file sizes below icons, but not in this situation. I think it can be disabled in Nautilus, but that will have to be done after we sort out the desktop.

---

### Post by Vadi on 2008-06-08
Oi. Try doing 'sudo apt-get install -f' in the terminal. What does that do?

---

### Post by FoxTheCave on 2008-06-08
Yep, when I try and install anything, it just doesn't work.

---

### Post by tom66 on 2008-06-08
Any specific error message? Like,"E: Broken packages"?

---

### Post by FoxTheCave on 2008-06-08
Tried it vada, all I got was the same thing I always get when I try and install something:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

---

### Post by tom66 on 2008-06-08
Have you done what it suggests?

---

### Post by FoxTheCave on 2008-06-08
I'm going to sound like a real idiot, but I don't understand what its suggesting.

---

### Post by Vadi on 2008-06-08
Do 'sudo dpkg --configure -a'.

Meanwhile, I'm going to try this myself, because there's also a similar thread - install OK, updates, and it breaks. :/

---

### Post by FoxTheCave on 2008-06-08
Thank you all! Programs now install fine!

However, how do I get rid of those annoying space messages beneath the icons?

---

### Post by the8thstar on 2008-06-08
Open any folder, go to Preferences in the menu, set the icon size to 100% on the display tab and you should be good to go.

---

### Post by tom66 on 2008-06-08
Open a Nautilus window, any file window, then do the following:

[LIST=1]
[*]Edit > Preferences
[*]Click 'Display' (tab)
[*]Change as appropriate.
[/LIST]

---

### Post by FoxTheCave on 2008-06-08
Thank you, you've all been very helpful!

---

### Post by the8thstar on 2008-06-08
Don't forget to click on the little medals to thank us!

---

### Post by tom66 on 2008-06-08
No problem, enjoy Ubuntu!

---

