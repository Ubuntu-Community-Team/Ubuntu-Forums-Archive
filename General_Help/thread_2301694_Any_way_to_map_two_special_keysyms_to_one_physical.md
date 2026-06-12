---
title: "Any way to map two special keysyms to one physical key?"
date: 2015-11-04
forum: General Help
---

### Post by trigone on 2015-11-04
Hi!

My deal: i wish to set one single physical key to produce the same result as typing two special keysyms at the same time (eg, any of: ctrl+alt, shift+ctrl, shift+altrGr/lvl3, etc), so that if i wanted to type eg. ctrl+alt delete, i would only need to type one key in addition to <delete> in order to do that. Of course, the purpose is not just a shortcut for one operation, but for the whole range of combinations that require more than one special key.
So, is there any way, any trick, to do that under Linux?
xmodmap doesn't seem to like it very much, it always outputs error messages...

Thanks in advance! Have a nice day. :)

EDIT: edited (thanks to vasa1) to replace the french names of some keysyms by their proper english version.

---

### Post by trigone on 2015-11-04
Btw i wanted to put this thread in the general help forum; i'm not even sure how it ended up here, must be my bad...

---

### Post by cariboo on 2015-11-04
moved by request.

---

### Post by trigone on 2015-11-05
thanks Cariboo!

---

### Post by trigone on 2015-11-05
anyone? :(

---

### Post by vasa1 on 2015-11-05
> **trigone said:**
> anyone? :(

Maybe you can explain what you mean by *maj* and *suppr*?

---

### Post by trigone on 2015-11-05
ha, what an absurd situation! i got mixed up between english and french keysym abbreviations -_- I actually meant respectively <shift> and <delete>
Thanks so much ever for having pointed this out! I edited my post.

---

### Post by mc4man on 2015-11-05
If you worked backward from intended  result then xdotool is simple to use, eg. bind a 3 key result  to a 2 key combo 
(- xdotool key key1+key2+key3

Otherwise you seem to want to create a new modifier, single key = 2 modifiers. What key(s) are you going to give up? (I've none here..

---

### Post by trigone on 2015-11-05
Well as i said, it's not just about one single 3-key combo, but about every 3-key combo that would be of the type "alt-ctrl+something", or "shift-ctrl+something", or else, without having to care about which app will listen to which combo: a transparent total remapping. To try and copy all existing combos of every possible application would be a relative nightmare, although it's still a possibility, but i'm seeking for less hacky than that...
I happened to have gotten a keyboard with no less than 13 keys all on the line of the space bar that i could comfily use as modifier, so you see it's not the hardest part of the equation ^^

---

