---
title: "How do you execute a command before shutdown?"
date: 2007-03-21
forum: General Help
---

### Post by will_in_wi on 2007-03-21
I want to have a command run automaticly when a user clicks shutdown. In gentoo you can add the command to /etc/conf.d/rc.stop. Is there any equivelent in ubuntu?

Thanks

---

### Post by raja on 2007-03-21
I think what you want is /etc/init.d/halt

---

### Post by will_in_wi on 2007-03-21
That could do it, but I would rather not edit a file in init.d if possible because it gets replaced on updates. Is there a file that is meant for this task? What does /etc/rc.local do? This is not on my computer so I don't to make a hack because it would fail in the long run.

Thanks

---

### Post by scxtt on 2007-03-21
can't you put a script in /etc/rc6.d/ to be run when you switch to that runlevel? - if 6 is the "shutdown" runlevel ... i can't remember w/ all the HP/Linux/Sun we have here @ work :p

edit: doh, guess that's just too obvious for me (that it's 0) :p -- and i do mostly rebooting at work, halting is a rarity ...

---

### Post by astoltz on 2007-03-21
runlevel 0 is "halt" and 6 is "reboot".  There is a utility which will assist in adding scripts to the various /etc/rc*.d/ directories. ```
man update-rc.d
```

---

### Post by will_in_wi on 2007-03-21
I will make an initscript to run on shutdown, but isn't there something easier? Is there enough time before feisty to make an intiscript that is part of the default install that simply runs the commands in /etc/default/rc.start on startup and the commands in /etc/default/rc.stop on shutdown? This would help a lot of people I think.

Thanks

---

### Post by will_in_wi on 2007-03-21
I made an initscript that does what I want. Is there any chance of getting this into feisty? It consists of three text files that by default do absolutely nothing.

I am posting this here in hopes that others can improve this. I think that this is so trivial and so powerful that maybe an exception can be made for it. It probably needs a tad bit of cleanup.

Instructions are to edit /etc/default/admin.start or stop and add the needed commands then add the admincommands initscript to your runlevels.

I made a feature spec here: [https://blueprints.launchpad.net/ubuntu/+spec/initscript-for-admin-commands/](https://blueprints.launchpad.net/ubuntu/+spec/initscript-for-admin-commands/)

How do I contact an admin who can do this?

Thanks a lot.

---

