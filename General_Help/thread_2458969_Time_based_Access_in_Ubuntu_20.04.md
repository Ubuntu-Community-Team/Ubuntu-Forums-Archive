---
title: "Time based Access in Ubuntu 20.04"
date: 2021-03-08
forum: General Help
---

### Post by midlajkp888 on 2021-03-08
Hello brother, 

Is there any way in ubuntu that we can set time/hourly/month based access restriction in ubuntu 20.04 for multiple users, which the users are accessing through RDP!!

---

### Post by TheFu on 2021-03-08
_Any way_?  Sure.  Script it.

However, RDP really isn't secure and shouldn't be used. Same for VNC.  If you use NX-based access, then you can add and remove allowed users in config files using either groups or individual userids. Enable and disable those lists using scripts by specific times which are handled in your scripting.  Or if the users are on the same LAN, why not use simple remote X11 instead?  It has been around for 40 yrs and works. Much less overhead, no need for 3rd party junk, assuming the client machines each have an X/Server.

People often think that locking an account in the passwd DB is sufficient, but ssh using keys doesn't care.  ssh using passwords (which is a bad idea) would check the passwd DB for locked or not.  If you use LDAP for user management, this should be possible too, just the commands to lock/unlock would be ldap commands.

The sshd_config manpage is quite extensive and explains the options you'd need.  AllowGroups DenyGroups, AllowUsers, DenyUsers.  I'd tweak the settings in the /etc/ssh/sshd_config.d/ directory, not in the main file.  To enable a file there, just have the filename as .conf.  When you want to disable it, mv the file so it doesn't end in .conf.  Of course, any change would require sending a -HUP signal to the sshd processes and existing connections wouldn't be impacted.  Only new connections.  There are timeout for inactively methods for ssh, but end-users will quickly learn to prevent those disconnections - I know that I did.

Those are just a few ideas. There are lots of others if you think outside the box - like giving each user their own lxd container for use. Then you can start and stop the container based on scripting.  That would certainly prevent access outside the allowed times, but you'd need to patch each lxd container efficiently.  For 5 users, this would be easy.  For 500 users, it becomes a little harder and you'd want a local apt-cache to speed up patching.

[https://www.techrepublic.com/article/using-pam-to-restrict-access-based-on-time/](https://www.techrepublic.com/article/using-pam-to-restrict-access-based-on-time/) shows how to use PAM to restrict access by time/date. Don't assume that works with every access method available until you test.

Lots of other possible solutions exist too.  The real root issue you are trying to solve would determine other options and considerations.  For example, if the access is only allowed from specific IPs, tweaking firewall rules for the ports could be a method.  I've seen some routers that will enable and disable access to IPs based on times and DoW too.

---

