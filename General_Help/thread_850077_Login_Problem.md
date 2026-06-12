---
title: "Login Problem"
date: 2008-07-05
forum: General Help
---

### Post by DarknessEnemy on 2008-07-05
Hello

I screwed up my ubuntu recently, so I re-installed it. 

I was just playing around, then I reset it. I boot on ubuntu (Everything normal), but when I logged in, I get the wallpaper and panels, like I logged correctly, then the screen crashes, the screen goes black and takes me back to the login screen, I try again and the same happens. I don't get enough time to get to terminal, synaptic, etc. What should I do? Should I re-install it again? Is there a solution?

The last thing I did was open "new login", so took me back to login screen, so I logged again, I dont know if this was the problem.

PD: I have screw up a lot my ubuntu. So, maybe some people here knows me so Im sorry to disturb again. Im just plain no good.

Thanks in advance.

---

### Post by LinuxRocks713 on 2008-07-05
Is your disk full? Ubuntu (actually GNOME) has this bug where you can't login with a full disk.

Restart in recovery mode and show us the output of ```
df -h
```.

Else, your GNOME Config files may be bad. Try:

```

cd /home/*username*
mv -r .gnome2 .gnome2backup
mv -r .gnome2_private .gnome2privatebackup
# do the following one in recovery mode
cd /home/*username*
mv -r .gvfs .gvfsbackup
# now restart and login
sudo shutdown now -r

```

---

### Post by DarknessEnemy on 2008-07-05
How do I start on recovery mode? (maybe I should put this on absolute beginner).

And I dont think the disc is full. I took plenty of the disk space for it and its recently istalled.

---

### Post by firefox791 on 2008-07-05
I have a similar problem, except that i don't get to see anything more than the orange-beige-color befor i get a blank screen, and whoop-dee-do im back at the login.

I tried the Options > Sessions > GNOME failsafe, and i could login there, but i dont wont to permanently use the failsafe mode...

~fox

---

### Post by wolfe on 2008-07-07
I too am having this problem.  I can get into gnome in failsafe mode, compiz loads, kiba-dock loads, in fact all my startup items are there and work.  But whenever I log in to a regular gnome session, my computer reboots.

---

