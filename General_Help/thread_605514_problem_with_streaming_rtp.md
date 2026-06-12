---
title: "problem with streaming rtp"
date: 2007-11-07
forum: General Help
---

### Post by Keps on 2007-11-07
hi everybody, i have a little problem.
I made a client-server application for streaming audio. i tested it with two pc with Windows and it seems go.
Then i tried with one pc with linux and i found some problems.
Infact if in the pc with linux i launch the client, it is waiting for rtp packets (but it receive the packets...i controlled the traffic of the net) and if i launch the server, it don't send nothing in the net.

i installed correctly the jmf, infact [http://java.sun.com/products/java-media/jmf/2.1.1/jmfdiagnostics.html]("http://java.sun.com/products/java-media/jmf/2.1.1/jmfdiagnostics.html") told that everything is ok...

why this application go on win and not in linux?

someone have the same problem?

thank to all

---

### Post by Keps on 2007-11-10
i fixed it...
i had to modify /etc/hosts :
127.0.0.1 localhost
ip hostname

bye

---

