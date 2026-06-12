---
title: "keeping terminal window open after a launcher command exits"
date: 2005-05-12
forum: General Help
---

### Post by 23meg on 2005-05-12
what i'd like to do is create a launcher with the "run in terminal" option that will display info on a terminal (can be gnome-terminal or Eterm). in order the see the info i need the terminal window to stay open until i close it, but since the commands i use lead to an "exit", the terminal window shuts down the instant it appears. how can i make it "stay"?

---

### Post by nad on 2005-05-12
Gconf->apps->gnome-terminal->profiles->Default->exit_action close | restart .

Restart really does restart. Close....

Looks like an option to keep the terminal open would be nice. Suggest it as a wishlist item.

---

### Post by 23meg on 2005-05-12
hmm, there must be a command line option for gnome-terminal to launch it with a specific profile. i can combine that with this gconf trick to do what i want, maybe? i'll check out!

edit: oops, there's an option in profiles/edit/title and command that controls that value in gconf anyway.

---

### Post by 23meg on 2005-05-12
got it. the command line should be like

```
gnome-terminal --window-with-profile=[your profile name] -e=[your commands] 
```

where [your profile name] is the name of a profile you've created that has the "keep terminal window open" option selected, or has the gconf line in nad's post.

however, gnome-terminal seems to launch very slowly with these options. it takes about 5 seconds to display the initial window, 3 more to switch to the profile, and about 3 more before starting to execute commands. a bug, maybe? can anyone replicate this?

---

### Post by Sam on 2005-05-13
There is an another way. You can append "read" at the end of the script you run to have the user press the enter key for exiting.

E.g.
```
#! /bin/sh

<your commands go here>

read
```

---

### Post by 23meg on 2005-05-14
alright, that works a lot better. for example, to view disk usage in local drives i just launch this script now:

```
#!/bin/bash
df -l
read
```

and gnome-terminal instantly pops up with the info, and disappears the instant i hit enter. thanks.

---

