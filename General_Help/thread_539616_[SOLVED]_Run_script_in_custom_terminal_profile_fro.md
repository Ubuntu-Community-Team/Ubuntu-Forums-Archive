---
title: "[SOLVED] Run script in custom terminal profile from main menu"
date: 2007-08-31
forum: General Help
---

### Post by dje on 2007-08-31
I have a backup script which i made a launcher for in Applications >> System tools. In the launcher properties i selected 'Application in terminal' but this only launches it in the default terminal profile. Is it possible to make the script launch in a custom profile, thanks in advance

---

### Post by dje on 2007-09-02
Solved:

I had to change the launcher command to: gnome-terminal --window-with-profile=WHICHEVER PROFILE YOU WANT

I also had to change it to 'Application' instead of 'Application in terminal'

Next open a terminal and go Edit >> Profiles.. and select the profile you put in the above command and click edit. Go to 'Title and Command' and at the bottom tick 'Run a custom command instead of my shell', below that enter the command you wish to execute when the terminal opens.

---

