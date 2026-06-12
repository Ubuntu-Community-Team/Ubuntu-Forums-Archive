---
title: "Want to stop and start minecraft server from a webserver..."
date: 2012-10-23
forum: General Help
---

### Post by fizgig on 2012-10-23
So I've got minecraft server running fine on my headless ubuntu server installation.  I have a minecraft-server.conf file in me /etc/init folder so I start it with "service minecraft-server start" or stop it similarly but I can only do that as root.

On my internal web site (not accessible from the outside world) I have a link to a script that trys to start the service and a link to another script that trys to stop the service using the commands above.  Again, those scripts work great if I run them as root.

Trouble is, I'd like apache (running as www-data) to be able to run those scripts as well which means www-data needs permission to start and stop that one service.

Anyone know how to do that?  Googling around seems to indicate that I can modify my sudoers file.

For testing, I added the line:

```
username ALL = NOPASSWD: /usr/bin/service
```which would theoretically give all service permissions to everyone which I don't want to do in the end but will at least let me test the concept.  That line doesn't work.  I'm out of ideas.

---

### Post by Cheesemill on 2012-10-23
The syntax of your sudoers edit is wrong.

You could try adding the following ***to the bottom*** of your sudoers file:
```
www-data ALL=(ALL) NOPASSWD: /usr/bin/service minecraft-server
```This should let the www-data user run only the command 'sudo service minecraft-server' (with either start or stop afterwords) without a password.

Remember that you still need to use sudo in front of the command, you just don't get prompted for a password.

---

### Post by fizgig on 2012-10-23
Thank you for your suggestion.  I changed the line to match yours.  I then switched to user www-data and tried "sudo service minecraft-server start" from the prompt but I was asked for a password.

I did a "which service" command to find that the service command appears to reside in /usr/sbin/service so I modified the command accordingly but I still get the password request.  I don't know what the password is for www-data and I suppose it doesn't matter since a request will stop apache from going forward anyhow.

Any other suggestions?

---

### Post by Cheesemill on 2012-10-23
Can you post the contents of your sudoers file please.

---

### Post by fizgig on 2012-10-23
Sure!

> # /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

Defaults        env_reset

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root    ALL=(ALL) ALL

# Allow members of group sudo to execute any command after they have
# provided their password
# (Note that later entries override this, so you might need to move
# it further down)
%sudo ALL=(ALL) ALL
#
#includedir /etc/sudoers.d

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL



www-data ALL = (ALL) NOPASSWD: /usr/sbin/service minecraft-server

Error =
> start: Rejected send message, 1 matched rules; type="method_call", sender=":1.53" (uid=33 pid=20361 comm="start) interface="com.ubuntu.Upstart0_6.Job" member="Start" error name="(unset)" requested_reply=0 destination="com.ubuntu.Upstart" (uid=0 pid=1 comm="/sbin/init))

---

### Post by steeldriver on 2012-10-23
This is well above my paygrade really but I *think* your issue may be that 'start' and 'stop' are not simple parameters to the /usr/sbin/service command, but are commands in their own right

```
$ which {start,stop}
/sbin/start
/sbin/stop
```So you may find that you need to give the complete command in sudoers

```
... NOPASSWD: /usr/bin/service minecraft-server **start**
```Probably you won't need a separate entry for the service stop command because both start and stop are symlinked to /sbin/initctl afaik

---

### Post by fizgig on 2012-10-23
Fascinating.  Never noticed that symlink...

Adding the word "start" made it work. I did have to have a similar entry for the stop command.  No big deal though.

Thank you all for your help!

---

