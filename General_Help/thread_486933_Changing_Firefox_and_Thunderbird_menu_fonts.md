---
title: "Changing Firefox and Thunderbird menu fonts"
date: 2007-06-28
forum: General Help
---

### Post by jordon on 2007-06-28
I just moved my Firefox and Thunderbird profiles from my Ubuntu desktop to my new Ubuntu laptop. On both computers, I have the default application font set to DejaVu Sans Condensed, but on the new computer, Firefox and Thunderbird use the original (non-condensed) font for menus, dialog boxes, etc. (The fonts displayed on web pages are fine.) I can't remember what I did to fix that problem on the old computer, but I do know that I didn't hack userChrome.css. Can anyone lend a hand?

---

### Post by jordon on 2007-06-29
Never mind. Editing userChrome.css wasn't so hard, and it did the trick for both Firefox and Thunderbird. All I had to do was add this:

```

* {

font-family: "DejaVu Sans Condensed";

}

```

Still, I wonder what I did the first time if it didn't involve editing userChrome.css.

---

