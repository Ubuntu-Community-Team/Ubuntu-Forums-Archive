---
title: "sudo don't ask for passw!"
date: 2007-01-08
forum: General Help
---

### Post by pcomelade on 2007-01-08
Hi all,

I'm running (K)Ubuntu edgy (kernel 2.6.17-10-386). When I run a command under "sudo" it runs cleanly without asking a password. I have already run "sudo -k" and the problem persists. When I restart linux and run a "sudo-ed" command (for example "sudo su"), it runs without asking a password!.
I'm attaching the uncommented lines in /etc/sudoers:
----------------------------------------------------------------------------------

Defaults        !lecture,tty_tickets,!fqdn
root    ALL=(ALL) ALL
%admin ALL=(ALL) ALL

----------------------------------------------------------------------------------

Does anybody knows what is going on?
If the problem persists I will end up disabling "sudo" (I have already enabled the root password).

Thanks in advance!!!

M;

---

### Post by taurus on 2007-01-08
Double post!  Look here instead, [http://www.ubuntuforums.org/showthread.php?t=334033](http://www.ubuntuforums.org/showthread.php?t=334033).

---

