---
title: "[SOLVED] Shared documents as on windows... the OS we detest"
date: 2008-06-26
forum: General Help
---

### Post by rolandixor on 2008-06-26
How do I get something like the all users shared documents on windows?
I need to set up some one else's ubuntu installation to work like this because it has a tiny hard drive.

Any suggestions? (BTW, I can use the command line if needed, so don't give me some over simple answer LOL, unless it's that simple :P)...

---

### Post by rolandixor on 2008-06-26
I should add, I need an answer ASAP. I'd like to surprise them by finishing before tonight!!! :D

---

### Post by wootah on 2008-06-26
> **rolandixor said:**
> I should add, I need an answer ASAP. I'd like to surprise them by finishing before tonight!!! :D

You should add, that it would be nice if some kind person with some spare free time would be able to answer your question because you would like to surprise them.

---

### Post by rolandixor on 2008-06-26
wha?
would you like a cookie (since we are going to be all irrelevant here, which is kule for the fun of it)

---

### Post by rolandixor on 2008-06-26
would /usr/share/Music/blablabla work?

---

### Post by lswest on 2008-06-26
you could possibly (not sure, never tried it) assign a different /home/ folder to the new user when creating it using the adduser command in the terminal.  I'm not at a linux computer right now, but I think it might work - check out the man page.

---

### Post by rolandixor on 2008-06-26
not sure what you're getting at LOL.

I want to achieve something like the examples folder. I have a generally idea, but I just need to know if I'm on the right track by using something like what I mentioned above.

---

### Post by lswest on 2008-06-26
wait, so basically you want to create a home folder per user, but have a default folders like the folder "examples" in Ubuntu?  I thought you wanted each user using the same home folder.  What you can do is just create some folder (under /etc or /usr, doesn't matter) and create symbolic links to the folder using the ln -s command, and you may have to change permissions, but that's how I'd do it.

maybe post in clear layman's terms what folder you want where, how the home folder set up ought to be, etc.

---

### Post by rolandixor on 2008-06-26
kinda what I thought. Thanks, I was right.

I want to create something like:

/home/this/that

which would represent

/usr/share/that

and be writable to everyone under /home

---

### Post by rolandixor on 2008-06-26
I'll get right to it...

Thanks guys!!!

---

### Post by lswest on 2008-06-26
yeah, then create the folder in /usr/share/, set permissions properly (probably easiest would be read/write permissions to all users) and then create the symbolic link with ```
ln -s /usr/share/that /home/this/that
```

No problem, glad we were able to help and thanks for the thanks!

---

### Post by rolandixor on 2008-06-26
now, I haven't been using BBcode too much, how do I close this thing and mark it as solved? lol
I need to spend a little less time on Ning forums (I'm almost as popular as the CEO! LOL)

---

### Post by lswest on 2008-06-26
just go up to the top of the thread, there should be an option "thread tools" click that and choose "mark thread as solved" and voilá, thread solved.

This is pretty much the only forum I'm active on :P

---

### Post by rolandixor on 2008-06-26
lol thanks man :D

---

### Post by lswest on 2008-06-26
lol np, glad I was able to help!  And again, thanks for the thanks, always nice to have your help appreciated ^^

---

### Post by KeyserSoze93 on 2008-06-26
sudo su

mkdir /home/public

chmod 777 /home/public

umask 000 /home/public

---

