---
title: "help with grep"
date: 2007-12-31
forum: General Help
---

### Post by dachinster on 2007-12-31
Hi guys,
I am trying to show the running processes on a linux mail server.

however, I am trying to EXCLUDE a process called simscan which occurs hundreds on times and clutters the output

I am currently using ps -aux and I want to pipe my output to the screen and exclude all occurrences of simscan.

Also, how do I exclude more than one term, example exclude simscan and apache?

Can grep do this?
If not, is there any other command that can do this?

---

### Post by oscarsfriend on 2007-12-31
> **dachinster said:**
> Can grep do this?
If not, is there any other command that can do this?

1) Don't know.

2) Try piping output though sed, and use a regexp to delete the unwanted lines.

---

### Post by dagnabit dang doohickey on 2007-12-31
```
ps -aux | grep -v simscan
```
```
ps -aux | grep -v 'simscan\|apache'
```

---

### Post by ghostdog74 on 2007-12-31
> **dachinster said:**
> Hi guys,
I am trying to show the running processes on a linux mail server.

however, I am trying to EXCLUDE a process called simscan which occurs hundreds on times and clutters the output

I am currently using ps -aux and I want to pipe my output to the screen and exclude all occurrences of simscan.

Also, how do I exclude more than one term, example exclude simscan and apache?

Can grep do this?
If not, is there any other command that can do this?

```

ps -aux | egrep -v "simscan|apache"

```

---

### Post by dachinster on 2007-12-31
Thanks dagnabit!
That works perfectly.
At first it did not work, but I double checked and the ' ' quotes are important

Thanks again

---

### Post by ghostdog74 on 2007-12-31
> **oscarsfriend said:**
> 1) Don't know.

If you don't know, don't post.

---

### Post by oscarsfriend on 2007-12-31
> **ghostdog74 said:**
> If you don't know, don't post.

I didn't know the answer to the first question, but I did have an answer to the second.

---

### Post by dachinster on 2007-12-31
Hi guys, just a modification. If I want to list ONLY the processes:

Qmail related services
  clamd
  freshclam
  spamd
  qmail-send
  tcpserver on ports 25, 110, 143
  sslserver on ports 465, 993, 995

Can I use this command?
ps -aux | grep 'clamd\|fresh\|qmails\|tcp\|ssls'

I tried it and I get some output, but I also get an error:
Warning: bad syntax, perhaps a bogus '-'? See /usr/share/doc/procps-3.2.3/FAQ

---

### Post by p_quarles on 2007-12-31
The leading dash in the "aux" option is deprecated, and will always return that syntax error. It *works*, but it's deprecated. To get rid of the error message:
```
ps aux | grep 'clamd\|fresh\|qmails\|tcp\|ssls'
```

---

### Post by dachinster on 2007-12-31
hey thanks p_quarles
that works :)

I do not quite understand what you mean by deprecated. Has the leading dash become obsolete for linux commands or just for ps ?

---

### Post by p_quarles on 2007-12-31
Just for ps. For historical reasons, ps uses two entirely different sets of option syntax. "Standard" syntax:
```
ps -ef
```
and "BSD" syntax:
```
ps aux
```
In BSD syntax, the "u" option indicates "user-oriented format," whereas "-u" indicates that a userlist will follow this option. So "ps -aux" actually looks for a user named "x". If it can't find that user, it will guess that you meant the "x" option, but will also warn you about the syntax. 

That's all in the man page, too, if you want a more detailed explanation.

---

### Post by dachinster on 2007-12-31
Thanks for the explanation!
While I am sure it is in the man pages somewhere, I am sure we can agree that the man pages for grep are very long and man pages in general are not well laid out to people who are not linux users that consult man pages regularly

---

### Post by ghostdog74 on 2007-12-31
> **dachinster said:**
> Thanks for the explanation!
While I am sure it is in the man pages somewhere, I am sure we can agree that the man pages for grep are very long and man pages in general are not well laid out to people who are not linux users that consult man pages regularly
man pages will be your life saver , if you don't have references or internet to get information from.
for what you want to do, just use ps -ef , or ps -eo args |egrep "process1|process2"

---

