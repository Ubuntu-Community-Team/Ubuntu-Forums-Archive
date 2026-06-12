---
title: "Chrome Remote Desktop Mouse Disappearing On 18.04"
date: 2018-11-13
forum: General Help
---

### Post by lyxandrah on 2018-11-13
Hey !

I've followed a guide on the internet to setup Chrome Remote Desktop on my laptop. Everything works fine except for one thing : the mouse cursor when remotely connected will randomly disappear. It doesn't seem to have any specific pattern but it tends to disappear whenever I open a window, whether it's a browser or anything else. It DOES seem to behave fine on built-in apps (Like Terminal or Nautilus/Dolphin).

Changing the Mouse Cursor theme seems to fix the issue for a few minutes but it comes back after a while.
What could fix that ?

Edit : I do not have a mouse attached to this laptop since it has a trackpad.

Oh and I'm using KDE Neon if that makes a difference

---

### Post by QIII on 2019-01-09
Hello!

This post should by rights be in the Other OSes (KDE Neon is Ubuntu-based, but is not Ubuntu), and it is also old and you may not even be around to see this answer -- or even care at this point.  However, I am going to leave it here for general information because this also affects Ubuntu *clients*, as in the machine from which one is working rather than the server being connected to.  This may also affect the behavior you are seeing on the server at the other end.

A colleague and I recently worked with a problem he was having with regard to Chrome Remote Desktop on his Ubuntu workstation.  There are apparently some regressions or newly introduced bugs that are causing a number of problems (his was launch icons for certain applications not working).

With a little bit of input on my part by way of suggestions -- but mostly his effort! --, diagnosis led to Chrome Remote Desktop as the culprit.  Then he found [this]("https://askubuntu.com/questions/963756/installing-google-chrome-remote-desktop-messed-up-my-box").

There are several possible corrective actions given, any of which may or may not work for particular cases.

My suggestion to him was to stop using Chrome Remote Desktop and I recommended NoMachine NX (free for personal use, but not open source) as an alternative now that it can also be installed on Windows, which is important to him because he is administering/accessing Windows machines from Ubuntu and Windows.  NoMachine NX has its own implementation of SSH built in , so he is also relieved of the necessity for pUTTY when he uses it from a Windows machine or tunneling VNC over SSH when using a Linux machine.

Cheers!

---

