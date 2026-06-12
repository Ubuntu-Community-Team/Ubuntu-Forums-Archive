---
title: "How do I loop a bash script?"
date: 2013-03-05
forum: General Help
---

### Post by linuxvstheworld on 2013-03-05
Let's say I were to make a backup script for a certain file or directory, is there a command I can put at the end of the script that tells the script to loop?

---

### Post by lykeion on 2013-03-05
It sounds like you want to use cron, see [https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)

---

### Post by Lars Noodén on 2013-03-05
For repeating the script, cron is the way to go.  

If you really want a loop and continuous execution, you could put a [while](http://tldp.org/LDP/Bash-Beginners-Guide/html/sect_09_02.html) loop in the script itself.

---

### Post by linuxvstheworld on 2013-03-05
So basically putting 'done' at the end loops it?

---

### Post by bab1 on 2013-03-05
> **linuxvstheworld said:**
> So basically putting 'done' at the end loops it?

If you want to create a loop in the script you should do [**_[COLOR="#0000CD"]this[/COLOR]_**.]("http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO-7.html")

---

### Post by drmrgd on 2013-03-05
I think there's some confusion here.  If looping a script (repeating an element of it over and over until a condition is met) is really want you want to do, then you might have a look into something like 'while', 'until', or 'for'.  See here (half way down) for more info:

[http://mywiki.wooledge.org/BashGuide/TestsAndConditionals](http://mywiki.wooledge.org/BashGuide/TestsAndConditionals)

If you want to repeat the whole script at certain times (which is what it seems like based on what you say the script is doing), then something like 'cron' or some other scheduler might be the way to go.  The 'done' statement just ends a 'do' statement (often in conjunction with a loop):

```
 while <condition>; do <something>; done 
```

Perhaps a more specific example of your script and / or what you want to do with it would be helpful.

---

### Post by dcstar on 2013-03-07
> **linuxvstheworld said:**
> 
...........
is there a command I can put at the end of the script that tells the script to loop?

```
exec $0
```

---

### Post by linuxvstheworld on 2013-03-07
> **dcstar said:**
> ```
exec $0
```

I just made a test script doing echo test and put the command you mentioned and it worked! I'll try out other methods also
that were suggested here, thanks!

---

### Post by linuxvstheworld on 2013-03-11
Is there a command like 

exec $0

That makes it loop a certain amount of times?

---

### Post by Lars Noodén on 2013-03-11
To loop it a set number of times, you can use conditionals like [while or for](http://mywiki.wooledge.org/BashGuide/TestsAndConditionals#Conditional_Loops_.28while.2C_until_and_for.29) inside the script itself.  That will not mix with exec, though.

---

### Post by apmcd47 on 2013-03-11
> **linuxvstheworld said:**
> Is there a command like 

exec $0

That makes it loop a certain amount of times?

To be honest I think you are better off rewriting the script to use a while loop as other posters have suggested. But if you insist on doing it that way and the script is otherwise passed no arguments you could put this code at the end:
```
if [[ "${1:-0}" -gt 1 ]]
then
   exec $0 $(( $1 - 1 ))
fi
```Now when you invoke your script include the number of times you want it to repeat as an argument to the script.

Andrew

---

### Post by HermanAB on 2013-03-11
Howdy,

If you need to loop over files and directories, then the best way is usually with the 'find' command and its 'exec' option.

---

