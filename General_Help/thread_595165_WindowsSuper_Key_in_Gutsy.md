---
title: "Windows/Super Key in Gutsy"
date: 2007-10-28
forum: General Help
---

### Post by AntiHeroJoe on 2007-10-28
I'm having a bit of a problem with my upgrade to Gutsy from Feisty. I used to have my windows key set to open the panel menu, but after upgrading this no longer works. I've tried changing my keyboard type in System > Preferences > Keyboard which did not work, and I checked in System > Preferences > Keyboard Shortcuts and I have the panel menu set to SUPER L, like if I click on it to set the key, and I press the windows key, it gives me SUPER L. I believe then that the system should be recognizing this keypress, but it's not opening the panel menu. Any ideas? I'm running Gutsy on a Dell Inspiron E1505 w/Compiz-Fusion max/custom graphics setting (dunno if this might interfere?)

---

### Post by ed-koala on 2007-10-28
Compiz has it's own shortcut section.  Open your compiz settings, open general options, select Actions tab, then expand the general section.  Set your shortcut there and see if that helps.

---

### Post by AntiHeroJoe on 2007-10-28
hey man, looks like I can set something to SUPER plus another key using compiz, but not the SUPER key itself. I had this working great before, I could use the SUPER key for the panel menu, but I could also use it in combination with other keys for special effects...anyway to get that kind of functionality back?

---

### Post by ed-koala on 2007-10-28
I just checked my Gutsy install and it works fine.  What type of keyboard layout do you have?  A generic 105 key layout works perfectly for me.

---

### Post by AntiHeroJoe on 2007-10-28
I'm using the 105 generic layout as well...If I click next to show main menu in the key column, it says "New accelerator...", now if I just hit the SUPER key, nothing happens. But if I hit, say, SUPER+Z, it accepts that. I just want to be able to hit the SUPER key itself. Thanks for your help, btw!

---

### Post by ed-koala on 2007-10-28
Ok, I think - MAYBE - I know what the problem is.  If you have any other action tied to the super key, like SUPER-Z to maximize a window, then you'll never be able to use just the Super key, cause you'd never be able to get to the Z part.

I just checked my setup, and I have the opposite problem of you, I can't select any other key with the windows super key.  Strange.  I can select a key THEN super tho.  Might have something to do with compiz tho, I know there was another person who had a key mapping issue and he was able to set it in Compiz to get it to work.  Perhaps because Compiz DOES use the Super + <key> binding that is inhibiting the other shortcuts.  Just theorizing tho.

---

### Post by ed-koala on 2007-10-28
Think I found an answer for ya!!!

Changing my keyboard layout from 105 key to 104 key changed the behavior of the super key bindings.  Try that out and see what happens.

---

### Post by AntiHeroJoe on 2007-10-28
I tried killing all SUPER key bindings, that didn't work. Tried the 104 key layout, that didn't work either. This behavior is like the control or alt keys...they don't work independently but require an additional keystroke to work. In my searches I saw something about the super key being mapped as a modifier? Any ideas in regards to this? Is there a way to make it NOT be a modifier so I can use it independently?

---

### Post by ed-koala on 2007-10-28
I'm just about  out of ideas ... but let me ask this, when you try to make a shortcut does it say Mod or Super?  If you get Mod, make sure under Keyboard - Layout Options - Alt/Win key behavior ... make sure Default is checked.  I tried making Super is mapped to Win keys and that didn't do it for me, but is another option to try.  After this, I'm out of ideas, but some combo of all this SHOULD get you what you want.

---

### Post by AntiHeroJoe on 2007-10-28
It just says super, and my windows key is bound to super, which is the default anyway. I'll keep messing around, but if anyone has any suggestions, suggest away!

---

### Post by psiklotron on 2008-02-13
I had the same problem, I finally got it to work! :-)

What worked for me:
1. System->Preferences->Keyboard shortcuts
2. I had the 'Pause' binding set to 'Super+L'. I removed it (click on it and hit backspace) - so it read "Disabled"
3. Voila! Super started working as expected.

edit: It seems *any* super+<key> binding in system->preferences->keyboard shortcuts will mess it up in compiz. So remove anything that says super+<key> in there.

This is the description of the problem I had:

1. I can register Super+<somekey> in compiz settings (it shows up as the keybinding) but it does not trigger the action. When I press super+<somekey>, nothing happens.
2. <something>+super+<something> works, but only in that order. Example, alt+super+a works, but super+alt+a wont' work.

Any ideas? The ones suggested so far did not work.

My configuration:
1. Ubuntu 7.04 on a Compaq Presario V2000 notebook.
2. Running Compiz/Fusion

---

