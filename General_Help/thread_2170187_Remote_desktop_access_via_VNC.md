---
title: "Remote desktop access via VNC"
date: 2013-08-25
forum: General Help
---

### Post by Abaminog on 2013-08-25
Hello!

Here is what I am trying to achieve... I have 2 Ubuntu laptops on a local wireless network (both connected to Internet via a router). They have their assigned IP addresses 192.168.1.XXX ('CLIENT') and 192.168.1.YYY ('SERVER'). I want to be able to access the Unity desktop run by user USER on SERVER via connecting to it from CLIENT. This can be needed for diagnostics or assistance with ongoing tasks. In other words, I need remote desktop monitoring and control.

There are lots of publications on this forum and on the Internet generally on how this can be achieved. But unfortunately the advice is sometimes a bit controversial and an exact sequenceof actions/commands not always given. I want to be able to get this done in a simple way without having to dig deep down into the Linux configuration aspects. This is how I would ideally see this working:

1. On SERVER I install x11vnc via         sudo apt-get install x11vnc
2. Question: Do I need to initialise/launch the VNC server on SERVER once it's installed? Or is it done automatically?
3. I use Remmina Remote Desktop client included in the standard Ubuntu distro (I have it in mine anyway) to connect to the running VNC server and access the USER's running desktop.

Is this all that it needed or are there any other tricks that need to be taken into account? Why does it have to be more complicated than this? Please note that I am not concerned with complex network security issues etc. I'd rather get it working first in a simplest possible way and then move on to more advanced things.

A word of advice would be greatly appreciated. Thanks!

---

### Post by steeldriver on 2013-08-25
At least from 12.04, a Vino server is installed as part of the regular Ubuntu desktop - so it shouldn't even be necessary to install x11vnc. Just go to the dash, select 'Desktop Sharing', and click the check boxes. Then fire up Remmina on the other box and enter the server details.

---

### Post by Abaminog on 2013-08-25
Thanks, Steeldriver! Very helpful suggestion. I tried and it worked... well, almost. When I try to connect to one of the users (incidentally, a member of the admin group), I can see and control the desktop remotely via VNC connection. But when I try to connect to 'simple' users with no admin rights, all I can see is a blank black screen, although the connection is established. It's the same effect as if I am connecting to an admin user who is currently not logged in or whose desktop is not active. I wonder if this is to do with the rights of non-admin users to use the VNC server (?) I have ticked the necessary boxes in the Desktop Sharing menu. So not all so simple...

---

### Post by hmandmpsaunders on 2013-08-26
I use 

ssh -CX username@ipaddress of local server
gnome-session --session=ubuntu-2d

Works very well for me

---

### Post by Abaminog on 2013-08-26
> **hmandmpsaunders said:**
> I use 

ssh -CX username@ipaddress of local server
gnome-session --session=ubuntu-2d

Works very well for me

Thank you. But isn't it right that the way you proposed is meant to launch a new X-session on a remote host instead of getting access to the already running X desktop and taking control over it? I am looking to achieve the latter.

---

### Post by steeldriver on 2013-08-26
did you remember to uncheck the 'You must confirm each access to this machine' box for the unprivileged user? otherwise the remote connection *will* hang at a black screen until the user on the active desktop accepts it

---

### Post by Abaminog on 2013-08-26
> **steeldriver said:**
> did you remember to uncheck the 'You must confirm each access to this machine' box for the unprivileged user? otherwise the remote connection *will* hang at a black screen until the user on the active desktop accepts it

Yes, it is unchecked

---

