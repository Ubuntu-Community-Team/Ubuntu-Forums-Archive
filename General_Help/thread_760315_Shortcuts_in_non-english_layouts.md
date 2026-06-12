---
title: "Shortcuts in non-english layouts"
date: 2008-04-20
forum: General Help
---

### Post by yesint on 2008-04-20
Dear All,
There is one very annoying and extremely inconvenient thing in Linus in general and in Ubuntu in particular: the behaviour of keyboard shortcuts in non-english layouts. If one presses Ctrl+V in, say, Russian layout it does not trigger the paste command because it is not "V" but cyrillic "M". In Window$ and MacOS this problem does not exist - all shortcuts are **always** mapped to english layout. 
Few apps (pidgin for exapmle) implement this, but all other and the system itself does not. 
This problem really makes many non-english speaking people give up with Linux because it is just not as convenient as familiar Window$ in routine everyday text editing (imagine changing the layout any time you want to copy-paste).
This problem was already posted here few times, but with no answers.
Is it possible to solve this problem in Linux on the system-wide level? 
Any ideas are appreciated!

---

### Post by Brucevdk on 2008-04-20
Do you encounter this behavior in all programs are just a select few (such as Firefox for example)? I  tried it out using Arabic and the only programs that were misbehaving in my case were Firefox/Thunderbird.

If the latter is the case. [This bug report over at Mozilla.org](https://bugzilla.mozilla.org/show_bug.cgi?id=69230) seems to indicate that at least in the case of Firefox it should be resolved in the next major release (3.0).

In the meantime you can use the switch group keyboard option (System -> Preferences -> Keyboard -> Group Shift/Lock behavior) as a workaround.

---

