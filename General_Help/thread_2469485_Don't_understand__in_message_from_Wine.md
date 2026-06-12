---
title: "Don't understand \\ in message from Wine"
date: 2021-11-30
forum: General Help
---

### Post by Ralph L on 2021-11-30
Wine mono is messed up on my computer. My backup system flagged it as a file that it couldn't read. So I tried to uninstall it by bringing up Terminal and entering "wine uninstaller" to start the wine program with uninstaller as the parameter. However I got the error message "wine: could not open working directory L"unix\\home\\ralph\\Desktop\\", starting in the Windows directory." I don't even know what this means and google couldn't find anything that helped me. 1. What are the double \\ for? I've never see this. 2 What does the "L" mean? I don't have any directory L. Why does it say unix? That's not a directory that I know about. I have a Bridge (card game) program that runs under wine and it still seems to work, so I guess wine mono is not needed for that.
Any help is appreciated...........

---

### Post by Holger_Gehrke on 2021-11-30
The double '\' are - in this case - a compromise notation between Windows - which uses '\' as a separator for elements in a directory path - and Unix / Linux which uses '\' as an escape character that takes away special meaning from the following character. So '\\' in Wine simply means '\' as far as Windows (programs) are concerned. It says Unix because it means the real file system and not the virtual filesystem that a Windows application will see when running under wine. It says Unix and not Linux because Wine is meant to run under any Unix-like OS on X86 hardware. No idea what the 'L' is supposed to mean, might mean 'Literal' as in it was given that string as a parameter from something and not as a variable.

So it looks to me like it's trying to read or change to the directory '/home/ralph/Desktop/' and failing for some reason and switching to the Windows directory - probably '~/.wine/drive_c/windows/'.

Holger

---

### Post by Ralph L on 2021-11-30
Holger
Thank you very much. That was really informative.

---

