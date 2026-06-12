---
title: "two failed upgrades..."
date: 2006-10-27
forum: General Help
---

### Post by Zaskoda on 2006-10-27
So I tried upgrading to edgy on two machines.. both failed. :(

Laptop will boot, but only to prompt. Xserver fails to launch...

Server won't boot... 

Gonna start with the laptop I guess. When it tries to boot a text screen with screwed up characters tells me x failed to load and asks me if I wanna see the output... when I say yes it just goes to another blank screen with an ok button.

StartX from the prompt errno 111 - connection refused - unable to connect to X server... no such process. etc.

Where do I even begin?

---

### Post by Zaskoda on 2006-10-27
Holy crap, easy fix...

sudo apt-get install xorg

Wonder what else didn't get upgraded right ;)

---

