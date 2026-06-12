---
title: "Run Software Updates via Terminal Command?"
date: 2013-05-17
forum: General Help
---

### Post by tecknomage on 2013-05-17
I want to create a Launcher that runs **Software Update** via **Root Terminal**.

**I've tried:**

[LIST=1]
[*]/usr/lib/kde4/libexec/kdesu-distrib/kdesu gnome-terminal sudo apt-get update 
[*]/usr/lib/kde4/libexec/kdesu-distrib/kdesu sudo apt-get update 
[/LIST]

#1 just opens the **Terminal Dialog** but I don't see the command and results I get doing manually

#2 seems to do the update, but no **Terminal Dialog** at all

What is the correct command line that would show the **Terminal Dialog**, execute the command *sudo apt-get update*, AND show results :confused:

In other words, look exactly what I see if I run the command manually from Terminal.

---

### Post by snowpine on 2013-05-17
I personally use:

```
sudo apt-get update
sudo apt-get dist-upgrade
```

YMMV.

---

### Post by oldos2er on 2013-05-17
I type **i**, then **up**. In ~/.bashrc I have the alias ```
alias i='sudo -i'
```
In /root/.bashrc I have the alias ```
alias up='apt-get update && apt-get dist-upgrade'
```

---

### Post by tecknomage on 2013-05-17
> **snowpine said:**
> I personally use:

```
sudo apt-get update
sudo apt-get dist-upgrade
```

YMMV.

That's what you use in **Terminal manually**.

**For a launcher, the command is one-line.**

Something like *sudo **{?}** apt-get update*

What I need (*and forgot*) is **{?}**, the character or characters to run more than one command.  Note the placement of **{?}** could be wrong.

As I stated, launcher command-line *sudo apt-get update* seemed to work, but the **Terminal Dialog** _never opened_ to show command and results.

---

### Post by sync on 2013-05-18
To get commands to run in the terminal window that's opened, you need to use the -x flag.  So something like: "gnome-terminal -x sudo apt-get update && sudo apt-get dist-upgrade" should work.

edit: Of course if you're opening a root terminal then the sudo's shouldn't be necessary.

---

### Post by tecknomage on 2013-05-19
> **sync said:**
> To get commands to run in the terminal window that's opened, you need to use the -x flag.  So something like: "gnome-terminal -x sudo apt-get update && sudo apt-get dist-upgrade" should work.

edit: Of course if you're opening a root terminal then the sudo's shouldn't be necessary.

**That worked** \\:D/

Thanks.

---

