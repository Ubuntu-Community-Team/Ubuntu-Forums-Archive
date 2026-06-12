---
title: "Ubuntu Errors Running Commands from the Command Line"
date: 2008-06-06
forum: General Help
---

### Post by dee_kay on 2008-06-06
This is the latest problem in a series that I've had with my Gutsy install.  Out of the blue my laptop stopped booting to Gnome and dropped me to the command line.

Since then I've had to run a forced fsck which seemed to work, i.e. I'm back at the command line.

I want to start GDM but for some reason, probably stupid (I'm not very good at Linux yet), it's resisting all attempts.

I've tried

#sudo /etc/init.d/gdm start

It just puts up a command line in reply, i.e. looks like nothing happened.

#sudo dpkg-reconfigure gdm

That errors with "dpkg-reconfigure: command not found"

#sudo apt-get install ubuntu-desktop

That errors with "apt-get: error while loading shared libraries: libapt-pkg-libc6.6-6.so.4.5: cannot open shared object file: No such file or directory"

I know this is something pretty fundamental but at this point, being relatively new to Linux, I really need some help or some pointers for new stuff to try.

Any suggestions welcome.

Thanks,
Dave

---

### Post by cariboo on 2008-06-06
What happens if you enter startx at the prompt?

Jim

---

### Post by dee_kay on 2008-06-08
> **cariboo907 said:**
> What happens if you enter startx at the prompt?

Jim

Hi Jim,

I get an error

> /usr/sbin/startx: line 127: /usr/bin/mcookie: No such file or directory

then five lines of

> xauth: error while loading shared libraries: libXau.so.6: cannot open shared object file: No such file or directory

followed by a new error

> xinit: error while loading shared libraries: libX11.so.6: cannot open shared object file: No such file or directory

then back to one line of the first error line

> xauth: error while loading shared libraries: libXau.so.6: cannot open shared object file: No such file or directory

Does that make any sense?

I've dome some research on mcookie.  It's an executable that generates a random number for for use with the X system authorisation process.  That's makes some sense of the error messages.  Apparently I can download the util-linux package and reinstall it from there.  The snag with this is that I'm still getting an error when I issue an apt-get command.

Can anyone give me a pointer or two?

Rgds,
Dave

---

