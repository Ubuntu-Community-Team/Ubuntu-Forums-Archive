---
title: "Homebrew Removal Issue at Startup"
date: 2020-07-12
forum: General Help
---

### Post by jjhange on 2020-07-12
Hi, 
I'm running Ubuntu 20.04.

I recently removed Homebrew from my system and now after restart I'm getting the below error.  I've Googled this but unless I've missed it I haven't found much of a solution.  Could anyone here help?

> Error found when loading homejoe) profile:
home/user.profile: line 28: /home/linuxbrew/linuxbrew/bin/brew. No such file
or directory
As a result the session will not  configured correctly.
You should fix the problem as soon as feasible.

---

### Post by EuclideanCoffee on 2020-07-12
This happens at what point? After login? Is this terminal output?

Could you provide the later part of your bash_history, so it's easier to determine what was done to cause the issue?

---

### Post by Impavidus on 2020-07-13
Removing the software didn't remove references to it from your home directory. It appears there's such a reference in your .profile file. Open your .profile in your favourite text editor, scroll to line 28 and fix it.

---

