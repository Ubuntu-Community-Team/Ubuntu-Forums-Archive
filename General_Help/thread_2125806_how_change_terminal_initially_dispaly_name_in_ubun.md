---
title: "how change terminal initially dispaly name in ubuntu?"
date: 2013-03-15
forum: General Help
---

### Post by adasi on 2013-03-15
My ubuntu terminal show as

**mmh@mmh2-PC04:~$**

i want to change it as

**user@mmh2-PC04:~$**

please  help me?

---

### Post by CaptainMark on 2013-03-15
Do you mean the literal term user or do you mean your user name?

The way to do it is to open the file /home/[your user]/.bashrc and add the line:
 export PS1="insert bash prompt here"

just make up your bash prompt for your user, there are certain keywords you can use, [this site will generate bash prompt lines for you]("http://www.kirsle.net/wizards/ps1.html")

or you can add the line to the file /etc/bash.bashrc to make the prompt system wide for all users

---

### Post by vamp774 on 2013-03-15
I think the first portion is the user @ <machine_name> .  If you create a different user account you'll see that user @**mmh2-PC04**

---

