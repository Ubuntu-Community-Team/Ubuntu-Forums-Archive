---
title: "Advice: from Mint to LUBUNTU on new notebook"
date: 2013-08-25
forum: General Help
---

### Post by vittorio2 on 2013-08-25
Hi there! :D
i'm new to this forum, not so much to the linux world. i got an acer notebook (v3-571G) dual booted with windows7+mint13
my graphic card is a NvidiaGeforce630M with optimus technology, and i have read about the lack of compatibility of these cards with linux: i tried to install "bumblebee" to disable it and save energy because i noticed a huge decrease of battery life compared to windows7 sessions. 

something strange happened, now my mint has a strange appearance, similar to GnomeClassic, i don't like it so much (i choosed mint 'cause i love cinnamon), battery life isn't much longer than before,  and i was thinking about to switch to Lubuntu

i know it's so much lighter, i like LXDE appearance, and i would like to ask you if it's reccomended to use such a distro on a new pc, especially to save battery life.

i don't need particular programs to run on linux session, i just need chromium and libreoffice

What do you think about it? :P

---

### Post by Boab1993 on 2013-08-25
Hi vittorio2,
Lubuntu has a great enviroment if all you care about is speed and efficiency for programs such as chromium or office.

However since your coming over from mint, bare in mind that Lubuntu is not as graphically editable as mint, it takes alot of effort to make it look 'good'.

Try looking at Xubuntu, it is built to be lightwieght and energy efficient but is far more pleasing to eye, so i hear.

---

### Post by vittorio2 on 2013-08-25
thank you for your reply boab! 
i tried for a long time ubuntu and xubuntu, i like them but i just want to have the longest possible battery life and lubuntu seems the best one :D

about customization, that's not a problem, i don't care so much about graphical effects and the "untouched" LXDE would not be a problem

i read that xubuntu is now less lighter than the past, it's too much similar to ubuntu because of its many libraries in the recent versions

so, my doubts are about the graphic card... in lubuntu will i have better performance?

---

### Post by Boab1993 on 2013-08-25
Your correct lubuntu will be the one with the best battery life and performance.

I use Lubuntu on my netbook which is from 2008 has the basic intel Atom and no GPU, it has a battery life of 4 hours and has performance almost better than my desktop PC on windows 7 - which has a quad core processer, a SSD etc.

So yes its a very light and handy desktop if all you care about is efficiency.

---

### Post by 3rdalbum on 2013-08-25
Whoa, whoa, whoa. Hold on a moment. Let's go less drastic.

Rather than remove Linux Mint and install Lubuntu to get a lighter desktop, why not just install LXDE?

```
sudo apt-get install lxde
```

At the Linux Mint login screen you can choose LXDE.

Linux Mint, Ubuntu, Lubuntu and every other *buntu share exactly the same base system. Taking Linux Mint and running LXDE will give you the exact same level of performance as installing Lubuntu, because the desktop is the only difference.

Also, LXDE itself will be a bit more responsive than Cinnamon, but it won't make your programs run much faster on a modern computer. Which yours is. But you can certainly try it, it doesn't cost anything and there's no risk to installing a different desktop.

---

### Post by vittorio2 on 2013-08-25
> **3rdalbum said:**
> Whoa, whoa, whoa. Hold on a moment. Let's go less drastic.

Rather than remove Linux Mint and install Lubuntu to get a lighter desktop, why not just install LXDE?

```
sudo apt-get install lxde
```


i'm going to try it now! :D 

i'll let you know friends :biggrin::biggrin:

---

### Post by Boab1993 on 2013-08-25
> **3rdalbum said:**
> Whoa, whoa, whoa. Hold on a moment. Let's go less drastic.

Rather than remove Linux Mint and install Lubuntu to get a lighter desktop, why not just install LXDE?

```
sudo apt-get install lxde
```

At the Linux Mint login screen you can choose LXDE.

Linux Mint, Ubuntu, Lubuntu and every other *buntu share exactly the same base system. Taking Linux Mint and running LXDE will give you the exact same level of performance as installing Lubuntu, because the desktop is the only difference.

Also, LXDE itself will be a bit more responsive than Cinnamon, but it won't make your programs run much faster on a modern computer. Which yours is. But you can certainly try it, it doesn't cost anything and there's no risk to installing a different desktop.

Hmm, i didnt know this actually.

I always thought that vanilla lubuntu vs lxde mint, lubuntu would always win due to it being built for the job.

I might actually try this myself later, lubuntu gets very dry after a while.

Always learning.

---

### Post by oldrocker99 on 2013-08-25
There is virtually zero risk in installing a different desktop in Linux; the worst thing that might happen is that the desktop might not work, at which point CTRL-ALT-DELETE will almost always bring up a Log Out? command. If it doesn't, try CTRL-ALT-F1 to open a new console, which you'll need to log into, and then issue "sudo shutdown -r now" to reboot. 

This is what happened to me when I installed KDE 4.11, which (for some reason) just put up the System Settings window for a desktop, with no menu, etc. While it's a pain to reboot, it's WAY better than hitting the reset button or cycling the power. CTRL-ALT-F1 can be a lifesaver if you get a hard lockup as well. Keep it in your arsenal!

---

