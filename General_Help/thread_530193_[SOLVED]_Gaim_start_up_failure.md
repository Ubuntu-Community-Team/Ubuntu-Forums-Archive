---
title: "[SOLVED] Gaim start up failure"
date: 2007-08-20
forum: General Help
---

### Post by jim_p on 2007-08-20
Earlier today I logged on to my msn account from gaim and logged out after a while.
In the meantime, the only use I did of my internet connection was to do an antivirus update to a
laptop running windows. 
And now, 2-3 hours later,when i try to log in again, gaim crashes with this error (in terminal)
```
Attempt to register the same DBusConnection with the message bus, but it is already registered
Segmentation fault

```

What is this? I remember having set to "remember my status at logon" to yes, if this helps.
At least, can I disable my account and enable my brother's to check instead?


I am using Dapper and Gaim 2.0.0.5 beta. Gaim was installed from a .deb file I downloaded from the net since in the official repos there is only gaim 1.5

EDIT: I tried reinstalling but no luck

---

### Post by kellemes on 2007-08-20
Could very well be a bug..
Why don't you get [the newest release]("http://www.pidgin.im/download/source/").

Edit: By the way Gaim is called Pidgin these days.

---

### Post by dragonwings on 2007-08-20
i found  to login i had to change my status message 
eg from available to away ,
then it will activate 
then i just change it back to avaialable or whatever i want 

pain in the *** i know ,so if ya find a fix please send me a message on how to.

---

### Post by jim_p on 2007-08-20
The thing is that I dont see a thing so as to do something!!
The gaim window does not appear, in the taskbar i can see "starting gaim" for 1 sec and ....poof...
it's gone! No tray icon, no taskbar icon, nothing

And I know about pidgin, I tried compiling from source but failed.

These situations meke me think I have had enough of this LTS thing ](*,)

---

### Post by eap1935 on 2007-09-05
Try renaming /home/you/.gaim/status.xml to something else. Then gaim should start up for you. You run into this when you set status to offline before you quit gaim. I've been hoping the repositories would actually let me install pidgin, but I guess I'll have to wait for the next release.

---

### Post by jim_p on 2007-09-06
Actually I removed gaim, deleted the whole .gaim folder, found a repo that contains 2.0.0.3beta and started again from zero.

Plus I have found a script here in ubuntuforums that downloads, extracts, downloads all the dependencies and eventually installs pidgin from source. Too bad it stops on the 5th or so dependency file because it is not included in the LTS repos.

Anyway, next time I will make good use of your tip :)

---

