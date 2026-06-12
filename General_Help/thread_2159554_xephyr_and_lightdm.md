---
title: "xephyr and lightdm"
date: 2013-07-03
forum: General Help
---

### Post by planarian on 2013-07-03
I'm trying to figure how to nest X sessions within lightdm using Xephyr, employing two separate accounts. When I execute ```
ssh -XfC  account-name@my-computer lightdm-session
``` on the client side I get a cascade of errors, so clearly I either need to make changes to my lightdm configuration, or to use something other than lightdm-session in the ssh command. Pointers, anyone?

---

### Post by Toz on 2013-07-03
If you are looking at running a local nested X session, you can simply run:
```
dm-tool add-nested-seat
```
...to open up a second nested session.



If you want to run a remote nested session, it gets a little more complicated. On the remote host, create the file **/usr/local/bin/nestedX** with the following content:
```
#!/bin/bash
export XDG_SEAT_PATH=/org/freedesktop/DisplayManager/Seat0
/usr/bin/dm-tool add-nested-seat
```
...and make the file executable. Then from the guest system:
```
ssh -XfC  account-name@my-computer nestedX
```
(Note: ensure that openssh-server is installed and properly configured and that port 22 is allowed through the firewall).

dm-tool (part of lightdm) seems tailored to this but I can't seem to find much in the way of documentation. Passing it --help shows some info:
```
$ dm-tool --help
Usage:
  dm-tool [OPTION...] COMMAND [ARGS...] - Display Manager tool

Options:
  -h, --help        Show help options
  -v, --version     Show release version
  --session-bus     Use session D-Bus

Commands:
  switch-to-greeter                   Switch to the greeter
  switch-to-user USERNAME [SESSION]   Switch to a user session
  switch-to-guest [SESSION]           Switch to a guest session
  lock                                Lock the current seat
  list-seats                          List the active seats
  add-nested-seat                     Start a nested display
  add-local-x-seat DISPLAY_NUMBER     Add a local X seat
  add-seat TYPE [NAME=VALUE...]       Add a dynamic seat
```

The one thing I haven't been able to figure out is how to change the viewable screen dimensions of the nested session.

---

### Post by planarian on 2013-07-03
Thanks for bringing dm-tool to my attention!

I used your remote-host instructions because although I'm working on a single machine, I want to import a session from another login. Unfortunately, although ```
ssh -XfC  account-name@my-computer nestedX
``` produces the right login prompt, when I enter the password it opens a nested session onto my current desktop, not the one I logged in for....

---

### Post by Toz on 2013-07-03
> **planarian said:**
> I used your remote-host instructions because although I'm working on a single machine, I want to import a session from another login. Unfortunately, although ```
ssh -XfC  account-name@my-computer nestedX
``` produces the right login prompt, when I enter the password it opens a nested session onto my current desktop, not the one I logged in for....

Just to confirm, you are trying to connect to an existing login session on the same computer but have it display in a nested session? If so, I'm not sure thats possible with lightdm.

---

### Post by planarian on 2013-07-03
Yes that is what I'm trying to do. But here's the odd thing: If I reverse the client and server, the process works. In fact if I merely execute ```
dm-tool add-nested-seat
``` from the second account (without ssh), the first account appears in a Xephyr window *without even asking me for a password*. Not only is that  bizarre, it would seem to be a significant security hole!

[EDIT: I may have misunderstood your question. I'm trying to use an existing login, but NOT to connect to an existing session. Rather than login to a virtual terminal, I'd like to access my second account from a window within the first]

---

### Post by Toz on 2013-07-03
> **planarian said:**
> Yes that is what I'm trying to do. But here's the odd thing: If I reverse the client and server, the process works. In fact if I merely execute ```
dm-tool add-nested-seat
``` from the second account (without ssh), the first account appears in a Xephyr window *without even asking me for a password*. Not only is that  bizarre, it would seem to be a significant security hole!

I am unable to replicate that. Whenever I create a nested seat (from either login), I am greeted with the login screen.

---

### Post by planarian on 2013-07-03
I just realized that my primary account had autologin enabled. Once I switched it off, the greeter appears no matter which account I start from (the desired result). Thanks very much! Now if only I can figure a way to increase the display area....

---

### Post by planarian on 2013-07-04
Well, I have it [straight from the horse's mouth]("https://answers.launchpad.net/lightdm/+question/231876") that there's currently no way to change Xephyr's display area when it's invoked by dm-tool. At the project leader's suggestion, I've submitted a bug report. If anyone here would like to cast a vote, it would probably help speed things along....

---

### Post by Toz on 2013-07-04
> **planarian said:**
> Well, I have it [straight from the horse's mouth]("https://answers.launchpad.net/lightdm/+question/231876") that there's currently no way to change Xephyr's display area when it's invoked by dm-tool. At the project leader's suggestion, I've submitted a bug report. If anyone here would like to cast a vote, it would probably help speed things along....

Thanks. I've added my name to the affected users list.

---

### Post by planarian on 2013-07-06
While we're waiting for a *proper* update, I decided to go ahead and roll my own. Please understand that I'm not an experienced C hacker -- caveat emptor -- but the attached executable/src ought to do the trick:

```
dm-tool.modifed add-nested-seat -screen 800x600
```
```
dm-tool.modifed add-nested-seat -fullscreen
```

My changes only add accommodation for -screen and -fullscreen. The code was taken from version 1.6.0.

---

### Post by Toz on 2013-07-06
You should post this to the bug report - maybe they can make use of it.

---

