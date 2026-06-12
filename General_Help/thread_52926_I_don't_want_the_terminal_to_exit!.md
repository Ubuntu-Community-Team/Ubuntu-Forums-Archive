---
title: "I don't want the terminal to exit!"
date: 2005-07-29
forum: General Help
---

### Post by dbcoder on 2005-07-29
Well, I have a small problem that hopefully one of you can help me with.


I'm making my fluxbox menu right now, and I have one command like [exec] (fortune) {gnome-terminal -e fortune}

The problem is that it when fortune ends, the terminal ends. All I want to know is if there is a way to keep that terminal open so I can enter more commands afterwards.

I have many terminal programs that do this, so it wouldn't just be for something trivial like fortune, it's just an example.

Thanks in advance.



EDIT: OOOps! I realized I put this the COMPLETE wrong section... I'm so sorry.  Admin, can you please move it?

---

### Post by garlito on 2005-07-30
You can create a new profile in gnome-terminal, called for example fortune-terminal. Then configure it to run a custom command instead the shell.

Write that command, named for example fortune-shell and put it in the PATH of executable files:

#!/bin/bash
fortune && exec bash

Finally your command will be:

gnome-terminal --window-with-profile=fortune-terminal

I hope this helps you and sorry my very bad english :)

---

