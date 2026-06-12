---
title: "Password complexion in Linux vs Windows"
date: 2006-12-10
forum: General Help
---

### Post by Robert Leithe on 2006-12-10
Hi,

What am I doing wrong when Ubuntu 6.10 won't accept my passwords?

When I enter my username and password at logon, I'm being told I've entered a wrong username or password - when I know that's not the case.

Example. As of today, I'm using a fairly uncomplex password. An old password I used under Windows is j0szeN4vn%. Somehow Ubuntu won't accept this. I live in Norway, and hence use Norwegian (Bokmal) keyboard layout. I have checked and rechecked that this isn't a problem (I've entered my password in the username field and can see for myself that it spells out correctly).

I've also entered the password in clear text prior to changing it, so I can verify there shouldn't be any difference at the time of change and at the time of logon.

So what could this be? I have tried various passwords, but they all (the complex ones - as I call them) fail during logon. Why?

I end up logging on as root and resetting my user's password.

Sincerely
Robert Leithe

---

### Post by strabes on 2006-12-10
maybe it won't accept non-alphanumeric characters like % ?

---

### Post by viciouslime on 2006-12-10
It should do, else it wouldn't be very secure. You say you use a Norwegian keyboard layout, is this set as the system default? If it is only set as your user's default then on the GDM the keyboard will probably be an american layout.

---

### Post by chalex on 2006-12-10
Perhaps an easy way to check is:
1) hit Ctrl+Alt+F1 to switch to console
2) type your password for your username to see what the resulting input is

I'm not sure if GDM uses the same keyboard mapping as the console login, there might be more programs involved.

---

### Post by Robert Leithe on 2006-12-10
I typet my password in the username field, just to verify that the keyboard layout is set to Norwegian (Bokmal). So this shouldn't be the problem.

---

### Post by viciouslime on 2006-12-10
Oops, I can't have read your first post properly...

In that case, I am at a complete loss, for now I suppose you'll just have to choose another password and meanwhile maybe try asking for help on launchpad?

---

### Post by Robert Leithe on 2006-12-10
Please forgive a Linux newbie, but what is launchpad?

---

### Post by riven0 on 2006-12-10
Launchpad is where you can report bugs. Go to [Launchpad]("https://launchpad.net/"), create an account and report the bug there. They may have a fix.

EDIT: BTW, you may first want to check out the bugs already reported. It may already have a workaround. Click on The Ubuntu Distribution to get started.

---

### Post by Robert Leithe on 2006-12-10
Thanks :)

EDIT: I found some bug reports on this issue (at least it looks like it to me). [https://bugs.launchpad.net/distros/ubuntu/+source/sudo/+bug/41350](https://bugs.launchpad.net/distros/ubuntu/+source/sudo/+bug/41350)
I added a comment to the existing reports.

---

