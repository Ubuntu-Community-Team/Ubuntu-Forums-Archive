---
title: "Backing up Huawei phone"
date: 2023-09-14
forum: General Help
---

### Post by dwater on 2023-09-14
I recently upgraded my laptop to 23.04 - well, I tried, but the upgrade failed so I did a clean install, and so I lost all my configuration. I do have everything in a backup, so there's that.

However, I previously would back up my Huawei phone to a Samba share on my laptop - been doing this for years, and I seem to recall it not being too difficult to set up. The back up is on an external disk drive.

Post-upgrade, however, and I am having trouble. There weren't the same options on the nautilus menu and after searching for solutions, and installing samba/etc, I still don't have any options in nautilus.

I'm happy to start from scratch, which I suspect I might have to do. Is there a 'how to' to get samba going again, or other help?

---

### Post by guiverc on 2023-09-14
You've pasted this question in the *Official Flavors* part of *Ubuntu Forums*, and as a *Lubuntu *question specifically, but is this what you're using?  `nautilus` is the file-manager of GNOME, and Lubuntu provides `pcmanfm-qt`.

You can *non-destructively *re-install a Lubuntu system rather easily (*any Ubuntu Desktop flavor in fact; Ubuntu Desktop too though its a touch more complicated as how can vary slightly on release*), so I'll provide the Lubuntu *Understanding Checklists* link where the *non-destructive* re-install is called *_Install using existing partition_.  *It's what I use if a *release-upgrade* goes wrong, and I lack time to fix it (*or even I lack time for the* *release-upgrade to run, as re-install is so quick*).

[https://discourse.lubuntu.me/t/testing-checklist-understanding-the-testcases/2743](https://discourse.lubuntu.me/t/testing-checklist-understanding-the-testcases/2743)

Another link where I describe the same thing is [https://askubuntu.com/questions/446102/how-to-reinstall-ubuntu-in-the-easiest-way/1451533#1451533](https://askubuntu.com/questions/446102/how-to-reinstall-ubuntu-in-the-easiest-way/1451533#1451533) as the Lubuntu link I used first was intended for QA (*Quality Assurance*) testers, and not end-users.

I won't help with SaMBa sorry, I've not used it since ~2017 which was too long ago.

---

### Post by dwater on 2023-09-14
Oops, I got there by searching for samba, and seeing 'general help' figured it was ok...I didn't notice the parents. I don't know how I managed to select 'lubuntu' instead of 'ubuntu' - must have been a slip of the mouse and/or I need new glasses (or increase the font size).

Yes, it's ubuntu, not lubuntu. I don't immediately see how to change that :/ Perhaps I need to just start again...I didn't paste it.

My question is only about Samba, though, but thanks anyway.

---

### Post by dwater on 2023-10-04
I eventually found this:

[https://bbs.archlinux.org/viewtopic.php?id=254678](https://bbs.archlinux.org/viewtopic.php?id=254678)

"
[COLOR=#444444][FONT=sans-serif]client min protocol = CORE[/FONT][/COLOR]
[COLOR=#444444][FONT=sans-serif]server min protocol = CORE[/FONT][/COLOR]
"

and that did the trick.

---

