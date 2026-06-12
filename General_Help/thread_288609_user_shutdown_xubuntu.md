---
title: "user shutdown xubuntu"
date: 2006-10-30
forum: General Help
---

### Post by hulluPeruna on 2006-10-30
Hi 
I am running mythtv on Xubuntu installing hardware and mythtv was no challenge ( thanks to the ubuntu team !!!). But I spend the better part of the weekend trying to enable a normal user to shutdown the machine via a script. ](*,) The script is called from the remote control!  
The script is no problem but giving the user the right to shutdown does not seem to be so easy.
I went for the sudo approach 
here my sudoer file :

# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
# Host alias specification

# User alias specification

# Cmnd alias specification
Cmnd_Alias      CMD_POWEROFF= /sbin/shutdown
# Defaults

Defaults        !lecture,tty_tickets,!fqdn

# User privilege specification
root    ALL=(ALL) ALL

mythtv  ALL=  NOPASSWD: CMD_POWEROFF

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

calling "shutdown" as mythtv user does not work with out password. If anybody bring some light in my dark world I be really thankful](*,) 

HP

---

