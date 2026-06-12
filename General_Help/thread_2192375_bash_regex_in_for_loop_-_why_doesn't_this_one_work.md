---
title: "bash regex in for loop - why doesn't this one work?"
date: 2013-12-07
forum: General Help
---

### Post by Dreamer Fithp Apprentice on 2013-12-07
This:
```
#! /bin/bash

for DEVICE in "$(ls /dev/?d??*)"
do
    if [[ $DEVICE =~ /dev/[sh]d[a-z][1-9]+ ]]; then
        echo "$DEVICE"
    fi
done

/bin/bash
```is intended to return a list of all hard drive partitions. It assumes they are all designated /dev/sdLN or /dev/hdLN where L is a lower case latin letter and N is a whole number with no leading zeros. If the assumption is wrong that's because my knowledge is imperfect and I'd appreciate enlightenment. But the real problem is that my logic or my syntax fails. The regex passes ANYTHING the ls output sends it. The only limitation on returns is whatever I build into the ls. 

So:

Main question:
What's wrong with my regex? In posting this I just noticed I should probably change "[1-9]+ " to "[1-9][0-9]* to catch partitions with a 0 iin the name on disks with more than 9 partitions, but that isn't the problem here. ATM I have only one hd installed and it has less than 10 partitions. I am trying to address the most general case though.

Alternate question:
Is there a way to further restrict the ls command so it returns ONLY the results I want? Functionally, that would accomplish the goal of the script even more elegantly. I don't ask this as the main question both because I"m pretty sure the answer is "no" and because I'd still want to know why my regex doesn't work the way I expected even if there is a better way altogether.

I should have mentioned that in the case of the system I'm on atm for example, it returns /dev/cdrom in addition to the responses I want. I've tested this under Precise, 32 bit and Saucy, 32 bit with the same results. I'm on the Saucy atm and the bash version is
GNU bash, version 4.2.45(1)-release (i686-pc-linux-gnu).

---

### Post by steeldriver on 2013-12-07
I *think* that the issue is that by quoting the ls variable i.e. [COLOR=#ff0000]**"**[/COLOR]$(ls /dev/?d??*)[COLOR=#ff0000]**"**[/COLOR] you are forcing a non-regex match - however generally it's best to avoid anything like $(ls /dev/) - the output of  `ls` is meant to be human readable and is likely to break when parsed in  a script (although I don't think that's the reason your current script  is failing).

Maybe you could use bash extended globs instead of a regular expression? In which case you can do the match you want without a further test e.g.

```

#! /bin/bash

shopt -s nullglob
shopt -s extglob

for Device in /dev/@(h|s)d[a-z]+([0-9])
do
    echo "$Device"
done

```

(notice that the + goes in front i.e. **+([0-9])** is the glob equivalent of regex **[0-9]+** ) or just

```
ls /dev/@(h|s)d[a-z]+([0-9])
```

---

### Post by Dreamer Fithp Apprentice on 2013-12-08
Thanks, Steeldriver! All 3 of those work for me.> **steeldriver said:**
> I *think* that the issue is that by quoting the ls variable i.e. [COLOR=#ff0000]**"**[/COLOR]$(ls /dev/?d??*)[COLOR=#ff0000]**"**[/COLOR] you are forcing a non-regex matchI can't honestly say I understand that yet but you must be right. When I take out the quotation marks it works. I should have thought of trying that. While I don't completely understand quotation marks I DO understand that I don't understand if that doesn't sound too Cheneyesque. So taking them out where it seems to me they ought to be or adding them where it seems to me they ought not to be is usually one of the things I try when all else fails. I studied the output with the -x switch on the shebang line with and without the "-marks and "for" seems to wrap the whole expression in a pair of single quotes upon expansion, so that```
for DEVICE in $(ls /dev/?d??*)
```expands to```
for DEVICE in '$(ls /dev/?d??*)'
```and```
for DEVICE in "$(ls /dev/?d??*)"
```becomes```
for DEVICE in '"$(ls /dev/?d??*)"'
```I haven't followed the logic all the way through yet, but that must be the beginning of it.> **steeldriver said:**
> Maybe you could use bash extended globs  instead of a regular expression? In which case . . . This works  also. Totally new to me. Looks like useful stuff. I got some readng to  do. > **steeldriver said:**
> or just```
ls  /dev/@(h|s)d[a-z]+([0-9])
```Wow! I'd have bet money that  wasn't possible. I had no idea ls was that flexible. You're quite a  wizard! Thanks!

---

### Post by steeldriver on 2013-12-08
TBH I don't use the extended glob features very often and find myself checking the syntax every time - there are a few good references on the web e.g. [Greg's wiki]("http://mywiki.wooledge.org/glob"). You should also take a look at the [Bash Pitfalls]("http://mywiki.wooledge.org/BashPitfalls") page - notice that the #1 pitfall is the [for i in $(ls *.mp3)]("http://mywiki.wooledge.org/BashPitfalls#for_i_in_.24.28ls_.2A.mp3.29") construct

---

### Post by Dreamer Fithp Apprentice on 2013-12-08
Thanks for the links. Both look worth study. The second has already clarified things for me a bit. :)

---

