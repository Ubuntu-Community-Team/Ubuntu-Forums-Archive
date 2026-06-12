---
title: "APPORT Requires Privileged Access - Enter password"
date: 2014-02-14
forum: General Help
---

### Post by Rick St. George on 2014-02-14
After upgrading to v13.10, a window pops up;

"An application is attempting to perform an action that requires privilieges. Authentication is required to perform this action .... Enter Password"

Vendor:  Apport
Action:   com.ubuntu.apport.apport-gtk-root

---------------------------

I'm always leary when something is trying to access root, or requests privileged access that I did not request.
What does this mean and is it safe? Anyone know!?!?

Rick

---

### Post by Dave_L on 2014-02-14
Apport is a legitimate diagnostic package:
[https://wiki.ubuntu.com/Apport](https://wiki.ubuntu.com/Apport)

It runs automatically when an error is detected. I don't know why it's running in this particular situation.

---

### Post by grahammechanical on 2014-02-14
Apport will help us report a bug by collecting log files and stuff. As these files may include certain information that we may not want to be included in the bug report Apport asks permission to collect this information and it informs us of the fact that sensitive information is being included. We have the option to cancel.

Apport is enabled by default in the development branch of Ubuntu but it should be disabled by default in a stable release version. Go to System Settings>Security and Privacy>Diagnostics and make sure that the box "Send error reports to Canonical" is not ticked.

Regards.

---

