---
title: "Middle-click paste random behavior with Firefox and Gnome terminal"
date: 2024-08-29
forum: General Help
---

### Post by maxacc on 2024-08-29
Hi,

I'm using Ubuntu 24.04 with Gnome (Wayland) (fresh install).

I have a very annoying issue with the primary selection / middle-click paste : when I select some text in Firefox and try to paste it with middle-click in gnome-terminal, it randomly works. Either it works as expected ; either it pastes a previous selection.[IMG]https://ubuntuforums.org/attachment.php?attachmentid=294155&stc=1[/IMG]See for example this screencast : [ATTACH]294155[/ATTACH] (I needed to zip the webm because the forum does not accept webm).

I haven't defined the issue well yet. It's not always reproducible and I'm not sure it's only with Firefox and gnome-terminal (although gnome-text-editor is not affected by it).

I would appreciate any help to clarify the issue and maybe get to a point where it's defined precisely enough to warrant a bug report.

Thanks

---

### Post by currentshaft on 2024-08-29
Because middle-click is not a true clipboard, it's a selection buffer.

Why not just use regular clipboard with Control-C/Control-V as intended?

---

### Post by TheFu on 2024-08-29
Clipboards don't work for everyone.  I absolutely hate them. They break things that have worked for 30 yrs.  Keyboards are slow for this specific select/paste workflow. 
Gnome believes is it a good idea: [https://wiki.gnome.org/Initiatives/Wayland/PrimarySelection](https://wiki.gnome.org/Initiatives/Wayland/PrimarySelection)
> Still, many longterm X users have become reliant on this easter egg, and in particular terminal users have a hard time using the awkward Shift-Ctrl-C combination instead (since Ctrl-C is not available in terminals). 

If it isn't working under Wayland, you can switch to X11.

---

### Post by maxacc on 2024-08-30
I've been using Ubuntu for more than 10 years. I have always used the primary selection feature, and for me it's a major productivity boost.

I switched to Xorg and it seems to be working (as I said the behavior is random so it may pop up again at some point). I would prefer to use Wayland though.

It's possible that the issue is caused by some old configuration that I have in ~/.config or $HOME somewhere. I'll have to do some digging.

---

### Post by yannok on 2024-10-01
I face exactly the same problem on a fresh install of Ubuntu 24.04.1 : unpredictable behavior with middle-click paste : sometimes it works, sometimes it pastes a previous entry. I had been using this feature hundreds times a day, this is a terrible regression.

---

### Post by dragonfly41 on 2024-10-01
I don't know if CopyQ might help. It keeps a history of cllpboard actions and you can look back to review your actions in case of glitches. A Clipboard "Wayback Machine".

---

### Post by alexhung2 on 2024-11-03
I opened a bug @ [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/2085634](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/2085634). Hope it will get some attentions if more people report the same issue.

---

