---
title: "Missing FreeRADIUS files - permissions issue?"
date: 2018-02-08
forum: General Help
---

### Post by xinatron on 2018-02-08
My first post as a complete newbie, hoping to play with FreeRADIUS.

[B]Ubuntu Server 17.10.1
FreeRADIUS 3.0.15[/B]

After a relatively straightforward setup of the server, I have installed FreeRADIUS.

**freeradius -v** shows the correct version
**sudo freeradius -CX** shows configuration appears to be ok

The next step, according to various setup guides, is to edit some of the config files, however I am unable to locate any of them. One example:

sudo vi /etc/freeradius/clients.config - this just opes a blank file, there's no configuration information in there.

If I browse to the directory and try to list the files, I get a permission denied error:

[B]cd/etc/freeradius
ls
ls: cannot open directory "." : Permission denied
dir[/B]
**dir: cannot open directory "." : Permission denied**

I can, however, do this:
[B]sudo ls
3.0
sudo ls
3.0
sudo ls -lh
total 4.0K
drwxr-xr-x 9 freerad freerad 4.0k Feb 8 13:51 3.0[/B]

It's the same with **sudo vi /etc/freeradius/radiusd.confcd - **it just creates a blank file, I have no access to the actual config file I need to edit.


I am not sure if this is a permissions issue or a FreeRADIUS issue, however I'm now stuck as I need to get to the config files and have no idea what to do next. After a couple of hours of trying to work this out, I thought it would make an appropriate first post.

Any help or advice would be very much appreciated.

Thank you.

---

