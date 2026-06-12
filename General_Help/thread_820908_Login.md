---
title: "Login"
date: 2008-06-06
forum: General Help
---

### Post by rlacroix8 on 2008-06-06
I am a newbie who just installed Ubuntu 8.04 within Windows XP on my Dell Latitude D810. When trying to boot Ubuntu, I am asked for a username and password. I remember to have given a password when starting the installation process, but NOT a username. I can now not get past this login screen - please help

---

### Post by lisati on 2008-06-06
Do you remember if you were you asked for your first name and last name, and what you entered? Try your first name as a user name.

---

### Post by rlacroix8 on 2008-06-06
Thanks. Did try my first name, both in all lower case and with initial cap; did not work.

---

### Post by rlacroix8 on 2008-06-06
Second reply to Lisati. On the bottom right of the login screen my machine seems to have been given the name "richard-laptop" I have tried this also as a user name, but that did not work either.

Richard

---

### Post by bodhi.zazen on 2008-06-06
Boot to recovery mode

Then, at the command line enter :

less /etc/passwd

Scroll up / down with the arrow keys, type q to quit. Your username will be in that file.

At the command line type :

reboot

---

### Post by HDave on 2008-06-06
Might be an easier way to do this, but reboot using the "safe mode" choice in the boot menu.  This will boot into a non-graphic environment that puts you at a terminal prompt.

Once you get to the prompt, do this:

```
 cat /etc/passwd
```

You will see a bunch of text where each row represents a user account and the user name is the first thing on each row.  Look through them (should be 10-20 users) and see if something jogs your memory.  Write it down and reboot normally by typing "exit".

---

### Post by lisati on 2008-06-06
> **rlacroix8 said:**
> Second reply to Lisati. On the bottom right of the login screen my machine seems to have been given the name "richard-laptop" I have tried this also as a user name, but that did not work either.

Richard

Just an aside: "richard-laptop" is your computer's name - mine nearly ended up with that name ("Lisati" is Samoan for "Richard")

How did you get on with the suggestions of booting in recovery mode?

---

### Post by rlacroix8 on 2008-06-06
Am going to try the recovery mode right now. However, am in XP, have to get out and boot Ubuntu. Will be back later, hopefully from within Ubuntu. In teh meantime, many thanks, particularly for my first lesson in Samoan!

---

### Post by bodhi.zazen on 2008-06-06
> **bodhi.zazen said:**
> Boot to recovery mode

Then, at the command line enter :

less /etc/passwd

Scroll up / down with the arrow keys, type q to quit. Your username will be in that file.

At the command line type :

reboot

> **HDave said:**
> Might be an easier way to do this, but reboot using the "safe mode" choice in the boot menu.  This will boot into a non-graphic environment that puts you at a terminal prompt.

Once you get to the prompt, do this:

```
 cat /etc/passwd
```

You will see a bunch of text where each row represents a user account and the user name is the first thing on each row.  Look through them (should be 10-20 users) and see if something jogs your memory.  Write it down and reboot normally by typing "exit".

We should have just :

```
ls /home
```

:lolflag:

---

### Post by lisati on 2008-06-06
> **rlacroix8 said:**
> Am going to try the recovery mode right now. However, am in XP, have to get out and boot Ubuntu. Will be back later, hopefully from within Ubuntu. In teh meantime, many thanks, particularly for my first lesson in Samoan!
You're welcome. 
(I'm not Samoan but my wife is)

---

### Post by rlacroix8 on 2008-06-06
Many thanks!! This worked, although I was initially thrown off by a screen that read: 

Recovery Menu

Resume >>>>>>>>> Resume Normal Boot
Root >>>>>>>>>>  Drop to Root Shell [this I choose]
xfix >>>>>>>>>>  Try to Fix X Server

My username was on the last line in that file. That same line had "User,,," Why the three commas?

Richard

---

### Post by rlacroix8 on 2008-06-06
Thanks, Tried this, but I do not have a "safe" mode in the boot menu. Instead I used the "recovery mode", see bodhi.zazen's reply abd that worked.

Again, thanks to all!

Richard

---

### Post by rlacroix8 on 2008-06-06
This comes from within Ubuntu. You were right originally; my first name is apparently my user name. Have no idea why this did not worked when, I believe, I tried it. Is there possibly a mximum number of tries at login allowed, after which the system does no longer respond?

---

### Post by bodhi.zazen on 2008-06-06
> **rlacroix8 said:**
> This comes from within Ubuntu. You were right originally; my first name is apparently my user name. Have no idea why this did not worked when, I believe, I tried it. Is there possibly a mximum number of tries at login allowed, after which the system does no longer respond?

No there is not, you can attempt a log in as many times as you like.

Linux is case sensitive and you may have inadvertently hit caps lock ? Not sure.

---

### Post by Joeb454 on 2008-06-06
I've never found there to be one :)

My username (as you may have guessed) is "joe"

It took me a while to get used to the way caps are handled in Linux

---

### Post by HDave on 2008-06-06
> **bodhi.zazen said:**
> We should have just :

```
ls /home
```

:lolflag:

I am truly embarrassed.

---

### Post by rlacroix8 on 2008-06-07
Dave and bodi... I am learning, thanks! Yes, ls /home is elegant. The name comes even up in [COLOR="Blue"]blue[/COLOR] 

Richard

---

### Post by rlacroix8 on 2008-06-07
Dave and bodi... I am learning, thanks! Yes, ls /home is elegant. The name comes even up in blue

Richard

---

