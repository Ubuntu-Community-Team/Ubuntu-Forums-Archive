---
title: "[SOLVED] Time delayed execution of command - script"
date: 2008-05-23
forum: General Help
---

### Post by ene_dene on 2008-05-23
Let's say that I make a script:
```

#!/bin/bash
/usr/local/bin/some.command

```
What would I add to this script to delay execution of some.command for, let's say 120seconds? How would that script look then?

---

### Post by MeKino on 2008-05-23
I think sleep (120) should do it.

---

### Post by sdennie on 2008-05-23
```

#!/bin/bash

sleep 120

/usr/local/bin/some.command

```

---

### Post by ibuclaw on 2008-05-23
If you want to have the sleep time as an argument.
ie:
```
./execute 120
```

Then this will allow you to do so:
```

if [ $1 ] && [ $1 -gt 0 ]
then sleep $1
fi
# RUN COMMAND HERE #

```

Regards
Iain

---

### Post by sdennie on 2008-05-23
Elegant solution, tinivole.

---

### Post by ene_dene on 2008-05-23
Thank you guys!

---

### Post by ibuclaw on 2008-05-23
Your welcome.

Though, one can go one step further with this, and you can have your script set off at a designated time:
```

#!/bin/bash
#USER VARIABLES
export runhour=12
export runmins=00
export runsecs=00

#SYSTEM VARIABLES
export curhour=$(date +%H)
export curmins=$(date +%M)
export cursecs=$(date +%S)

# A few commands to figure out the time till Noon #
export sethour=$((runhour - curhour))
export setmins=$((runmins - curmins))
export setsecs=$((runsecs - cursecs))

if [ $sethour -le 0 ]
then export sethour=$((sethour + 23))
fi
if [ $setmins -le 0 ]
then export setmins=$((setmins + 59))
fi
if [ $setsecs -le 0 ]
then export setsecs=$((setsecs + 59))
fi

echo "It is "$sethour"hrs, "$setmins"mins and "$setsecs"secs till Noon"

```
Then, you'd have the command:
```
sleep "$sethour"h "$setmins"m "$setsecs"s
```
To sleep for that amount of time.

But this is probably far beyond the scope you were aiming for.
And besides, it may be best to use a cronjob instead!

Regards
Iain

---

### Post by sdennie on 2008-05-23
> **tinivole said:**
> 
Though, one can go one step further with this, and you can have your script set off at a designated time

...

But this is probably far beyond the scope you were aiming for.
And besides, it may be best to use a cronjob instead!


Now you're just showing off...  ;)

---

### Post by ene_dene on 2008-05-23
For this script sleep 120 is just enough, but no doubt that this is useful and in future I'm sure I'll use it.

---

### Post by ibuclaw on 2008-05-23
> **vor said:**
> Now you're just showing off...  ;)

Just throwing ideas round the pond.

I think the OP should know the broad range of possibilities of achieving the task at hand.
As it is quite literally endless!

But besides the point, I don't feel that using High Level Programming Languages is really showing off.

If I were to make a solution in brainfuck, whitespace or bitcode.
**THEN** I'd be showing off...

---

### Post by sdennie on 2008-05-23
> **tinivole said:**
> Just throwing ideas round the pond.

I think the OP should know the broad range of possibilities of achieving the task at hand.
As it is quite literally endless!

But besides the point, I don't feel that using High Level Programming Languages is really showing off.

If I were to make a solution in brainfuck, whitespace or bitcode.
**THEN** I'd be showing off...

Haha.  Nothing says "showing off" like giving a solution that starts with: "use Acme::Bleach;".

---

### Post by ibuclaw on 2008-05-23
> **vor said:**
> Haha.  Nothing says "showing off" like giving a solution that starts with: "use Acme::Bleach;".

:lolflag:

That or giving your python scripts a "**soul**".

[PHP]import soul[/PHP]

---

### Post by shrinathk87 on 2008-08-11
Is it possible to schedule programs..? i mean we have TASK Scheduler in windows...what abt ubuntu..?

Suppose i want to start Azureus download manager at 8pm..how can i set up my comp so that it automatically starts at 8pm, even if i am not around..?

Thanks

---

