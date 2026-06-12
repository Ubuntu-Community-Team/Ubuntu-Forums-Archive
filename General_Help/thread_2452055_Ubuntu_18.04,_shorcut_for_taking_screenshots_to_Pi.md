---
title: "Ubuntu 18.04, shorcut for taking screenshots to Pictures folder/clipboard not working"
date: 2020-10-15
forum: General Help
---

### Post by thosecars822 on 2020-10-15
Hello

The following first two shortcuts work fine.[B]
PrtSc[/B] &#8211; *Save a screenshot of the entire screen to the &#8220;Pictures&#8221; directory.*
**Alt + PrtSc**  &#8211; *Save a screenshot of the current window to Pictures*.

Nonetheless for some reason the following 4 shortcuts do not seem to work.[B]

**Shift + PrtSc** &#8211; [/B][I]Save a screenshot of a specific region to Pictures.
*I do not see this command places anything on the pictures folder.*

[/I]I also tried the next 3 shortcuts and I tried to paste with Ctrl+V on Abiword and nothing gets pasted.[B]
Ctrl + PrtSc[/B] &#8211; *Should copy the screenshot of the entire screen to the clipboard.*
**Shift + Ctrl + PrtSc** &#8211; *Should copy the screenshot of a specific region to the clipboard.*
**Ctrl + Alt + PrtSc** &#8211; [I]Should copy the screenshot of the current window to the clipboard.
[/I]
Do you have any idea about what I could be doing wrong?

Thanks in advance

---

### Post by GhX6GZMB on 2020-10-15
The shell commands for doing this kind of thing are "scrot" and "xclip". The first takes the screenshot, the second places it on the clipboard.
I made my own shortcut keys using these commands:

**sh -c 'scrot -o /tmp/clip_$(id -u) -e 'xclip -selection clipboard -t image/png < $f''**    (full screen)
**sh -c 'scrot -o -u /tmp/clip_$(id -u) -e 'xclip -selection clipboard -t image/png < $f''**    (active window)
**sh -c 'scrot -o -s -f /tmp/clip_$(id -u) -e 'xclip -selection clipboard -t image/png < $f''**    (screen area)

The screenshots will be copied to the /tmp directory and subsequently be available on the clipboard.

Unfortunately, there are ambiguities in the man pages for "scrot" concerning the -o and -f options (though they work). Use this one to be certain:
[https://manpages.debian.org/testing/scrot/scrot.1.en.html](https://manpages.debian.org/testing/scrot/scrot.1.en.html)

Cheers.

---

