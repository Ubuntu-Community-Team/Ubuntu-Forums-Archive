---
title: "Keyboard problem in 13.10"
date: 2013-10-21
forum: General Help
---

### Post by bach on 2013-10-21
I run Ubuntu on a DELL XPS 13 notebook that has an US keyboard configured as US alternative international. After upgrading to version 13.10 I can no loger get a cedilla by typing accute apostrophe + c. Instead, I get &#263; . What should I do to get a c with cedilla (ç)? I am using Ubuntu Gnome 13.10 64 bit. P.S. I did NOT have this problem with version 13.04. It started after I upgraded to 13.10.

---

### Post by 3WFhdmG on 2013-10-21
Every update since 8.04 (if I remember well) had this problem right after the update! Why?
It's really tiring have to always find a workaround to deal with that every time Ubuntu is updated.
More care should be taken about that specific issue that affects every user who needs to type in Portuguese.

---

### Post by ashwinjn on 2013-12-14
Found a fix! Launch this app called 'dconf editor'. Open Desktop -> ibus -> and click on General. Now check the box next to 'use-global-engine' and 'use-system-keyboard-layout'. This worked for me!

---

### Post by llazarte on 2013-12-16
After trying many suggestions, I accidentally discovered that simply pressing "Right Alt" + "," produces "ç"

Not the most elegant solution, but it lets me go on with my work.

(by the way, "dconf editor" gave me he answer "Unknown command 'editor'".

---

