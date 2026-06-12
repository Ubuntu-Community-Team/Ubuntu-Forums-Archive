---
title: "Confused over $HOME/"
date: 2007-03-05
forum: General Help
---

### Post by dryder on 2007-03-05
Hi,

A very 'obvious' thing to most, I agree, but I have been reading so much documentation I am now befuddled.

Many docs refer to something being in $HOME/..../...

Sometimes I find the files they refer to in usr/, /myname, /"my home folder" or /etc

Please - does $HOME/ have a specific meaning/start directory?

I have googled and searched the site for $HOME but nothing comes up.

Many thanks,
David

---

### Post by ffxr on 2007-03-05
its /home/whateveryourusernameis

so if your user name is dryder on ubuntu/linux...

it would refer to  /home/dryder

---

### Post by dryder on 2007-03-05
Many thanks ffxr,

David 

How's the weather there? I miss the snow ... :)

---

### Post by scxtt on 2007-03-05
you can also do **echo $HOME** to find out what it is, which is the case for (almost) anything preceeded by a "$" (variables) ...

echo $TERM
echo $PATH
echo $PWD
etc.
:)

---

### Post by strabes on 2007-03-05
Also, you can use "~" to refer to your home directory. This is useful because it's not username specific. So you could do either:

```
ls ~/.mozilla
```
or
```
ls /home/yourusername/.mozilla
```

---

### Post by dryder on 2007-03-06
Thanks everybody .. :)

---

