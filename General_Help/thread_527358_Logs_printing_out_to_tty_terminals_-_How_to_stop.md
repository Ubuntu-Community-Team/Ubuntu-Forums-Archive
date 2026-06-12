---
title: "Logs printing out to tty terminals - How to stop"
date: 2007-08-16
forum: General Help
---

### Post by jedcred on 2007-08-16
I'm getting shorewall firewall log messages, as well as other system log messages, printing out directly to the terminal (tty1 and tty2 in my tests) and I'd like not to get them while I'm working in the terminal, since it makes it hard to read the output of what I'm doing to get a random log interspersed with my work.  This does not happen, however, in gnome using the terminal application. Also, stopping logging is not an option. TIA.

---

### Post by jedcred on 2007-08-16
Page two already? :) 
Bump

---

### Post by jedcred on 2007-08-16
Even killing or reconfiguring syslogd doesn't stop the messages from coming; something else must be writing them to terminal. Hmm...

---

