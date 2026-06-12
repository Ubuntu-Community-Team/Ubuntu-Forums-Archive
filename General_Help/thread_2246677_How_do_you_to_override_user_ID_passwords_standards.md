---
title: "How do you to override user ID passwords standards?"
date: 2014-10-02
forum: General Help
---

### Post by carmen2012 on 2014-10-02
I've setup an Ubuntu 14.04 computer for my very young kids.  I want to get them in the habit of using userIDs and passwords, but because they are so young, they'll have trouble with complex passwords.

I'm trying to use a simple password like "sunshine" but the system won't let me save the password because it doesn't meet the minimum requirements for the password.

Is there a way through the GUI to override this?

Thank you

---

### Post by Lars Noodén on 2014-10-02
If you don't mind the shell, you can use [passwd](http://manpages.ubuntu.com/manpages/trusty/en/man1/passwd.1.html) from the administrator account:

```

sudo passwd carmen2012 

```

Or for just that one user from that user's own account.

Either way, you can press ctrl-alt-T to get the terminal window you need but I'm not sure how to override the GUI utility itself.

---

### Post by carmen2012 on 2014-10-02
Thank you, this worked perfectly!

---

