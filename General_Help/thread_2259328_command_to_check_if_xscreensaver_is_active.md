---
title: "command to check if xscreensaver is active"
date: 2015-01-03
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2015-01-03
I am using xscreensaver on xubuntu 14.04
i could just check for the screensaver process, but i have it on random mode so it changes every few minutes

---

### Post by steeldriver on 2015-01-03
Not quite sure what you're asking, but perhaps

```

xscreensaver-command -watch

```

From [FONT=courier new]man xscreensaver-command[/FONT]:

```

       -watch  Prints a line each time the screensaver  changes  state:  when
               the  screen  blanks, locks, unblanks, or when the running hack
               is changed.  This option never returns; [B]it is intended for use
               by shell scripts that want to react to the screensaver in some
               way[/B].  

```

---

### Post by Holger_Gehrke on 2015-01-03
Take a look at the man page for xscreensaver-command, especially the option -watch or -time. Is this what you need ?

---

### Post by pqwoerituytrueiwoq on 2015-01-03
> **steeldriver said:**
> Not quite sure what you're asking, but perhaps

```

xscreensaver-command -watch

```

From [FONT=courier new]man xscreensaver-command[/FONT]:

```

       -watch  Prints a line each time the screensaver  changes  state:  when
               the  screen  blanks, locks, unblanks, or when the running hack
               is changed.  This option never returns; [B]it is intended for use
               by shell scripts that want to react to the screensaver in some
               way[/B].  

```how do i use that in a script when the process does not exit
i can use -time, but for the sake of knowledge

---

### Post by steeldriver on 2015-01-03
Can you be more specific about what you're trying to do, exactly?

---

### Post by Dennis N on 2015-01-03
If you want to watch it's activity over time, use **htop** and filter (F4) for xscreensaver.

See screenshot attached. I have xscreensaver-demo superimposed, so you have two processes - that and the daemon.

---

### Post by sisco311 on 2015-01-03
> **pqwoerituytrueiwoq said:**
> how do i use that in a script when the process does not exit
i can use -time, but for the sake of knowledge

The man page provides an example in perl. In bash you could try something like:
```
xscreensaver-command -watch | while read -r line
do
    if [[ $line =~ ^BLANK ]]
    then
        : do something
    fi
done

```

---

### Post by pqwoerituytrueiwoq on 2015-01-03
thanks

---

### Post by pqwoerituytrueiwoq on 2015-01-03
@[**[COLOR=#C61919][B]steeldriver**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=1627500")
trying to fully automate my DIY keyboard 12v led light that i connected to my rPi via a single channel relay
here is my script
i have not tested it yet, but it should work
i don't use blank cause i have had a issue with my system not restoring the display when my tv goes off and the computer comes on (nvidia bug, that comes and goes)
```
#!/bin/bash
state=0
xscreensaver-command -watch | while read -r line;do
        if [[ $line =~ ^BLANK ]] || [[ $line =~ ^RUN ]] && [ $state -eq 0 ];then
                state=$(curl "http://10.0.0.25:81/relay.php" 2> /dev/null)
                if [ "$state" = "true" ];then
                        curl "http://10.0.0.25:81/relay.php?off" 2> /dev/null
                        state=1
                else
                        state=0
                fi
        elif [[ $line =~ ^UNBLANK ]] && [ $state -eq 1 ];then
                curl "http://10.0.0.25:81/relay.php?on" 2> /dev/null
                state=0
        fi
done
```

---

### Post by schragge on 2015-01-03
@**pqwoerituytrueiwoq**
This
```
[ $line =~ ^BLANK ]
```should be this```
[[ $line =~ ^BLANK ]]
``` Same for ^UNBLANK. Operator =~ is only defined inside [[ ]]. Unquoted $line is also OK only inside [[ ]]. Inside [ ] it should always be quoted: [ ] is just a syntactic sugar for *test*, and unquoted expanded variables in command parameters are subject to word splitting.

---

### Post by pqwoerituytrueiwoq on 2015-01-03
i was testing and editing my post, when you posted, i figured that out
i tried to see if it worked in shell and ended up making it bash

---

