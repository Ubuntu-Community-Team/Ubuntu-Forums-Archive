---
title: "Init.d script for a simple application: scmpc"
date: 2007-11-11
forum: General Help
---

### Post by DarkDead on 2007-11-11
Hi all. I've installed [MPD]("http://ubuntuforums.org/showthread.php?t=31763") and a daemon called [SCMPC]("http://webadedios.net/modules/wordpress/archives/otra-de-lastfm-enviando-lo-que-escucho") which is a last.fm scrobbler that runs on background.
To run it I just need to type ```
scmpc
``` in the terminal.

Now I'm trying to create an init.d script to run scmpc every time the computer is turned on. As I don't know scripting I used some examples in the Gentoo Forums: [http://forums.gentoo.org/viewtopic-t-438701-postdays-0-postorder-asc-start-0.html]("http://forums.gentoo.org/viewtopic-t-438701-postdays-0-postorder-asc-start-0.html")
I came up with this:
```
#!/bin/sh

start () {
   start-stop-daemon --start --quiet --exec /usr/local/bin/scmpc -- -f /home/david/.scmpc/scmpc.conf
   eend $?
}

stop () {
   start-stop-daemon --stop --quiet --exec /usr/local/bin/scmpc --oknodo
   eend $?
} 
```
Then I followed the steps here: [http://www.vivaolinux.com.br/dicas/verDica.php?codigo=7762]("http://www.vivaolinux.com.br/dicas/verDica.php?codigo=7762") to add it to the init.d.
As I expected it doesn't work. The script must be a huge crap.
Does anyone know how to write one or where can I find an example one for Ubuntu?

---

### Post by justin_guerin on 2007-11-11
Ubuntu ships with an example script meant for creating custom init scripts.  It's /etc/init.d/skeleton.  It's liberally commented so it shouldn't be too hard to customize for your needs.

You may find the Debian Policy Manual informative as well:
[http://www.debian.org/doc/debian-policy/ch-opersys.html#s-sysvinit](http://www.debian.org/doc/debian-policy/ch-opersys.html#s-sysvinit)

Good luck,
Justin

---

