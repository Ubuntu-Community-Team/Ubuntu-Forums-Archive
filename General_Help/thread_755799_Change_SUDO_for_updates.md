---
title: "Change SUDO for updates?"
date: 2008-04-15
forum: General Help
---

### Post by becatlibra on 2008-04-15
I have found vague references to this but am hoping for more specific guidance.

I am looking to add the update manager, synaptic and apt-get to a list somewhere so that I do not have to key in a password to use them (just me, not other users).  I know I read about this with another program somewhere in the past but don't remember . . . 

Can anyone shed some light on this?

Thanks

---

### Post by Sef on 2008-04-15
System > Administration > Software Sources > Updates

---

### Post by becatlibra on 2008-04-15
While that allows security updates without verification, I am looking more for the syntax to add these items (update-manager, synaptic, aptitude and apt-get) to the sudoers file . . . 

Can someone help with that?

Thanks

Benjamin

---

### Post by VoidedCheck on 2008-04-15
If that was supposed to be a joke, it's not funny.
Becatlibra, ignore Lord Illidan's "advice", that's a recursive "remove links" command that doesn't ask for confirmation.

EDIT:  Looks like the offending post was deleted.  Good job mods, that was a fast response.

---

### Post by cdenley on 2008-04-15
If you want to allow the admin group to run certain commands without requiring a password, then edit /etc/sudoers by using this command...
```

sudo visudo

```
...then add this line to the end
```

%admin ALL = (ALL) NOPASSWD:/full/path/for/command

```

I wouldn't recommend this. Your password is required for a reason.

---

### Post by becatlibra on 2008-04-15
I'm a sysadmin of 4000+ systems and have been using linux for 10 years - ubuntu is a recent thing for me.

I know root privileges can be dangerous.  However I have apf and bfd setup on this machine and it is not accessible from the outside world either (only this internal network).

I appreciate the concern, but I'm not a n00b and get tired of typing my 30+ character password every time I wish to do updates or installs

Thanks for the syntax help.

Regards,

---

