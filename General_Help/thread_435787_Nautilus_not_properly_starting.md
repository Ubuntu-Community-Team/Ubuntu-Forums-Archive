---
title: "Nautilus not properly starting"
date: 2007-05-07
forum: General Help
---

### Post by Felford on 2007-05-07
OK, so I've been using Ubuntu for a while fine now, and recently upgraded from Edgy to Feisty (7.04). It worked fine to start with, but (I'm pretty sure I didn't really do anything) now when I start in any mode except "Failsafe Gnome" all my window borders disappear. No title bar at all - it's not hugely useful.

It's not really a problem - I'm just using failsafe mode exclusively, although it would be nice if I could set it to *always* sign on into failsafe mode rather than having to fiddle with it each time.

I did a quick search, and I can't seem to find this problem anywhere. The only thing I noticed differently about the startup in normal mode and in failsafe was that "Nautilus" came up in the little bar full of startupy things that appears when you log in in failsafe but **not** in normal. I think this is the problem, but I've no idea how to go about fixing it - I'm a fairly recently converted windows user, so I don't really know anything about making linux work, although I'm keen to find out. Anyways, any help with this would be much appreciated - thanks in advance.

---

### Post by bapoumba on 2007-05-07
hello,
it might be some user configuration file that is corrupted.
To test that, create another user:
```
sudo adduser test
```
assuming you choose "test" to login. Setup a password, the rest of the infos can be kept blank.
Login with this test user, do you have problems ?

---

### Post by Felford on 2007-05-07
OK, a test user seems to work properly, so it'll be something in my user configuration. :) That helps, but as I say I'm recently converted, and I'm not really sure how to fix that - at least I know what the problem is now.

I *did* have a look at preferences/sessions and have a look at the startup scripts in there, but simply adding "nautilus" didn't achieve anything - I didn't think it would, but I don't know what else to do...

(off topic - perhaps this should be moved to the "Beginner talk" section...)

---

### Post by bapoumba on 2007-05-07
I'll get back to you later on. May be others can help you through.
You can rename some of your conf files in your /home folder:
.gnome
.gnome2
.gconf
One by one, to start with. Put an extension (.bak for ex) and logout then log back in.
A default conf file will be created. You can find the culprit.

Ok to move the thread, General Help is fine too. Can you wait a little? (I have to run ^^).

---

### Post by Felford on 2007-05-08
OK, so if I rename each of them and the log out/back in again, it will create a default conf file - whereabouts will this be, and once that's done do I just delete the old one and manually set all my settings back to the way I want them?

Thanks for the quick replies by the way :)

EDIT:: It seems that I tell lies! I now see nautilus starting in the starty-up-tell-you-which-programs-are-starting thing. (What's the name of that by the way? :p ) But I tried each of them in turn - no luck. Is it worth me trying some others, and if so which ones might be a good place to start?

---

### Post by bapoumba on 2007-05-08
Hum, not sure. I would have bet on .gconf

Could you post a screenshot? (are you talking of the session startup menu?).

---

### Post by Felford on 2007-05-08
I'll get a screenshot up in just a minute, but .gconf did nothing except reset all my theme settings...

(I noticed this time round that I don't think the "panel" started up, and when I click on "showdesktop" in my bottom right corner, it displays an error)

EDIT:: OK, in that mode all the keyboard shortcuts (such as print screen and alt-tab) are disabled, BUT:

After browsing to "Take screenshot" in applications/accessories I noticed something about "Window effects". It mentioned something about window borders, but it was all greyed out (I don't have the "Desktop Effects" enabled), but anyway I went to "System/Desktop effects" and hit "Enable"... It returned an error that it was unable to, but interesting also restored all my window borders :D Problem solved - I don't know why it should do this, other than the fact that these effects are still in beta if I'm not mistaken? Thanks for trying to help - I appreciate it :)

---

