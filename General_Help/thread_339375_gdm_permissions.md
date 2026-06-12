---
title: "gdm permissions"
date: 2007-01-15
forum: General Help
---

### Post by jake3988 on 2007-01-15
I recently did the comprehensive sound guide solution thing and gdm had to be reinstalled, however, when I boot I get this failed message:

Server Authorization directory (Daemon/ServAuthDir) is set to /var/lib/gdm but is not owned by user root and gruop gdm.  Please correct the ownership or gdm configuration and restart gdm.

I assume I'll have to use a live cd, but what exactly do I have to modify and to what to make my machine boot?  

Thanks!!

---

### Post by taurus on 2007-01-15
Boot into recovery mode from GRUB menu and at the prompt, change the ownership back

```
chown root:gdm /var/lib/gdm
shutdown -r now
```

---

### Post by jake3988 on 2007-01-15
Thanks for such a quick response.  The recovery thing didn't work [the loadup hangs] but I did the live cd approach and loaded it.

But now a different VAGUE error 'X could not be started due to an internal error look at syslog for more information'

However, there's almost none to speak of.

All I really got is this: kernel: [17181879.436000] request_module: runaway loop modprobe binfmt-464c

modprobe just doesn't work.  Loading a module also halts the 'recovery' section too


I have a feeling this is unworkable and just plain not worth it.  Why it stopped working I have no clue either.  Should I just burn to dvd the partition and start over or is there anyway I can pull myself out of this mess.

Note: I got here because I did the Comprehensive Sound Guide rebuilding of the kernels and it removed (and reinstalled) packages like gdm and thus causing all the problems.

Anyone that's ever had this happen to them, I'd like to know how you got it back up and working again.


THANKS!!!

---

### Post by taurus on 2007-01-15
You can look at /var/log/Xorg.0.log to see what's the error message is for X.

```
less /var/log/Xorg.0.log
(hit the space bar for the next 24 lines...)
```

---

### Post by jake3988 on 2007-01-15
Whelp, that was a bad idea.  When it kicks the dust, it displays every log file with the following tag attached like this:

/var/log/syslog.0:failed. Read-only file-system!
...


So... its not appending the fail messages properly.  So... I think I'm hopelessly screwed at this point.

Unless someone inc yourself has any other ideas?

---

### Post by jake3988 on 2007-01-16
Bumping myself.

Also to note that my live cd is INSANELY slow.  Could it be because I burned the cd image to a dvd?  The installation process stalls (i usually give it 10 minutes before deciding yes, it did) at random points.

---

