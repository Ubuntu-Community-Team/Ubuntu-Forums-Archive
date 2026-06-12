---
title: "Major problems after creating an account."
date: 2007-02-24
forum: General Help
---

### Post by dillonish on 2007-02-24
I recently installed Ubuntu 6.10 on my family's older computer, because I figured it might help it run better, because it was locking up often.

Anyways, everything seemed to be working fine (except my internet connection, which I was working on at the time) until I changed the first account and made a new account.

I renamed the one I started with Admin and gave it an admin password, edited a couple of other forms on the Profile creation screen that basically just renamed everything from the previous name to Admin.
Then, I created a new account for myself, and edited those same forms to say my new login name.

However, when I logged out and tried to log back in, a number of errors came up. After I had typing in my username and password (i've tried both accounts):

> Your home directory is listed as '/home/admin' but it does not appear to exist. Do you want to log in with the / (root) directory as your home directory?
It is unlikely anything will work unless you use a failsafe session.

Since "No" brought me back to the username form, I selected "Yes". Then, I was given this warning.

> User's $HOME/.dmrc file is being ignored. This prevents the default session and language from being saved. File should be owned by user and have 644 permissions. User's $HOME directory must be owned by user and not writable by other users.

So, I selected OK. It seemed to begin logging in, but then right there the following came up.

> Your session only lasted less than ten seconds. If you have not logged out yourself, this could mean that there is some installation problem or that you may be out of diskspace. Try logging in with one of the failsafe sessions to see if you can fix this problem.

Now, I'm definitely not out of diskspace and I don't think there was an installation problem, so I must have messed something up with the editing/creation of the profiles. ANYWAYS, I clicked the View Details box, and this is what it said:

> /etc/gdm/PreSession/default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/default: running: /vsr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x (etc...)
/etc/gdm/Xsession: Beginning session setup...
(gnome-session: 4351): libgnomevfs-WARNING** unable to create  ~/.gnome2 directory: No such file or directory.
Could not create per-user gnome config directory '/home/admin/.gnome2': No such file or directory.

So I hit okay and it brought me back to the initial login screen. I tried using all of the other 'Sessions' like the Failsafe GNOME and Default, etc. but they all produced the same results. However, Failsafe Terminal still works, though the warning popups still do show.

Basically, I'd like to know whether I should re-install Ubuntu altogether, if possible (and could you tell me how?), or if I could get some code to put in the Terminal that may fix the problem. As you can see I'm new to Ubuntu, however, I am fairly computer literate.

Any suggestions are very greatly appreciated. Thank you!

---

### Post by taurus on 2007-02-24
There are a few accounts/usernames in /etc/group that you cannot use as your login name and admin is one of them.  It's best to do a fresh install at this point then.

---

### Post by dillonish on 2007-02-24
Wow, why is it like that?

And how do I uninstall...

---

