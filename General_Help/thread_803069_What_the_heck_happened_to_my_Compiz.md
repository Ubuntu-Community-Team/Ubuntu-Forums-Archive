---
title: "What the heck happened to my Compiz?"
date: 2008-05-22
forum: General Help
---

### Post by theShaggy on 2008-05-22
Okay, I've been running Hardy 64bit with not a single problem for nearly a month and a half.  I have a Nvidia 7300GS with the latest beta driver that has been running flawlessly.

Just about half an hour ago, however, I was playing City of Heroes with Cedega, which hasn't had graphics troubles since I upgraded to the beta driver.

Anyway, the game randomly hung on me (which hasn't happened since I installed more RAM), and when I rebooted the computer, Compiz is broken.

I don't just mean "it is mucked up until I restart it," I mean I have rebooted the computer three times, uninstalled and reinstalled Compiz, and searched what I can, but it is outright broken.

I try to use compiz --replace, but that just screws my screen up entirely, losing title bars and the Gnome panel.  I'm using Metacity and all my screenlets are cluttering me up at the moment.

I've tried reconfiguring Xorg, just to see what driver is running, but it doesn't get to the video options, it stops when I finish the keyboard stuff.

I'm completely lost.  What do I do?  Can someone give me some idea?  I was doing nothing out of the ordinary when this thing hit.

---

### Post by gnivler on 2008-05-22
Probably unrelated but my compiz works but stopped automatically starting today for a reason I haven't yet found.  I noticed there were some X updates, installed those earlier...  Searching threads for more troubleshooting info.

---

### Post by theShaggy on 2008-05-22
No that... doesn't help me at all.  As of now, my computer is completely unusable.

It looked as if my OpenGL was corrupt, so I reinstalled my Nvidia driver.

Now, when it books, it displays "Out of Range" on my monitor.  The login screen is there, I just can't find it.

Somebody please help!  Please help me.  My computer has completely melted on me for no reason that I can figure and I am on a seperate machine entirely now.

---

### Post by theShaggy on 2008-05-22
Okay, I seem to have solved it, I restored a month-old version of Xorg.conf.

I'm not sure what happened, but at least I've got it working now.

---

