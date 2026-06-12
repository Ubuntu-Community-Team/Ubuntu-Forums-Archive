---
title: "Bash Files"
date: 2012-11-23
forum: General Help
---

### Post by netwo on 2012-11-23
I would like to make thisfunction work though ... actually i'm not able to fix the problem :/

ms="`date +%m`"
if ["11" == "11"]; then
                echo "$ms"
        else
                echo "not working"
        fi

---

### Post by papibe on 2012-11-23
Hi netwo.

A few tips about the syntax:

Backticks are deprecated, prefer this syntax:
```
ms="$(date +%m)"
```
The 'if' construction needs space between its tokens:
```
if [ "11" == "11" ]; then ...
```
In terms of what you need to do, and if it is doing it right, there's no much information.

What are you trying to do?

Regards.

---

### Post by netwo on 2012-11-24
If the month is november then do a certain cOmnand line

---

### Post by papibe on 2012-11-24
Then you need to compare the results of date to 11:

For instance comparing numbers
```
ms=$(date +%m)

if [ $ms -eq 11 ]; then
    echo "doing certain command."
else
    echo "doing nothing."
fi
```
Or comparing strings:
```
ms="$(date +%m)"

if [ "$ms" == "11" ]; then
    echo "doing certain command."
else
    echo "doing nothing."
fi
```
Let us know how it goes.
Regards.

---

### Post by netwo on 2012-11-25
Actually thank you very much for the help to get this script work. i wanted to have some good tutorial if you have some please.

---

### Post by papibe on 2012-11-25
Here are a couple of resources:
[LIST]
[*][Command Line Resources]("https://help.ubuntu.com/community/CommandLineResources")
[*][Linux Command Line Learning Resources]("http://ubuntuforums.org/showthread.php?t=1909108")
[/LIST]
Regards.

---

### Post by CaptainMark on 2012-11-25
Im always referring to this guide [http://tldp.org/LDP/abs/html/](http://tldp.org/LDP/abs/html/) for bash syntax

---

