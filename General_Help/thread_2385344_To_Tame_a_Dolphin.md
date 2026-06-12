---
title: "To Tame a Dolphin"
date: 2018-02-19
forum: General Help
---

### Post by Hasimir on 2018-02-19
So I'm taking Dolphin File Manager out for a spin and two things elude me:
- how to make it use a **dark theme** (my current Gnome Theme, set through Gnome Tweaks, is Paper with the Global Dark Theme option turned on)
- how to **open as Root**

---

### Post by vasa1 on 2018-02-19
> **Hasimir said:**
> ...
- how to **open as Root**
I think you can't in 17.10. [s]Whenever you perform an action that needs root, you'll be prompted for your password.[/s]

[https://cgit.kde.org/dolphin.git/commit/?id=0bdd8e0b0516555c6233fdc7901e9b417cf89791](https://cgit.kde.org/dolphin.git/commit/?id=0bdd8e0b0516555c6233fdc7901e9b417cf89791)
[https://forum.kde.org/viewtopic.php?f=224&t=141836](https://forum.kde.org/viewtopic.php?f=224&t=141836)

Also, could you please describe your usage in which you seem to require to use root so extensively?

Re. the dark theme, dolphin is a qt app and so you need a qt theme.

Correction: I can get the password prompt for Kate, not for Dolphin.

---

### Post by Hasimir on 2018-02-19
> **vasa1 said:**
> I think you can't in 17.10. Whenever you perform an action that needs root, you'll be prompted for your password.

I would be ok inserting the password every time.
The problem is... I can't find a way to do it o_O
To tell Dolphin "hey I want to open this folder as Root!" so that then Dolphin asks me for the password.

---

### Post by dragonfly41 on 2018-02-19
If you must .. 

gksu dolphin

[edit]
Actually this command launches my 16.04 dolphin as root but UI is screwed up.

I don't use dolphin at all.

---

### Post by vasa1 on 2018-02-19
> **Hasimir said:**
> I would be ok inserting the password every time.
The problem is... I can't find a way to do it o_O
To tell Dolphin "hey I want to open this folder as Root!" so that then Dolphin asks me for the password.

I added one more link to my previous post. Maybe [https://forum.kde.org/viewtopic.php?f=224&t=141836#p381356](https://forum.kde.org/viewtopic.php?f=224&t=141836#p381356) in that thread addresses the issue.

I think people have recommended Midnight Commander as a file browser that meets this aspect.

---

### Post by Hasimir on 2018-02-19
> **vasa1 said:**
> 
Also, could you please describe your usage in which you seem to require to use root so extensively?


Sometimes I need to access some folder that is set for Root-Access only.
For example, in my quest to give a dark theme to Dolphin, I was trying to follow a guide online that instructed me to put stuff into a /usr/shared/themes folder... or something like it. And I was unable to do it because none of my file managers (Nautilus, Pantheon, Dolphin) were able to access that folder with root privileges :(

---

