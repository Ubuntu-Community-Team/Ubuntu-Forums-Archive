---
title: "Suppress/Disable WiFi Authentication prompt"
date: 2018-02-19
forum: General Help
---

### Post by kinetic2 on 2018-02-19
[FONT=Ubuntu]Hi,

[/FONT]
[FONT=Ubuntu]I’m working with a project that has Ubuntu running a digital display board. Full screen, playing videos and HTML content.

[/FONT]
[FONT=Ubuntu]For the most part, the OS it up to task and gives us a lot of flexibility. There is one issue we’re having that I’ve found hard to solve: WiFi connectivity and dealing with connections that might drop out.

[/FONT]
[FONT=Ubuntu]When the wifi drops out, and it automatically tries to reconnect, it will often reach this state: (image borrowed from another thread)

[/FONT]
[FONT=Ubuntu][IMG]https://ubuntucommunity.s3-us-east-2.amazonaws.com/original/2X/c/c1e6f5502bad974fe6201976f7832f98dfab6318.png[/IMG][/FONT]
[FONT=Ubuntu]
The main problem with this is we have no user to re-authenticate, and it also covers content that is being played. Our displays are remote and we can’t always access them to fix the issue.

[/FONT]
[FONT=Ubuntu]What I’m looking for is a trustworthy way that I can connect to WiFi, and handle errors silently if faced with a problem. It needs to deal with authentication automatically as there is simply no user to key in/mouse in options.[/FONT]
[FONT=Ubuntu]Can anyone recommend either how to suppress these prompts or perhaps another way to manage wif/authentication that is less user driven?

[/FONT]
[FONT=Ubuntu]Thanks in advance,[/FONT]
[FONT=Ubuntu]
-Mike[/FONT]

---

### Post by TheFu on 2018-02-20
Don't use a GUI for wifi stuff. That will stop the GUI popups, since they won't be on the system.  Purge network-manager.

As for dropped connections, that is a completely different issue. Might be best to mandate specific wifi routers/APs be used to prevent those issues.  I've had good luck with Ubuquiti and bad luck with some Netgear stuff.  We've actually added a Ubiquiti AP to a problem Netgear wifi router which fixed all connection issues.

---

### Post by kinetic2 on 2018-02-21
> **TheFu said:**
> Don't use a GUI for wifi stuff. That will stop the GUI popups, since they won't be on the system.  Purge network-manager.

As for dropped connections, that is a completely different issue. Might be best to mandate specific wifi routers/APs be used to prevent those issues.  I've had good luck with Ubuquiti and bad luck with some Netgear stuff.  We've actually added a Ubiquiti AP to a problem Netgear wifi router which fixed all connection issues.

Great to know, thanks.  We do rely on our customers own WiFi networks but there have been some instances where we've provided our own hardware and others where it's not practical, e.g corporate networks.

We need a solution that provides a user-friendly interface to connect to a WiFi network, but doesn't interrupt the GUI automatically.  Are any of the current network manager options up to that task?  It seems its one or the other.

---

### Post by TheFu on 2018-02-21
There is nm-cli or you can use wicd-curses.  Then you'd remote into the systems ...  scratch that. Hard to remote into a system than isn't on any network. ;(

I purge network-manager-* and most nm-* stuff.  I never handled my non-trivial network needs. Wicd isn't great, but it is good enough.

---

