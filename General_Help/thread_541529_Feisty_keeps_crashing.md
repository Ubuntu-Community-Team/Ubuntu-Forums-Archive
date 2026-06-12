---
title: "Feisty keeps crashing"
date: 2007-09-02
forum: General Help
---

### Post by darkenemy on 2007-09-02
i was recently changing the pixle length on the top toolbar in feisty, and i accidently made it really big (50 pixels or so) and it crashed my session. now when i try to log back in, i am allowed to go only as far as the main log in screen (where you can pick sessions and so forth). as soon as i log in, after about 10 seconds it crashes, bringing me back to the main log in screen, where the process seems repeat itself. can anyone help me fix this? im quite new and have had much difficulty with this.

---

### Post by tzulberti on 2007-09-02
You could delete you home gnome folder: /home/username/.gnome loggin from console as the user, and "rm -rf .gnome". You could also change names, using "mv .gnome .gnome-backup". Then try loggin to gnome. It should loggin into the default configuration.

---

### Post by darkenemy on 2007-09-02
nope-none of that made a difference.  every so often, when i try logging in, right after it crashes, for just a split second (barely enough to read anything), a page with black background and white text appears.  one of these times i was able to make out that i said something about my alsa drivers, for midi stuff.  is it possible alsa needs to be disabled or uninstalled?  the commands you gave me seemed to do nothing.  its possible i did something wrong, im not quite sure where the console is....sad to say... but i did try it in the terminal session.  if there is a way to delete my settings for my desktop, maybe that will fix it?

---

### Post by darkenemy on 2007-09-03
*ok, so maybe i am missing this piece of the puzzle.  how [I]exactly* do i delete my home folder? do i log into the failsafe terminal session? i have already tried playing with the 
"userdel" command to see if i can delete my user, but at no luck. is there a way to create another user and just transfer all my actual files to that one?

---

### Post by mckryptyk on 2007-09-04
Do not delete anything until you try this.

In your failsafe terminal type this:

```
gconf-editor
```

go to Apps --> Panel ---> Toplevels ---- > Top_panel_screen

double click on size and change the number to 24.

File ---> Quit

Restart Gnome session.

Cheers.

---

