---
title: "Firestarter confuses me..."
date: 2007-07-28
forum: General Help
---

### Post by namelessone on 2007-07-28
I thought that firestarter was just a nice frontend to iptables, and it doesn't actually have to be in the system tray to work...but that doesn't seem to be the case.

When I don't start firestarter, I can play the game Savage and access windows shares on other computers. But when I start firestarter and try to do the same things, I can't. The little tray icon turns red and says it blocked something.

Why is this so? Am I *really* blocking packets when I don't start up the firestarter gui?

---

### Post by yorkie on 2007-07-28
when you start firestarter it will run with the default settings or the settings you have chosen .here`s a tutorial to help you understand the program .

[http://www.fs-security.com/docs/tutorial.php](http://www.fs-security.com/docs/tutorial.php).

---

### Post by namelessone on 2007-07-29
yes, I understand how firestarter is supposed to work... the point is, it's not. I shouldn't have to start the gui to start the firewall. It should be running all the time in the background with it's init.d script.

The odd thing is, /etc/init.d/firestarter status returns nothing. It should return either Firestarter is running, or Firestarter is not running...

---

