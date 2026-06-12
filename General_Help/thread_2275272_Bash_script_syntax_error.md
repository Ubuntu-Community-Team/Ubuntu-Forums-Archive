---
title: "Bash script syntax error"
date: 2015-04-25
forum: General Help
---

### Post by kevin_vanryck on 2015-04-25
It's been more than half a year since my last bash script, here I am learning it again!

What could be causing the following error?

```
#!/bin/bash
[...]
mytemp=$(/opt/vc/bin/vcgencmd measure_temp) | cut -d= -f2 | cut -d"'" -f1
[...]
                if [ ($mytemp % step) -gt ($lastlimit + $step) ]; then
                        sendPush $mytemp
                        ($mytemp % step) > /home/pi/scripts/lasttemp.txt
                fi

```

```
./temp.sh: line 30: syntax error near unexpected token `$mytemp'
./temp.sh: line 30: `        if [ ($mytemp % step) -gt ($lastlimit + $step) ]; then'
```

And $mytemp is empty somehow. The piping to cut is going wrong. (I used set -xv to see it)
Thanks for the help!

---

### Post by matt_symes on 2015-04-25
Hi
> 
if [ ($mytemp % step) -gt ($lastlimit + $step) ]; then

```
if [ ($mytemp % **$step**) -gt ($lastlimit + $step) ]; then
```

?

Kind regards

---

### Post by Holger_Gehrke on 2015-04-25
Are those supposed to be arithmetic evaluations ? Then they should be written as '$(( expression ))' without '$'  before the variables in the expression:
```

 if [ $(( mytemp % step )) -gt $(( lastlimit + step )) ] ; then

```
Also, there needs to be a space between ']' and ';'
And the 5th line should probably read
```

echo $(( $mytemp % step )) > /home/pi/scripts/lasttemp.txt

```

---

