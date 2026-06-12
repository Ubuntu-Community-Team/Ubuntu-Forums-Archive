---
title: "free command. How to get meaningful values"
date: 2019-05-04
forum: General Help
---

### Post by donbcilly on 2019-05-04
[FONT=arial]I'm trying to get some memory values into a graph.[/FONT]
If I use free I get:

```
~$ free
              total        used          free        shared    buff/cache   available
Mem:        7'864'952     1'944'612      122'524      241'176     5'797'816     5'373'284

```
[FONT=arial]('s added by me for easy reading).

Now, if I have roughly 8G of RAM and I used 2G, I should have roughly 6G free, not 0.1...
Which I guess is under "available".
So what is "free"? And "used"?
:-?

[/FONT]

---

### Post by oldfred on 2019-05-04
Man is always your friend for details of a command.
man free

System normally caches applications in RAM as you often reuse something. It only releases that RAM if oldest and space needed for something newer.
Linux ate my RAM! -  memory use cache
[http://www.linuxatemyram.com/](http://www.linuxatemyram.com/)
Difference between Details screen on RAM and free command
[http://askubuntu.com/questions/743649/new-16gb-of-ram-installed-yet-i-see-15-3-on-my-system-why?noredirect=1#comment1106622_743649](http://askubuntu.com/questions/743649/new-16gb-of-ram-installed-yet-i-see-15-3-on-my-system-why?noredirect=1#comment1106622_743649) &
[https://askubuntu.com/questions/184217/why-most-people-recommend-to-reduce-swappiness-to-10-20/184221#184221](https://askubuntu.com/questions/184217/why-most-people-recommend-to-reduce-swappiness-to-10-20/184221#184221)

---

### Post by sisco311 on 2019-05-04
Free RAM is wasted RAM:
[https://www.howtogeek.com/128130/htg-explains-why-its-good-that-your-computers-ram-is-full/](https://www.howtogeek.com/128130/htg-explains-why-its-good-that-your-computers-ram-is-full/)

EDIT: ninja'd by oldfred :)

---

### Post by donbcilly on 2019-05-04
Thank you. Very informative.
So if I wanted to display info (say in a conky monitor) :-\" on how much memory Is ***actually*** available - as in before the system starts to use swap - I use total-available (to get used), and get a meaningful value, right?

---

### Post by CatKiller on 2019-05-04
The conky object **memeasyfree** is probably what you're looking for.

---

### Post by donbcilly on 2019-05-04
Yes. Cool. Thanks, Gives a very sensible value.
For the graph, I'm using ${execbar free -m | awk '(etc.)} so am I correct in thinking that if I use total-available I can get a percentage of the actual usable RAM?
I mean a value that is actually useful in estimating performance.

[EDIT] BTW, the conky I'm making [is this]("https://www.pling.com/p/1302912/").

---

### Post by donbcilly on 2019-05-05
Well, all I had to do is believe the docs and experiment a little.

The conky code:
```
${font sans-serif:style=Bold:size=7.5}${goto 4}${voffset 2}Ram:          used of               (              free)
${color 8de7f4}${font sans-serif:style=Bold:size=8}${goto 36}${voffset -13}${execpi 40 free -m | awk '/Mem:/ { print int( $7/$2*10 ) }'}%
${color 8de7f4}${font sans-serif:size=8}${goto 108}${voffset -13}${execpi 40 free -m | awk '/Mem:/ {printf("%.2f\n",$2/1024)}'}Gb
${color 8de7f4}${font sans-serif:size=8}${goto 156}${voffset -13}${execpi 40 free -m | awk '/Mem:/ {printf("%.2f\n",$7/1024)}'}Gb
${voffset 4}${color 8de7f4}${execbar free -m | awk '/Mem:/ { print $7/$2*10 }'}${color}
```

Produces this:

[IMG]https://i.ibb.co/L6TGXj1/rambar.png&quot;[/IMG]

Which looks OK.
So, thanks to you all, I not only have a monitor reporting useful values, but also quite a bit more RAM :)

---

### Post by donbcilly on 2019-05-07
Minor correction (in case someone wants to use the code)... I pasted the wrong line - from some testing.
The line that actually prints the "more meaningful" values is

```
free -m | awk '/Mem:/ { printf int(( $2-$7 ) /$2*100) }'
```
(which gives - at that moment) 23% used - and conversely 77% free.

Whereas free...

```
              total        used        free      shared  buff/cache   available                    
Mem:           7680        1210        2250         284        4219        5907 
```

reports 2250 free, which is some 30%,

---

