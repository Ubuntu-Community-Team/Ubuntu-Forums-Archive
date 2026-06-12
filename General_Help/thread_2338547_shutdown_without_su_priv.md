---
title: "shutdown without su priv"
date: 2016-09-29
forum: General Help
---

### Post by colmax on 2016-09-29
found anyone can pass shutdown commands with switches to ubuntu 16.04 without su 
just seems a big control issue

shutdown -r now
shutdown -h now

Cheers c

---

### Post by ajgreeny on 2016-09-29
I admit I was surprised to see your post and immediately tried this out, and you are correct, with no query of "Are you sure?" or anything like that.

I will investigate further.

---

### Post by ian-weisser on 2016-09-29
Not seeing any systemd bugs in Launchpad that match this description.
Perhaps you are the first to discover....

---

### Post by ajgreeny on 2016-09-29
Here you go.  It seems it is a feature, not a problem.

[http://askubuntu.com/questions/774740/why-does-reboot-and-poweroff-work-without-super-user-privileges-in-ubuntu-16](http://askubuntu.com/questions/774740/why-does-reboot-and-poweroff-work-without-super-user-privileges-in-ubuntu-16)
[http://askubuntu.com/questions/789058/how-to-make-sbin-shutdown-sbin-reboot-etc-require-sudo-again-in-16-04](http://askubuntu.com/questions/789058/how-to-make-sbin-shutdown-sbin-reboot-etc-require-sudo-again-in-16-04)

It doesn't tell us why, but does seem to suggest it is a deliberate decision.

---

### Post by mc4man on 2016-09-29
> **colmax said:**
> found anyone can pass shutdown commands with switches to ubuntu 16.04 without su 
just seems a big control issue


Why? Can't see any reason why shutting down or restarting should require root auth.

---

### Post by &amp;KyT$0P# on 2016-09-29
> **mc4man said:**
> Why? Can't see any reason why shutting down or restarting should require root auth.
You're thinking of a "typical" client desktop computer.  I can think of several situations this could be quite bad on a server.

---

### Post by ajgreeny on 2016-09-30
And if more than one user was logged in it could be a problem in a desktop.

Thinking about that; can more than one user be logged in at the same time?  I have only one user on any of my computers so I don't know the answer to that question.

---

### Post by mc4man on 2016-09-30
> **ajgreeny said:**
> And if more than one user was logged in it could be a problem in a desktop.

Thinking about that; can more than one user be logged in at the same time?  I have only one user on any of my computers so I don't know the answer to that question.
If another user is logged in the command won't complete & you're informed of such. It does also provide & inform of  a systemctl command to override & do a shutdown/reboot if desired.
It would be impracticable to require root auth  to restart or shut down, how would a non admin user do so, wait until admin user was available?

---

### Post by ajgreeny on 2016-09-30
> **mc4man said:**
> <Snip>
It would be impracticable to require root auth  to restart or shut down, how would a non admin user do so, wait until admin user was available?
The GUI allows shutdown and restart with no root authorisation, and always has done so, as far as I'm aware, but doing so in terminal or command-line TTYs, and perhaps therefore in most servers, has always in the past needed authorisation.

---

### Post by kpatz on 2016-09-30
I just tried it in my 16.04 VM.  If I launch a terminal from the desktop and run "shutdown -r now" it shuts down with no superuser privileges required.

If I access a shell via ssh and run "shutdown -r now" it doesn't work without sudo.

So, it's only when you're on the desktop itself that you can shutdown without privileges.  Remote access still requires sudo.

---

### Post by mc4man on 2016-09-30
> **kpatz said:**
> I just tried it in my 16.04 VM.  If I launch a terminal from the desktop and run "shutdown -r now" it shuts down with no superuser privileges required.

If I access a shell via ssh and run "shutdown -r now" it doesn't work without sudo.

So, it's only when you're on the desktop itself that you can shutdown without privileges.  Remote access still requires sudo.
Correct, the same from a tty, sudo is required. So not sure that this thread is about anything. (certainly no mention of server, ect.
The only issue n the past was shutting down with other users logged in & that has been addressed to extent possible.

---

### Post by nothingspecial on 2016-09-30
It's worked this way for ages

---

### Post by colmax on 2016-10-01
i do apologise
seems my dementia got in the way 
gui shutdown doesnt need su but terminal allows switches which could potentially be damaging to the system such as auto-format etc
Much thanks on your feedback - shows me how much i still need to learn
cheers c

---

### Post by ajgreeny on 2016-10-01
> **colmax said:**
> i do apologise
seems my dementia got in the way 
gui shutdown doesnt need su but terminal allows switches which could potentially be damaging to the system such as auto-format etc
Much thanks on your feedback - shows me how much i still need to learn
cheers c
No need to apologise as in previous versions of Ubuntu, or certainly previous LTS versions, those shutdown commands do need root permissions and authorisation, which is why I was surprised and said as such in post #2.

I am still running 14.04 (Xubuntu) so was not aware of this change before your thread was started.

---

