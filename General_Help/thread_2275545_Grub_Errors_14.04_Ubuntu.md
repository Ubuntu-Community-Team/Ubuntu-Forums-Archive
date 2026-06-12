---
title: "Grub Errors 14.04 Ubuntu"
date: 2015-04-27
forum: General Help
---

### Post by allen2 on 2015-04-27
Dunno if this is related - I was having AMD black-screen display issues when I updated the kernel, so I used grub customizer to set the default boot to a kernel that functioned.

I've tried reinstalling grub (via [http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)).

I used the purge and reinstall method.  I can still boot into my system :p so I didn't need to chroot.  I can't select any of the other bootup options though.

Upon update-grub I'm getting a syntax error in line 608.   Opened the file in gedit and I see line 608 as:

```
function gfxmode {    set gfxpayload="${1}"
    if [ "${1}" = "keep" ]; then
        set vt_handoff=vt.handoff=7
    else
        set vt_handoff=
    fi
}
```

I made a pastebin of the entire grub.cfg.new (bash syntax highlighting) if it's easier.  Random guess say's the above function didn't use proper ending syntax (happened a lot in my basic coding classes; i did not manually alter grub config files).  Or perhaps because set vt_handoff= is blank afterward.
[http://pastebin.com/0QuMnPzS](http://pastebin.com/0QuMnPzS)

**Update:  **I think I got it.  It was the set vt_handoff= was blank.  After re-reading the code, I searched the block of code and found this:
[https://answers.launchpad.net/grub-customizer/+question/244345](https://answers.launchpad.net/grub-customizer/+question/244345)
> [COLOR=#333333][FONT=Ubuntu]Here's your solution:[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu] - click "Affichage" or "View" -> "Show Placeholders"[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu] - then look at the submenu named "Versions précédentes". There should be an entry namend "(script du code)".[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu] - move it to the top of the list (or at least out of the submenu)[/FONT][/COLOR]

So the error was indeed caused by Grub-Customizer.

---

