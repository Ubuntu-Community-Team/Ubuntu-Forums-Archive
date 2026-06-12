---
title: "Changed username, can't login"
date: 2008-02-14
forum: General Help
---

### Post by Trevorius on 2008-02-14
When I installed my current version of Kubuntu, I made a slight typo on my username, (one so  letter off) and eventually it bugged me enough that I tried changing it. 

On my first reboot after changing it, it kept saying "login failed", so like someone here suggested in anther thread, I changed it bak by logging in in recovery mode and editing "/etc/passwd" back to my old username. Now it accpets the password, but when loading, it says "can't start Kstartupconfig, check installation".

I'm hoping I don't have to reinstall, because this is the most functional of the four installations I've had since moving to linux (1x Sabayon 2x U gutsy 1x Ku gutsy)

Prolly won't make a difference, buy specs for notebook are 1.8 Ghz x2 64, 2 GB ram, Nvidia GO 7600 graphics, 160 GB HDD @  5400 rpm.

---

### Post by dcstar on 2008-02-14
> **Trevorius said:**
> When I installed my current version of Kubuntu, I made a slight typo on my username, (one so  letter off) and eventually it bugged me enough that I tried changing it. 
.......

How?

---

### Post by Trevorius on 2008-02-14
I just went into the user accounts menu, clicked on my username, and added the extra letter to it.

---

### Post by farruinn on 2008-02-14
What changes exactly did you make to /etc/passwd?

---

### Post by Trevorius on 2008-02-15
In the two instances where my username appeared (both in the last line) I removed a letter to make it my old username.

---

### Post by Sokertes on 2008-02-15
you may have to boot into recovory and look at the /home dir to see what your home dir name is set at. 

Been there and done that. Not thinking before hitting enter. Either lack of sleep or lack of caffine. Hey it's my story and I'm sticking to it


Sokertes

---

### Post by Nevermind042 on 2008-02-15
> **Sokertes said:**
> you may have to boot into recovory and look at the /home dir to see what your home dir name is set at. 

Been there and done that. Not thinking before hitting enter. Either lack of sleep or lack of caffine. Hey it's my story and I'm sticking to it


Sokertes

I am having the same problem, only I'm not sure how to "boot into recovory and look at the /home dir". I know how to boot into the Terminal then I type cd /home

but then what?

---

### Post by Nevermind042 on 2008-02-15
found the solution... I think.

Had to go into terminal, typed
cd (which brought me to home)
dir (which listed all directories)
mv <previous user name> <target user name> (which renames the folder)

and it logged in like a charm!

---

### Post by Trevorius on 2008-02-15
> **Nevermind042 said:**
> found the solution... I think.

Had to go into terminal, typed
cd (which brought me to home)
dir (which listed all directories)
mv <previous user name> <target user name> (which renames the folder)

and it logged in like a charm!
I offer my sincerest, most heart-felt thanks!!

---

### Post by Trevorius on 2008-02-15
For some reason, I assume due to my recent troubles, I haven't been able to open adept package manager or Konsole. When trying to open adept, it just sits there trying to load for about 30 seconds, then just stops. Konsole gives the message, "Konsole is unable to open a PTY (pseudo teletype). It is likely that this is due to an incorrect configuration of the PTY devices. Konsole needs to have read/write access to the PTY devices."

Anyone know what's going on with this (or how to fix it)?

---

### Post by Trevorius on 2008-02-16
I also can't open wine aparently...

---

### Post by farruinn on 2008-02-16
It sounds like you've really botched your user settings/permissions/etc. I would recommend creating a new administrative user, if you can do that.

---

### Post by Trevorius on 2008-02-18
I don't seem to be able to do it graphically, and I'm not sure how to do it using the teminal (which would also be difficult without Konsole). Isn't there any was I can just go in and edit the affected configuration files?

---

### Post by Trevorius on 2008-02-18
Any help would of course be most appreciated! :KS

---

### Post by farruinn on 2008-02-19
With the useradd command you can create a new user (read up on the man page to find out what flags you need and whatnot, let us know if you still need help though). Then with the command visudo you can modify the sudoers file (give the new user sudo rights). visudo will put you in the vim editor, so if you're not comfortable with that practice a bit first.

If you find you need to change your username or something about your user again in the future, you might try the usermod command.

---

