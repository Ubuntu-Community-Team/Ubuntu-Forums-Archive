---
title: "Windows/Super keyboard shortcuts - MULTIMEDIA!"
date: 2007-11-14
forum: General Help
---

### Post by denisesballs on 2007-11-14
I've seen this all over the place, and found a few workarounds but not for this issue specifically. In Gnome Keyboard Shortcuts you can't use the WIndows/Super key plus another key in combination. It doesn't act like a "modifier" like it does in KDE apparently. So I found a workaround for some of the issues [here]("http://ubuntuforums.org/showpost.php?p=3290670&postcount=5"). 

That workaround does work for some shortcuts where it make the Windows/Super key called "Mod4", however it doesn't work for Gnome multimedia shortcuts like Play, Pause, Next Track etc. What my goal here is to make Rhythmbox or other Gnome players use the same keybindings as like Amarok, so Super+C for Pause, Super+B for next track etc. Has anyone figured out how to do this? Doesn't it seem silly not to be able to use the Windows/Super key for shortcuts since it does nothing else in Linux???

---

### Post by denisesballs on 2007-11-16
bumpity bump please

---

### Post by bingoUV on 2007-11-16
I have managed to use same shortcuts for rhythmbox and amarok. I have beryl running, so I can define keyboard shortcuts to my own shell scripts. The script that pauses, checks whether rhythmbox or amarok is running. Accordingly it issues a signal to them (amarok --play-pause or rhythmbox --play-pause or something like these). Similarly for next track, stop etc.

---

