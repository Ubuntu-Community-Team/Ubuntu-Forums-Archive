---
title: "wine run problem"
date: 2005-09-21
forum: General Help
---

### Post by peterthewolf on 2005-09-21
I have a small program called WinWordFind that runs on windows. Basically you key some letters in to a screen and the program produces some matches from a text file.
I have written the following script to call the program

#!/bin/sh

# winword

cd "/home/peter/.wine.0509202245/fake_windows/winword"
wine WinWordFind
exit 0  

I have chmod -x so that only need to key ./winword. Works fine!!

I then set an icon on the desktop with the following in the launcher command

/home/peter/./winword

When you double click the icon the program runs but the window footprint is about half and there is no text. If you key some letters in and press where you know the search key is, then the program goes through the motions and presents the result  but is blank through no text. If you press the button which you know is the exit then it exits properly.

Any suggestions.

---

### Post by peterthewolf on 2005-09-21
I should of mentioned that I put the script in /home/peter

---

### Post by peterthewolf on 2005-09-22
Forget it

I had not run winetools and installed arial fonts on doing this all OK

Wonder which fonts it used from the command line?

---

