---
title: "Administrative apps won't launch... dbus?"
date: 2008-05-29
forum: General Help
---

### Post by _DD_ on 2008-05-29
8.04, installed the day before yesterday with all updates applied...

Whenever I enter an administrative program it either doesn't load at all (displays in the window list for a while then disappears) or loads and I can't unlock it (I click the unlock button and it hangs for a while, then says an unexpected error has occurred and it couldn't be unlocked).

If I run them from the terminal then I get errors such as...

```
** (users-admin:6899): CRITICAL **: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
```

If I try and run "sudo users-admin" I get...
```
** (users-admin:7316): CRITICAL **: Unable to lookup session information for process '7316'
```
...and the unlock button is greyed out, and I can't change anything. "gksudo users-admin" gives me the same useless window but no error in the terminal.

I'm in the admin and policykit group.

I've tried reinstalling policykit, gnome system tools. I've spent ages googling and nothing people mention works!

I had this for problem yesterday and fixed it by removing apache and making sure my hosts file was correct for loopback. The top line of /etc/hosts reads...

```
127.0.0.1 localhost mattlaptop
```

(and mattlaptop is the name in /etc/hostname)

I can ping localhost. I've tried restarting hal, dbus and policykit in various orders. I can also sudo. HELPPP!!!

](*,)

Thanks :)


EDIT:
If I log out and log back in again then they kinda work. The only thing I can think of is that this time I logged in with my password rather than the fingerprint reader (via fprint). Could this really make any difference?
Also, administrative apps such as the package manager which launch with gksu still won't run from the menu, but if I run them from the terminal (with exactly the same commadn as is being used in the menu item) then they open instantly with no errors.

---

### Post by _DD_ on 2008-05-29
Ok, I think I've tracked the issue down to the fingerprint reader. Removed the line from the common-auth pam file and now everything works.

Next question is why, and how can I reenable the fingerprint reader without screwing everything up? While it is a gimmick, its quicker than typing a long password!

---

### Post by _DD_ on 2008-05-29
More detective work...

It would appear that scanning my finger while the app is showing to be loading makes it work!

**however**

That only works for the administrative programs which run under gksu.

All the ones which run under your normal user and then require you to press the unlock button are still broken.

Any ideas?

---

### Post by zyrorl on 2008-07-22
I also have this issue would be really good if someone could work out a solution to this:( anything with gksu works fine though.

---

