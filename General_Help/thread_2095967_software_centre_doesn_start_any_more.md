---
title: "software centre doesn start any more"
date: 2012-12-18
forum: General Help
---

### Post by Sander Malschaert on 2012-12-18
I've tried to install skype in ubuntu 12.04 like this:

[https://help.ubuntu.com/community/Skype](https://help.ubuntu.com/community/Skype)

After the first step thinks have taken a turn for the worse however. At the moment I can't open the software centre any more. I have an error message in the top right of task bar that reads:

An error occurred, Please run Package Manager from the right-click menu or apt-get in a terminal to see what's wrong. The error message was: 'Error: Opening the cache (E: Malformed line 56 in source list /etc/apt/sources.list (dist parse), E:The list of sources could not be read., E:The package list or status file could not be parsed or opened.)'. This usually means that your installed packages have unmet dependencies

line 56 in the sources.list file now reads:

deb [http://archive.canonical.com/](http://archive.canonical.com/) partner

what am I missing here?

---

### Post by plucky on 2012-12-18
> **Sander Malschaert said:**
> I've tried to install skype in ubuntu 12.04 like this:

[https://help.ubuntu.com/community/Skype](https://help.ubuntu.com/community/Skype)

After the first step thinks have taken a turn for the worse however. At the moment I can't open the software centre any more. I have an error message in the top right of task bar that reads:

An error occurred, Please run Package Manager from the right-click menu or apt-get in a terminal to see what's wrong. The error message was: 'Error: Opening the cache (E: Malformed line 56 in source list /etc/apt/sources.list (dist parse), E:The list of sources could not be read., E:The package list or status file could not be parsed or opened.)'. This usually means that your installed packages have unmet dependencies

line 56 in the sources.list file now reads:

deb [http://archive.canonical.com/](http://archive.canonical.com/) partner

what am I missing here?


It should be ```
deb http://archive.canonical.com/ubuntu precise partner
```

Edit the **/etc/apt/sources.list** file and correct

Good Luck

---

### Post by Sander Malschaert on 2012-12-18
It looks like I have to log in as root to do so since atm I don have the permissions. Or is there a better way to circumvent this?

---

### Post by plucky on 2012-12-18
> **Sander Malschaert said:**
> It looks like I have to log in as root to do so since atm I don have the permissions. Or is there a better way to circumvent this?

Why do you have to login as root?

Can you not use ```
gksudo gedit /etc/apt/sources.list
```

Good Luck

---

### Post by Sander Malschaert on 2012-12-18
@plucky Thanks for the help! I used "sudo gedit" command to edit sources.list and software centre is working fine again. Funny thing is that I still don't see skype in the software centre. I'll consider this one solved though.

edit: you may have noticed that I'm at the bottom end of my ubuntu learning curve here ;) No worries though I'll get there in the end.

---

### Post by plucky on 2012-12-19
> Funny thing is that I still don't see skype in the software centre. I'll consider this one solved though.

Skype should be in the **Partner** repository,so if you open Software Sources and make sure the **Partner** repository is enabled and then run ```
sudo apt-get update
``` it should then appear in **Software Centre**

Good Luck

---

