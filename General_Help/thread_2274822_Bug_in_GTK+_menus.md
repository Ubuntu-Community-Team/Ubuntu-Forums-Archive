---
title: "Bug in GTK+ menus?"
date: 2015-04-22
forum: General Help
---

### Post by anthony60 on 2015-04-22
Hi,

I tried to search for an existing bug report but could not find anything easily.

When I open menus (for instance open file on some browser), I have to "waste" one character before I can type in a file name. For instance, if a folder contains "myfile", I would normally just start typing the name, like "myf" and it would select it already. But with my new laptop (Ubuntu 14.10), the first character is ignored systematically (note that using "ctrl" or "alt" works as well, though somehow not "space" for the wasted character). Similarly when I play with "zenity --list ...", the same issue occurs with the dropdown options, which is what makes me think it's a GTK+ issue maybe.

Anyone has similar issues (and maybe a solution!)?

Thanks!

---

### Post by mc4man on 2015-04-22
In very limited cases where I'd use 'open file' &* type something*  there is no issue here. 
Maybe try disabling ibus if not using, System Settings > Language Support > Keyboard input method system: > None

---

### Post by anthony60 on 2015-04-22
Do you mean you don't observe the "wasted" character?

To reproduce the issue with zenity: "zenity --list --column col abc def ghi"

I tried on a linux mint machine I have around and it doesn't suffer from that problem (nor did previous versions of ubuntu I used in the past)

---

### Post by mc4man on 2015-04-22
> **anthony60 said:**
> Do you mean you don't observe the "wasted" character?
)
Correct, no problems
I'd suggest you start planning on a new install of 15.04 as 14.10 is almost EOL & was crappy from the get-go

---

### Post by anthony60 on 2015-04-23
Thanks, crazy that it just came out! Fortunate coincidence.... IF it fixes my problem! Still, I appreciate the input!

EDIT: (post-upgrade) and that DID fix it!

---

