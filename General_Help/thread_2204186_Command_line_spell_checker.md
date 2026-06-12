---
title: "Command line spell checker"
date: 2014-02-07
forum: General Help
---

### Post by bill-lancaster on 2014-02-07
I am using 'spell' as a command line spell checker.
Can anyone tell me how to change the default dictionary to British? 
```
spell ~/Documents/spell.txt -b

```spell: /usr/lib/ispell/british.has: cannot open

---

### Post by vasa1 on 2014-02-07
Do you have *ibritish* installed? What does *apt-cache policy ibritish* tell you?

---

### Post by bill-lancaster on 2014-02-07
this is the result:-
ibritish:
  Installed: (none)
  Candidate: 3.3.02-6
  Version table:
     3.3.02-6 0
        500 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) saucy/universe amd64 Packages

---

### Post by vasa1 on 2014-02-07
I think you'll need to install *ibritish* then. See what *apt-cache show ibritish* says about what that package does.

---

### Post by bill-lancaster on 2014-02-07
How simple - sudo apt-get install ibritish
does the job!

many thanks

---

### Post by vasa1 on 2014-02-07
Welcome!

---

### Post by bill-lancaster on 2014-02-07
While I have the attention of someone so knowledgeable, I have posted a new thread regarding adding word to the dictionary!
Thanks again

---

