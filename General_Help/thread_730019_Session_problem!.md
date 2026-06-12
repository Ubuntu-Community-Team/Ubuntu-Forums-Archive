---
title: "Session problem!"
date: 2008-03-20
forum: General Help
---

### Post by spdaniel91 on 2008-03-20
Hi guys!

I recently did a nice customization to my Gutsy. I added Kiba, a Leopard theme and some icons. I wanted to set Kiba to load on start up, but instead of just adding the program to the list, I wrongly checked the "automatically load active programs that were open when I log out" (It was something like that). Well, I killed the gnome-panel thing, because I didn't want the top panel since I had kiba.

But here's the problem. About 10 secs after I log in, Kiba (and the rest of X, I think) freezes. I can only press Control+Alt+Backspace to log out. Since I have no gnome-panel, (or I don't know how) I can't shut Kiba down and reopen it.

Is there any file of the session settings? I can load Ubuntu in recovery mode with root, but I don't know how to access my account (daniel) session settings trough root.

---

### Post by OptikKnight on 2008-03-20
spdaniel91,

You can find a lot of session settings in your home directory using this command:

```
find ~/ -iname *session*
```

This will produce a (potentially long) list of files. I experience session errors occasionally due to some Nautilus quirks, so I find the session files for nautilus (they include 'nautilus' in the path in the list) and delete them. This resets back to a "blank"  session. You'll need to identify the appropriate session file (probably not for Nautilus) and remove it. You might also consider backing it up first.

Note that this may not actually be the cause of your problem. Hopefully it's this simple, but having never worked with Kiba I can't guarantee that this is your solution.

Good luck, and feel free to post further questions.

 -- Sam

---

