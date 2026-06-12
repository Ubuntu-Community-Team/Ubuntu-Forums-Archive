---
title: "Nautilus script"
date: 2014-11-26
forum: General Help
---

### Post by luca24 on 2014-11-26
Hey folks. My first forum :)

Im a noob with linux sorry in advance. I have a little question concerning nautilus scripts. I have installed ABGX360 (Little program for xbox 360 isos) and I created a script to help me launching it easily.

My scrypt basicly Launch a command on the terminal.

```
#!/bin/bash
gnome-terminal --window-with-profile=abgx360 -x abgx360 -af3 $1
``` 

Giving I copied  it from some one else Im not fully sure to understand, because this program have basically options to be selected, and I would like to add them to this little script and Im not sure how to write them.

Here for example its the list of command option from the program (First image) and the second image its the recommended settings for my program. 
[ATTACH=CONFIG]258215[/ATTACH] [ATTACH=CONFIG]258216[/ATTACH]
Looking at it I would say I would need, and some others codes,```
-c -e
```  there is aswell two ```
--
``` followed of a short text. Is that a comment ? or a extension of a command I could do ?, LIke ```
-d (For checking my DVD)  OR -nodvdcheck (For NOT checking my dvd) opposite command ?
```
Im sorry if I couldn't be clear. 

Taking out the first question, going back to the way I could write them on the script. This is really killing me: 
For adding any of those -c -e etc.... how should I write them on it ?  Would Like this be ok?? (taking note the -af3 was already there,)
```
#!/bin/bash
gnome-terminal --window-with-profile=abgx360 -x abgx360 -af3 $1

To

#!/bin/bash
gnome-terminal --window-with-profile=abgx360 -x abgx360 -af3 [COLOR=#00ff00]-c -e [/COLOR]$1

```

Im sure its really really simple and stupid, im not that bad in informatic but some time you need to start from the base to be able to climb  

Thank you very much for any answer Have a  nice day

---

