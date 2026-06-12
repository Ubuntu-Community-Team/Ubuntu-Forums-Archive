---
title: "How can I kill the Caps Lock in 14.04?"
date: 2014-06-27
forum: General Help
---

### Post by egeezer on 2014-06-27
I had one technique to kill the caps lock with xmodmap and another that used a script in /usr/share/X11/xorg.conf.d.  They have worked on distros up through 13.10, but neither is effective in 14.04.

I'm currently running Ubuntu with Xcfe on top.  Anyone have an idea how to do it?

(I'm still fuming that the old keyboard options of 10.04 were abandoned!)

Thanks in advance for any help!

---

### Post by buzzingrobot on 2014-06-27
Use the keymapping tool in XFCE settings to map the key to nothing.

---

### Post by egeezer on 2014-06-27
Mystery#2: Now, 4 hours later, my xmodmap tweak just started to work, though  it doesn't persist despite being in Application Autostart.  The script method is still  powerless, however, so I'm still open to suggestions.

---

### Post by egeezer on 2014-06-27
Sorry, buzzingrobot, my second post apparently ovelapped yours.  With the Xfce desktop on top of Ubuntu, there is no access to such keymapping in the Settings Manager.  And the only setting in the Settings Editor keyboard-layout is the default XkbDisable, which was checked.  I unchecked it, tried again, and still no result.  I fear I would have to be running the pure Xubuntu to do the script trick (yes, that script did work on pure Xubuntu 14.04).

I will probably reinstall this setup as pure Xubuntu; I had set it up to try the MATE desktop, didn't like it, and added the Xfce4 desktop.  Pretty much of a mess right now anyway, with all that on top.

---

### Post by egeezer on 2014-06-27
Aha! buzzingrobot, I saw your reply to the **Permanently remapping capslock** article, and checked your dconf method.  I'm pretty sure that will work for me, and my BIG thanks for it!  I'll give it a shot the next time I log out or restart - for now, the xmodmap tweak is keeping me safe.

---

