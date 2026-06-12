---
title: "Help with menu items"
date: 2008-02-02
forum: General Help
---

### Post by jorwex on 2008-02-02
Hey all,

I can successfully launch my fresh install of Matlab by this command:
sh /usr/local/matlab75/bin/matlab 

if im in a terminal.

just now i right clicked the applications menu and went to 'edit menus' and created a launcher for matlab in the education menu. I clicked add and made the new entry and pasted the same command that launched it in the terminal that i have above.

the splash window for matlab appears if i use the new launcher in my applications menu, and then in dissapears and matlab never shows up. i tried it again in the terminal and matlab launched fine. just now i doublechecked what i have in the command field of the launcher, and it says the same thing...

what am i doing wrong?

---

### Post by jorwex on 2008-02-04
Anyone? (bump)

---

### Post by jorwex on 2008-02-04
got it!

sh /usr/local/matlab75/bin/matlab -desktop

is the correct command. apparently you need the "-desktop" on the end

---

