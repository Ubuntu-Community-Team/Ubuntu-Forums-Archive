---
title: "Xforwarding... Cannot Open Display..."
date: 2004-11-29
forum: General Help
---

### Post by Choi on 2004-11-29
Hello.

I have a problem when I try to display a application from another Unix computer on my Ubuntu distro. Even though I have added the other computer to the xhost list ($xhost +ipadress), the application on the other computer are not allowed to open a display on my computer...

Does anyone know of a good trick to fix this? Is there a config file which blocks computers from display applications on my computer even though I have allowed them through the xhost application?

Any ideas?

---

### Post by daniels on 2004-11-29
TCP listening is not enabled by default, because the authentication is trivial to bypass (if you do 'xhost +localhost', anyone with a reverse DNS name with localhost in it, e.g. localhost.fooishbar.org, has full access to your X session), and the consequences of having your X session hijacked are very, very serious.  If you want to run X applications, run 'ssh -X remotehost', and start the X application in that session.

---

