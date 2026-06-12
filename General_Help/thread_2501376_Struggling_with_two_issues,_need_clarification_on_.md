---
title: "Struggling with two issues, need clarification on what to do"
date: 2024-10-04
forum: General Help
---

### Post by wales4ever on 2024-10-04
Hello all, new user in peace.

I should say at the outset that I am not an Ubuntu expert but I am doing my best to learn and improve.

I have two issues with fixing two Ubuntu issues (ion an ASUS laptop, Windows 10 and runs on a Power Shell).

After I do 'apt update' the following error messages show up: 

**E: Could not open lock file /var/lib/dpkg/lock-frontend - open (13: Permission denied)**
[B]E: Unable to acquire the dpkg frontend lock (/var/lib/dpkg/lock-frontend) are you root?

[/B]I've since been told many things on other forums about this, from 'OMG your Ubuntu is screwed, nothing can fix this at all' to 'just do a reboot' and 'enter sudo install -D -m755 /var/lib/dpkg && sudo apt-get update will solve this' as well as 'All you have to do is to run the previous command by adding sudo in front of it. Please DO NOT change directory permissions, at least at this stage.'

It's annoying as I don't know who or what to believe, and none of the 'advice' comes from actual experts.

Therefore, if anybody does 100% know how to solve these issues and can tell me what to type in to Ubuntu in order to fix it, I would be grateful if that person could tell me.  

To the best of my knowledge, I've not done anything that I shouldn't (such as delete a file etc.) but Windows has been acting up on the laptop quite a bit recently and my ESET NOD 32 Antivirus can slow it down as well.

Many Thanks

Veryconfused(dot)com

---

### Post by nicolasdentremont on 2024-10-04
You'll have to run the apt update and apt upgrade command with sudo.

---

### Post by Norm24 on 2024-10-04
```
sudo apt update
```

---

### Post by grahammechanical on 2024-10-04
If you open Software & Updates>Updates tab you may find that Ubuntu is set to Automatically Check for Updates> Daily. While that check is taking place if we run the sudo apt update command we will get an error message saying could not open lock file. We have to wait until the automatic check is finished. I just thought it might be useful for you know this in case you get this similar error message.

Regards

---

### Post by wales4ever on 2024-10-05
Thanks for the help so far!

I've managed to remove the offending file and hopefully a reboot and update will fix it.

Fingers and other digits crossed.

---

