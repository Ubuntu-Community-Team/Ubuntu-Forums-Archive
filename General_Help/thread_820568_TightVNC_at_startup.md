---
title: "TightVNC at startup"
date: 2008-06-06
forum: General Help
---

### Post by esullivan on 2008-06-06
I installed TightVNC, but it will not accept connections until I login.  How can I set it to run as service?

---

### Post by sizzam on 2008-06-06
One way to do it is by way of the '/etc/rc.local' file.   The commands in that file will be run whenever the machine boots.    You could add a command to start tightvncserver as your username (above the 'exit 0' line) by doing this:

```
$ sudo gedit /etc/rc.local
```

```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

su yourusername -c "tightvncserver"

exit 0

```

---

### Post by esullivan on 2008-06-09
Didn't work, just for clarification when you put "tightvncserver" do I put THAT or path to it?

---

### Post by sizzam on 2008-06-09
Hmm, it works for me.   It should be 'tightvncserver', the path isn't needed because it lives in /usr/bin.

After reboot does this command return anything?
```
$ ps -ef|grep tightvnc
```

It probably spun it up on :1, so you would connect to it like this:
```
$ vncviewer localhost:1
```

You can specify the display number you want it to use by adding the number to the line in /etc/rc.local, for example:
```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

su yourusername -c "tightvncserver :20"

exit 0
```

By default the session is just a window with a terminal on it.   In the past I have used Fluxbox for my background VNC session:
```
$ sudo apt-get install fluxbox
```

And then configured the VNC session to use that via the ~/.vnc/xstartup with this in it:
```
#!/bin/sh

xrdb $HOME/.Xresources
xsetroot -solid grey
xterm -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &
startfluxbox &
```

---

### Post by esullivan on 2008-06-09
> **sizzam said:**
> 
After reboot does this command return anything?
```
$ ps -ef|grep tightvnc
```

Returned this:

beinet    6089  6071  0 14:04 pts/0    00:00:00 grep tightvnc

---

### Post by sizzam on 2008-06-09
Did you install tightvncserver from the repos?
```
$ sudo apt-get install tightvncserver
```

Can you post the contents of your /etc/rc.local file?

---

### Post by esullivan on 2008-06-09
```

#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

su BEINET -c "tightvncserver"

exit 0

```

---

### Post by sizzam on 2008-06-09
Just to make sure its not something simple, is your username 'BEINET' or 'beinet'?   When you open a terminal, does it say "BEINET@" or "beinet@"?

---

### Post by esullivan on 2008-06-09
> **sizzam said:**
> Just to make sure its not something simple, is your username 'BEINET' or 'beinet'?   When you open a terminal, does it say "BEINET@" or "beinet@"?

Yeah that's the username.  Can I put root?  I am in IT, just a BIG Linux guy.

---

### Post by sizzam on 2008-06-09
I wouldn't recommend having a VNC session to root.   What happens when you run this command from a terminal:
```
su BEINET -c "tightvncserver"
```

---

### Post by esullivan on 2008-06-09
It says unknown user, however I am looking in Users and Groups and I see it right there.

---

### Post by sizzam on 2008-06-09
Linux is case-sensitive.   Type it exactly as it appears before the @ symbol at your command prompt when you open a terminal, or exactly as it appears in Users and Groups under the 'Login Name' column.  If its all lower-case, use lower-case letters.

---

### Post by esullivan on 2008-06-09
ok I did su beinet -c "tightvncserver" and it had me set a password.

Now when I do that it has me enter the user password then says
```

beinet@beinet:~$ su beinet -c "tightvncserver"
Password: 

New 'X' desktop is beinet:2

Starting applications specified in /home/beinet/.vnc/xstartup
Log file is /home/beinet/.vnc/beinet:2.log

```

---

### Post by sizzam on 2008-06-09
That command should now work from the /etc/rc.local file.  If the terminal that you get by default in your VNC session is not sufficient, check out my previous post regarding Fluxbox.  Its nice and lightweight, works pretty well in a VNC session.

---

### Post by esullivan on 2008-06-09
Ok so I can login but just the terminal, I'll look into the post you mentioned before.

Thanks for the help man!

---

