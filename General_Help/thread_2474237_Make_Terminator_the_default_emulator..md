---
title: "Make Terminator the default emulator."
date: 2022-04-24
forum: General Help
---

### Post by Hewjr100 on 2022-04-24
I have tried some ideas from  a google search, but they do not work.  Anyone know better.

Henry

---

### Post by #&amp;thj^% on 2022-04-24
I'm in the dark on what you've tried:
```
gsettings set org.gnome.desktop.default-applications.terminal exec /usr/bin/terminator
gsettings set org.gnome.desktop.default-applications.terminal exec-arg "-x"
```

---

### Post by dragonfly41 on 2022-04-24
I use yakuake

[https://www.slant.co/versus/2444/2449/~terminator_vs_yakuake](https://www.slant.co/versus/2444/2449/~terminator_vs_yakuake)

---

### Post by Hewjr100 on 2022-04-24
This is what I tried,thought is was straight forward enough:

[https://ubuntuhandbook.org/index.php/2022/03/change-default-terminal-ubuntu/](https://ubuntuhandbook.org/index.php/2022/03/change-default-terminal-ubuntu/)

Henry

---

### Post by #&amp;thj^% on 2022-04-24
Providing you want Terminator and have it installed already:
```
sudo update-alternatives --config x-terminal-emulator
```
 
```
There are 7 choices for the alternative x-terminal-emulator (providing /usr/bin/x-terminal-emulator).

  Selection    Path                             Priority   Status
------------------------------------------------------------
* 0            /usr/bin/terminator               50        auto mode
  1            /usr/bin/gnome-terminal.wrapper   40        manual mode
  2            /usr/bin/koi8rxterm               20        manual mode
  3            /usr/bin/lxterm                   30        manual mode
  [COLOR="#FF0000"]4            /usr/bin/terminator               50        manual mode[/COLOR]
  5            /usr/bin/uxterm                   20        manual mode
  6            /usr/bin/xfce4-terminal.wrapper   40        manual mode
  7            /usr/bin/xterm                    20        manual mode

Press <enter> to keep the current choice[*], or type selection number: 
```
my case i selected 4
and when i do [Ctrl] + [Alt] + [t]
terminator opens as expected

---

### Post by Hewjr100 on 2022-04-24
1fallen, no luck for me manual mode was #2 but terminator does not open.  Is there a way to add it to the context menu of Nuatilus?

Henry

---

### Post by dragonfly41 on 2022-04-25
Try this extension I just found by searching  (although I favour using Krusader instead of Nautllus)

[https://github.com/mwahlroos/Nautiterm](https://github.com/mwahlroos/Nautiterm)

---

### Post by ActionParsnip on 2022-04-25
> **dragonfly41 said:**
> I use yakuake

[https://www.slant.co/versus/2444/2449/~terminator_vs_yakuake](https://www.slant.co/versus/2444/2449/~terminator_vs_yakuake)

Yakuake is fab. I use tilda myself, super lightweight :)

---

### Post by vanadium on 2022-04-25
> **dragonfly41 said:**
> Try this extension I just found by searching  (although I favour using Krusader instead of Nautllus)

[https://github.com/mwahlroos/Nautiterm](https://github.com/mwahlroos/Nautiterm)

I use [nautilus-open-terminal](https://github.com/Stunkymonkey/nautilus-open-any-terminal). As a nice extra bonus, it allows to set a shortcut key for use within nautilus to "Open terminal here". (Actually, I use that extension only for this functionality).

To remove the now superfluous default entry in the right-click menu, remove "nautilus-extension-gnome-terminal".

---

### Post by #&amp;thj^% on 2022-04-25
> **vanadium said:**
> I use [nautilus-open-terminal](https://github.com/Stunkymonkey/nautilus-open-any-terminal). As a nice extra bonus, it allows to set a shortcut key for use within nautilus to "Open terminal here". (Actually, I use that extension only for this functionality).

To remove the now superfluous default entry in the right-click menu, remove "nautilus-extension-gnome-terminal".

+1
No third party package(s) needed
I don't use nautilus, i use nemo.
Write your own script and put it to: ~/.local/share/nautilus/scripts/

An example might be more clear:
```

#!/bin/bash
code -n ${NAUTILUS_SCRIPT_SELECTED_FILE_PATHS}
```
give proper permissions:
```
chmod 744 OpenByterminator.sh
```
Finally, copy/move this file to ~/.local/share/nautilus/scripts/

The Context Menu should be ready to use.

this one was kind of fun as well: [https://www.omgubuntu.co.uk/2020/07/open-folder-in-terminal-ubuntu-plugin](https://www.omgubuntu.co.uk/2020/07/open-folder-in-terminal-ubuntu-plugin)
vanadium had already pointed out.

---

### Post by dragonfly41 on 2022-04-25
Again, elaborating on my personal preference for Krusader (I know it comes with KDE baggage) but I can right click on any file
and I can Open With ..  or run a Custom UserAction on the selected filepath. An example might be running through pandoc.
It is very easy using Krusader as the project manager.  There is a builtin Terminal.
Many custom useractions can be built. That is why I adopted it rather than Nautilus.
Even Terminator can be configured.

---

### Post by Hewjr100 on 2022-04-25
1fallen we are good.  Everybody, thanks for your input.  Someday I might be as good as all of you at this.

Henry

---

