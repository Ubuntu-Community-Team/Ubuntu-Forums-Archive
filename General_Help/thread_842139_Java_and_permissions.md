---
title: "Java and permissions"
date: 2008-06-27
forum: General Help
---

### Post by X-dark on 2008-06-27
I just noticed when I run Java program with a sudo I get more java functionalities. Let me explain.
I noticed with the Netbeans installer and with Netbeans when I run them with a sudo the graphical interface used is the java one and not the system one. I suspect java lacking of some permissions to be fully run without root privileges.
My java version is the last Sun Java from the repository :
```
java version "1.6.0_06"
Java(TM) SE Runtime Environment (build 1.6.0_06-b02)
Java HotSpot(TM) Server VM (build 10.0-b22, mixed mode)

```

---

### Post by Gunman1982 on 2008-06-27
First of all I wouldn't recommend using netbeans with sudo. You don't need to and its a security hole. Furthermore it may block you from working with it as a normal user afterwards (changed configs which are not readable anymore for the user).

I guess what you noticed was, as a normal user NetBeans runs its graphical user interface with java too but tries to stick to your overall design (ubuntu design). If you start it with sudo it doesn't use the design by your (gnome-)desktop but rather falls back to the default java GUI design.

I can assure you that the GUI runs as a java program itself.

---

### Post by X-dark on 2008-06-27
I agree with you about running it as a super user. Not such a good idea.

You're correct about what I noticed. But I want it to run with Java GUI design which is more usable I think. How can I achieve that as a normal user ?

---

