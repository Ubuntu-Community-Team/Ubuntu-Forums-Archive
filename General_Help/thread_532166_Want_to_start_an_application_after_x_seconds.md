---
title: "Want to start an application after x seconds"
date: 2007-08-22
forum: General Help
---

### Post by wconstantine on 2007-08-22
Hey. I got a little problem when I start the computer. I want my conky to start some seconds after in sessions so it gets into the right position. Otherwise gnome panel will overlap my conky.

Do someone know a way to make an app start after some seconds instead of at once?

I've tried with:
sleep 5 -c conky -c .conkyrc

But conky doesn't start by that.

---

### Post by wconstantine on 2007-08-22
Solved it!

I created a file named conky.sh with the contents:

#!/bin/bash

sleep 10

conky

And then I put the filename in sessions.

---

