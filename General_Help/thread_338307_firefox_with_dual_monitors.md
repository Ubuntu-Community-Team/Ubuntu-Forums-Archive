---
title: "firefox with dual monitors"
date: 2007-01-14
forum: General Help
---

### Post by zedd2006 on 2007-01-14
ok, i have a dual monitor set up where each monitor is it owns desktop, is there a way i can get firefox to open in my other monitor while its open in my first monitor? it always tells me that firefox is already running, i can close all firefox browsers and then open it in monitor 2, but then i cant open it in monitor 1, so im back tot he same problem, i cant have a browser open in both screens at once, is there a way to fix this?

---

### Post by bodhi.zazen on 2007-01-14
> **zedd2006 said:**
> ok, i have a dual monitor set up where each monitor is it owns desktop, is there a way i can get firefox to open in my other monitor while its open in my first monitor? it always tells me that firefox is already running, i can close all firefox browsers and then open it in monitor 2, but then i cant open it in monitor 1, so im back tot he same problem, i cant have a browser open in both screens at once, is there a way to fix this?

LOL

Open a new windows within firefox:

File -> New Window ...

---

### Post by majoridiot on 2007-01-14
> **bodhi.zazen said:**
> LOL

Open a new windows within firefox:

File -> New Window ...

you misunderstood the problem.  zedd can't open a second instance of firefox on screen 2 if
one is running on screen 1.

i've got a 3 head setup and it's the same... i can open any number of firefoxes on screens 1/2
(shared desktop) but can't open firefox on screen 3 if there is an open instance on 1/2-- and
vice versa.  i haven't found a way around this.  i'm assuming that it's due to firefox's inability
to communicate with itself between seperate x sessions.  just assuming, tho.

it would be great if someone has a way around this.  i haven't searched exhaustively for a fix,
as my screen 3 is normally running mythtv and it is only an occasional annoyance.

---

### Post by bodhi.zazen on 2007-01-14
Oh, why didn't you say so ....

In a terminal run:```
firefox -P
```

That will open your profile manager.

Create a new profile, say Test.

Then to open a new session:

```
firefox -P Test
```

You can have as many profiles as you wish.

The only problem is you will need to re-install themes and extensions for each profile ...

8)

---

### Post by majoridiot on 2007-01-15
> **bodhi.zazen said:**
> Oh, why didn't you say so ....

In a terminal run:```
firefox -P
```

That will open your profile manager.

Create a new profile, say Test.

Then to open a new session:

```
firefox -P Test
```

You can have as many profiles as you wish.

The only problem is you will need to re-install themes and extensions for each profile ...

8)

great info to know, thank you... but just a little off.

```
firefox -ProfileManager
```

to create a new profile and then-

```
firefox -P <profile>
```

to run a new instance of firefox with the new profile

---

### Post by zedd2006 on 2007-01-15
thanks guys

---

### Post by hfw on 2007-06-15
Just wanted to say thanks to the above posters.  I found myself having this same problem tonight.  I added the 

-P <profile> 

to the command line in the shortcut for firefox on my panel in my second monitor...very cool

---

