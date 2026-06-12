---
title: "Evolution uninstalled by upgrade"
date: 2008-04-29
forum: General Help
---

### Post by petri on 2008-04-29
I performed sudo apt-get update etc in Terminal and ended upp with uninstalled Evolution.

When I try to reinstall it I got the message it won't be installed because it depends on evolution-data-server which is simply not going to be installed. No other message.

Edit: Using Hardy 64-bits

---

### Post by Jeremy Jackins on 2008-04-29
Also had evolution removed through the update manager.

trying to reinstall it:

```

$ sudo apt-get install evolution
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help resolve the situation:

The following packages have unmet dependencies:
  evolution: Depends: evolution-data-server (>= 2.21.92) but it is not going to be installed
E: Broken packages

```

---

### Post by Shako73 on 2008-04-29
Same thing here...

Tried many ways to fix that... not solved, SINCE 9AM !!!

Will wait till next update, like I do when things like this happens,

humm :confused:

---

### Post by petri on 2008-04-29
The next update has come.

The update didn't fix the Evolution problem but just install it again (either in Terminal or Synaptic) and you got your mail back.

I did though need to reboot my computer.

---

