---
title: "gcc"
date: 2006-11-30
forum: General Help
---

### Post by cytutchi on 2006-11-30
hey people...

just wanted to ask something about the gcc...
i m kinda new in dapper so i thought about the absolute beginner talk but also maybe this is something of general help...anyway 

as i can see from the adept i have gcc-4.0 installed!!!

but when i type the command make in the konsole it returns an error that it canot find gcc!

my thought is that maybe indeed what is installed is gcc-4.0 and not gcc so it is a prob. of the name! but if so wouldnt that be a tupid problem or maybe  i m wrong thinking that so...any advice would be usefull cause cant run tools that need to use "make" command n gcc is involved!

---

### Post by cytutchi on 2006-11-30
actually just found in adept as well another gcc n installed that as well but now the prev. prob is fixed but now if i press:

./configure .............then i get:

checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.

if press make i get:

bash: make: command not found


anybody some help?

thenx in advance!

---

### Post by po0f on 2006-11-30
cytutchi,

```
[FONT="Courier New"]$ sudo aptitude install build-essential[/FONT]
```

---

### Post by cytutchi on 2006-11-30
:):):):)
happy cytutchi now!
WORKING FIINNNEEEEEEE!!!!!!!!!!

:) 

thenx

---

### Post by The Iron Curtain on 2006-12-01
Exact same problem, except when I did
```

sudo aptitude install build-essential

```
 I get:

```

dfoer@dfoer-laptop:~$ sudo aptitude install build-essential
Password:
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavail able)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another proc ess using it?
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavail able)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another proc ess using it?
dfoer@dfoer-laptop:~$


```
Any help?
 Thank you!

---

### Post by LLRNR on 2006-12-01
You should close your Adept / Synaptic package manager first...

---

### Post by The Iron Curtain on 2006-12-02
Thank you!

---

