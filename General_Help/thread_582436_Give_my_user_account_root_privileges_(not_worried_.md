---
title: "Give my user account root privileges (not worried about security)"
date: 2007-10-19
forum: General Help
---

### Post by tbrown11 on 2007-10-19
I'm looking for someone to point me to the proper file which I can edit my user ID to give myself root control over my entire PC (ie. no need for passwords to write/edit/install/remove/etc.). After installing Feisty months ago, I had found the answer to this on google, but after a fresh install of Gutsy yesterday I of course cannot find it this time. Once again I do not care about the security concerns, I am willing to risk my data (it is only a computer after-all). Thanks for any help you can provide! :)

---

### Post by mdurham on 2007-10-19
why not just use root?

---

### Post by jordanmthomas on 2007-10-19
Look into running visudo.  I believe your answer is near the bottom of it.
```
sudo visudo
```

find this:
```
# Same thing without a password
# %wheel        ALL=(ALL) NOPASSWD: SETENV: ALL

```
press i to enter edit mode, and delete the hash mark from the %wheel line.  Then, hit esc and then :wq <enter>

---

### Post by bodhi.zazen on 2007-10-19
Reference : [http://www.gratisoft.us/sudo/man/sudoers.html](http://www.gratisoft.us/sudo/man/sudoers.html)

---

### Post by tbrown11 on 2007-10-19
mdurham: tried root at one point, just makes organization easier by having the user folders, settings, etc.


jordan, I couldn't find the code you had listed, so here is the contents of the file:

```
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
# Defaults

Defaults        !lecture,tty_tickets,!fqdn

# Uncomment to allow members of group sudo to not need a password
# %sudo ALL=NOPASSWD: ALL

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root    ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

tommy   ALL=(ALL) NOPASSWD: ALL
```

---

### Post by jordanmthomas on 2007-10-19
Ahh, Ubunt's sudoer file must be different than mine.
You can add that line at the end, although it already looks like you don't need a password.

Check out bodhi.zazen's link, it should help you out.

---

### Post by bodhi.zazen on 2007-10-19
Look ... up ... in ... the ... file ...

> # Uncomment to allow members of group sudo to not need a password
# %sudo ALL=NOPASSWD: ALL

Change this to :

```
# Uncomment to allow members of group sudo to not need a password
%sudo ALL=NOPASSWD: ALL
```

add yourself to the group "sudo", log out and back in ...

Or :

```
tommy ALL=NOPASSWD: ALL
```

---

### Post by tbrown11 on 2007-10-20
Thanks for all of your help jordan and bodhi. I uncommented the line and it seems to have worked. Interestingly, I first tried your 2nd suggestion and upon restart, the gnome settings daemon failed, leaving me with a Windows safe-mode-like plain desktop. All went back to normal after reverting the file back. Thanks again... the great wealth of community knowledge is what made me settle with Ubuntu after recently making the jump from Windows :)

---

