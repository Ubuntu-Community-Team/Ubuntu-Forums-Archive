---
title: "Unremember login application settings"
date: 2008-04-26
forum: General Help
---

### Post by natirips on 2008-04-26
I had my computer automatically remember applications being run just prior to every log out, but now I wan't do unremember them. How do I do that?
I only have options to remember currently open applications or turn on/off (with the checkbox) automatic remembering at logout.

It's Ubuntu 8.04.

---

### Post by Zorael on 2008-04-26
I'm confused. Isn't toggling it off what you want to do?

To remove the saved session manually, I think you can delete the ~/.gnome2/session file. I don't run Gnome myself so I can't say for sure.

---

### Post by natirips on 2008-04-26
> **Zorael said:**
> I'm confused. Isn't toggling it off what you want to do?
When I toggled the option off, it just kept running the same programs at every startup, always the same set - the last saved one.
> **Zorael said:**
> To remove the saved session manually, I think you can delete the ~/.gnome2/session file. I don't run Gnome myself so I can't say for sure.

Thanks. I opened the file with gedit and removed a few lines, now it doesn't load all the windows that I had opened before the last time I logged off with the auto-remembering option on.

---

### Post by Zorael on 2008-04-26
At least it worked. :>

I found something on launchpad, looks related. So at least developers know about it.
[https://bugs.launchpad.net/gnome-session/+bug/34321](https://bugs.launchpad.net/gnome-session/+bug/34321)


edit: Might want to tag thread as solved.

---

### Post by natirips on 2008-04-26
This wasn't the issue in my case, I thought of this rahter as a missing feature, I just couldn't find a (simple) way to clear my remembered programs list.

---

