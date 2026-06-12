---
title: "Problems with gui-permission elevation"
date: 2013-11-01
forum: General Help
---

### Post by kveldulfur on 2013-11-01
Hi, I have several machines running Ubuntu 12.04 and they need to authenticate via AD, and we are using PBIS to achieve this.

Users can log in, and users in the AD sudoers group have sudo and everything appears to work fine, until a network user, say bob, who is in the sudoers file and can run sudo commands via terminal without  problems tries to install software via the ubuntu software center. The prompt asks for the password for a local sudoers account (systemuser) set up so that the machine can be administered in case of network failure.

So the question is: how can I get the gui password prompt to ask bob for bobs sudo password instead of systemusers?

Another question: the terminals are supposed to use UTF-8 encoding, but they default to ansi encoding, and gnome terminal options wont let me remove ansi, or set UTF-8 as default. I resorted to putting the following in .bashrc, with no luck:
```
export LANG="en_US.UTF-8"
export LANGUAGE="en_US:en"
export LC_CTYPE="en_US.UTF-8"
export LC_NUMERIC="en_US.UTF-8"
export LC_TIME="en_US.UTF-8"
export LC_COLLATE="en_US.UTF-8"
export LC_MONETARY="en_US.UTF-8"
export LC_MESSAGES="en_US.UTF-8"
export LC_PAPER="en_US.UTF-8"
export LC_NAME="en_US.UTF-8"
export LC_ADDRESS="en_US.UTF-8"
export LC_TELEPHONE="en_US.UTF-8"
export LC_MEASUREMENT="en_US.UTF-8"
export LC_IDENTIFICATION="en_US.UTF-8"
export LC_ALL=

```Yes, that is a terrible terrible fix, and I feel appropriately bad for having considered it, (doubly so because it doesn't even seem to work), but there is a shockingly small amount of information about this problem out there.

---

### Post by jamesisin on 2014-10-22
I too am seeing this issue in an Ubuntu 14.04.1 64 bit machine attached to AD.

I can sudo and gksudo as expected but when the gui spawns the elevation dialog it is tied to the local admin account.

So if I click the icon for Synaptic I get a dialog specifically requesting the password for the local administrator account.  However, if I hit the terminal and type *gksudo synaptic* I get the gksudo dialog where I can enter my user credentials and thus open Synaptic.

I know I sorted this out on a previous installation, but I can't remember what I did back then.

---

