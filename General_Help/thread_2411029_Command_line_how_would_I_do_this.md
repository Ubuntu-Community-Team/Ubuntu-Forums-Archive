---
title: "Command line how would I do this?"
date: 2019-01-23
forum: General Help
---

### Post by adrian-h on 2019-01-23
This is probably needing some scripting but I can not figure it out.

I am looking at /etc/fail2ban/filter.d directory and all the conf files it contains.  I am trying to match which ones I should be using to match the attacks I find in the logs.  So I thought if I do a cat *.conf > ~/allconf.txt

I would get one long text file to print off containing all configurations then I can go through the list and select which jails I should use.

But not all .conf files tell me what name they are, so

I am trying to think of a way for the text file to have the name of the file, then the contents of the file, then the name of the next file and contents etc.
A bit like echo *.conf cat *.conf, echo *.conf cat *.conf, echo *.conf cat *.conf, etc

My skills are not up to it.  can anyone suggest an idea or have a scripts I can try and understand.

Cheers

Adrian

---

### Post by CatKiller on 2019-01-23
That sounds like an ideal application for a for loop.

You can use >> rather than > if you want to append text to the end of a file instead of replacing the text.

I'm writing from a phone, so I can't really do the syntax for you. I'm sure you can figure it out from there.

---

### Post by dragonfly41 on 2019-01-23
For analysing multiple log files (and other files) I would try [petit]("http://crunchtools.com/software/petit/")

---

### Post by adrian-h on 2019-01-24
Thanks for the responses I will have a look at these when home from work tonight.

It is appreciated getting idea's in.

Adrian

---

### Post by sisco311 on 2019-01-24
heads or tails?

head:
```
head -n-0 *.conf
```
tail:
```
tail -n+1 *.conf
```

---

### Post by adrian-h on 2019-01-24
@sisco311

All I can say is WOW them lines are going in to my book to remind me to figure out what is happening.

Thank you, they print the output in a format I can print to the page and act as a look up for me.

typical format of the output is

```
==> uwimap-auth.conf <==
# Fail2Ban filter for uwimap
#

[INCLUDES]

before = common.conf

[Definition]

_daemon = (?:ipop3d|imapd)

failregex = ^%(__prefix_line)sLogin (?:failed|excessive login failures|disabled|SYSTEM BREAK-IN ATTEMPT) user=\S* auth=\S* host=.*\[<HOST>\]\s*$ 
            ^%(__prefix_line)sFailed .* override of user=.* host=.*\[<HOST>\]\s*$

ignoreregex = 

# Author: Amir Caspi
```


So I see the name of the conf file and it's details.

Just perhaps if I have printed sheets and I am not flicking between screens I can figure why my fail2ban is not working.

Thank you.

Adrian

---

