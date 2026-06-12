---
title: "How can I update Wine 0.9.95 to version 1.0?"
date: 2008-05-17
forum: General Help
---

### Post by Johnson on 2008-05-17
How can I do that most easy way? I'm a pretty fair newbie.

Want to update my current Wine I got from doing
sudo apt-get install Wine

The version I have is 0.9.95
But I hear the version 1.0 is out, but how I get that without doing it all messy?

---

### Post by ibuclaw on 2008-05-17
Wow... that was quicker than I expected (I must have been day dreaming the last several months!)
I still remember when it was 0.9.46!

Erm... to answer your question (I'm just doing it myself right now) :D

Read here:
[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

```

wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -
sudo wget http://wine.budgetdedicated.com/apt/sources.list.d/hardy.list -O /etc/apt/sources.list.d/winehq.list
sudo apt-get update
sudo apt-get install wine

```

Regards
Iain

---

### Post by kostkon on 2008-05-17
Assuming you are using Hardy, [you can add the *Wine* repository to your software sources list]("http://www.winehq.org/site/download-deb") and then install it from *Synaptic*.

Alternatively, you can grab the deb from the [*The WineHQ .deb packages archive*]("http://wine.budgetdedicated.com/archive/index.html").

And actually, the 1.0-rc1 is out, not the 1.0.

---

