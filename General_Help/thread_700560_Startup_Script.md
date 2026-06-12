---
title: "Startup Script?"
date: 2008-02-18
forum: General Help
---

### Post by Grax on 2008-02-18
Using: 7.10 Server

I have a CSS server configured to run and would like to get it automatically start at boot.

I've tried adding a script to /etc/init.d/, however the CSS server output spams the console.  How can I get the game server to run in the background?

I've tried putting & at the end of the line.

Thanks,

Andrew

---

### Post by pointone on 2008-02-18
Add "> /dev/null 2>&1" to the end of the command. This will send all the output to oblivion.

---

### Post by Grax on 2008-02-19
Thank you.  Worked great!

---

