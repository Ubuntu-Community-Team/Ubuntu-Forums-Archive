---
title: "Run prog in backround and retrieve PID"
date: 2007-05-12
forum: General Help
---

### Post by Dudsmacka2 on 2007-05-12
Correct me if I am wrong, but you run a program in the background by ending the command with "&".

How can I put the PID into a variable as I launch the program in the background?

---

### Post by jimbob on 2007-05-12
Yes, you can start a command line program in the background by adding & at the end.

I believe the PID is assigned by the system - you cannot do it yourself.  You can find it easily after the program starts. 
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="1"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by Dudsmacka2 on 2007-05-12
How can I find it after the prog has started?

---

### Post by robrmd9 on 2007-05-12
Well, if you enter for example:

```
gedit &
```

You will see something like:

```
[1] 2062
```

With 2062 being the PID.

---

### Post by Wim Sturkenboom on 2007-05-13
```
ps -ef | grep *program_name*
```

---

### Post by stylishpants on 2007-05-13
It is in this environment variable: $!

---

