---
title: "xlock and custom passwords"
date: 2007-02-09
forum: General Help
---

### Post by munkar on 2007-02-09
hi, does anyone know how i would create a password specifically for xclock, so that when it prompts me for a password, i can enter the custom pwd instead of my user password?

[supposedly]("http://www.garayed.com/linux/206939-xscreensaver-xlock-password-2.html") i should be able to do this with the -cpasswd command line option or by using an .xlockrc file.

but Ubuntu's default build of xlock (from Synaptic) doesn't have the -cpasswd option, and i don't know how to give an encrypted password to .xlockrc. also, i don't know if this stuff only works on [shadow password systems]("http://www.mirbsd.org/man1/xlock.htm")?

>      If the machine is using a shadow password system, then xlock
     may not be set up to get the real password and so must be
     given one of its own. This can be either on the command
     line, via the -cpasswd option, or in the file
     $HOME/.xlockrc, with the first taking precedence.	In both
     cases an encrypted password is expected (see makekey(8)).
     If neither is given, then xlock will prompt for a password
     and will use that, also storing an encrypted version of it
     in $HOME/.xlockrc for future use.

---

