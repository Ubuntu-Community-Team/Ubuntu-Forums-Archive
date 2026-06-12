---
title: "Unity first search delay time speed up!!"
date: 2014-05-13
forum: General Help
---

### Post by mr-fabio90 on 2014-05-13
Hello everybody, i found a trick to avoid waiting during unity first search.

You just have to:


[LIST=1]
[*]Open terminal 
[*]sudo apt-get install xdotool 
[*]Download the attached script
[*]Make it executable (chmod +x script.sh) 
[*]Copy it to you /usr/bin folder (run on terminal sudo cp script.sh /usr/bin/) 
[*]Open "startup applications" in dash 
[*]Add new startup command 
[*]Chose a name and use this in the command field: /usr/bin/script.sh 
[*]Save and close 
[/LIST]

On reboot your dash is automatically opened and closed at the same time so that everything loads in background. 
NOW when you'll open the dash you'll have it fully loaded and ready to search with out waiting time!!

HAVE FUN!!
[ATTACH]253119[/ATTACH]

---

