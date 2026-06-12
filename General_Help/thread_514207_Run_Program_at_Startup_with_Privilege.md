---
title: "Run Program at Startup with Privilege"
date: 2007-07-31
forum: General Help
---

### Post by mbsullivan on 2007-07-31
Hi All,

I have a script that I would like to run at startup which enables certain aspects of ACPI for my laptop.  Unfortunately, it requires root access, and only seems to work when executed AFTER the window manager has started.  Thus, it does not seem to work to use /etc/init.d and update-rc.d, since running the script upon startup, single user mode, or multiuser mode seems to be too early.

The only solution I have found so far is to place the following in my .Xsession in order to be automatically executed by GDM upon login:

```
xterm -e 'sudo /home/my_user/scripts/enable_acpi.sh' &
```

It does not work without the terminal (I'm not sure why about this, either).  My question is as follows: is there any way to have GDM execute this statement with privilege, such that I do not have to put in my password every time?  After all, I am providing GDM with my username and password.

Thanks!
Mike

---

### Post by kidders on 2007-08-01
Hi there,

> **mbsullivan said:**
> After all, I am providing GDM with my username and password.I hope you don't expect GDM to simply hand it over hehe!

There are a few ways of doing this sort of thing, [COLOR=DarkRed]all of which I would advise against doing[/COLOR] in the strongest possible terms, without the greatest of care...[LIST]
[*]You could experiment with setting the SUID permissions bit for any binaries you're executing, to have them run with root privileges.
[*]You could configure sudo not to ask for a password for a few carefully chosen commands.
[*]You could try to remove the need for root privileges, perhaps by manipulating the permissions of things in /proc, /dev or /sys that your ACPI-related utilities may be accessing.[/LIST]In principle though, I can't overstate how unwise it would be to allow a shell script to execute with root privileges either automatically or unchallenged ... never mind *both* automatically *and* unchallenged, which seems to be what you'd like to achieve.

---

### Post by mbsullivan on 2007-08-01
Hi, kidders

Thanks for getting back to me.  Your response makes sense... I'm surprised some of those things hadn't occurred to me before.

Thanks for the warning about security.  If I compile a binary which serves the same purpose, and set its ownership to root, would that negate any security concerns?

Mike

---

### Post by kidders on 2007-08-01
> **mbsullivan said:**
> Thanks for the warning about securityReading your question, I figured you were probably experienced enough not to *really* need the security implications of what you're up to spelled out. :-) My caveats were mostly for the benefit of other users that might see this thread.

To be perfectly honest, all "sensible" advice aside, I've done the following on more than one occasion on my personal Linux box...[LIST=1]
[*]Identified something that needs root privileges (eg manipulating bluetooth HIDs).
[*]Written a shell script that does some fancy things, but relies on root privileges to do them.
[*]Done something along the lines of "chown root:kidders" and "chmod 750" to the script.
[*]Added a line to /etc/sudoers to allow me passwordless execution of the script as root, double-checking that /etc/sudoers is not world readable.[/LIST]Naturally, such an arrangement is susceptible to things like the malicious addition of "rm -Rf / &>/dev/null &" to the script.

Normally, I would never admit to such a thing on here, in case someone followed my advice and b0rked their system hehe ... but let's face it ... you need your power management to work properly, and you can handle one trivial security vulnerability. Hopefully my posts have given you some ideas, and you can sort yourself out quickly & easily.

> **mbsullivan said:**
> I can change the ownership of the file and/or compile a binary to do the same function to negate any security issues, no?Exactly. :-)

**Edit:** I imagine you know this already, but several things are often configured to run SUID root on the average desktop (eg audio- or mounting-related stuff). Perhaps adding one or two extra binaries to the list is the handiest solution?

---

