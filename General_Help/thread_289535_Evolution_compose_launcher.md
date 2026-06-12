---
title: "Evolution compose launcher"
date: 2006-10-31
forum: General Help
---

### Post by sockrebel on 2006-10-31
I'm trying to create a launcher in my gnome-panel so that when I click on it, it'll "compose a new message" in Evolution.  Is there a command that'll do that?  Anybody have ideas how to make that work?

---

### Post by localuser on 2006-10-31
evolution mailto:

evolution mailto:localuser@localhost.com

evolution mailto:localuser@localhost.com?subject="foo"

The problem with this is that after you either close the compose window or send the email, there is derivative processes left in memory.  I'm not sure how to automatically remove those.

---

### Post by sockrebel on 2006-10-31
> The problem with this is that after you either close the compose window or send the email, there is derivative processes left in memory.  I'm not sure how to automatically remove those.

These derivative processes are not an issue if an instance of Evolution is still running, right?

---

### Post by localuser on 2006-10-31
> **sockrebel said:**
> These derivative processes are not an issue if an instance of Evolution is still running, right?

Well, I believe that an instance of the mailto: process that you initiate still runs, which seems strange to me.  I'm not quite sure why that is.

[Edit]
Try it out.  After issuing the mailto: command, enter the following:

ps -ef | grep evolution

---

### Post by nealmcb on 2008-06-11
It would help to know exactly what process you're seeing.  I'm told that no new threads remain beyond what normally runs for evolution, and that is true for me.  If you don't have any evolution processes at all, then you may end up with an evolution-data-server process afterwards, and I don't know how to avoid that.

If someone has a tip on a nice existing icon to use for the launcher, I'm interested.  I'm on hardy now....

---

### Post by nealmcb on 2008-06-21
A good icon seems to be /usr/share/icons/gnome/scalable/actions/mail-message-new.svg

---

