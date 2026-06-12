---
title: "How to prevent screenshots from being taken..?"
date: 2013-04-03
forum: General Help
---

### Post by KingNeil on 2013-04-03
Is there any modification I can make to the Ubuntu operating system, or program I can install.. to prevent screenshots from being taken..? Like, not just with PRINT SCREEN or any particular program... but just, prevent it from working, period..?

It's probably not possible, because the pixels are rendered, and thus, I assume they could be captured... but still, I thought I would ask...

Here is a StackOverflow thread on the topic, but I think it's Windows oriented

[http://stackoverflow.com/questions/455623/how-can-i-prevent-users-from-taking-screenshots-of-my-application-window](http://stackoverflow.com/questions/455623/how-can-i-prevent-users-from-taking-screenshots-of-my-application-window)

---

### Post by CaptainMark on 2013-04-03
Try removing the package gnome-screenshot, that *may *work although you might find that the whole gnome base depends on it, so if you get a whole load of other packages about to be removed, i wouldn't bother

EDIT: I just tried another easier way that works and doesn't involve removing vital packages,```
sudo chmod 000 /usr/bin/gnome-screenshot
```

---

### Post by KingNeil on 2013-04-03
OK, thanks... But the question is... could somebody still just use their own custom program to take a screenshot...?

Like.. could a hacker just install a program, other than gnome-screenshot, that would still allow them to secretly take periodic screenshots after hacking the computer, as we saw with the Stuxnet virus etc..?

---

### Post by Cheesemill on 2013-04-03
If a hacker gets into your system to the point that they can install software it's already too late, nothing you do can change this.

---

### Post by CaptainMark on 2013-04-03
And if a hacker has breeched your system up to the point where he/she can install programs on your system, then screenshots are the least of your worries. Your metaphorical boat is sunk and you're still trying to pump water out. Also if a hacker was in your system he can easily just broadcast your entire screen session without additional software anyway so your not going to stop them that way.  Your best bet is to lock down any wireless networks with as much security as you can, and make sure that if you are messing around with any external networking tools like ssh over the internet then study study study, make sure you know exactly what you're doing before you do it.

---

