---
title: "How do you use the &quot;at&quot; command?"
date: 2007-12-23
forum: General Help
---

### Post by Bou on 2007-12-23
This must be one of the simplest tasks ever, but for some reason I can't manage to do it. Could you guys tell me how to properly use the "at" command?

For example, I want to launch Totem at 18:00. What's the right command to do that?

Thanks in advance.

---

### Post by Ryoushi19 on 2007-12-23
at -f '/your file' (insert your time here)

---

### Post by dlegend on 2007-12-23
Try this:

> 
at -t 18:00 totem


Never used the at command before but it is documented here: [http://www.computerhope.com/unix/uat.htm](http://www.computerhope.com/unix/uat.htm)

I'm sure this would work though (but a file is required to be specified

> 
at -t 18:00 -f filename.sh


where filename.sh is the file that has the bash script you want to execute in.

---

### Post by Bou on 2007-12-23
> **dlegend said:**
> at -t 18:00 totem

~$ at -t 18:00 totem
at: invalid option -- t
Usage: at [-V] [-q x] [-f file] [-mldbv] time
       at -c job ...
       atq [-V] [-q x]
       atrm [-V] job ...
       batch

> **dlegend said:**
> at -t 18:00 -f filename.sh
> **Ryoushi19 said:**
> at -f '/your file' (insert your time here)

Hum, do you have to specify a file? Can't you just give it the command to run? :(

---

### Post by dlegend on 2007-12-23
> **Bou said:**
> ~$ at -t 18:00 totem
at: invalid option -- t
Usage: at [-V] [-q x] [-f file] [-mldbv] time
       at -c job ...
       atq [-V] [-q x]
       atrm [-V] job ...
       batch




Hum, do you have to specify a file? Can't you just give it the command to run? :(

I am trying through the terminal now. My previous statement was wrong -- proper format is:

> 
at -f /path/file.sh 18:00


Can't figure out how to execute a command rather then a file though..

---

### Post by nick_h on 2007-12-23
> Can't figure out how to execute a command rather then a file though..
The at command reads from stdin by default so you can use something like:
```
at 18:00 <<eof
totem
eof
```
However, there is a problem with running GUI applications.  The at command will not run in a GUI environment so the variable DISPLAY will need setting or the display will have to be defined in another way.

You can always type:
```
echo $DISPLAY
```
in your GUI environment to find the appropriate value.

I tried:
```
at now <<eof
totem --display=:0.0
eof
```
It almost works but I get an error.

---

### Post by nick_h on 2007-12-23
It looks like you have to set the DISPLAY variable.
```
echo 'export DISPLAY=:0.0; totem' | at now
```
You can also use the here document approach if you prefer.

---

### Post by dlegend on 2007-12-23
> **nick_h said:**
> It looks like you have to set the DISPLAY variable.
```
echo 'export DISPLAY=:0.0; totem' | at now
```
You can also use the here document approach if you prefer.

Awesome find. I'm fairly new to Linux myself but I try to help where I can -- in the process I seem to be learning a lot as well =)

---

