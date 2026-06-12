---
title: "Firefox 2.0 strange font sizes"
date: 2007-10-23
forum: General Help
---

### Post by pyrofreek_9 on 2007-10-23
Hello everyone!
I've been using Ubuntu for awhile now, I'm not new to Linux, so I can generally fix problems that occur, but since installing Gutsy (it was a clean install, not an upgrade), I've been having issues with Firefox. The interface font is larger than all the other fonts on the system, and it causes some issues in dialogs, etc. It only happens in firefox 2.0, v3 works fine, but many of the extensions that I use don't work properly in v3. So far, I've tried purging firefox, and all related packages (gnome-support, ubufox, etc) and reinstalling them, I've tried installing firefox directly from mozilla.org, and it does the same thing from there as well. I've removed my firefox profile directory completely and reopened firefox (to force it to create a new one), and it still does the same thing. I've tried changing dpi on my system, and the dpi option in about:config in firefox, and nothing is working!
I think it's probably something simple, but I can't figure it out, so I'm wondering if anyone has any more ideas?

---

### Post by NilsE on 2007-10-23
I was just wrestling with this myself.

I ended up setting the DPI in FF about:config back to -1 (uses system DPI)

Changed the font selections in FF preferences to not allow sites to set fonts.

Set the fonts to ones I liked and kind of balanced between the sites but then went back to the default fonts and set all the sizes to 10. I use 10 on the desktop with the same fonts.

Still tinkering but atleast now the big fonts came down and the minimum is reasonable on the eyes.

I am interested in hearing if there is a better fix.

---

### Post by UK-Wobbie on 2007-10-23
> **pyrofreek_9 said:**
> Hello everyone!
I've been using Ubuntu for awhile now, I'm not new to Linux, so I can generally fix problems that occur, but since installing Gutsy (it was a clean install, not an upgrade), I've been having issues with Firefox. The interface font is larger than all the other fonts on the system, and it causes some issues in dialogs, etc. It only happens in firefox 2.0, v3 works fine, but many of the extensions that I use don't work properly in v3. So far, I've tried purging firefox, and all related packages (gnome-support, ubufox, etc) and reinstalling them, I've tried installing firefox directly from mozilla.org, and it does the same thing from there as well. I've removed my firefox profile directory completely and reopened firefox (to force it to create a new one), and it still does the same thing. I've tried changing dpi on my system, and the dpi option in about:config in firefox, and nothing is working!
I think it's probably something simple, but I can't figure it out, so I'm wondering if anyone has any more ideas?

Have you had a go going to "View" Then to "Text size"?

May i ask how did you get your bottom toolbar like that? :confused:

---

### Post by pyrofreek_9 on 2007-10-23
I actually did figure out a way to fix this. I just added a directory in my firefox profile in ~/.mozilla/firefox/[random_chars].default/ called chrome, and added a file called userChrome.css to that, and just put in this:
```
* {
    font-size: 13px
}
```
So far, it seems okay

And UK-Wobbie, its called avant window navigator, you can find out about it here: [http://wiki.awn-project.org/index.php?title=Main_Page]("http://wiki.awn-project.org/index.php?title=Main_Page")

---

