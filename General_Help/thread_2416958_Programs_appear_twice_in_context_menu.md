---
title: "Programs appear twice in context menu"
date: 2019-04-18
forum: General Help
---

### Post by RegUB on 2019-04-18
After upgrading 14.04 to 16.04, I find that some programs appear twice in the context menu, i.e. when you right-click on a file to get the 'Open With...' submenu. See the attached screen shot, where gedit appears twice. It's not a showstopper, but I'm curious to know the reason. Can it be fixed? 

I wondered if it might be because an alternative version of the same program had been installed, but that's not the case - both menu options open the same version of the program.
[ATTACH=CONFIG]283048[/ATTACH]

---

### Post by #&amp;thj^% on 2019-04-18
This list gets created by analyzing .desktop files located at:
```

/usr/share/applications
~/.local/share/applications
```

There might be more than one usecase per application in this example, take for example the media player banshee which has three .desktop files by default:
```

$ ls -1 /usr/share/applications/banshee*
/usr/share/applications/banshee-1-audiocd.desktop
/usr/share/applications/banshee-1.desktop
/usr/share/applications/banshee-1-media-player.desktop

```
The only difference between those files is the starting parameter and the MimeType list.
```

    banshee-1.desktop: General media files
    banshee-1-audiocd.desktop: Audio CD's
    banshee-1-media-player.desktop Audio player (Also used by rhythmbox, vlc, and others)
```

So we have three 'Banshee Media Player' in the 'Open with' list (and maybe also in the 'Main Menu').

The other way of filling this space is by creating personal .desktop files in ~/.local/share/applications. Either manually or by using a tool. alacarte (or right-click on 'Main Menu' -> 'Edit Menu') is one of those.

Every time you create or move an application within alacarte, a new .desktop file gets placed inside ~/.local/share/applications. Disabling an application will "remove" it from the 'Main Menu', but not from the 'Open with' list.
But the 'Delete' button does, by creating a identical copy from /usr/share/applications into ~/.local/share/applications and adding Hidden=true to the .desktop file, thus "overwriting" the system-wide inherited values.

Deleting two of those entries from alacarte results in:
```

$ ls -1 ~/.local/share/applications/banshee*
/home/user/.local/share/applications/banshee-1-audiocd.desktop
/home/user/.local/share/applications/banshee-1-media-player.desktop

```
Removing any entries from ~/.local/share/applications will reverse to the preexisting state (three banshee items).
if you really don't have any duplicates in those two folders, try removing any duplicates from alacarte or playing with the Hidden=true option in the corresponding .desktop files.
**In other words, If you look in "~/.local/share/applications" and "/usr/share/applications" you can remove duplicates from those two places.**
Sorry this was long in the tooth but this information is needed here to make the correct choice.

---

### Post by RegUB on 2019-04-18
Thanks for taking the time to write such a comprehensive and very helpful reply. There was only one .desktop file, but were two entries showing in alacarte, one of which was disabled, so I deleted it which has fixed the problem.

---

### Post by #&amp;thj^% on 2019-04-18
Thanks for the kind words, and when satisfied with outcome could you mark this as solved, as this topic crops up from time to time and may help others when searching for a solution.
Kind regards

---

