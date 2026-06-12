---
title: "One alias to execute two commands?"
date: 2007-02-01
forum: General Help
---

### Post by FaceorKneecaps on 2007-02-01
I have a lot of aliases but they are each for one command only.  

I have:  
alias c='clear'   and 
alias l='ls -l'  

but is there a way to make one alias for both (alias c='clear THEN  ls -l)  ? 
It would be great if that worked with the CD command to, If I write 'cd /media' it will automatically go to /media and list it's content.

I am just starting using the Terminal for all my needs but cant seem to find any good websites for practical tips. I use the 'Linus command MAN page' but it's a bit confusing for a newbie.

Thanks..

---

### Post by Nik_Doof on 2007-02-01
```
alias c='clear;ls -l'
```

This [guide](http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html) should help you.

---

### Post by der_joachim on 2007-02-01
An alternative is to try the following (although it is not really necessary for this alias): 
```
command1 && command2
```
This snippet of code will execute command2 if command1 has executed successfully.

---

