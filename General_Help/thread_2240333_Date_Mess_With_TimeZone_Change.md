---
title: "Date Mess With TimeZone Change"
date: 2014-08-19
forum: General Help
---

### Post by clalian on 2014-08-19
Hello everyone,
This morning, I changed my TimeZone to my Country.
I used the command: 
**[COLOR=#000000][FONT=Arial]sudo dpkg-reconfigure tzdata[/FONT][/COLOR]**

I then checked the date, and it matched my local time perfectly.
No problem.
Yet a short while later, I was checking some files, and in the date/time colums, the hour:minutes had disappeared.
Now they are replaced my the year 2014.

I attach screenshots.
On the left, you can see the output of when I ran the command ls -alF
You can see the hour:minutes column.

On the right of the screenshot, you can see the output of the command ls -alF
The hour:minutes has disappeared and it is replaced now by "2014".

Any idea how I can get back the time (hour:minutes) formatting?

Thank you!
:)


[ATTACH=CONFIG]255637[/ATTACH]

---

### Post by clalian on 2014-08-20
Hello,
Wondering if anybody has any idea what is going on here.

I have googled, yet haven't stumbled upon an answer.

All help is appreciated!
:)

---

### Post by Ksiencha on 2014-08-20
I'm really far from expert or advanced user, but I found some discussions ([here]("http://stackoverflow.com/questions/13999300/bash-ls-output-a-time-of-modification-of-files-including-year-and-seconds") and [here]("http://superuser.com/questions/355318/how-to-have-linux-ls-command-show-second-in-time-stamp")). I hope that you'll find something helpful there. ;)

---

### Post by clalian on 2014-08-20
On my way to check those out Ksiencha!

Will report back... thanks!

---

### Post by Habitual on 2014-08-20
open a terminal and type
```
alias ls
```
you may see something akin to formatting like this:
```
alias ls='ls --time-style="+%b %d %Y %l:%M %p"  --color=auto'
```

type 
```
unalias ls 
```
and then issue 
```
ls
```

See any difference?

You may wish to look for an "alias ls" in one of your . files.

the default in ~/.bashrc is 
```
alias ls="ls --color=auto"
```

I set mine in .aliases to 
```
alias ls='ls --time-style="+%b %d %Y %l:%M %p"  --color=auto'
``` because I like it that way!

YMMV.

---

