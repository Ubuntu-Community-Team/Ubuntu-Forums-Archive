---
title: "Screen/Gnome messed up after disk error"
date: 2008-06-16
forum: General Help
---

### Post by g0nzo on 2008-06-16
Hi!

I had (hope it's gone now) strange problem with my disk - suddenly it became read-only. After restarting the system, it had started to check for errors and broke during this check. I ran fsck manually and it found lots of errors that are supposed to be fixed now.

But when I log in, I get really strange looking Gnome panel - I can't see minimize/maximize/close buttons on windows titlebars, it doesn't display my wallpaper, I don't get icons in the menu, default icons are changed, maximum screen resolution that I can set is 1024x786... 

I tried changing settings, but it seems that setting are ok - it seems that they survived disk failure.

I tried to reinstall gnome with 'sudo apt-get --reinstall intall gnome', but there's no difference.

Any tips for bringning Gnome look back, like it's right after Ubuntu install?

UPDATE:
I removed all gnome related dirs in my home:
rm -rf .gnome .gnome2 .gconf .gconfd .metacity .gnome_private .gnome2_private

And while all icons and setting are now back to defaults, it still looks like crap. It seems that something is broken with my graphics card - I can only set 1024x768 and it seems that only 256 colors are displayed. I got ATI x550 and previously it worked fine (although I couldn't get 3D acceleration to work through proprietary drivers or envyng). 

What packages should I reinstall to fix graphic cards drivers?

---

