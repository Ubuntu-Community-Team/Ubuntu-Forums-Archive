---
title: "Firefox scrollbar revert to original behaviour?"
date: 2016-05-02
forum: General Help
---

### Post by surferX on 2016-05-02
Using 14.04LTS, my system updated to firefox 46.0, and now the scrollbars no longer scroll one page at time when clicked either side of the button. e.g. clicking below the button shold scroll one page down.

How can I revert to the original behaviour?

Thanks in advance.

---

### Post by vasa1 on 2016-05-02
What you want is called **legacy scrolling** by the GNOME developers: 
Edit or create *~/.config/gtk-3.0/settings.ini* to have *[Settings]* as the first line and *gtk-primary-button-warps-slider=false* on a subsequent line by itself. This works in most gtk3 applications including Firefox but is said not to work in some. Alternatively, right-click instead of left-clicking works in all applications. And, if you want legacy scrolling system-wide, sudo edit */etc/gtk-3.0/settings.ini*.

Whenever you edit *settings.ini*, the change maybe effective only after closing and re-opening Firefox. You may even need to log out and log back in.

---

### Post by surferX on 2016-05-02
Thanks that fixed it,

Quick question why do these changes occur when I am using a LTS release?

Or is something that reset by using the ubuntu setting app, or the unity tweaks?

---

### Post by vasa1 on 2016-05-02
> **surferX said:**
> Thanks that fixed it,

Quick question why do these changes occur when I am using a LTS release?

Or is something that reset by using the ubuntu setting app, or the unity tweaks?

If your problem is solved you can mark it [SOLVED]: see [https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads).

Re. *why do these changes occur when I am using a LTS release?*, that's entirely a decision taken by the Firefox developers. It has nothing to do with Ubuntu or its settings *per se*. Firefox 46 across Linux distros is now gtk3. Up till version 45, Firefox was gtk2.

---

### Post by Mel_Blakey on 2016-05-06
I created a text doc named 'settings.ini' with the following in it:

> [Settings]

gtk-primary-button-warps-slider=false

and saved it to: ***~/.config/gtk-3.0/***

Is this correct as it doesn't work :(

---

### Post by vasa1 on 2016-05-06
> **Mel_Blakey said:**
> ...
Is this correct as it doesn't work :(
That looks correct to me. Which text editor did you use?

Please provide the output of *file $HOME/.config/gtk-3.0/settings.ini*. Did you completely close all Firefox processes and then restart? Firefox?

---

### Post by Mel_Blakey on 2016-05-06
Thanks for quick reply

I used Gedit

> .config/gtk-3.0/settings.ini: ASCII text

I closed firefox & rebooted.

---

### Post by vasa1 on 2016-05-06
I don't know why it isn't working for you :(

---

### Post by Mel_Blakey on 2016-05-06
No probs.....but, thanks for trying!

---

