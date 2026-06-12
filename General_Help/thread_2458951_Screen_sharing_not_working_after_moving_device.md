---
title: "Screen sharing not working after moving device"
date: 2021-03-07
forum: General Help
---

### Post by silam2 on 2021-03-07
Running Ubuntu 20.04. Set up screen sharing and tested it on my Win10 laptop using VNC viewer, and it works. I then move the device to a new location where the machine is plugged into a different switch and the unit is running headless. I can still SSH into the box.

However when I run "sudo netstat -tulpn | egrep 5900" in this new physical location, nothing shows up. Any idea why screen sharing appears turned off when I move the unit and turn it back on?

While the unit is headless, I do have a dummy plug in the display port.

---

### Post by TheFu on 2021-03-07
Well, if you can ssh in, would using the best practice of using an ssh-tunnel for VNC not work?  There are lots and lots of how-to guides about doing exactly this.

Or you could use x2go, based on the NX protocol, that includes ssh tunneling in the protocol. Prior to 20.04, ssh-keys were fully supported with x2go. I haven't researched why they aren't anymore, since I only have 1 20.04 system today.

Any chance the IP address wasn't static and got a new IP?  That would break lots of stuff.

---

### Post by ActionParsnip on 2021-03-07
is there a local firewall configured?

---

### Post by silam2 on 2021-03-07
Just figured it out actually - needed to set auto-login to get vino started up!

---

### Post by TheFu on 2021-03-07
> **silam2 said:**
> Just figured it out actually - needed to set auto-login to get vino started up!

Depending on the environment, auto-login could be a huge security fallure.
Have you tried starting the vnc-server using systemd?  Look at systemd "unit" config files.
The trick would be to start it running with the specific userid, on a user-specific port, with specific environment variables - like HOME.


or use x2go.

---

### Post by HermanAB on 2021-03-07
VNC is a guaranteed method to get your machine hacked.  Just search this forum for all the tales of woe.  SSH can do the same (but slower) and is secure.

---

### Post by dragonfly41 on 2021-03-07
Depending on your usage, if data privacy is not too much an issue, try running some Ubuntu apps in the cloud at [https://www.rollapp.com/home](https://www.rollapp.com/home).

I am on free Starter account (running one app at a time) using Dropbox, but have experimented with Premier rollApp account (multiple apps) for a month.
There are some drawbacks I found, such as some apps not yet being available (a long "wishlist") and some being old versions and lack of persistence with free account. Also it lacks a forum like this one.
But it can be useful for shared tutorials, working from shared Dropbox account to pass files to the apps.

---

