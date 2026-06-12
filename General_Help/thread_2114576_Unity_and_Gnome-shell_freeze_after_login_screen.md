---
title: "Unity and Gnome-shell freeze after login screen"
date: 2013-02-10
forum: General Help
---

### Post by chrisguitar on 2013-02-10
Hello everyone,

i have the following problem:

Yesterday my laptop (Lenovo Thinkpad Edge E320, Ubuntu 12.04) crashed and now it freezes after the login screen everytime i use gnome-shell, gnome classic (with effects) or Unity.
I can see the top-bar (without any icons) and the quickstart-bar on the left (in Unity). I can also see a message telling me, that i am now offline, when no Wifi is reachable. In this state it freezes and i can only move the mouse
Gnome classic (no effects) and Unity 2D (and regular Unity in recovery mode) work fine.
What are the ressources which Unity and gnome-shell but not Gnome classic (no effects) and Unity 2D use?
Some x.org stuff?

I already tried unity --reset it didn't help.

A day before this i had a botched apt-get upgrade. I had to interrupt it, after it didn't respond anymore. Afterwards gnome-shell didn't work anymore (because it was partly updated to 3.6 in this process) but Unity worked fine.
I could successfully finalize the upgrade through apt-get dist-upgrade in Unity and gnome-shell worked again afterwards.

I thought everything was fine until my laptop froze and i am in this situation now.


Can anyone help?

---

### Post by chrisguitar on 2013-02-10
Maybe compiz is the cause for this problem (but i'm not sure).

When i execute unity --reset in unity 2D get errors like those in the linked image.
[http://dl.dropbox.com/u/20762665/Foto%2010.02.13%2022%2008%2048.jpg]("http://dl.dropbox.com/u/20762665/Foto%2010.02.13%2022%2008%2048.jpg")

EDIT: well maybe the reason for this is, that i executed the command in unity 2D...

---

### Post by chrisguitar on 2013-02-11
Can anyone tell me at least what the ressources are that Unity/Gnome 3/Gnome classic use, but which are not used by Unity 2D/Gnome classic (no effects)?

That would help me to localize the error.

---

### Post by fdrake on 2013-02-11
> **chrisguitar said:**
> Hello everyone,

i have the following problem:

Yesterday my laptop (Lenovo Thinkpad Edge E320, Ubuntu 12.04) crashed and now it freezes after the login screen everytime i use gnome-shell, gnome classic (with effects) or Unity.
I can see the top-bar (without any icons) and the quickstart-bar on the left (in Unity). I can also see a message telling me, that i am now offline, when no Wifi is reachable. In this state it freezes and i can only move the mouse
Gnome classic (no effects) and Unity 2D (and regular Unity in recovery mode) work fine.
What are the ressources which Unity and gnome-shell but not Gnome classic (no effects) and Unity 2D use?
Some x.org stuff?

I already tried unity --reset it didn't help.

A day before this i had a botched apt-get upgrade. I had to interrupt it, after it didn't respond anymore. Afterwards gnome-shell didn't work anymore (because it was partly updated to 3.6 in this process) but Unity worked fine.
I could successfully finalize the upgrade through apt-get dist-upgrade in Unity and gnome-shell worked again afterwards.

I thought everything was fine until my laptop froze and i am in this situation now.


Can anyone help?

since your proble is relate to an upgrade why don't you try to see if it's still persisting:
```

sudo apt-get upgrade && sudo apt-get update

```

---

### Post by chrisguitar on 2013-02-11
Thanks for the reply.

I already did this.
I re-installed Unity and compiz.
I ran a package-repair.

Nothing helped.

This is the 4th time my ubuntu-system got maneuvered into a state which required a re-install.
I gave up now and installed Mint.

Everything is like 3 times faster now.
Good bye Unity, i tried my best to like you...

---

