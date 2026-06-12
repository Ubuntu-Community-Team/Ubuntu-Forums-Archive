---
title: "[SOLVED] sudo still requires password"
date: 2007-12-26
forum: General Help
---

### Post by apanloco on 2007-12-26
I have searched but not found a solution to this. I am trying to allow sudo without password for a user. I have uncommented a line in /etc/sudoers that should allow this, and I am in the "sudo" group. Still no go. And yes I have even restarted the computer. As you see the "uncomment to allow..." line is uncommented...

da@brutus:~$ sudo cat /etc/sudoers
[sudo] password for da:
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
# Defaults

Defaults        !lecture,tty_tickets,!fqdn

# Uncomment to allow members of group sudo to not need a password
%sudo ALL=NOPASSWD: ALL

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root    ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL



and I am in the sudo group:

da@brutus:~$ groups
da adm dialout cdrom floppy sudo audio dip video plugdev scanner lpadmin admin netdev powerdev mythtv smb


I can't figure it out, please help!

/A

---

### Post by InGunsWeTrust on 2007-12-26
I went through the process of changing the sudo file to allow sudo with no password and I noticed a few weird things that may have caused you to trip up and not get the result that you want. First you MUST heed the warning to use the visudo command to edit the sudoers file. Second you must press Ctr + O to save the file. When it wants to save the file notice the filename that it wants to save it as: /etc/sudoers.tmp you simply want to save it as /etc/sudoers not /etc/sudoers.tmp so delete the .tmp off the end of the file name. It will say the file already exists and ask if you want to overwrite it. Press Y for yes. I don't know if you have to restart or not after that but it should work and allow you to sudo without a password.

---

### Post by apanloco on 2007-12-27
I do use "sudo visudo" to edit the file. I do save it. I should have been more clear...

Could it be that I am both in group "admin" _and_ in group "sudo", and thus the "admin"-rule overrides the "sudo"-rule and prompts me for password? Haven't tried this, I am at work.

Also the reason you have to use "visudo" is because it does syntax checking after copying the file over /etc/sudoers so you don't screw up your system by a small mistake.

(I use Kubuntu 7.10.)

/A

---

### Post by rich.bradshaw on 2007-12-27
Why would anyone want to do this?

---

### Post by apanloco on 2007-12-27
This is a first step in a more complicated sudoers setup. I just want to make sure that my changes go in effect, and they surely don't.

(Answer two: Just because you don't... :) )

/D

---

### Post by Joshua Swink on 2007-12-27
I was looking at `man visudo`, and behold:

[INDENT]       When multiple entries match for a user, they are applied in order.  Where there are con&#8208;
       flicting values, the last match is used (which is not necessarily the most specific
       match).
[/INDENT]

The last rule to match your user was the admin group, so the "%sudo ALL=NOPASSWD: ALL" rule was overridden.

---

### Post by apanloco on 2007-12-27
Thank you very much :) I wonder, are you guys not in "admin" group? ... Why am I? Put me there myself?

Problem solved...

/A

---

