---
title: "the alt + tilde (super) keyboard shortcut issue and ccsm"
date: 2013-12-11
forum: General Help
---

### Post by b_ice99 on 2013-12-11
[http://ubuntuforums.org/showthread.php?t=1863115&page=2](http://ubuntuforums.org/showthread.php?t=1863115&page=2)
(closed thread on the subject)
I followed this thread to install ccsm and try to unbind the key, and unbound several other keys I wanted to use.  I'm not using the same software, it's for binding the key as a hotkey for world of warcraft which I noticed I couldn't do in linux distros like ubuntu and fedora

(quoted from other post)
1) Install the compizconfig-settings-manager package
2) The setting we are all searching for is Desktop -> Ubuntu Unity Plugin -> Switcher
3) Change "Key to flip through windows in the switcher" to something else

Unbinding the key though, isn't the solution.  When you unbind the key like outlined in this other post, you MUST replace it with something or the keybind will remain mapped.  I tested this by unbinding the key entirely / disabling the shortcut in ccsm and when I launched wow again I tried to use alt+tilde only to start 'alt tabbing' through windows.  This usually crashes wow for me.
When I returned to ccsm I tested this out and sure enough it said disabled, but the shortcut was still working.  I re enabled it and **changed it** though to something I didn't use (alt+end) and then re-disabled it.  Alt+end still worked to change windows, even though it was suppose to be disabled, but sure enough alt+tilde was now free to use and worked in wow.

I wanted to try to update the closed thread for anyone who followed it and ended up like me with ccsm open, the keybind disabled and asking 'now what' looking for other keybinds to disable.

---

