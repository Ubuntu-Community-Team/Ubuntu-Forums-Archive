---
title: "how set font size in thunderbird"
date: 2019-11-17
forum: General Help
---

### Post by Skaperen on 2019-11-17
every time i try to write new email to send with thunderbird, it opens a window with a text font that is too small for me to read even with corrective lenses (the screen is in focus but the letters are just too small).  i can enlarge the font (ctrl+roll mouse) and that makes it readable.  thunderbird does not remember this setting to use each time that window opens.  the thunderbird help describes a place to change the font that does not exist that begins with tools>options but "options" is not an available choice.  and that 3rd match item for "font size" is describing a setting that does not persist.  i would like to know what to do to get a font size of about 18 minimum to read what i am writing and to read what is incoming and not explicitly set.  incoming that is set, i'd like to make be at least 75% larger.  anyone know how to do this in thunderbird?

---

### Post by uRock on 2019-11-17
I went to the button with the three lines in the upper right, then selected Preferences, then in the new window I selected the Display tab.

---

### Post by Skaperen on 2019-11-18
i don't get "Display" as a choice.

---

### Post by Artim on 2019-11-18
Newer ain't always better.  I use Seamonkey, which does what both Thunderbird and Firefox do, but faster and more reliably.  And Seamonkey has *thousands fewer lines of code* than Firefox!  It has been trouble-free on my Xubuntu for years.

---

### Post by speartip on 2019-11-18
You need to go to Thunderbird's Menu (The 3 lines) - Preferences - Preferences - Composition. Under the "General" Tab you will see the Font Box, which is probably set to "Variable Width". Next to that You'll see "Size". This allows you to set the Font Size from Tiny to Huge. That Setting should stick.

---

### Post by uRock on 2019-11-18
> **Skaperen said:**
> i don't get "Display" as a choice.

If you go into the software center and search Thunderbird, do you have the deb or the snap installed? I haven't installed the snap, so not sure if it is different.

---

### Post by walts48 on 2019-11-18
> **Skaperen said:**
> i don't get "Display" as a choice.

Display is the 2nd tab in the Preferences window.
Select the Formatting tab in Display.
Click Advanced.
Set the Font size settings to your liking for both Latin and Other Writing Systems.
You may also want to disable the Font Control settings.

---

### Post by Skaperen on 2019-11-18
> **uRock said:**
> If you go into the software center and search Thunderbird, do you have the deb or the snap installed? I haven't installed the snap, so not sure if it is different.

would [COLOR=#0000cd][FONT=courier new]**dpkg -l**[/FONT][/COLOR] list it the same either way?

when i do [COLOR=#0000cd][FONT=courier new]**ls -l /snap**[/FONT][/COLOR] all i see is a [COLOR=#800080][FONT=courier new]**README**[/FONT][/COLOR] file.  does that mean i have no snaps (i hope so)?

---

### Post by Skaperen on 2019-11-18
i'm not seeing *any* tabs.

---

### Post by speartip on 2019-11-19
Have you tried my suggestion in post 5?

---

### Post by uRock on 2019-11-19
It should be seen here.

---

### Post by Skaperen on 2019-11-20
> **speartip said:**
> You need to go to Thunderbird's Menu (The 3 lines) - Preferences - Preferences - Composition. Under the "General" Tab you will see the Font Box, which is probably set to "Variable Width". Next to that You'll see "Size". This allows you to set the Font Size from Tiny to Huge. That Setting should stick.

i can get to that. when i make changes, nothing changes size.

---

### Post by Skaperen on 2019-11-20
> **uRock said:**
> It should be seen here.

OK, i got there under Preferences > Preferences.

it started with "16" highlighted and some extremely small text in the composition window.  i selected "18" and it got *much* larger.  went back to "16" and it got a bit smaller but still _way larger than it started_.  went back to "18".  the section where i read incoming mail is not changing size by that.  ctrl+mouseroller does change size but it doesn't stay.  in other apps ctrl+mouseroller size changes do stay.  so i wonder how that widget is trying to save the size or if it even tries.  i have never developed a GUI app, so i have no idea.

---

### Post by Skaperen on 2019-11-20
> **Skaperen said:**
> i'm not seeing *any* tabs.

there's a _2nd step_, selecting "Preferences" _again_, to get there.  on it, now.

---

### Post by Skaperen on 2019-11-20
> **speartip said:**
> Have you tried my suggestion in post 5?

just did.  been busy for a couple days.  but it revealed that 2 step Preferences > Preferences path.

i wonder how much of this stuff i can design in my own GUI apps when i get to that point.  i tend to see a lot of crazy ways things are done in many GUI apps and wonder if that is just the way those widgets work.  i'll be coding mostly in Python, so i'll have to deal with yet another layer of stuff.

---

### Post by Skaperen on 2019-11-20
different posts have tried to send me to 3 different places.  Preferences>Preferences>General doesn't have any size change widget, but the other 2 do.  still not getting anything but ctrl+mouseroller to change the size in the reading view.  and any changes by ctrl+mouseroller don't stick (maybe they shouldn't as it would be nice to have a temporary change).

---

### Post by walts48 on 2019-11-21
> **Skaperen said:**
> different posts have tried to send me to 3 different places.  Preferences>Preferences>General doesn't have any size change widget, but the other 2 do.  still not getting anything but ctrl+mouseroller to change the size in the reading view.  and any changes by ctrl+mouseroller don't stick (maybe they shouldn't as it would be nice to have a temporary change).

Well, it is hard to help since you don't indicate what changes you made and where.

Maybe this will help. [https://www.ghacks.net/2013/01/18/how-to-change-the-font-of-mails-in-thunderbird/](https://www.ghacks.net/2013/01/18/how-to-change-the-font-of-mails-in-thunderbird/)

---

### Post by Skaperen on 2019-11-22
i think part of the problem is that they keep changing the layout and i can't find where things are when trying to follow instructions exactly.  but while "menu surfing" i did get a pop-up window with a "Display" tab.  eventually i found that the 2nd "Preferences" selection got me to that window.  the 1st "Preferences" choice got the 2nd "Preferences" choice, but the menus were overlapping and collapsing.  i figured out how to move the mouse to keep them up and now i can reproduce getting there.  now i'm working to figure out what changes what and which are permanent and which are temporary.  and in the mean time, email i send to my family have giant letters when my intent is to just see what i am typing and receiving.

---

