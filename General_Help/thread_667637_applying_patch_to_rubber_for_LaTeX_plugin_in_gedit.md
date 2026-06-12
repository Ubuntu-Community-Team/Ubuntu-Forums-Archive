---
title: "applying patch to rubber for LaTeX plugin in gedit?"
date: 2008-01-14
forum: General Help
---

### Post by mental_u on 2008-01-14
i'm fairly new to ubuntu, and i've been trying to set up the gedit latex plugin to take over from my bad old days of using winshell.  everything appears to be in working order, except that if there are any spaces in the path or filename to the .tex file that i'm compiling, the rubber crashes.  on gnome live, there is a patch for the rubber that does compilation ([http://live.gnome.org/Gedit/LaTeXPlugin/FAQ](http://live.gnome.org/Gedit/LaTeXPlugin/FAQ)), but i cannot figure out how to apply it.  anyone out there know how one applies these things?

---

### Post by Juffo-Wup on 2008-01-14
It seems to me (sorry, I don't know for sure :-?) that you would have to apply the patch by doing something like the following: 

[LIST=1]
[*] Open up a terminal.
[*] Copy the patch file to the directory where the Python source code is located.
```
sudo cp /path/to/the/patch/rubber-1.1-spaces.patch /usr/share/rubber/rubber/rules/latex/
```
[*] Go to said directory.
```
cd /usr/share/rubber/rubber/rules/latex/ 
```
[*] Install the 'patch' utility if you don't have it already.
```
sudo apt-get install patch
```
[*] Use said program to apply the patch.
```
sudo patch -b < rubber-1.1-spaces.patch
```
Which will also create a backup of the patched file.
[/LIST]

And I *hope* that helps you, because I just learned of the patch utility :D

---

