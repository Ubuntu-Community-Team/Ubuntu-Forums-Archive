---
title: "Making service scripts"
date: 2015-11-09
forum: General Help
---

### Post by jerome1232 on 2015-11-09
I have this little home server and I have a few game servers I run on it. Many times I will see some nice scripts written up for some servers that turn it into a services and allow you to easily start, stop, restart, and etc like any other service on the system, and as a bonus you can make it auto start on startup.


Is there some sort of general guide to writing these service scripts, everything I've seen seems very thrown together and I  don't know what half the script is doing, I'd like to make my own somewhat simple scripts that do only, well you know, what I script them to do.


Specifically I run csgo:ds and 2 minecraft dedicated servers, I know there are a few other scripts for these popular games available out there but I have had trouble finding guides on how to make these wonderful scripts myself in the past. Currently I just have an overtly simple run script for csgo and an update script for it. I keep it open in a byobu window and manually shut it down to update it. There has got to be a better way to script a way to autoshut it down every week (like, turn it into a service and have a cron job that shuts it down and updates it maybe?) and attempt to update or something.

---

### Post by TheFu on 2015-11-09
I learned by following all  the examples and learning the scripting language used.
However, with systemd, things-be-changin'.

---

### Post by jerome1232 on 2015-11-10
For the time being I'll be on trusty until a new LTS release. That means upstart jobs for me? I think I saw a wiki for it, [https://wiki.ubuntu.com/SystemdForUpstartUsers](https://wiki.ubuntu.com/SystemdForUpstartUsers)

Maybe I can whip something together with what I do know.

---

### Post by jerome1232 on 2015-11-14
Okay so I got one working for csgo, it was pretty simple to do. Only I want cron to stop the server and start an update process that must be done by the steam user.

Currently only root can start or stop jobs, In my reading I can see you can create something called session-jobs for upstart that will be started by the user.

I got that from: [http://upstart.ubuntu.com/cookbook/#session-job](http://upstart.ubuntu.com/cookbook/#session-job)

I'm a little confused, it seems I must create the two system jobs that lists, then place my config where? Would I have to modify it?

---

