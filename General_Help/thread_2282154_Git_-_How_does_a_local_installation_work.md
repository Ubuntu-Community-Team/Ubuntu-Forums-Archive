---
title: "Git - How does a local installation work"
date: 2015-06-12
forum: General Help
---

### Post by Drenriza on 2015-06-12
Currently i am trying to figure out how a local installation of Git works.

I am not entirely sure what questions i should ask, because i think so far Git is flighty in how it actually works / functions.

As i understand when you install the "git-core.deb" package you install a local version of git
**Note. Though i don't understand the description i apt-cache ***git-core - fast, scalable, distributed revision control system _(obsolete)_*

The local installation can than be used as a local revision system.

[LIST]
[*]Where does Git store the committed local data?
[LIST]
[*]Does it store the data in the folder you initialized as the Git repository which is linked to a local DB?
[LIST]
[*]git init /path
[LIST]
[*]If data are stored in the local init folder and not linked to a DB (with its own table), how does it distinguish different versions of what you commit?
[/LIST]
[/LIST]
[/LIST]

[*]What kind of database (if any) does git-core install on your local system?
[LIST]
[*]Is it a smart text file, NOsql, MySQL, PostgreSQL / something else?
[/LIST]
[/LIST]

---

### Post by TheFu on 2015-06-15
There are a few youtube videos which introduce git nicely. Most of the workflow for git is a "social agreement."  There isn't any "master" - just an agreement what Joe has the master repo. Your repo and Joe's repo aren't any different, so if you do better work or Joe gets tired, then everyone can switch to using your repo as the "official project repo" ... it is purely an agreement.

You'll want to use a shell, not a GUI to get the most understanding. The **pwd** is absolutely critical to using git.

Randall Schwartz has the good intro video which will explain what you ask. There is also a free PDF ebook Pro-GIT.

Oh - and networked use of git is dependent on ssh and ssh-keys. For a singly person setup, there isn't any need to use ssh.

Which other VCS have you used? Which DVCS have you used?

---

