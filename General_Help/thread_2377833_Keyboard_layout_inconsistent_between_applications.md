---
title: "Keyboard layout inconsistent between applications"
date: 2017-11-17
forum: General Help
---

### Post by bocanaki on 2017-11-17
Hi!

Long time user first time poster. I have an issue today I was hoping someone could help me with.

I just installed the latest version of Ubuntu, coming back from trying out Manjaro, and everything works perfectly except for my keyboard.

My keyboard is configured for Swedish and it works properly until I open a terminal. After that the layout will be English in all applications, it will however still be in Swedish in the terminal and things like the application search.

Any idea what is going on?

Thanks in advance!


**UPDATE 1**

It seems that GNOME overwrites my xkb settings, running **setxkbmap se** fixes the problem, but only for the current session. I am not sure how to make it persistent yet.

[B]UPDATE 2

[/B]So it turns out there was a completely legitimate explanation for this. I had added the line **setxkbmap -option caps:none** to my **.bashrc** (this was to disable my caps key under Arch). Adding the **-layout se** option solved everything, so now everything is fine.

---

