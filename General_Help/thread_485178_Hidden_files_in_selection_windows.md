---
title: "Hidden files in selection windows"
date: 2007-06-26
forum: General Help
---

### Post by buttari on 2007-06-26
Hi all,
for some unknown (to me) reason, since a couple of days ago, every time I open a file selection window all the hidden files are shown. For example, if I do File->Open file on Firefox, I get a huge list of all the hidden and non-hidden files in my home dir. Does anybody know why this happens and how to hide the hidden :) files again?

Thanks

Alfredo

---

### Post by arvevans on 2007-06-26
CTRL-h

Oops!  That works in the File Manager, but not in Firefox.
Wait one while I find the hidden file toggle in Firefox...

---

### Post by coffeecat on 2007-06-26
Ctrl-H will only last as long as the window is open.

**buttari**, you've managed to change your nautilus preferences somehow. Open a Nautilus window, go to Edit > Preferences. Choose first tab (Views) and uncheck 'Show hidden and backup files'.

**Edit:** - no that doesn't seem to make a difference with Firefox > File > Open File. When you say 'file selection window' do you mean a Nautilus file manager window, or are you just talking about Firefox?

---

### Post by buttari on 2007-06-26
Well,
thanks for the quick answer. Actually in Nautilus the hidden files are not shown (and the "show hidden files" in the View menu is correctly unchecked). I am talking about the window that pops up when you hit File->Open File in any program, or, for example the windows that pops up when you hit the "Attach" button in Evolution.

Thanks

Alfredo

---

### Post by arvevans on 2007-06-26
CoffeeCat

Do the Nautilus settings also affect Firefox?
_._

---

### Post by buttari on 2007-06-26
> **arvevans@earthlink.net said:**
> CoffeeCat

Do the Nautilus settings also affect Firefox?
_._

No, it doesn't. Moreover, I cannot find anything on gconf-editor

Alfredo

---

### Post by arvevans on 2007-06-26
I looked thru all the stuff in Firefox at "http://about.conf" and came up with nothing obvious that would solve his problem.  Maybe reloading Firefox is the obvious solution?
Arv
_._

---

### Post by Rui Pais on 2007-06-26
hi,
right click on the windowlist that contains the list of hidden files.
Do you see an option 'Show hidden file (check/unchecked)'?

---

### Post by coffeecat on 2007-06-26
Sorry to introduce a red herring with Nautilus. If it's happening with the window that pops up with File > Open File in **any** app, then I would have thought it would have been a gconf thing, although I see you have looked in there already.

I'll have a rummage through the gconf editor myself. It's a bit of a labyrinth in there. If I find anything I'll post back.

---

### Post by buttari on 2007-06-26
> **arvevans@earthlink.net said:**
> I looked thru all the stuff in Firefox at "http://about.conf" and came up with nothing obvious that would solve his problem.  Maybe reloading Firefox is the obvious solution?
Arv
_._

What do you mean by reloading? just close and reopen? I did it many times already (it's a laptop...). Anyway the problem does not only affect Firefox but all the programs where you can make a file selection (so, basically 99% of the applications installed in my system). For example, even if I do
```
zenity --file-selection
```
the window that pops up contains all the hidden files.

Alfredo

---

### Post by Rui Pais on 2007-06-26
> **coffeecat said:**
> Sorry to introduce a red herring with Nautilus. If it's happening with the window that pops up with File > Open File in **any** app, then I would have thought it would have been a gconf thing, although I see you have looked in there already.

I'll have a rummage through the gconf editor myself. It's a bit of a labyrinth in there. If I find anything I'll post back.

It's a gtk file selection, general to a lot of apps. Check my previous post, please.

---

### Post by buttari on 2007-06-26
> **Rui Pais said:**
> hi,
right click on the windowlist that contains the list of hidden files.
Do you see an option 'Show hidden file (check/unchecked)'?

Hey that was quick!
Thanks Rui, this fixed the problem. I should have checked it by mistake.

Alfredo

---

### Post by Rui Pais on 2007-06-26
> **buttari said:**
> Hey that was quick!
Thanks Rui, this fixed the problem. I should have checked it by mistake.

Alfredo

:)

---

### Post by arvevans on 2007-06-26
[INDENT] Re: Hidden files in selection windows
hi,
right click on the windowlist that contains the list of hidden files.
Do you see an option 'Show hidden file (check/unchecked)'?
__________________[/INDENT]

That works individually, but is it persistent across all applications?

After looking in .profile, and all the other ."something" files in the home directory I don't see anything that obviously causes this situation.  I must have overlooked something.

Disregard my earlier comment about re-loading Firefox.  I was thinking that it was a Firefox-only problem.

Arv
_._

---

### Post by Rui Pais on 2007-06-26
> **arvevans@earthlink.net said:**
> [INDENT] Re: Hidden files in selection windows
hi,
right click on the windowlist that contains the list of hidden files.
Do you see an option 'Show hidden file (check/unchecked)'?
__________________[/INDENT]

That works individually, but is it persistent across all applications?

After looking in .profile, and all the other ."something" files in the home directory I don't see anything that obviously causes this situation.  I must have overlooked something.

Disregard my earlier comment about re-loading Firefox.  I was thinking that it was a Firefox-only problem.

Arv
_._

Well i checked using gedit and swiftweasel and it seems that the answer is yes. 
They seems to share the info. The status of gtk file selection is saved with the last app that contains it is closed.

both open:
gedit (set Show hidden) and swiftweasel (not Show hidden).

- close gedit then swiftweasel -> saved status Not show hidden
or:
- close swiftweasel then gedit -> saved status Show hidden

---

