---
title: "Changing your default shell"
date: 2007-10-18
forum: General Help
---

### Post by iver2435 on 2007-10-18
This is a low priority question, but I just was wondering if I could get rid of an annoyance I'm having with my school's main UNIX server.

My school uses csh as the default shell for students.  I've submitted a request to the IT people and they said NO to me getting my default shell changed to bash.  They did suggest that I just add a line to my .login file that spawns a bash shell.

So I did and it works and I have my beloved bash shell and all my environment variables, life is good....

However, when I go to log out now, I have to type "logout" twice.  Is there any way (OTHER THAN chsh, because the admins removed it) to change my default shell without root access?

Like I said....my worst case scenario is that I have to type 7 more keystokes to logout, so not a big deal, but if anyone out there has a solution, I would appreciate it.

---

### Post by dcstar on 2007-10-18
> **iver2435 said:**
> This is a low priority question, but I just was wondering if I could get rid of an annoyance I'm having with my school's main UNIX server.

My school uses csh as the default shell for students.  I've submitted a request to the IT people and they said NO to me getting my default shell changed to bash.  They did suggest that I just add a line to my .login file that spawns a bash shell.

So I did and it works and I have my beloved bash shell and all my environment variables, life is good....

However, when I go to log out now, I have to type "logout" twice.  Is there any way (OTHER THAN chsh, because the admins removed it) to change my default shell without root access?

Like I said....my worst case scenario is that I have to type 7 more keystokes to logout, so not a big deal, but if anyone out there has a solution, I would appreciate it.

The login shell is set in your account, only an Administrator can change that (but it is really a trivial change).

Your problem (and solution) is bureaucratic, not technical.

---

### Post by ebs16 on 2007-10-22
I ran into the same issue using my university's linux computers.  To cleanly use bash instead of csh, add the following two lines to the .cshrc file in your home directory:

```

setenv SHELL /bin/bash
exec bash -l

```(that's a lowercase L after bash)

Note that launching bash with the -l parameter bypasses the settings in your .bashrc file.  If you'd like to retain or use .bashrc settings, rename the file to .bash_profile and leave it in your home directory.  Don't forget to clear the bash settings you made to your .login file.

---

