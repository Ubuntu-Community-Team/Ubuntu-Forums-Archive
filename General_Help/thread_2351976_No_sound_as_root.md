---
title: "No sound as root"
date: 2017-02-08
forum: General Help
---

### Post by joaokleiber on 2017-02-08
Hi, I`m new to this forum.
For some reasons, I have to changed my user to a root user(I know that is not recommended). 
Then my user dont have a sond enable, but normal users have enable.
I searched for solutions already, but I did not find any solutions that worked.

Any ideas?

Thanks to advance!

---

### Post by Bucky Ball on 2017-02-08
Welcome. You'd be better to post about the issue you're having with not being able to login as a normal user. If you can only log in as root, you have a problem that trumps 'no sound as root'. ;)

And you're correct; logging in and running permanently as root is definitely not recommended.

---

### Post by joaokleiber on 2017-02-08
Thanks to reply. The problem occurs only when I log in with root user.

Thanks to advance.

---

### Post by ajgreeny on 2017-02-08
Why do you login as root?

It is definitely not recommended and you are unlikely to get much help here if you have enabled the root user account.

---

### Post by Frogs Hair on 2017-02-08
Moved to *General Help*.

---

### Post by joaokleiber on 2017-02-08
> Why do you login as root?

It is definitely not recommended and you are unlikely to get much help here if you have enabled the root user account.

Its because Im a developer and my workspace is located at /opt/, so i need to be a root to edit this workspace.

Thank you for replying.

---

### Post by coffeecat on 2017-02-08
> **joaokleiber said:**
> Its because Im a developer and my workspace is located at /opt/, so i need to be a root to edit this workspace.

You need to clarify whether you mean you are logging into a GUI as root, or into a shell as root. As far as the former is concerned, please read this forum policy:

[https://ubuntuforums.org/showthread.php?t=1486138](https://ubuntuforums.org/showthread.php?t=1486138)

Although that specifically refers to tutorials about logging into a GUI, as a matter of consistency we simply don't support anyone doing anything on a desktop where they have logged into the GUI as root. Running a root terminal is a different matter, and you should be able to do everything you need to do in /opt from a terminal.

---

### Post by Impavidus on 2017-02-08
If you really want to work in /opt, why not change the ownership of /opt? Or a subdirectory of /opt. I don't think there's any standard stuff that gets installed there, only some third-party .debs.

---

