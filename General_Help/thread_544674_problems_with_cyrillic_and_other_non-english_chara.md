---
title: "problems with cyrillic and other non-english characters"
date: 2007-09-06
forum: General Help
---

### Post by EvergreyNY on 2007-09-06
just recently updated to gutsy and everything has been mysteriously working fine. 

except i seem to have lost certain character support in my applications. when i load music files in rhythmbox that contain anything except the 26 letters in the standard english alphabet, they dont show. rhythmbox displays everything correctly in the missing files tab (tags, paths, and all), but nautilus does not even recognize that the tracks exist (not displayed). they are all tagged correctly because everything was working fine prior to the upgrade. 

anyone else have this problem or know of a solution?

---

### Post by jamvegan on 2007-09-06
I do not normally use Rhythmbox, but since I recently did a clean install of Feisty on this machine I decided to try opening a non-latin file in it, to see if I got the same problem as you.  I didn't.  The hiragana displays properly in all of Rhythmbox's windows and in the Gnome panel at the bottom of the screen.  I checked Rhythmbox's preferences for anything that might fix (or cause) your problem, and found nothing.  I'm wondering if you somehow either changed your default language setting or the font that Rhythmbox uses.

What is the output if you type this?
```
echo $LANG
```
Mine is en_US.UTF-8.  I think you should be okay with any UTF encoding.

Other than that, I'm not sure what to check.  Good luck!

---

### Post by EvergreyNY on 2007-09-07
I get en_US.UTF-8 as well.

---

