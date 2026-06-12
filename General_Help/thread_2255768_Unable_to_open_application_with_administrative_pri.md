---
title: "Unable to open application with administrative privilege"
date: 2014-12-07
forum: General Help
---

### Post by uzumakifahim on 2014-12-07
Hi,

I'm using Ubuntu 14.04 with just only one admin account. Previously, I needed to start "Geany" with administrative privilege. For that reason, I started Geany from terminal using "gksu geany" command. Now, I want to start Geany without administrative privilege. The problem is, when I simply click on the Geany icon it's giving me the following message :

```
Geany tried to access the Unix Domain socket of another instance running as another user.
This is a fatal error and Geany will now quit.
```

I just want to get rid of this annoying message and start Geany without any administrative privilege. Please help anyone to solve this.

---

### Post by ajgreeny on 2014-12-07
Do you get the same error if you start geany in terminal with command **geany**?

---

### Post by uzumakifahim on 2014-12-08
Thanks for the reply. No I don't get any error when I start Geany from terminal, but when I want to start Geany without terminal, I face this error message.

---

### Post by mc4man on 2014-12-08
Where is this icon that you are clicking on?

---

### Post by nerdtron on 2014-12-08
Geany could already be running another instance/process.

```
 ps aux | grep geany
```

Try to kill the pocess.

---

### Post by ajgreeny on 2014-12-08
Is it impossible to have more than one instance of geany running at any time?  I've never used it as far as I can remember, and have no idea if you can or not.

---

### Post by nerdtron on 2014-12-08
> **ajgreeny said:**
> Is it impossible to have more than one instance of geany running at any time?  I've never used it as far as I can remember, and have no idea if you can or not.

I'm not sure. But at least could be a reason why geany won't launch. Just suggesting ways to reduce the variables

---

### Post by uzumakifahim on 2014-12-10
> **nerdtron said:**
> Geany could already be running another instance/process.

```
 ps aux | grep geany
```

Try to kill the pocess.


This is the O/P and still showing the error message.

```
fahim     3451  0.0  0.0   4680   820 pts/1    S+   06:52   0:00 grep --color=auto geany

```

---

### Post by mc4man on 2014-12-10
> **uzumakifahim said:**
> This is the O/P and still showing the error message.

```
fahim     3451  0.0  0.0   4680   820 pts/1    S+   06:52   0:00 grep --color=auto geany

```
that means it's not running.

Could you post how you're starting geany as a user

If you go this what happens  - 
gtk-launch geany

If you log out &  into a guest session can you start geany normally?

---

