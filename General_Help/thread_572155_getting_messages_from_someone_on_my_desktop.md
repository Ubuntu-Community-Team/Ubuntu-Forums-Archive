---
title: "getting messages from someone on my desktop"
date: 2007-10-10
forum: General Help
---

### Post by deadwait on 2007-10-10
hi 
, i have been getting messages from someone directly on my gnome desktop, the next time this happens ill put up  a screenshot of it, its like the guy has my name ( but my user name is also the same ) 
and he's put up a message which says " hi deadwait he he ha ha ha " it had come up on my machine at the bottom right corner when i clicked it the message just closed, how do i find out whats going on? is there a way to send such messages on a local lan, because i have a doubt its being sent from maybe one of my office colleagues, and how do i find out who?
any help is greatly appreciated

---

### Post by Lord Illidan on 2007-10-10
Are you using Gutsy?

EDIT : Also, get a firewall..

---

### Post by notwen on 2007-10-10
Sounds similar to a win.popup msging system, lol.  Please post back if you find out more info.

---

### Post by 3rdalbum on 2007-10-10
Change your password; the guy may have used SSH to log into your computer and then used dbus to fire messages onto your notification area. That's theory on my part - I'm only going by what little I've seen on some man pages. But if that's what's going on, he's got access to your whole computer.

You should be able to stop him by simply unplugging your network cable, changing your password, rebooting, then plugging the cable back in. (you have to unplug the cable FIRST, otherwise he will be notified that the computer is shutting down, and he can issue a command that will cancel the shutdown).

---

### Post by bashologist on 2007-10-10
Did the message look something like zenity?
```
zenity --warning --text 'hi deadwait he he ha ha ha' --title 'I H4X J00'
```

---

