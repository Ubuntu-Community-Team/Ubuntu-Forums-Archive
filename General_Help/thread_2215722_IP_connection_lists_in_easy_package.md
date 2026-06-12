---
title: "IP connection lists in easy package?"
date: 2014-04-08
forum: General Help
---

### Post by Barkester on 2014-04-08
I've experimented with a few programs that show where my packages come and go, but they do so much more making it distinctly inconvenient.

  Is there a command or program that will ONLY show me all current connections in a nice list? I'd find such as a great conmpliment to the system monitor.

  Alternatively, is there a command for Wireshark or other network tool that would easily isolate this information in a nice list?

  Would just like a nice list of every outside connection is all. Than, if I get curious about one, I can open something else.

   Thanx again guys/girls.

---

### Post by Lars Noodén on 2014-04-08
Does 'netstat -ntup' do what you want?  What do you mean by current connections?  [netstat](http://manpages.ubuntu.com/manpages/trusty/en/man8/netstat.8.html) will show the state of UDP and TCP connections.

---

### Post by Barkester on 2014-04-09
Netstat is good, but I'm hoping for something that will just monitor constantly rather than having to repeatadly use the command similar to the way system monitor works where new connections will automaticly be added to the list and all I need do is open the window or even keep the terminal in the corner. 

   Just hoping there's something more convenient is all. Might not be.Thanks for the reply.

---

