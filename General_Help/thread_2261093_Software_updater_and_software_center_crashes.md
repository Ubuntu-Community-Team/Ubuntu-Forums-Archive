---
title: "Software updater and software center crashes"
date: 2015-01-16
forum: General Help
---

### Post by Hvidemose on 2015-01-16
[LEFT][FONT=Liberation Serif, serif]I have these two problems with software updater and software center crashing. It seems to be related. The problems started at the same time, which was just around last software update.[/FONT][/LEFT] [LEFT][FONT=Liberation Serif, serif]When I try to open the software center, either nothing happens, or it gives a error message.[/FONT][/LEFT] [LEFT][FONT=Liberation Serif, serif]The software updater gives me this message unknown source: [/FONT][FONT=Liberation Serif, serif]<class 's[/FONT][FONT=Liberation Serif, serif]ystemError'>(E:[/FONT][FONT=Liberation Serif, serif]Type'”deb' is not known on line 1 in source list[/FONT][FONT=Liberation Serif, serif] /etc/apt/sources.list.[/FONT][FONT=Liberation Serif, serif]d/google.list[/FONT][FONT=Liberation Serif, serif])[/FONT][/LEFT] [LEFT][FONT=Liberation Serif, serif]I have tried to uninstall, and install software center again, but no luck.[/FONT][/LEFT] [LEFT]

 [/LEFT] [LEFT][FONT=Liberation Serif, serif]Can anyone help me, to get these functions to work again?[/FONT]
[/LEFT]

---

### Post by Hvidemose on 2015-01-16
Now I installed the Synaptic. When I open it, i get this error message:
> E: Typen »&#8220;deb« er ukendt på linje 1 i kildelisten /etc/apt/sources.list.d/google.list
E: Listen over kilder kunne ikke læses.
Gå til arkiv-dialogen for at rette problemet.
E: _cache->open() failed, please report.

---

### Post by Holger_Gehrke on 2015-01-16
There's (obviouly) something wrong with the file '/etc/apt/sources.list.d/google.list' From the error-messages I would guess that you've edited it in the past and copy-and-pasted an extra '"' or two into the file.

---

### Post by Hvidemose on 2015-01-16
[LEFT]Ok, I found the fix in different locations.

[/LEFT]
 [LEFT]Firs I deleted the /etc/apt/sources.list.d/google.list:
[/LEFT]
```
sudo rm -rvf /var/lib/apt/lists/*
sudo apt-get update sudo shutdown -r now
```

And then i uninstalled, and reinstalled Software center:
```
sudo apt-get remove software-center
sudo apt-get install software-center
```

---

### Post by ian-weisser on 2015-01-16
That's quite a sledgehammer approach to fix a typo in one easily-edited text file.
I would have tried Holger_Gehrke's approach.[**[COLOR=#000000][/COLOR]**]("http://ubuntuforums.org/member.php?u=1961578")[**[COLOR=#000000][/COLOR]**]("http://ubuntuforums.org/member.php?u=1961578")

---

