---
title: "How can I randomize beep?"
date: 2008-02-29
forum: General Help
---

### Post by Arenlor on 2008-02-29
I am thinking that I can possibly use my computer as an alarm clock by writing a bash script that sets it to sleep for however long then do a while true; beep -f RANDOM -r RANDOM2 -d 300; done
A question that ties in with this is, is there any way to make a bash script accept a variable? For example if I made that script is there any way I could run it from the command line where it'd be ./alarm.sh S where S is the number of seconds I want it to sleep?

---

### Post by erginemr on 2008-02-29
Regarding variables (or literally speaking, arguments):

you can represent arguments with $1 (first argument), $2 (second argument), etc. 

So, when you write the following shell script:
```
#!/bin/bash
echo "Your first argument is = $1" 
echo "Your second argument is = $2"
```
and run it with:
```
chmod u+x your_script
./your_script hello bye

```
you get the following output:
```
Your first argument is = hello
Your second argument is = bye
```
For more, the following is a crash course tutorial on Bash:
[http://www.arachnoid.com/linux/shell_programming.html](http://www.arachnoid.com/linux/shell_programming.html)

---

### Post by erginemr on 2008-02-29
On a second thought, I have nothing to say if this is for the sake of learning bash scripting. But if your sole purpose is to have an alarm clock application, I can suggest you to try:
[http://www.getdeb.net/app/Alarm+Clock](http://www.getdeb.net/app/Alarm+Clock)
[http://www.getdeb.net/app/AlarmClockApp](http://www.getdeb.net/app/AlarmClockApp)

The first one looks really professional.

---

