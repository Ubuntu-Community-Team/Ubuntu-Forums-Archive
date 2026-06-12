---
title: "synaptic not asking for the password"
date: 2006-07-11
forum: General Help
---

### Post by jordilin on 2006-07-11
Sometimes I haven't done any sudo for a while and when I open synaptic to add some package it doesn't ask me for the password, when it normally asks for it. Is it a fault?

---

### Post by Paerez on 2006-07-11
If you use anything that asks for a password (such as most of the items on the System -> Administration menu) that counts as a password-ask. So if it has been 30 minutes and you open up Disks for example, and you put the password in, Synaptic will open without pass, since you recently proved you have the authentication.

If you leave it for 10 minutes and do nothing, then open synaptic without a pass, then you may have a problem.

---

### Post by jordilin on 2006-07-11
Well, I installed Ubuntu Dapper as a normal user without privileges, and every time I have to do some admin task I use sudo entering the password I chosed in the installation. I suppose you are right in the sense that if I enter some password to do some administration it remains there for a while. But, if it remains there, then it means that you are using the Desktop with root privileges for some time, so this could be a security problem. Any explanation why?

---

### Post by Paerez on 2006-07-11
You are not using the desktop as root, don't worry. If you have used a terminal, then you will understand that Gnome is running gksudo, which is like sudo with a gtk interface.

If you haven't used a terminal, then it works like this:
-Gnome wants to run admin app
-Gnome asks for the app to be run in admin mode
-If you haven't run a command in admin mode for a while, it prompts the pass
-It runs *just* that application as admin
-It remembers that you were admin recently

If you try to run another admin app within about 5 mins of another one that you were approved for, it assumes that you are still you.

So don't worry, the whole desktop is not being run as root, just the one app.

---

### Post by jordilin on 2006-07-11
thanks for the explanation

---

### Post by Paerez on 2006-07-11
keep in mind though, if you run synaptic, then leave your computer, for the next 5 minutes anyone could use your computer and do whatever they wanted.

I map the Win key + L to "lock screen" so I can lock it quick if I left it in admin mode and I had to run. Most of the time, since its a laptop, I just close the screen, and I set xscreensaver to ask for a password. Closing the screen runs the screensaver, so I don't have to worry about people hijacking computer.

Granted this is kind of silly, because my roommate can barely use windows :D

---

### Post by nanotube on 2006-07-11
Paerez: not silly, just good security policy. :)

another note - it is possible to configure sudo so that it asks you for password every time (without the 15 minute timeout between uses where it doesn't ask). i think it's an option you can set in /etc/sudoers. 

aha, it is. from "man sudoers":

> timestamp_timeout
                   Number of minutes that can elapse before sudo will ask for a passwd again.
                   The default is 15.  Set this to 0 to always prompt for a password.  If set
                   to a value less than 0 the user&#8217;s timestamp will never expire.  This can
                   be used to allow users to create or delete their own timestamps via sudo
                   -v and sudo -k respectively.

so, you execute command "sudo visudo", that will bring up an editor with contents of sudoers. find the line that looks like:
```
Defaults        !lecture,tty_tickets,!fqdn
```
and make it look like
```
Defaults        !lecture,tty_tickets,!fqdn,timestamp_timeout=0
```

and that will make sudo ask password every time.

how's that for a solution? :)

edit: alternatively, as per "man sudo", if you execute command "sudo -K", that will reset the timestamp manually, so that next time you need to sudo, you will be asked for password. if you don't want to edit your sudoers like above, you can just execute "sudo -K" before you leave your computer, so that nobody can use sudo behind your back :)

---

