---
title: "What is Wayland"
date: 2019-11-08
forum: General Help
---

### Post by RobGoss on 2019-11-08
Hello everyone I was wonder about something I've seen it mentioned a few times and was wondering if someone could explain how **Wayland** works and does every Ubuntu based OS have it installed 

Thanks so much

---

### Post by uRock on 2019-11-08
This may be helpful in answering some of your questions. [https://wiki.ubuntu.com/Wayland](https://wiki.ubuntu.com/Wayland)

---

### Post by HermanAB on 2019-11-09
Wayland is a new implementation of X, with a reduced feature set.  Whether Wayland is any good, depends on your use case.  For the kind of things I like to do, I need X.

---

### Post by kc1di on 2019-11-09
[This link]("https://www.secjuice.com/wayland-vs-xorg/") may also be of help.

---

### Post by linuxenthusiast on 2019-11-09
Wayland is essentially an implementation of an X server, and it is built not to be an extension of the existing X server.

Instead, it wants to have its own set of libraries where clients (i.e client applications) are free to talk to a Wayland server using the Wayland Protocol.

---

### Post by TheFu on 2019-11-09
> **HermanAB said:**
> Wayland is a new implementation of X, with a reduced feature set.  Whether Wayland is any  good, depends on your use case.  For the kind of things I like to do, I need X.

+1.  I need X11 network support too. I run very few programs locally on the machine I'm at. Most run on more powerful hardware somewhere else and only the GUI is displayed locally.   This is something that people using MS-Windows often have never seen or thought about.

---

### Post by yaminb on 2019-11-12
> **TheFu said:**
> +1.  I need X11 network support too. I run very few programs locally on the machine I'm at. Most run on more powerful hardware somewhere else and only the GUI is displayed locally.   This is something that people using MS-Windows often have never seen or thought about.

Honest question here.

Given today's powerful computers, what is the use case for running an application remotely, but not having the powerful server provide a remote desktop session.
I hope the question is clear. It's not about your local computer being powerful enough. It's about the remote powerful computer being powerful enough that if you wanted to run some application on it, you would just remote desktop/vnc... into it.
In other cases, those remote powerful applications are run as web applications or web services on the remote server; accessible via the browser.

At least that's been my experience. I'm really just curious on the use case that x11 network would have in todays world.

---

### Post by TheFu on 2019-11-12
Not sure I understand the question.  

VNC is nothing like remote X11 from a flexibility and useability perspective.  A browser running on 1 remote system.  8 xterms are each running on 8 different systems.  Thunderbird is running on yet another remote system.  The windows for each program appears to be a local window. Select/paste between them works just as expected for any other local-running program.  On a 3 monitor setup, just move any of those remote windows to any monitor you like. Not trapped on a single monitor.

A number of hard-to-setup environments are installed on specific systems - like a compile sever or a language translation server.  These systems are maintained by different teams.

Different remote systems have different security requirements. 

Why have to setup a full remote desktop solution for each of these, when remote X11 provides it without that overhead and honors all the existing Unix permissions which have been working since the 1970s?  Knowing how to share files in a team is well understood.

I'm probably misinterpreting the question.

---

### Post by RobGoss on 2019-11-12
> **uRock said:**
> This may be helpful in answering some of your questions. [https://wiki.ubuntu.com/Wayland](https://wiki.ubuntu.com/Wayland)

Thanks so much for the link

---

### Post by Skaperen on 2019-11-12
a likely confusing aspect of these diagrams is the use of the term "client" which might suggest there is a user there.  instead, they should be labelled "application" and described as conducting communication in a way that mimics a client/server model.  a place that this can be especially confusing is an X/VNC server which would communicate with applications (like clients) and one or more VNC clients (real clients).  that would be 2 kinds of clients.

one aspect of X that i have found to be confusing to a lot of people is that X is a server.  they generally are unaware that when they start an application that it makes a connect to X (the server) to create and operate a window.  they often assume that since they already are in X that starting the application there passes access to X to that application (X would be like a client in this model).  the internet web infrastructure is similar to this model, too, furthering that confusion about X as a server.  imagine the web browser controlling hardware directly (no need for X or Wayland) or a world of internet applications trying to communicate with each X server.  a VNC client connecting to a world of VNC servers might be much simpler, but it would be so inefficient and insecure.

---

