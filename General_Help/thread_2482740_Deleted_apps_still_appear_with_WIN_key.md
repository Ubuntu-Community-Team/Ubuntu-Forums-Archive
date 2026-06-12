---
title: "Deleted apps still appear with WIN key"
date: 2023-01-09
forum: General Help
---

### Post by klundermann on 2023-01-09
Sometimes when I use the WIN key to find an app that I wish to run, apps that I (thought I had) removed appear.  I guess I did not fully remove them.

How can I track these down and fully remove them?

---

### Post by ne29914 on 2023-01-09
Remove the relevant .desktop files. You'll find them in /usr/share/applications and $HOME/.local/share/applications

---

### Post by mIk3_08 on 2023-01-09
> **klundermann said:**
> Sometimes when I use the WIN key to find an app that I wish to run, apps that I (thought I had) removed appear.  I guess I did not fully remove them.
How can I track these down and fully remove them? If the app is installed from snap you can locate the icon from here,
```
ls /var/lib/snapd/desktop/applications/
```
Just find the .desktop file icon from the command above. Regards and cheers.

---

### Post by klundermann on 2023-01-18
Thank you for the suggestions, but after looking in all three locations, I've not been able to find what I'm looking for.  Just in case it's relevant, I'll mention that what I'm trying to remove is a vestige of the tor browser.

---

### Post by ActionParsnip on 2023-01-19
Are they applications you installed using WINE by any chance?

---

### Post by klundermann on 2023-01-26
No -- I've never used WINE.

---

### Post by tea for one on 2023-01-26
> **klundermann said:**
> Just in case it's relevant, I'll mention that what I'm trying to remove is a vestige of the tor browser.
Certainly relevant.
What is the vestige?

Anything to do with tor-browser launcher?
> When you first launch Tor Browser Launcher, it will download TBB from
[https://www.torproject.org/](https://www.torproject.org/) and extract it to ~/.local/share/torbrowser,
and then execute it.
Cache and configuration files will be stored in ~/.cache/torbrowser and
~/.config/torbrowser.

---

### Post by klundermann on 2023-01-29
> **tea for one said:**
> Certainly relevant.
What is the vestige?

Just the appearance of a  tor browser  option when I use the windows key (see attached photo).


> Anything to do with tor-browser launcher?

I would think so, but I have completely removed the directories with names beginning with "tor" from both  .cache  and  .config .

---

