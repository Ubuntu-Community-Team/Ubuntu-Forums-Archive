---
title: "cairo-clock on startup"
date: 2019-01-09
forum: General Help
---

### Post by frankdn01 on 2019-01-09
Having trouble configuring macslow's cairo-clock on startup.  If started from the startup folder, I get this (image borrowed from another user [thanks!]):

[ATTACH=CONFIG]282159[/ATTACH]


I attempted to fix this by starting it from a script instead.  The command line I'm using is:

nohup cairo-clock -t radium -x 1200 -d -o -i -w 127 -g 127 2> /dev/null &

Which, while it does start the clock, ignores all the argv's.  All options are set to their defaults.

And and all hints much appreciated!

---

### Post by pn-2019 on 2019-03-29
Hi frankdn01

I solved this problem by using the following command in the (18.04) startup dialog:

[COLOR=#000000][FONT=Ubuntu][SIZE=3]bash -c "sleep 12; /usr/bin/cairo-clock -x 1157 --width 157 --height 157 --theme Bright --sticky --seconds"[/SIZE][SIZE=3]  
[/SIZE][SIZE=1]
[SIZE=2]The idea came from the post seen in:

[https://ubuntuforums.org/showthread.php?t=1341631&p=10536376#post10536376](https://ubuntuforums.org/showthread.php?t=1341631&p=10536376#post10536376)

sleep time seems to be an important factor, in my case 7 (sec. ?) were not enough, of cause the original 5 (seconds) did not work.

good luck!

Peter

[/SIZE][/SIZE][ATTACH=CONFIG]282880[/ATTACH]

PS: [/FONT][/COLOR] sh -c 'sleep 12; cairo-clock -x 1157 --width 157 --height 157 -t Bright -i -s' worked as well according to
[https://www.mankier.com/1/cairo-clock](https://www.mankier.com/1/cairo-clock) [-w & -g instead of --width & --height gave me some trouble]

---

