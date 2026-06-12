---
title: "How do i set-up a viable listenable open port on skype on ubuntu 12.04?"
date: 2013-12-27
forum: General Help
---

### Post by deaton25 on 2013-12-27
How do i set-up a viable listenable open port on skype on ubuntu 12.04?

seasons greetings!

---

### Post by ian-weisser on 2013-12-29
Are you asking how to get your Skype to communicate with the rest of the world? So you can receive calls?

Or are yo asking how to get your Skype to listen for other (non-Skype) applications that want to use it's functionality?  Like a message bot?

---

### Post by deaton25 on 2013-12-29
thanks very much for getting back to me!!!
the problem is this:
i want skype to communicate with the rest of the world------and it does kind of.....
my skype passes the in-built echo test and
i've gone through several different netstat investigations and get LISTEN for my port(3394) as well as the four zeros 0 0 0 0
i've allowed the port to pass through my ufw --- sudo ufw status and my gufw both confirm that the port is allowed
i have even spoken with my brother on the other side of the continent with skype....
i have qbitorrent (port 6881) using the same system as my skype does---same router etc-- and its port is open-green
But.....my skype is CLOSED according to all the online port testing services i test it with
FYI: my gufw has a pre-configured skype button that registers/allows port 443/tcp----but port 443 is closed also!!!
what do i have to do so that the port scanners show that the ports are open???
one port scanner even says that ALL my ports are filtered!
i am really confused!!!! something doesn't make sense here
thanks

---

### Post by ian-weisser on 2013-12-29
I think you are reading too much into a port scanner's opinion of an open or closed port.
A port scanner is not a magic standard of truth. It's merely a security tool.
If the application works despite the port being "closed," then it's a fairly clever application.

You also may be reading too much into the term "port." A "port" implies a barrier with a specific opening. Computer ports are virtual. There is no barrier. "Open" and "Closed" are confusing terms that are not used by your system. I consider them worthless sales-pitch language.

Your system cares only about if a service is 1) bound to a port, 2) listening on that port, and 3) accepts a connection.
Generally, the first and second do not generate any response, so a port scanner will consider that port "closed"...even though you can have services listening on those ports.
The third, accepting the connection, will mark the port as "open" on a port scanner.

---

### Post by deaton25 on 2013-12-29
thank you for your thoughtful answer!

---

