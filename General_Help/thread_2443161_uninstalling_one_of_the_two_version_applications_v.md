---
title: "uninstalling one of the two version applications via terminal"
date: 2020-05-12
forum: General Help
---

### Post by tojonukokhadush on 2020-05-12
okay, here is the confusion. i had zoom app installed via software centre. someday it asked for the update and this was .deb file downloaded from the official site of zoom this time and i installed it via terminal.
Now, when i press the super key and type zoom. the confusion arises here. i have two zoom app shown. darn! i want to remove the older version of zoom and i want to do that VIA TERMINAL! thats the condition here, via terminal. now somebody help me how do i uninstall the particular older version only of the app via commandline. its just because i want to learn to play with terminal.

---

### Post by dino99 on 2020-05-12
Such request has already been asked many times, like: [https://askubuntu.com/questions/433609/how-can-i-list-all-applications-installed-in-my-system](https://askubuntu.com/questions/433609/how-can-i-list-all-applications-installed-in-my-system)

---

### Post by ajgreeny on 2020-05-12
Command 
```
snap list 
```
will show you the version of that and
```
dpkg -l zoom
```
should show you the version installed as a .deb.

I expect the snap will be version 5 and the .deb 3 unless it has been updated recently.

Keep the snap if it's  working well for you and remove the .deb version with
```
sudo apt remove zoom
```

This assumes the package is called by that name.

---

### Post by tojonukokhadush on 2020-05-12
thank you [[COLOR=#C61919]ajgreeny[/COLOR]]("https://ubuntuforums.org/member.php?u=27747")[COLOR=#000000] [/COLOR], this was what i needed exactly. the versions were 5.3 in snap and 5.4 in deb. the application directed me to update today only and that was how  i ended downloading .deb file.anyway its solved now. help appreciated.

---

### Post by ajgreeny on 2020-05-13
Ah!
The .deb version has moved on since I tried it about a month ago, then moved to the snap; it was at that time version 3.

---

