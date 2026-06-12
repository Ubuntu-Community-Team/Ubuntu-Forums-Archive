---
title: "sudo/root access to move files"
date: 2016-11-19
forum: General Help
---

### Post by g33zr on 2016-11-19
I want to move my wallpaper files to /usr/share/backgrounds. When I use other Linux distros, all I have to do is right-click on the appropriate folder and then open as root. This option seems to be unavailable in Ubuntu or is this something I can only do using cli? Please advise.

---

### Post by irv on 2016-11-19
First got to this Link. [https://help.ubuntu.com/community/NautilusScriptsHowto]("https://help.ubuntu.com/community/NautilusScriptsHowto")
If you would like some Nautilus Scripts, I have some at [http://wabasha-server.net/Nautilus%20Scripts/]("http://wabasha-server.net/Nautilus%20Scripts/")
The one named root-nautilus-here will open a Nautilus window in Root access. Use this with caution. See script below.

```
#!/bin/sh
# root-nautilus-here
# opens a root-enabled instance of a nautilus window in selected location
# requires sudo privileges and gksudo, which may involve security risks.
#Install in your ~/Nautilus/scripts directory.
#
# Placed in the public domain by Shane T. Mueller 2001
# Fixes provided by Doug Nordwall
#
# 2004.04.18 -- keith@penguingurus.com - Added gksudo usage to provide popup
#               password window if sudo has expired.  Line only echos got
#               root to std output.  But gksudo updates your sudo access
#               privs, so running nautilus with sudo will succeed
#               without asking for a password.


foo=`gksudo -u root -k -m "enter your password for nautilus root access" /bin/echo "got r00t?"`
sudo nautilus --no-desktop $NAUTILUS_SCRIPT_CURRENT_URI
```

---

### Post by g33zr on 2016-11-19
Thanks, Irv. I need to digest this a bit since the script didn't work the first couple of times.

---

### Post by deadflowr on 2016-11-19
Install nautilus-admin.
```
sudo apt install nautilus-admin
```
then when installed quit nautilus (nautilus -q)
and restart the file manager. 
An option to edit or open as administrator will now show in the right click options.

---

### Post by irv on 2016-11-19
Maybe you should just install a program wallch in the software center.

---

### Post by g33zr on 2016-11-19
Many thanks deadflower. Installing nautilus-admin worked. I should have thought of it before posting. #-o

---

### Post by oldrocker99 on 2016-11-19
Welcome to the forums! 

Your problem is solved, so please use Thread Tools to mark this thread as [SOLVED].

---

