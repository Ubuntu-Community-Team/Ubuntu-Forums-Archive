---
title: "GDM Errors after changing PAM settings"
date: 2006-10-19
forum: General Help
---

### Post by 00coday on 2006-10-19
In an effort to bring an Xubuntu server up to DoD security standards, I had to edit the /etc/pam.d/passwd file to enforce password restrictions.  The file looked like this when I got done with it:
#
# The PAM configuration file for the Shadow `passwd' service
#

#@include common-password
password required pam_unix.so Remember=5 minlen=9 dcredit=-2 lcredit=-2 ucredit=-2 ocredit=-2 md5

I rebooted the machine and issued the passwd command against a user account without issue.  I was able to log in via SSH using the new passwd and everything was fine.  

When I tried to log in via the GUI, I get an error saying that the session could not be created.  the contents of the ~/.xsession-errors is:

/etc/gdm/PreSession/Default:  Registering  your session with wtmp
and utmp /etc/gdm/PreSession/Default:  running:  /usr/bin/sessreg
âa       âw      /var/log/wtmp      âu      /var/run/utmp      âx
"/var/lib/gdm/:0.Xservers" âh "" âl ":0" "bob" session_child_run:
Could not exec /etc/gdm/Xsession startxfce4

Once I fail the GUI login, I can no longer connect via ssh for that user.  

I can log in with root via the GUI and ssh with not problem.

Any ideas?](*,)

---

