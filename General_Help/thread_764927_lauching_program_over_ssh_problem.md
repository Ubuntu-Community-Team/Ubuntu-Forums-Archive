---
title: "lauching program over ssh: problem"
date: 2008-04-24
forum: General Help
---

### Post by itix on 2008-04-24
Hi.
This is my situation; I am trying to launch a program called nclaunch, which is a unix program, and it's hosted by my school. I sign in to my client at school and navigate to the launch file folder and run the command nclauch -new & (which is a command to tell it to create a new project). That's where the issue is. I can get it to execute but not launch. Error code:

```
nclaunch: 05.50-p004: (c) Copyright 1995-2005 Cadence Design Systems, Inc.
Application initialization failed: no display name and no $DISPLAY environment variable

```

I guess I have to link X to the program somehow but I don't get how really.

---

### Post by HermanAB on 2008-04-24
This should work:
$ ssh -X -C -c blowfish joesoap@schoolserver "program"

Cheers,

Herman

---

### Post by itix on 2008-04-24
It did, thanx. However, I had to strip the "program"-part and navigate to the folder where it's located because my school has no binary link to the program.

EDIT: Hey! Have they removed the "thanx"-system? Why!? I liked the thanx-system
EDIT II: And where the hell is the "mark as solved"?? I want the old forum back!

---

