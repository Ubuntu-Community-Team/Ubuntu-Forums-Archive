---
title: "a purely virtual X11 server"
date: 2023-01-26
forum: General Help
---

### Post by Skaperen on 2023-01-26
i was planning to use x11vnc but just read more detail about it including that it frequently scrapes the video buffer to get the pixel data to send to the client over the VNC (RFB) protocol.  this is not what i want.  i want an X server that "renders" its display in a virtual RAM buffer and sends that data over the VNC (RFB) protocol to the client.  i know there is an X server that operates like a dead-end and puts data in a buffer but nothing more.  that seems to be a way to test clients where seeing the result is not needed.  then there is an X server that acts like a client, too, copying its rendered buffer (maybe in efficient pieces) to the window it has opened on another X server (probably the X server in use by who started this).  this latter server type would be what i want if it would use VNC (RFB) for client support.  does anyone know if there is the kind of server out there that want to use?  i need FOSS for this.

---

### Post by TheFu on 2023-01-27
xvfb is a pure virtual X11 server.  It is typically used when server programmers incorrectly link to X/Client libraries, so a server needs an X/Server to connect or the program dies.  There's no way to access that screen to my knowledge.  It is 100% virtual and works without any GPU.  I've used it to get Oracle server tools to work on HP-UX and Solaris servers. Neither had any GPUs, I'm 100% positive.

I doubt that's what you really want based on other posts.

I also know that x2go doesn't need any video hardware to work. I suspect this is really what you want.  It uses a network optimized VNC with transfers through ssh tunnels. All of this is hidden from users and X/Clients.  The combined VNC+compression+ssh is called the "NX protocol".  Sadly, all the implementations are different enough to be incompatible.

After screwing around with RDP and VNC for a few years, finding x2go has opened my eyes for what an efficient protocol can accomplish.  I don't understand why people are so much against even trying it.  Are they afraid that things will be 2-3x faster than the alternatives AND more secure?  I don't get it.

---

### Post by Skaperen on 2023-01-28
sounds like x2go is what i want as long as there is a server and a client that work together.  i have two goals.  one is to be able to access a cloud instance (EC2 on AWS) in a graphical way in addition to the usual text way (ssh alone).  two will involve trying to implement an NX switcher.  that is a process that serves one client and connects to multiple servers concurrently and allows that client to switch to which server it wants to work on.  or it can view all servers concurrently in a size reduced to fit and click on (or key press) which one it wants to switch to.

---

### Post by Skaperen on 2023-01-30
the ubuntu 20.04 repository does not have a package named x2go.  is there another name for it?  another place to get it built for ubuntu?  do i need to build it from source?

---

### Post by TheFu on 2023-01-30
> **Skaperen said:**
> the ubuntu 20.04 repository does not have a package named x2go.  is there another name for it?  another place to get it built for ubuntu?  do i need to build it from source?

On my 20.04 desktop, I have a PPA for it.  Google finds the project website and their instructions easily.  Sorta expected you to find those.  Maybe use {tab completion} to see the package names?
Here's what {tab completion} shows me:
```
$ sudo apt install x2go{tab}{tab}
x2gobroker                     x2goserver-desktopsharing
x2gobroker-agent               x2goserver-extensions
x2gobroker-authservice         x2goserver-fmbindings
x2gobroker-common              x2goserver-printing
x2gobroker-daemon              x2goserver-x2goagent
x2gobroker-loadchecker         x2goserver-xsession
x2gobroker-ssh                 x2gothinclient-cdmanager
x2gobroker-wsgi                x2gothinclient-chroot
x2goclient                     x2gothinclient-common
x2godesktopsharing             x2gothinclient-displaymanager
x2golxdebindings               x2gothinclient-management
x2gomatebindings               x2gothinclient-minidesktop
x2goserver                     x2gothinclient-smartcardrules
x2goserver-common              x2gothinclient-usbmount

```

---

### Post by Skaperen on 2023-02-01
i normally prefer sticking with the distribution repository, and considering projects not adopted as such to be away from the direction the community is headed.  i don't normally expect a PPA.  i prefer to build from source unless i already know and trust who built it.  the goal is to be sure i have matching source.  i expect the source is at their website.

---

### Post by Holger_Gehrke on 2023-02-01
Actually, x2go has been in the repositories since 12.04. There are several packages whose name starts with x2go (x2goclient, x2goserver, x2gobroker, x2godesktopsharing ...) but no package x2go. The ppa:x2go/stable is official, it's referenced on wiki.x2go.org as a way to get a more current x2go than the repositories offer.

Holger

---

### Post by saware on 2023-02-22
> **Skaperen said:**
> ii need FOSS for this.
Its not FOSS but Nomachine has a a no cost (free as in beer)  of their offering.
One free virtual / physical desktop (per machine.)
Works extremely well over low bandwith links.
Service via native (4000/tcp) or ssh or https.
Multiplatform and distros.
We use the full version with ~100  remote users and the free version on some aws instances emulating graphical workstations.

[https://www.nomachine.com/](https://www.nomachine.com/)

---

