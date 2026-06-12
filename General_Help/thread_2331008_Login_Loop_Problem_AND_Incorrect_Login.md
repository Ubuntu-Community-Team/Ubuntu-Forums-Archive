---
title: "Login Loop Problem AND Incorrect Login"
date: 2016-07-17
forum: General Help
---

### Post by porty6600 on 2016-07-17
Hi, I'm pretty new to Ubuntu, so please have some mercy on my newbness. I am having the login loop problem, and I can't even log in as a guest. So I was doing some research and found that first I need to hit Ctrl+Alt+F1 and try to log in there. The problem is that it keeps saying I have an incorrect login even though I'm inputting everything correctly. I read that this can be fixed from the terminal... Which I can't access. Any ideas of what I should do? It seems like I'm in a real mess.

---

### Post by porty6600 on 2016-07-17
Ok, so I actually am now able to log into the tty1 thing. So I have the terminal. What now? Something about .Xauthority?

---

### Post by steeldriver on 2016-07-17
Start by looking at permissions and ownership

```

ls -l ~/.Xauthority

```

also those of the .ICEauthority and whole home directory just in case

```

ls -l ~/.ICEauthority

ls -ld ~

```

---

### Post by porty6600 on 2016-07-17
Ok... I have a new problem now. I ran the following lines of code, thinking I could reinstall Unity:

sudo apt-get purge unity gnome-shell lightdm

sudo apt-get clean

sudo apt-get autoremove

sudo apt-get -f install

This suggestion had four upvotes, but on reflection, it seems like it was a stupid thing to do. Now I can't run commands like sudo apt-get update or anything without getting authentication errors. What should I do to fix this problem?

---

### Post by xeddog on 2016-07-17
See if this [https://ubuntuforums.org/showthread.php?t=2330790]("https://ubuntuforums.org/showthread.php?t=2330790") helps.

If you think it might, then boot to the recovery console, enable networking, then drop to root prompt and try from there.


Wayne

---

### Post by grahammechanical on 2016-07-17
Have you run the Ubuntu live session and backed up your data? You should do so. Re-installing might prove to be the simplest & quickest way to solve this.

---

### Post by misfitpierce on 2016-07-18
Agreed with running live session and backing up data then reinstalling. Much less painful unless of course you want to learn to fix things in ubuntu yourself in which case, theres no better way to understand ubuntu than fixing issues right out of the gate but if it gets to be too much and feels frustrating i'd go with grahammechanical's suggestion.

---

### Post by porty6600 on 2016-07-20
test

---

### Post by porty6600 on 2016-07-20
Well that one made it through! No 403. Nothing else though yet...

---

### Post by porty6600 on 2016-07-28
I ended up backing up my data, completely removing Ubuntu from my system, and doing a fresh install of 16.04. I've gotten everything set up the way I like, but now I'm having a couple of weird bugs that are really annoying. Basically every time I try to login, it either freezes on the login screen before I can start typing, or after I enter my password and hit enter, it will just show the desktop background and nothing else. I have to do a hard shutdown, then start it back up. Then after I login I'll gave to hit a few keys on my keyboard and wiggle my mouse to get the launcher and panel to show up. But waking it from sleep on subsequent startups, it freezes at some point. This is all on a fresh installation. I have forgotten to mention that I dual boot with Windows 10, if that helps any. Any help will be appreciated. :)

---

