---
title: "NOPASSWD doesn't work?"
date: 2007-07-11
forum: General Help
---

### Post by phile on 2007-07-11
I'm trying to set up a script containing a sudo command to mount a share on a NAS disc. I want to set it up so it will run without asking for a password. Digging around these forums, I find lots of help about editing the sudoers file which I have tried. Unfortunately, the script still refuses to run without a password.

My edited sudoers file goes like this:

```
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root
#
# See the man page for details on how to write a sudoers file.
# Host alias specification

# User alias specification

# Cmd alias specification

# Defaults

Defaults        !lecture,tty_tickets,!fqdn

# User privilege specification
root    ALL=(ALL) ALL

#Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

# My alteration
philip ALL = (root) NOPASSWD: /home/philip/Scripts/MountLinkstation

```
Now according to all the help I can find, this should work. But it doesn't... If I run the script ("MountLinkstation") out-of-terminal, nothing happens and if I run it in-terminal, I get asked for a password.

philip is a member of the admin group, but I have tried setting this up with another user who is not, and that gave exactly the same results.

I specifically want to get this working so that I only grant NOPASSWD rights to this script (ie not elevating all members of %admin to NOPASSWD or whatever). Can anyone think of anything I have missed that might explain why NOPASSWD doesn't work for me?

Ubuntu 7.04, by the way.

Phil

---

### Post by kerry_s on 2007-07-11
because " philip " is not the script, there's also to many spaces. Also there are caps in the name.

mv /home/philip/Scripts/MountLinkstation /home/philip/Scripts/nas

```
%nas ALL=(root) NOPASSWD: /home/philip/Scripts/nas
```

in terminal

```
sudo addgroup nas

gksudo gedit /etc/group

```

now add " philip " to the " nas " group

---

### Post by phile on 2007-07-12
Many thanks for your help! I tried that exactly as you show, but that doesn't work either - I get the same result as before (asked for a password in terminal, nothing happens out of terminal).

One other thing: I find it does work if I have previously made administrative changes (for example, fiddled with network settings) and in so doing, had to give my password. Is this of relevance?

Edit: one more thing. Typing sudo -l gives the following response:

```
User philip may run the following commands on this host:
     (ALL) ALL
     (root) NOPASSWD: /home/philip/scripts/nas
```

Note I've altered the 'Scripts' directory to 'scripts'

Phil

---

### Post by phile on 2007-07-12
_

---

### Post by kerry_s on 2007-07-12
okay, try moving it to /usr/bin, i'm guessing the permissions on the script are your's instead of root, which might be throwing it off. other than that it should work, i run several no password apps.

---

### Post by kerry_s on 2007-07-12
you know i been thinking about your script, if it needs to be run as root you should just put it in /usr/bin and have it auto-launched with /etc/rc.local which runs as root at boot.no permissions/passwords needed.

i just saw you snuck a post in on me. :)

you can just use the session startup, you simply use a different named script.
if you want only it to only launch for certain people, then yes the session startup and sudoers is the way to go.

okay now your post disappeared, are you playing with me. :)

---

### Post by phile on 2007-07-12
> **kerry_s said:**
> okay now your post disappeared, are you playing with me. :)

yes, sorry about that! I thought I'd turned something up, but I was wrong (again...)

Yes, I do want separate startup scripts for two users, so I have to go with the sudoers and sessions thing.

I tried putting the script in usr/bin. Still no luck. I even changed the owner to root and that didn't work either.

There is clearly something most mysterious going on here.

The script itself issues a "sudo mount -t cifs blah-de-blah" command. Not sure if that is of any relevance. It's a plain text file that is set to be executable (flag set from a dialogue on Nautilus).

Phil

---

### Post by kerry_s on 2007-07-12
> "sudo mount -t cifs blah-de-blah" 

if it has permissions with in the file already, that certainly affect's how you run it.
can you post the script?

for example from what you posted there that would make it ask for a password. you would be better off just making your own script. something like>

```
#!/bin/sh
mount -t cifs://workgroup;Username:Password@IPorDNS/profile 

or if your using smb

#!/bin/sh
mount volume "smb://username:password@192.168.1.10/share"
```

---

### Post by phile on 2007-07-12
OK, the script I'm trying to run is:

```
sudo mount -t cifs //192.168.0.200/box /media/Box -o credentials=/home/philip/.smbcredentials,iocharset=utf8,file_mode=0777,dir_mode=0777
```

I got all this from various other forum postings... is a little knowledge a dangerous thing? :)

Phil

---

### Post by phile on 2007-07-12
Well, I tried those scripts (adapted of course). If I leave out sudo at the start of the second line, I get a message saying "mount: only root can do that". If I put the sudo in, I get asked for a password, just as before.

Hint of frustration creeping in... All I want to do is mount an individual network share at login, based on which user it is. It shouldn't be this difficult..

Ho hum

Phil

---

### Post by phile on 2007-07-12
One more thing: if I grant myself silly privileges with the following:

philip ALL=(ALL) NOPASSWD: ALL

Then the script runs fine. So it's not that NOPASSWD is being ignored - there's some interaction going on between the NOPASSWD tag and the script specification in the sudoers file.

---

### Post by kerry_s on 2007-07-12
> **phile said:**
> Well, I tried those scripts (adapted of course). If I leave out sudo at the start of the second line, I get a message saying "mount: only root can do that". If I put the sudo in, I get asked for a password, just as before.

Hint of frustration creeping in... All I want to do is mount an individual network share at login, based on which user it is. It shouldn't be this difficult..

Ho hum

Phil

if you take the "sudo" out you need to run it from /usr/bin you copy the program as root, that way it's a root file then the sudoers will work.

> philip ALL=(ALL) NOPASSWD: ALL

using that wont ask for password anywhere, it's almost like running as root full time.

---

### Post by phile on 2007-07-13
Yup, done all that. Still no dice. I even re-installed ubuntu in case some obscure setting had got messed up somewhere. Still doesn't work - the problem persists exactly the same.

Well, I give up. Thanks for your help kerry_s, but it looks like this ain't gonna fly, at least not on this particular box. Linux for humans, my ***. There should be a gui method for setting this kind of thing up by now. It's not like it's an uncommon thing to want to do...

Phil

Edit: just noticed my outburst got auto-censored. What I meant to say, was: Linux for humans, my donkey. Or something like that.

---

### Post by scxtt on 2007-07-13
try it like this:
```
%nas          ALL=(ALL)       NOPASSWD: sudo /home/philip/scripts/nas
```

---

### Post by kerry_s on 2007-07-13
I give up too! :lolflag:

---

