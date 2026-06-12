---
title: "terminal (with midnight commander) copy paste problem"
date: 2014-09-07
forum: General Help
---

### Post by budgerigar on 2014-09-07
When I use the terminal (I used LXterminal, although I have the problem with the others that I have tried), copying and pasting works fine, either with the mouse or keyboard.

It can take anything from a few minutes to about an hour of doing things when everything works fine, before suddenly any kind of pasting into the clipboard changes.

Whatever I paste has 0~ at the start and 1~ at the end, so if I copy

echo my name is budgie

it is pasted in the terminal as

0~echo my name is budgie1~

If I paste the same thing anywhere else, such as firefox, leafpad or even a new terminal window, the same copied or selected text will paste correctly without 0~...1~ added.


It is difficult for me to tell if this is a midnight commander problem or a terminal problem because I can't use the terminal for more than a few minutes without firing up mc to make navigating a lot easier. However, if this problem starts, then I exit mc, the same terminal will continue to mess up anything I paste. This had been happening on a recently installed Lubuntu 14.04 system, which broke a couple of days ago. I reinstalled everything, again a completely fresh installation. The problem is still here. Googling this problem is very difficult because google doesn't understand "0~" or "1~".

I have tried to keep a note of the last command performed before this problem arises, but there seems to be no link between this and the problem. It has happened after using "find", "rsync", "grep" and so on. Am I the only person in the world with this problem? I am tempted to think that this is a Lubuntu problem, but equally it could be midnight commander, even though the problem persists after exiting mc.

---

### Post by bapoumba on 2014-09-07
Probably this bug : [https://bugs.launchpad.net/terminator/+bug/1350334](https://bugs.launchpad.net/terminator/+bug/1350334)
Please also see here : [https://bugs.launchpad.net/terminator/+bug/1030562](https://bugs.launchpad.net/terminator/+bug/1030562)

---

### Post by budgerigar on 2014-09-08
Thank you very much. From the first link, it looks like this is a problem that could be sorted out, but probably won't be in the near future.

What I find really bizarre is that the command

printf "\e[?2004l"

pasted into the terminal where this problem happens, sorts this problem out, if only temporarily.

---

### Post by bapoumba on 2014-09-08
You are most welcome :)
I'm sorry I cannot help you further. Will test installing mc at some point.

---

