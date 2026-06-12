---
title: "Updating Package List - Extremely Slow"
date: 2014-02-21
forum: General Help
---

### Post by csavtche on 2014-02-21
Running ```
 sudo apt-get update
``` is a nightmare for me and I have no idea how to diagnose it. I was hoping to get some advice.

After getting/hitting/ignoring all the repos I get to "Reading Package Lists..." and this line literally takes 5 minutes. I'll be glad to supply files and lists. Thanks in advance.

---

### Post by ibjsb4 on 2014-02-21
Not much to go on.

Is this a fresh install?  First update is a big one.

What kind of processing power you got?  That can low things down.

Could be another download source would speed up that part.

What are you running?
```

lsb_release -a
```

---

### Post by csavtche on 2014-02-24
Ubuntu 13.04 - I update often.

Processing power is an interesting chuckle, it's definitely not that. I want to give you more to go on, and it's exactly why I'm here. If I knew what to look at I would look at it. What information would be helpful?

Things that would interest me - what happens during "Reading Package Lists...". Is apt going through dependencies? Is apt still pinging a repository? In other words, should I be looking for a slow, third party repo or is this a local package dependency issue?

---

### Post by csavtche on 2014-03-03
Bump, could anyone offer any advice?

---

### Post by ibjsb4 on 2014-03-03
13.04 has reached EOL.  Could be why updates are a problem.

[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

---

### Post by csavtche on 2014-03-06
A similar installation of 13.04 on other machines and virtual machines does not suffer puling repos. Thank you for the suggestion though....

I have a feeling it's one of the repos, how do I identify the problem repo? TIA

---

