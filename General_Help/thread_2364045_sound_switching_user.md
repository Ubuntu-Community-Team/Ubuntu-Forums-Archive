---
title: "sound switching user"
date: 2017-06-17
forum: General Help
---

### Post by Skaperen on 2017-06-17
i have had this long problem where sound cuts off when switching user in Unity.  sound seems to follow the instance of X that "owns" the console.  so i am thinking that i could get one of those USB sound "card" devices.  maybe Unity would not try to move it to a switched user?  any ideas?  anyone know what it would do?  also, any suggestion to get one that works in Linux.  i am running 16.04.2 LTS (Xenial Xerus) Desktop, updated within the last week.

my goal is to play music that is not interrupted when i switch user.

---

### Post by Skaperen on 2017-07-26
the "fix" is to run pulseaudio in "system mode".  there are lots of warnings about "system mode" but decided it was for me, deployed it, and am enjoying it.

here is the answer i got on the stack exchange site askubuntu:

[https://askubuntu.com/questions/939144/playing-audio-stops-in-unity-when-i-switch-user](https://askubuntu.com/questions/939144/playing-audio-stops-in-unity-when-i-switch-user)

---

