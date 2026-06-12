---
title: "grep configuration file"
date: 2006-11-06
forum: General Help
---

### Post by neumeka on 2006-11-06
I would like grep to automatically start with colors turned on.  Does anyone know where I should put the "colors=auto" statement?  Is there a standard conf file for grep in Ubuntu?

Thanks,
Kyle

---

### Post by bsussman on 2006-11-06
> **neumeka said:**
> I would like grep to automatically start with colors turned on.  Does anyone know where I should put the "colors=auto" statement?  Is there a standard conf file for grep in Ubuntu?

Thanks,
Kyle

[http://www.ccs.neu.edu/home/katz/unix-colors.html](http://www.ccs.neu.edu/home/katz/unix-colors.html) 'slpains it better than me.

There is no grep config file so .bashrc would be my choice.

BTW, thanks for bringing this feature to my attention - I just implemented it myself!  :D

---

### Post by brendon on 2006-11-06
Default grep options are placed in environment variables.  If your using bash add the following lines to your ~/.bashrc file:

```
export GREP_OPTIONS="--color"
```

If the following line is also added to ~/.bashrc it will change the default color:

```
export GREP_COLOR="1;31"
```

The number 31 (red) can be replaced with other colors.  Some available colors are:

30	black
31	red
32	green
33	yellow
34	blue
35	purple
36	cyan
37	white

---

### Post by mvaniersel on 2006-11-06
You can also do this:

```

alias grep='grep --color=auto'

```

For more info, see: [http://www.ss64.com/bash/alias.html]("http://www.ss64.com/bash/alias.html")

---

### Post by Rhubarb on 2006-11-06
I haven't done any of this myself, as I'm still learning here.
Hopefully someone else here can specifically address your problem.

I've found a few ways in these forums that might help you out:
[http://ubuntuforums.org/showthread.php?t=41538](http://ubuntuforums.org/showthread.php?t=41538)
[http://ubuntuforums.org/showthread.php?p=1706040](http://ubuntuforums.org/showthread.php?p=1706040)

There is one post here that has got your grep command that you want:
[http://ubuntuforums.org/showpost.php?p=1706502&postcount=7](http://ubuntuforums.org/showpost.php?p=1706502&postcount=7)

Hopefully you can get enough info to get you started here.
If not, you could always make up a bash script, make it executable, and place it in your /user/bin/ directory.

Edit:  Looks like there's allready a few people here kind enough to help you out :-P

---

### Post by neumeka on 2006-11-06
Thanks for the help!  I guess I didn't search the forums well enough...Will do that next time.

---

