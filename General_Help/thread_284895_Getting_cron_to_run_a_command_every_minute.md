---
title: "Getting cron to run a command every minute"
date: 2006-10-26
forum: General Help
---

### Post by anonOmus on 2006-10-26
I've been trying to get the cron daemon to run a program every minute with no sucess. Here is the output of crontab -l:

* * * * * /sbin/clientcheck

Am I doing something wrong?

---

### Post by streeto on 2006-10-26
Somebody correct me if I am wrong.
For periodic scheduling, it should be */period. I.e.,

*/1 * * * * /sbin/clientcheck

Please try and let me know it.

---

### Post by anonOmus on 2006-10-26
nope that does'nt seem to work :(

---

### Post by handband2 on 2006-10-26
> **anonOmus said:**
> I've been trying to get the cron daemon to run a program every minute with no sucess. Here is the output of crontab -l:

* * * * * /sbin/clientcheck

Am I doing something wrong?

anonOmus,

Try this:
```
01 * * * * /sbin/clientcheck
```

---

### Post by bsussman on 2006-10-26
> **streeto said:**
> Somebody correct me if I am wrong.
For periodic scheduling, it should be */period. I.e.,
<  

No - asterix means first-last as in 0-59 which is the original request :KS

 It works fine on my machines

```
bos@Dillon:/tmp$ crontab -e
crontab: installing new crontab
bos@Dillon:/tmp$ crontab -l
* * * * *  date >> /tmp/datestmp
bos@Dillon:/tmp$ sleep 180
bos@Dillon:/tmp$ cat datestmp
Thu Oct 26 09:52:01 EDT 2006
Thu Oct 26 09:53:01 EDT 2006
Thu Oct 26 09:54:01 EDT 2006
Thu Oct 26 09:55:01 EDT 2006
bos@Dillon:/tmp$ 
```
For more info:

```
bos@Dillon:/tmp$ man 5 crontab
```

---

### Post by streeto on 2006-10-26
From 'man 5 crontab':

       "Step values can be used in conjunction with ranges.  Following a  range
       with  ``/<number>''  specifies  skips of the number's value through the
       range.  For example, ``0-23/2'' can be used in the hours field to spec-
       ify command execution every other hour (the alternative in the V7 stan-
       dard is ``0,2,4,6,8,10,12,14,16,18,20,22'').  Steps are also  permitted
       after  an asterisk, so if you want to say ``every two hours'', just use
       ``*/2''."

In fact, you should not need */1, * is already "for every value of". Are you sure cron is running? Try running 'sudo invoke-rc.d cron restart'.


Also, check your system mail from the console, cron mails you the output of the scheduled task (if there is any). It may be having problems running the command. Just type 'mail' in the shell and see if you have anything.

---

### Post by bsussman on 2006-10-26
> **handband2 said:**
> anonOmus,

Try this:
```
01 * * * * /sbin/clientcheck
```

That will run once an hour at minute 1

---

### Post by bsussman on 2006-10-26
Does your script actually run from the command line correctly?

---

### Post by handband2 on 2006-10-26
> **bsussman said:**
> That will run once an hour at minute 1

bsussman,

Sorry, streeto was correct to have it run every minute:
```
*/1 * * * * /sbin/clientcheck
```

As bsussman said.  Check to see if your script runs correctly.

---

### Post by streeto on 2006-10-26
Both * and */1 work the same way. I just like the other form, remembers that I want it to be periodic rather than "any time". :D

---

