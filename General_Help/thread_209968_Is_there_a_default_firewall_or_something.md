---
title: "Is there a default firewall or something?"
date: 2006-07-06
forum: General Help
---

### Post by Particle on 2006-07-06
I've been using Ubuntu 6.06 as a dedicated Counter-Strike Source server for a few days now.  It has two NICs, one for intranet traffic and one for internet traffic.  While I was playing on the server tonight with a friend, something weird happened.

All of a sudden the server stops responding for me.  I drop, can't reconnect...I can't even ping the box.  However, I can connect to its VNC server over the intranet address and my friend could keep playing over the Internet on it.

Is there some default firewall in Dapper that I can turn off?  I don't understand why it would quit talking to my address all of a sudden.  It's annoying to not be able to play on my own server.  :(

---

### Post by woedend on 2006-07-06
to answer the question...nope.
sorry I can't be of more help than that.

---

### Post by KimEmbers on 2006-07-06
Ubuntu has firewall built-in on its kernel, its called iptables, but it lets everything go throw by default.

---

### Post by woedend on 2006-07-06
oh geebus not again...
hehe in any event lets say its not causing your problem.

---

### Post by vali on 2006-07-06
> Ubuntu has firewall built-in on its kernel, its called iptables,

The subsystem built-in on the linux kernel is called netfilter, not iptables. iptables is the userspace tool to manage it.

@Particle

You can see the active rules with

```
sudo iptables -L -n -v
```

and

```
sudo iptables -t nat -L -n -v
```

---

### Post by jazzmuzik on 2006-07-06
Install Firestarter via Synaptic (or command line) and run through the program's setup wizard. It's easy to do and everybody should do it.

---

### Post by woedend on 2006-07-06
not necessarily.
common sense and a good router really negates the need for a software firewall for a lot if not most users.

---

