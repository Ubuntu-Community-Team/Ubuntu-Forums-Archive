---
title: "[SOLVED] Clicking &amp;quot;Preferences&amp;quot; In Nautilus Closes Nautilus..."
date: 2008-06-21
forum: General Help
---

### Post by Jordinho on 2008-06-21
Whenever I click edit->preferences in nautilus, nautilus just closes and I never get to the preferences box. This (and about a million other annoying things) started about a week ago with a big update. How do I fix this. Is there a way to revert past an old update?

---

### Post by VMC on 2008-06-21
> **Jordinho said:**
> Whenever I click edit->preferences in nautilus, nautilus just closes and I never get to the preferences box. This (and about a million other annoying things) started about a week ago with a big update. How do I fix this. Is there a way to revert past an old update?

What do you mean "edit -> preferences". I don't see that. I have System > Preferences and it opens correctly. There is a directory under ~/home/.nautilus that has a lot of xml files. I have not had much trouble using Nautilus. Maybe someone else has a better solution.

---

### Post by Jordinho on 2008-06-21
You have to open a nautilus window, go to edit, and then go to preferences.

---

### Post by mc4man on 2008-06-21
What happens if you take the alternate route - system ->  preferences -> file management. If it's not listed try R. click applications -> edit menus -> highlight preferences and on right side enable file management

---

### Post by fragos on 2008-06-21
The problem might be the configuration itself. I tried without success to find the nautilus configuration file. Deleting corrupted configuration files will cause an application to start a new one with original defaults. You might try removing the .nautilus folder by renaming it or perhaps making changes with the Gnome Configuration Editor which might save an uncorrupted configuration file.

---

### Post by Jordinho on 2008-06-22
> **mc4man said:**
> What happens if you take the alternate route - system ->  preferences -> file management. If it's not listed try R. click applications -> edit menus -> highlight preferences and on right side enable file management

I got it to show up under preferences, but it still closes when I try to change anything under the display tab.

> **fragos said:**
> The problem might be the configuration itself. I tried without success to find the nautilus configuration file. Deleting corrupted configuration files will cause an application to start a new one with original defaults. You might try removing the .nautilus folder by renaming it or perhaps making changes with the Gnome Configuration Editor which might save an uncorrupted configuration file.

Okay, that worked. I renamed .nautilus and it created a new folder. I rebooted and now I can open preferences. This makes me think that maybe some of my other problems can be solved this way. Since that update my browser looks like this:

[http://img.photobucket.com/albums/v632/kamau84/Screenshot-1.png](http://img.photobucket.com/albums/v632/kamau84/Screenshot-1.png)

And some other theme-like things also changed:

[http://img.photobucket.com/albums/v632/kamau84/Screenshot2.png](http://img.photobucket.com/albums/v632/kamau84/Screenshot2.png)

I've tried changing the theme but it always looks pretty much the same afterwards. Is there possibly a quick fix for this too? Thanks both of you for your help.

---

### Post by mc4man on 2008-06-22
I'm not sure what you see wrong in the first screenie, actually you could give me a tip - what is that fourth toolbar and how did you get it.
As far as shot two, if you don't want the separators r. click on them and remove (or choose move if that's what you had in mind, if move is greyed out, unlock)
as far as folders (color ?), when i choose or change a theme I then customize it to get colors ect. as I want (or what's possible)

---

### Post by fragos on 2008-06-22
System-> Preferences-> Appearances-> Customize Button will give you very fine control to create the look you want.

---

### Post by Jordinho on 2008-06-23
> **mc4man said:**
> I'm not sure what you see wrong in the first screenie, actually you could give me a tip - what is that fourth toolbar and how did you get it.
As far as shot two, if you don't want the separators r. click on them and remove (or choose move if that's what you had in mind, if move is greyed out, unlock)
as far as folders (color ?), when i choose or change a theme I then customize it to get colors ect. as I want (or what's possible)

The separators are usually dotted but these are big and clunky. I want them but they're just one in a number of things that were just arbitrarily changed by that update. As for the googlebar, I had to get Googlebar lite since the official googlebar is not supported by Firefox 3. It's here: [https://addons.mozilla.org/en-US/firefox/addon/492](https://addons.mozilla.org/en-US/firefox/addon/492)

> **fragos said:**
> System-> Preferences-> Appearances-> Customize Button will give you very fine control to create the look you want.

That helped me to change the look of the window border but when I try to change the style of the icons (from GNOME to Crystal SVG) it doesn't change. That's why I think it's some error caused by that update. Things I should be able to change don't seem to want to. I'll see what else I can try to change.

---

