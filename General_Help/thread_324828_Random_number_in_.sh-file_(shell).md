---
title: "Random number in .sh-file (shell)"
date: 2006-12-24
forum: General Help
---

### Post by Jorik90 on 2006-12-24
Hello,

I'm looking for a way te create a random number between 1 and 4. The number should be created in a sh file, and should be used in the same file. Something like this:
```

#randomnumber generator (between 1 and 4)

#use it
xmms -Q /music/jingles/$randomnumber.mp3

```
Two problems: the random number won't work, I tried several scripts which I found on Google, non of them worked. Second, I think my use-it-code won't work. I think the $randomnumber should be escaped, or something like that..

I tried these examples: [http://www.linux.com/guides/abs-guide/randomvar.shtml](http://www.linux.com/guides/abs-guide/randomvar.shtml)
Resulting in erros about the syntax and the ('s and {'s etc..

Does anyone know how to do this?
Many thanks!

---

### Post by po0f on 2006-12-24
Jorik90,

If you're using Edgy, you will have to make the first line of your script:
```
[FONT="Courier New"]#!/bin/bash[/FONT]
```
I do this for all of my scripts, and to make it global as well run this command:
```
[FONT="Courier New"]$ sudo dpkg-reconfigure dash[/FONT]
```
and answer no.  Edgy's default shell interpreter is Dash, not Bash.  That's why the Bash tutorial you were using wasn't working.  ;)

---

### Post by Chimes on 2006-12-24
Try this out (make sure you have the bash shell):
```

#!/bin/bash
myrandnumber=`expr '(' $RANDOM '*' 4 / 32767 ')' + 1` 
#should you want to have a different range than 1-4:
#note that the first literal integer, the one multiplied by $RANDOM, denotes the length of the range
#note that the third literal integer, the one added at the end, denotes the position of the range (so if it were 8, the range would be 8-11).

xmms -Q /music/jingles/$myrandnumber.mp3

```

---

### Post by Jorik90 on 2007-01-03
Many thanks, It worked.
First I runned the solution of po0f and secondly I used the script from Chimes. And it worked!! Great!

---

