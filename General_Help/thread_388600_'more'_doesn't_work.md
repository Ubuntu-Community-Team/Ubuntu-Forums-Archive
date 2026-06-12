---
title: "'more' doesn't work"
date: 2007-03-19
forum: General Help
---

### Post by blagger on 2007-03-19
hi all,

my problem is simple: 'more' command doesn't do pagination.
for example if i issue 'more /var/log/syslog' i just get a single page.
same thing when i run something like 'ls -R / | more'.

i get the first page, and then it stops. it doesn't ask for --More--
is there something under /etc wrong? i tried to copy a /bin/more of another server, with no result.

i use dapper server. 'less' works, but why not 'more' ? any ideas?
thanks!

---

### Post by llamakc on 2007-03-19
Is it installed? "more" works for me on Edgy (Desktop).

---

### Post by fragos on 2007-03-19
Will it advance a page when you hit the space bar and quit to a prompt when you type "q"?  If you do System-> Preferences-> Preferred Applications-> System tab you can select a terminal emulator.  Mine is "GNOME Terminal".  Gnome terminal alows you to change the number of lines and characters per line when you resize the window.  I don't know if the other choices like xterm maintane the number of lines fixed and only resize the window.  It can be hard to diagnose a problem when you're unsure of how to create it.

---

### Post by blagger on 2007-03-20
no, it just shows a page, and then returns the prompt.

the $TERM variable is 'linux', $MORE is empty.
is there any other variables that can affect the 'more' behaviour?

---

### Post by fragos on 2007-03-20
My $MORE is also empty but my $TERM is different and says "xterm".  I don't know if that makes a difference in your issue.

---

### Post by blagger on 2007-03-21
well i've found what's happening.

i use text consoles, and they're activated in inittab. i want autologin so i put in inittab this line:

1:2345:respawn:/bin/login -f user >/dev/tty1 2>&1 </dev/tty1

in this console 'more' doesn't work.
in normal getty consoles, it works. why? i dunno.


thanks for your interest.

---

