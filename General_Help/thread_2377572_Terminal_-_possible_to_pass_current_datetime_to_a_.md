---
title: "Terminal - possible to pass current date/time to a command?"
date: 2017-11-14
forum: General Help
---

### Post by sprinterdriver on 2017-11-14
Hi.

Background: Doing some learning about rsync and try to set up a backup the way I want it to work. So far I have get the backup function to work just great, but I have one thing I can't figure out how to do. I want to get rsync create a new subdir into the backup directory every time there is at least one file that is taken backup off.

Therefore - my question is:
Does it exist a variable that I can call so that it returns todays date and time?

---

### Post by Holger_Gehrke on 2017-11-14
Would a command line substitution work for you purpose ?
(stupid example to show the syntax)
```

echo $(date)

```
This executes the command "date" and puts it's output into the command. You might have to play with options and parameters for date to get a format you like.

Holger

---

### Post by again? on 2017-11-14
This is a format I use.
```
echo $(date +"%Y-%m-%d_%H-%M")
```
```
glen@GU17:~$ echo $(date +"%Y-%m-%d_%H-%M")
2017-11-15_08-28
```

---

### Post by sprinterdriver on 2017-11-15
Thank you for explanation. I'll play around with the options next time I feel to backup something.

I put this thread solved - hope it's ok to ask later if something of details about topic doesn't work for me ;-)

---

