---
title: "Update notifier lit up but won't update?"
date: 2007-09-20
forum: General Help
---

### Post by Yleeyas on 2007-09-20
Hi folks,

The orange update notification icon just came on, but when I click it, and enter P/W nothing happens. When I mouse over the icon it says there are 18 updates available but that's it. I also tried Synaptic from the system/administration menu but it only asks for P/W and then nothing??
I'm running Dapper, and the last time I got an update was Sept 1, it being a linux image update to 2.6.15-29.58 (i think)

Any advice?:(
yleeyas

---

### Post by benx009 on 2007-09-20
hmmm, the only time that i had such a problem like this was when my repos were all messed up.  have you ever added an extra repository as a software source?  (if you don't know what i'm talking about, then you probably haven't:))

---

### Post by Yleeyas on 2007-09-20
Hi benx009,

Haven't messed with repos, ever :)

I think my problem may be abit bigger.
I tried starting Synaptic from terminal and got the following error message:

```
~$ gksu /usr/sbin/synaptic
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified


(synaptic:6317): Gtk-WARNING **: cannot open display:

```

Similarly for a few other sys admin programs; network-admin, and update-manager!

Do you have any ideas what caused this, or more importantly how to fix:confused:

yleeyas

---

### Post by Yleeyas on 2007-09-20
Problem solved folks.

Turns out I shot myself in the foot a couple of weeks ago :oops:

I followed some instructions to get firestarter to autostart, by editing /etc/sudoers.
Bad idea. I removed those changes and voila all those 'broken' apps now work :lolflag:

Now to find a way to autostart firestarter without messing everything else up.

Sorry for distracting you from real (non-self inflicted) problems

yleeyas  ):P

---

