---
title: "Log-In No Longer Works..."
date: 2023-04-25
forum: General Help
---

### Post by hawghaven on 2023-04-25
Hello All,
I'm using Ubuntu-Mate 18.04 bionic with kernel 4.15.0-209
I can NO longer log in to the desktop. I get the login screen with my user name, then type my password and hit ENTER and the screen goes blank, The HDD spins up as if it was going to the desktop, then right back to the login screen. I can't get to the desktop.
However, I can go to another machine and use VNC to connect and get my desktop. Is there a quick fix to this problem?
I can post any other info you need to solve this issue. This has been going on now for about a week and I have re-booted many times. Same issue.
Please help...
I'm good at CLI if I need to run code.

THANKS

---

### Post by ActionParsnip on 2023-04-25
18.04 is end of life in less than a week. You may want to use this a catalyst to upgrade to a newer release

---

### Post by hawghaven on 2023-04-25
> **ActionParsnip said:**
> 18.04 is end of life in less than a week. You may want to use this a catalyst to upgrade to a newer release

I have Ubuntu Pro installed. I'm good until 2028. Happy w/ what I have!

---

### Post by #&amp;thj^% on 2023-04-25
So many things cause this, and may require a lot of questions so hang in there.
First go to is show us this:
```
ls -la
```
Second is Nvidia involved?
and a bit deeper show this: >(permissions on the /tmp directory,)
```
cd /
ls -la
```
Next is space an issue?:
```
df -h ~

```
all space check:
```
df -h 

```

---

### Post by hawghaven on 2023-04-25
> **1fallen said:**
> So many things cause this, and may require a lot of questions so hang in there.
First go to is show us this:
```
ls -la
```
Second is Nvidia involved?
and a bit deeper show this: >(permissions on the /tmp directory,)
```
cd /
ls -la
```
Next is space an issue?:
```
df -h ~

```
all space check:
```
df -h 

```


1Fallen, Thank you for your help. I SOLVED the problem with the first command. I noticed all files belonged to me EXCEPT .Xauthority which belonged to ROOT.
I changed it to me and login works fine again. No Nvidia involved, and space is good.
I will mark this post as SOLVED.

---

