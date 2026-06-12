---
title: "Thunar: underscore and files order"
date: 2016-03-13
forum: General Help
---

### Post by SamInside on 2016-03-13
In Windows I used to put a underscore before certain files to make them stay on top of the file list.

However in Thunar the underscore is ignored and the file is put in alphabetical order basing on the characters which follow the underscore. How can I change this?


[ATTACH=CONFIG]267793[/ATTACH]

---

### Post by vasa1 on 2016-03-13
See [http://askubuntu.com/questions/41390/can-nautilus-use-correct-lexicographic-sort?rq=1](http://askubuntu.com/questions/41390/can-nautilus-use-correct-lexicographic-sort?rq=1) for related aspects.

Edit: the file manager I use, PCManFM, behaves as though the underscore isn't there at all.

Sorry to keep pecking away at this but [http://unix.stackexchange.com/questions/39827/how-do-i-make-ls-sort-underscore-characters-first?rq=1](http://unix.stackexchange.com/questions/39827/how-do-i-make-ls-sort-underscore-characters-first?rq=1) (even though it has to do with the terminal).

---

### Post by SamInside on 2016-03-14
Thank you for your answer, but I'm not sure what to do.
Should I try changing LC_COLLATE and alike, or should maybe rename all my files adapting to linux sorting? After all I'm in the process of moving permanently to Xubuntu.
But even in this case, what character sould I use in place of the underscore? If I got this right, there is none, I should use something like zeros, which looks quite horrible.
Sorry for the vague question, but I'm indeed a bit lost.

---

### Post by vasa1 on 2016-03-14
Well, whichever operating system you use, people advise being conservative in naming files to achieve cross-platform portability (and to avoid issues when you use the terminal).

Zero seems to work for me. I'm not sure why it would be horrible. And, if you are indeed planning to move to Linux, be prepared for more differences. Many, if not most, people here have made the switch and survived.

All the best :)

---

### Post by SamInside on 2016-03-14
> **vasa1 said:**
> I'm not sure why it would be horrible.
Yep, I guess I was exaggerating lol. I just liked _ more, less invasive I guess.

BTW I'm not new to linux, I used to play around with it years ago, then I sticked with Win7. Now with Win10 awaiting me near the corner I just got scared and here I am. :)
I was using open source software on Windows anyway, I may as well do this last step.

---

