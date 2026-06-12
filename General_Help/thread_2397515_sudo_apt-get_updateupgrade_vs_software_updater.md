---
title: "sudo apt-get update/upgrade vs software updater"
date: 2018-07-30
forum: General Help
---

### Post by Taylz on 2018-07-30
Hi all,

Why is it that when I go to the software updater to see if there are any updates available it reports to me that the system is up-to date, yet when i run sudo apt-get update --> sudo apt-get upgrade there appears to be updates? I also find it's sometimes the other way around too. The command line update will report nothing to update and the system updater does report a couple of updates.

What's the best method for ensuring everything is up-to-date?

Regards,

Tayl.

---

### Post by TheFu on 2018-07-30
The GUI tools expect that update was run already that day, earlier. As updates pass QA, they are made available, so depending on where you are in the world, there are probably different teams working and releasing.

Personally, I update once a week.  That way, if there are issues immediately after performing the updates, it is easier to trace.

Here's what I think people should do to maintain their Linux desktops.
[http://blog.jdpfu.com/2011/06/24/system-maintenance-for-linux-pcs](http://blog.jdpfu.com/2011/06/24/system-maintenance-for-linux-pcs)

---

### Post by Yellow Pasque on 2018-07-30
> I also find it's sometimes the other way around too. The command line update will report nothing to update and the system updater does report a couple of updates

Read apt-get manpage and note the difference between 'upgrade' and 'dist-upgrade'.

> What's the best method for ensuring everything is up-to-date?

apt-get update and then apt-get dist-upgrade. I prefer Synaptic for GUI (its 'Reload' button calls apt-get update).

---

### Post by &amp;KyT$0P# on 2018-07-30
> **Taylz said:**
> Why is it that when I go to the software updater to see if there are any updates available it reports to me that the system is up-to date, yet when i run sudo apt-get update --> sudo apt-get upgrade there appears to be updates?
Likely because those are [phased updates]("https://wiki.ubuntu.com/PhasedUpdates").

---

### Post by missmoondog on 2018-08-01
as Temujin said, " I prefer Synaptic for GUI (its 'Reload' button calls apt-get update). "

the easiest way to do it and most sensible, IMO. why bother having to type that stuff out in terminal when the gui is right there and does exactly what you want it to do? it works exactly the same way as windows does when you go to check for updates.

---

### Post by coffeefiend on 2018-08-01
I personally prefer the apt-get update. I like using command-line. I am still fairly green with Linux and I find that it is a great way to learn my way around.

---

### Post by TheFu on 2018-08-01
> **coffeefiend said:**
> I personally prefer the apt-get update. I like using command-line. I am still fairly green with Linux and I find that it is a great way to learn my way around.

Good points made above by all.

**Whatever works for you is how you should do it.**

I need to run the same commands on about 20 systems. Most don't have any GUI and I don't want to walk around, login, find some program in a menu, click 5 things, and wait on the few that do.  By using a shell/CLI, I have multiple solutions
* clusterSSH (opens remote terminals on different systems, I type into 1 and all the others get the same command(s) entered)
* a script that loops over all the different systems and runs each command (update/upgrade) over ssh
* Ansible (a professional devOps tool that also works over ssh connections
* and at least 10 other options. 
I can run the updates from 1 location and patch the local machine, 5 machines in a different rooms and the others thousands of miles away over the internet.

Many people setup automatic updates. I've been burned with that, so I won't do that anymore.  Had a DB server taken down over an update with an incorrect dependency.  NEVER AGAIN.  I suspect that normal end-users wouldn't harmed too much with automatic patching.  Server admins need to be much more careful.

Generally, the GUI tools only provide about 20% of the capabilities and usually only the most popular options. Plus the GUIs change every few years, which can be good or bad, depending on your perspective.  The CLI commands change much less often.  apt-get is basically the same interface since 2006, though fixes have been incorporated continuously all this time.

Regardless, you are the boss of your systems and should use the method that works best for your needs.

---

### Post by coffeefiend on 2018-08-01
> **TheFu said:**
>  _**automatic updates**_. I've been burned with that, so I won't do that anymore.  Had a DB server taken down over an update with an incorrect dependency.  NEVER AGAIN. 

One of the many reasons I am steering away from Windows 10.

---

