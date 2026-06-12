---
title: "Look for logings without passwords"
date: 2006-07-26
forum: General Help
---

### Post by pat270881 on 2006-07-26
Hello,

I want to write a script which looks for logins which have no password. In order to realize that I think I have to go through every line in the shadow file and look if the second field is empty or not.

I think I have to use something like this

In the course of that two questions occured:

1) I do not know how the regular expression should look like to test if the second field in the shadow file (e.g. user:passwd:...) is empty or not?

2) Furthermore I think I have to use the sed command to go through the lines in the shadow file. the problem is how can quote the shadow file as source for the sed command? - because when I look into the shadow file from command line I use the vipw -s command.

patti

---

### Post by philippe_carlo on 2006-07-26
A few comments: In my shadow file, password less logins have a "!" in the second field, so you should look for those. One way to do this is:
```
sudo cat /etc/shadow | grep ":\!:" | cut -d: -f1
```
which gives all password less logins.

Additional note: there's like hunderds of ways of doing this. cut, grep, sed awk and some bash make a nice mix.

---

### Post by pat270881 on 2006-07-26
Okay thank you very much, but how can I assign to a user no password which already has a password?

---

### Post by pat270881 on 2006-07-27
Is it not possible to look if the second field is empty?? :confused:

---

### Post by pat270881 on 2006-07-27
Is it not possible to look for the second field (the second ::) on every line in the /etc/shadow to check if this field is empty?

---

### Post by philippe_carlo on 2006-07-27
```
sudo cat /etc/shadow |  cut -d: -f1,2 | grep :$
```

---

### Post by pat270881 on 2006-07-27
Thank you for your reply and it works :), I want to ask something to this string:

sudo cat /etc/shadow |  cut -d: -f1,2 | grep :$

Okay, first cat reads all lines of the file and forwards all lines of the file to the cut command for example the first line:

visitor::13355:0:-1:-1:-1:-1:0

the cut command makes a cut between visitor and ::13355:0:-1:-1:-1:-1:0 this two substrings are then forwarded to the grep command and then I do not know what the grep command does with this two strings...? Could you help me once more with an explanation?

---

