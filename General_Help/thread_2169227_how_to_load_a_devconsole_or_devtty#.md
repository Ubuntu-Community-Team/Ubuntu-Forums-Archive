---
title: "how to load a /dev/console or /dev/tty#"
date: 2013-08-21
forum: General Help
---

### Post by el_terrible on 2013-08-21
Hi There,

I'm trying to load a TTY session with a piece of perl code -- example -->

open TTY,"/dev/tty0" or die "not connected to a terminal\n";
$exp->slave->clone_winsize_from(\*TTY);

... but it's failing because I'm assuming that I"m not loading the terminal session correctly.

Does anybody out there know how to load a TTY session easily?  Is there a simple command that I'm missing?  I tried 'chvt' but that's not working either since it's just changing the current environment.

Thanks in Advance,

Chacky

ps. not sure if it helps but I'm calling spawn off the perl Expect lib shortly afterwards

---

